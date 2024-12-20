---
layout: post-custom
title: "Spring条件注解-@ConditionalOnProperty的使用"
---

`@ConditionalOnProperty` 是 Spring Boot 框架中的一个条件注解，用于根据配置文件中的属性值来决定是否加载某个 Bean 或者配置类。

## 使用场景
1. **多环境配置**：根据不同的环境（如开发、测试、生产）启用不同的 Bean。
2. **特性开关**：通过配置文件控制某些特性的开启或关闭。
3. **模块化配置**：允许用户通过配置文件选择性地加载某些模块或组件。

## 基本语法
`@ConditionalOnProperty`的定义源码如下：

```java
@Retention(RetentionPolicy.RUNTIME)
@Target({ElementType.TYPE, ElementType.METHOD})
@Documented
@Conditional({OnPropertyCondition.class})
public @interface ConditionalOnProperty {
    //Alias for name().
    String[] value() default {};
    //属性前缀，比如：app.config
    String prefix() default "";
    //属性名称。如果prefix已经定义，那么它会被应用为每个前缀的完整键。
    //比如prefix=app.config，name=my-long-property，那么完整键就是app.config.my-long-property
    String[] name() default {};
    // 期望的属性值
    String havingValue() default "";
    // 如果配置中不存在该属性时的行为，默认为 false
    boolean matchIfMissing() default false;
}
```

从上述代码定义能看到`@ConditionalOnProperty`是被`@Conditional(OnPropertyCondition.class)`标记的：
- 被`@Conditional()`标记的注解表示该注解是个条件注解。
- `@Conditional()`的`value`值对应该注解的具体实现逻辑。

### 参数说明

|参数|说明|
|---|---|
|`prefix`|属性的前缀，默认为`""`。|
|`name`|属性名称，默认为`{}`。|
|`havingValue`|期望的属性值，默认为`""`。|
|`matchIfMissing`|如果配置中不存在该属性时的行为，默认为`false`，即属性不存在时不匹配。|


## 示例
### 1.简单示例
假设我们有个服务类`TestService`，希望根据配置文件中的`switch.test-service.enabled`属性来决定是否创建这个Bean。

配置文件内容如下：
```
# application.properties
switch.testservice.enabled=true
```

代码实现如下:
```java
@Service
@ConditionalOnProperty(prefix = "switch.testservice", name = "enabled", havingValue = "true")
public class TestService {
    public void test() {
        System.out.println("TestService is running...");
    }
}
```

该示例中当`switch.test-service.enabled=true`时，`TestService`才会被创建并注入到Spring容器中。

### 2.缺省值处理
如果我们希望在配置文件中没有定义某个属性时，默认启用某个 Bean，可以使用 `matchIfMissing=true`。

```java
@Service
@ConditionalOnProperty(
    prefix = "switch.testservice", name = "enabled", havingValue = "true",
    matchIfMissing = true
    )
public class TestService {
    public void test() {
        System.out.println("TestService is running...");
    }
}
```

## 条件注解的种类
Spring有各种条件注解，常见的条件注解有：

|注解|说明|
|----|---|
|`@ConditionalOnProperty`|如果有指定的配置，条件生效|
|`@ConditionalOnBean`|当容器中存在某个Bean时,条件生效|
|`@ConditionalOnMissingBean`|如果没有指定的Bean，条件生效|
|`@ConditionalOnClass`|当类路径下存在某个类时,条件生效|
|`@ConditionalOnMissingClass`|如果没有指定的Class，条件生效|
|`@ConditionalOnExpression`|根据表达式判断条件是否生效|


