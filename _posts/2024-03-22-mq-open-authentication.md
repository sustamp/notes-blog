---
# layout: post
layout: post-custom
title: "ibmmq、activemq开启连接认证以及应用程序的修改"
---

## 说明

本次开启认证，中间件需要重启才能生效。相关客户端程序需要追加认证代码进行调整。

我们拟定的生产上线步骤是：

1. 先制定ibmmq、activemq开启认证所配置的账号/密码，并告知开发以调整应用程序的配置。
2. 开发需要修改程序，在连接mq时追加认证需要的相关代码，并先行发布上线。观察功能是否正常。mq不开启认证时，程序连接附加的认证代码不会影响使用。
3. ibmmq、activemq 调整配置开启认证，并重启使之生效。
4. 开发检查程序功能是否正常。

## IBM Websphere MQ队列管理器开启认证

本文为Ibmmq开启连接认证CONNAUTH，并指定认证信息为：`AUTHINFO(SYSTEM.DEFAULT.AUTHINFO.IDPWOS)`对象

AUTHINFO的AUTHTYPE为`IDPWOS`模式，该模式为在操作系统层面进行用户连接认证。

认证的用户和密码其实就是安装MQ的服务器上的"系统账号"（保险起见，该账号也划入mqm用户组）。

> **请注意:**IBMMQ对用户标识的设定有长度限制。在 z/OS® 和 UNIX 和 Linux®上，用户> 标识的最大长度为 12 个字符。

所以我们在设定**账号密码**时，**长度不要超过12个字符**。

相关说明参考文档：<a href="https://www.ibm.com/docs/zh/was/9.0.5?topic=server-mq-connection-authentication" target="_blank">https://www.ibm.com/docs/zh/was/9.0.5?topic=server-mq-connection-authentication</a>


### 添加操作系统用户

Ibmmq的服务端安装在linux服务器上，故在该服务器上新增一个用户，相关指令如下：

```shell
# 添加一个用户：mquser，你也可以输入别的用户名。
useradd mquser
# 键入密码。请记住密码，连接ibmmq时需要输入用户名和密码
passwd mquser
# 划入mqm用户组
usermod -G mqm mquser
# 调整权限
chage -M 99999 mquser
```

### 开启队列管理器的连接认证

1. 登录ibmmq的安装服务器，并从root用户切换至mqm用户：
    
    ```shell
    su - mqm
    ```

2. 切换至ibmmq安装目录，并进入相应队列管理器的命令控制端：

    ```shell
    cd /opt/mqm/bin

    ./runmqsc QMORDER
    ```

    > **注意**：QMORDER为队列管理器的名称，请确认该名称在生产环境是否一致。

3. 进入命令行后，继续输入如下指令调整队列管理器的认证信息：

    ```shell
    ALTER QMGR CONNAUTH(SYSTEM.DEFAULT.AUTHINFO.IDPWOS)
    ```

4. 刷新配置

    ```shell
    REFRESH SECURITY TYPE(CONNAUTH)
    ```

5. 重启队列管理器

    ```shell
    # 输入end 或Ctrl + C 退出命令行

    # 在安装目录：/opt/mqm/bin下停止队列管理器
    ./endmqm testorder

    # 上述步骤无效可尝试强制关闭./endmqm -p testorder

    # 重新启动队列管理器
    ./strmqm testorder
    ```

以上步骤正常完成后，ibmmq认证开启已生效。

**NOTE：其他辅助指令（需要在命令行控制端使用）**

```shell
# 用于显示所有认证信息的内容
DISPLAY AUTHINFO() 
# 显示指定名称的认证信息的内容
DISPLAY AUTHINFO(识别名) 
# 显示当前队列管理器的信息
DISPLAY QMGR 
# 关闭连接认证，调整后要刷新配置，并重启队列管理器
ALTER QMGR CONNAUTH(NONE) 
```

### 应用程序调整

#### 1.java应用程序调整
##### 1.1场景1-使用java配置类进行ibmmq连接工厂初始化的
示例代码：

```java
	//创建主题工厂
	@Bean("ibmMqTopicConnectionFactory")
	public MQTopicConnectionFactory ibmMqTopicConnectionFactory() throws Exception{
    	MQTopicConnectionFactory mqTopicConnectionFactory = new MQTopicConnectionFactory();
    	//客户机自动重连的设置
    	mqTopicConnectionFactory.setTransportType(WMQConstants.WMQ_CM_CLIENT);
    	mqTopicConnectionFactory.setHostName(ibmmqProperty.getHost());
    	mqTopicConnectionFactory.setPort(ibmmqProperty.getPort());
    	mqTopicConnectionFactory.setChannel(ibmmqProperty.getChannel());
    	return mqTopicConnectionFactory;
	}

	//创建用户认证对象
	@Bean("ibmUserCredentialsConnectionFactoryAdapter")
	UserCredentialsConnectionFactoryAdapter userCredentialsConnectionFactoryAdapter(MQTopicConnectionFactory mqTopicConnectionFactory) throws Exception{
    	UserCredentialsConnectionFactoryAdapter userCredentialsConnectionFactoryAdapter = new UserCredentialsConnectionFactoryAdapter();
    	userCredentialsConnectionFactoryAdapter.setTargetConnectionFactory(mqTopicConnectionFactory);
    	if (StringUtils.isNoneBlank(ibmmqProperty.getUserId())) {
        	userCredentialsConnectionFactoryAdapter.setUsername(ibmmqProperty.getUserId());
        	userCredentialsConnectionFactoryAdapter.setPassword(ibmmqProperty.getUserPwd());
    	}
    	return userCredentialsConnectionFactoryAdapter;
	}

	//创建缓存连接工厂
	@Bean("ibmCachingConnectionFactory")
	public CachingConnectionFactory ibmCachingconnectionFactory(UserCredentialsConnectionFactoryAdapter userCredentialsConnectionFactoryAdapter){
    	CachingConnectionFactory cachingConnectionFactory = new CachingConnectionFactory();
    	cachingConnectionFactory.setTargetConnectionFactory(userCredentialsConnectionFactoryAdapter);
    	//设置ClientID,此操作需要在建立Connection之后,未使用Connection进行任何实际操作之前(包括创建session)进行;否则将会抛出异常.因为clientID是JMS server用来唯一标记链接的,因此在全局中不能重复
    	cachingConnectionFactory.setClientId(ibmmqProperty.getClientId());
    	cachingConnectionFactory.setSessionCacheSize(SESSION_CACHE_SIZE);
    	cachingConnectionFactory.setReconnectOnException(true);
    	return cachingConnectionFactory;
	}

	//创建JMS模板
	...
	//创建JMS监听器
	...
```    

##### 1.2 场景2-使用mvc-xml配置文件进行ibmmq连接工厂初始化的
与2.1类似，在现有节点基础上增加一个认证对象的节点，然后将其注入缓存工厂节点。

```xml
	<!-- 创建主题对象的链接工厂 -->
    <bean id="ibmJmsConnectionFactory" class="com.ibm.mq.jms.MQTopicConnectionFactory">
		<property name="hostName" value="127.0.0.1"/>
        <property name="port" value="20000"/>
        <property name="queueManager" value="QMORDER"/>
        <property name="channel" value="SVRCONN.GENERAL"/>
        <!--消费者标示id -->
        <property name="clientId" value="savenner-monitor" />
        <!--设置连接方式：MQJMS_TP_CLIENT_MQ_TCPIP支持自动重连？ -->
        <property name="transportType"> 
            <util:constant static-field="com.ibm.mq.jms.JMSC.MQJMS_TP_CLIENT_MQ_TCPIP" />
        </property> 
    </bean>


	<!-- 创建认证对象 -->
    <bean id="connectionCredentialsFactoryAdapter" class="org.springframework.jms.connection.UserCredentialsConnectionFactoryAdapter">
        <property name="targetConnectionFactory" ref="ibmJmsConnectionFactory"/>
        <property name="username" value="${IMB.mq.userName}"/>
        <property name="password" value="${IMB.mq.password}"/>
    </bean>

	<!-- 创建缓存连接工厂 -->
    <bean id="ibmQueueConnectionFactory" class="org.springframework.jms.connection.CachingConnectionFactory">
        <property name="targetConnectionFactory" ref="connectionCredentialsFactoryAdapter"/>
        <property name="sessionCacheSize" value="${IMB.mq.mqChannel.connectionFactory.sessionCacheSize}"/>
        <property name="reconnectOnException" value="${IMB.mq.reconnection}"/>
    </bean>
```

*NOTE：上述方式未经验证，请自行使用并测试*。

#### C#应用程序调整
完善MQQueueManager构造器的properties参数，添加用户账号、密码的参数。示例代码如下：

```csharp
Hashtable properties = new Hashtable();
properties.Add(MQC.HOST_NAME_PROPERTY, $address);
properties.Add(MQC.PORT_PROPERTY, int.Parse($port));    
properties.Add(MQC.CHANNEL_PROPERTY, $channel);
//2024-01-18 增加用户密码认证
properties.Add(MQC.USER_ID_PROPERTY, "mquser");
properties.Add(MQC.PASSWORD_PROPERTY, "your_paassword");
MQQueueManager myQueueManager = new MQQueueManager(sQMgrName, properties);
MQTopic mqTopic = myQueueManager.AccessTopic(...)
//后续代码省略...
```

## Activemq开启认证

### 修改activemq.xml
修改 activemq安装目录/conf/activemq.xml文件，在其中的broker节点中插入一个子节点，如下：

```xml
<!-- add a user to set connection authentication  -->
<plugins>
    <simpleAuthenticationPlugin>
        <users>
            <authenticationUser username="your_username" password="your_password" groups="users,admins"/>
        </users>
    </simpleAuthenticationPlugin>
</plugins>
```

更改完成后，重启activemq服务生效。

### 应用程序调整
#### 1.java应用程序调整
这里示例以mvc-xml格式注入Activemq的Bean工厂的配置方式，在连接工厂的节点增加账号属性userName, password即可：

```xml
<bean id="targetConnectionFactory" class="org.apache.activemq.ActiveMQConnectionFactory">
    <property name="brokerURL" value="failover:tcp://IP:PORT" />
    <property name="userName" value="your_username" />
    <property name="password" value="your_password" />
    <property name="transportListener">
        <bean class="plateno.push.rest.core.ActiveMQTransportListener"/>
    </property>
</bean>
```

#### 2.C#应用程序调整
1. activemq驱动的`IConnectionFactory`接口具备`IConnection CreateConnection(string userName, string password)`方法，按需要投递参数。

    ```csharp
    //初始化连接工厂
	IConnectionFactory objConnFactory = new ConnectionFactory(sUrl);
	IConnection objMQConn = objConnFactory.CreateConnection("your_username","your_password");
	ISession m_objMQSession = objMQConn.CreateSession();//使用事物化
	IMessageProducer objSendProducer = m_objMQSession.CreateProducer(new Apache.NMS.ActiveMQ.Commands.ActiveMQTopic(sTopic));
	//后续代码省略...
    ```

2. ConnectionFactory类本身具备UserName, Password属性，创建ConnectionFactory对象后设置这2个属性。