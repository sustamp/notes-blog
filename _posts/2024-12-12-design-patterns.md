---
layout: post-custom
title: "设计模式"
---

## 概述
设计模式(Design Pattern)是一套被反复使用、多数人知晓、经过分类的、代码设计经验的总结，使用设计模式是为了可重用代码、让代码更容易被他人理解并且保证代码可靠性。

设计模式的出现可以让我们站在前人的肩膀上，通过一些成熟的设计方案来指导新项目的开发和设计，以便于我们开发出具有更好的灵活性和可扩展性，也更易于复用的软件系统。

本文将对设计模式的内容分为如下部分：
1. 定义
2. 结构
3. 效果（优、缺点）
4. 适用场景

## 设计模式的分类及作用一览表

|类型|模式名称|作用|
|-|-|-|
|**创建型模式**|Creational Pattern|**关注对象的创建，为类的实例化提供方法**|
||单例模式|确保一个类只有一个实例，并提供全局访问点|
||简单工厂模式|提供一个工厂类，由参数决定如何实例化对象|
||工厂方法模式|定义创建对象的接口，但由子类决定实例化哪个类|
||抽象工厂模式|创建相关或依赖对象的家族，而不指定具体类|
||建造者模式|分步骤构建复杂对象，分离构造与表示|
||原型模式|通过复制现有对象来创建新对象，避免重复初始化|
|**结构型模式**|Structural Pattern|**关注类或对象的组合方式，优化结构的设计和拓展**|
||适配器模式|使不兼容的接口能够协同工作|
||桥接模式|将 抽象部分 与它的 实现部分 分离，使它们都可以独立地变化|
||组合模式|将对象组合成 树形结构 以表示“部分-整体”层次|
||装饰模式|动态地 为对象添加职责，避免子类爆炸|
||外观模式|为复杂子系统提供 统一的 简化接口|
||代理模式|为真实象提供一种代理以控制访问（如远程代理、虚拟代理）|
||享元模式|★★★★☆|★☆☆☆☆|
|**行为型模式**|Behavioral Pattern|**关注类或对象之间的通信和职责的分配，优化交互流程和算法**|
||模板方法模式|定义算法的骨架，将某些步骤延迟到子类实现|
||中介者模式|协调多个对象之间的交互，避免对象之间的耦合|
||策略模式|封装算法族，使其可以互相替换|
||观察者模式|定义对象间的一对多依赖，当一个对象状态改变时自动通知依赖者|
||职责链模式|让多个对象有序处理请求，避免耦合|
||命令模式|将请求封装为对象，支持撤销、队列等操作|
||解释器模式|★★★★★|★☆☆☆☆|
||迭代器模式|★★★☆☆|★★★★★|
||备忘录模式|★★☆☆☆|★★☆☆☆|
||状态模式|★★★☆☆|★★★☆☆|
||访问者模式|★★★★☆|★☆☆☆☆|

## 面向对象设计原则
面向对象设计需要解决的核心问题之一是如何同时提高一个软件系统的：
- **可维护性**
- **可复用性**

面向对象设计原则为支持可维护性复用而诞生，这些原则蕴含在很多设计模式中，它们是从许多设计方案中总结出的指导性原则。

面向对象设计原则也是我们用于评价一个设计模式的使用效果的重要指标之一。

### SOLID-CL设计原则
最常见的7种面向对象设计原则如下表所示:

|设计原则|定义|
|---|---|
|单一职责原则 (Single Responsibility Principle, SRP)|一个类只负责一个功能领域中的相应职责|
|开闭原则 (Open-Closed Principle, OCP)|软件实体应对扩展开放，而对修改关闭|
|里氏代换原则 (Liskov Substitution Principle, LSP)|所有引用基类对象的地方能够透明地使用其子类的对象|
|接口隔离原则 (Interface Segregation Principle, ISP)|使用多个专门的接口，而不使用单一的总接口|
|依赖倒转原则 (Dependence Inversion Principle, DIP)|抽象不应该依赖于细节，细节应该依赖于抽象|
|合成复用原则 (Composite Reuse Principle, CRP)|尽量使用对象组合，而不是继承来达到复用的目的|
|迪米特法则 (Law of Demeter, LoD)|一个软件实体应当尽可能少地与其他实体发生相互作用|

#### SRP(单一职责原则)
SRP(Single responsiblity principle)是最简单的面向对象设计原则，它用于控制类的粒度大小，简单定义为：
- 一个类或模块应该只负责一个职责或功能。

> 一个类不能太累！

单一职责原则告诉我们：
- 一个类（大到模块，小到方法）承担的职责越多，它被复用的可能性就越小。
- 承担职责过多的类，相当于职责耦合在一起，当其中一个职责变化时，可能会影响其他职责的运作，因此要将这些职责进行分离，将不同的职责封装在不同的类中。
- 如果多个职责总是同时发生改变则可将它们封装在同一类中。

单一职责原则是实现**高内聚**、**低耦合**的指导方针，它是最简单又最难运用的原。

设计人员需要发现类的不同职责并将其分离，而发现类的多重职责需要设计人员具有较强的分析设计能力和相关实践经验。

![SRP原则UML类图](https://sustamp.github.io/assets/pictures/design-patterns/UML-SRP.png)

#### OCP(开闭原则)
OCP(Open-Closed principle)是面向对象的可复用设计的第一块基石：
- 一个软件实体应当对扩展开放，对修改关闭。即软件实体应尽量在不修改原有代码的情况下进行扩展。

软件实体可以指一个软件`模块`、一个由多个`类`组成的局部结构或一个独立的`类`。

**抽象化**是开闭原则的关键：
- 通过`接口`、`抽象类`定义抽象层。
- 通过`具体实现类`进行拓展。

果需要修改系统的行为，无须对抽象层进行任何改动，只需要增加新的具体类来实现新的业务功能即可，实现在不修改已有代码的基础上扩展系统的功能，达到开闭原则的要求。

![OCP原则UML类图](https://sustamp.github.io/assets/pictures/design-patterns/UML-OCP.png)

#### LSP(里氏替换原则)
LSP(Liskov substitution principle)由2008年图灵奖得主、美国第一位计算机科学女博士Barbara Liskov教授和卡内基·梅隆大学Jeannette Wing教授于1994年提出。其严格表述如下：
- 如果对每一个类型为`S`的对象`o1`，都有类型为`T`的对象`o2`，使得以`T`定义的所有程序`P`在所有的对象`o1`代换`o2`时，程序`P`的行为没有变化，那么类型`S`是类型`T`的**子类型**。

简言之：
- 子类能够替换父类对象出现的任何地方，并且保证原来程序的逻辑行为不变。

LSP原则告诉我们，在软件中将一个基类对象替换成它的子类对象，程序将不会产生任何错误和异常，反过来则不成立，如果一个软件实体使用的是一个子类对象的话，那么它不一定能够使用基类对象。

**里氏代换原则**是实现**开闭原则**的重要方式之一，由于使用基类对象的地方都可以使用子类对象，因此在程序中尽量使用基类类型来对对象进行定义，而在运行时再确定其子类类型，用子类对象来替换父类对象。

使用LSP要注意如下几个问题：
- 尽量把父类设计为`抽象类`或`接口`，子类实现父类的所有方法。
- 增加新功能可以通过增加新的子类来实现，而无须修改原有子类的代码。

**举例**：在CRM(Customer Relationship Management)系统中，客户（Customer）可以分为VIP客户和普通客户，系统需要提供一个发送Email的功能。以下是UML类图示意：

![LSP原则UML类图](https://sustamp.github.io/assets/pictures/design-patterns/UML-LSP.png)

- 将`Customer`作为父类，`VIPCustomer`和`CommonCustomer`作为子类。
- 邮件发送`EmailSender`接受父类对象`Customer`作为参数，根据LSP原则，必然也能接受子类对象，它们都能被当做客户对象被处理。

在以下场景中都可使用LSP原则：
- 传递参数（*本示例*）
- 定义成员变量
- 定义局部变量
- 确定方法返回类型

#### ISP(接口隔离原则)
ISP(Interface Segregation Principle)定义：
- 使用多个专门的接口，而不使用单一的总接口，即客户端不应该依赖那些它不需要的接口

为各个类建立它们需要的专门接口，而不要试图去建立一个很庞大的接口供所有依赖它的类去调用。

举个例子，在CRM系统中可能具备如下功能：
- 从文件中读取数据
- 将数据转换为XML格式
- 图表显示
- 文字报表

当只使用一个接口实现上述功能时，如果具体的数据显示类不需要进行格式转换，那么它还是要实现xml格式转换功能(空实现)；如果数据显示类只是要创建和显示图表，那么它还要实现报表方法。


为此，应用ISP原则，将接口按职责划分成几个接口：
- 报表接口实现报表的相关方法，
- 图表接口实现图表显示相关的方法，
- 数据读取单独一个接口，
- 数据转换单独一个接口。

这样依赖，具体的显示类只要按需实现相关接口就行了，不用额外实现其他接口的方法。用UML类图示意如下：

![ISP原则UML类图](https://sustamp.github.io/assets/pictures/design-patterns/UML-ISP.png)


#### DIP(依赖倒置原则)
如果说开闭原则是面向对象设计的目标的话，那么依赖倒转原则就是面向对象设计的主要实现机制之一。它是**系统抽象化**的具体实现。

DIP(Dependency Inversion Principle)原则核心思想是：
- 高层模块不应该依赖底层模块，二者都应该依赖**抽象**。
- 抽象不依赖细节，细节应该依赖于**抽象**。

换言之：
- 针对`接口`编程，而不是针对实现编程。

传统的从上到下设计方式是逐级依赖，即`高层模块` -> `次级模块` -> `底层模块`。这样高层模块就依赖底层模块了，当某一模块需要修改，可能牵一发而动全身，影响较多不易维护。

而DIP是`高层模块` -> `抽象层` <- `底层模块`，使得它们同依赖抽象层，这样减少了类之间的耦合性，不同模块都可独立针对 `接口/抽象类` 进行并行开发，可维护性大大增加。

DIP要求我们在程序代码中传递参数时或在关联关系中，尽量引用层次高的抽象层类。即：
- 使用 `接口/抽象类` 进行 `变量类型`声明 、`参数类型`声明、`方法返回类型`声明及`数据类型的转换`等，而不要用具体类来做这些事情。

**举例**：司机需要不同的驾照才可以驾驶不同的载具，用UML类图表示DIP原则如下：

![DIP原则UML类图](https://sustamp.github.io/assets/pictures/design-patterns/UML-DIP.png)


实现DIP时我们针对抽象层编程，而将具体类的对象通过依赖注入的方式注入到其他对象中。

依赖注入(Dependency Injection，DI)是指：
- 当一个对象需要与其他对象发生依赖关系时，通过抽象来注入所依赖的对象。

常用的注入方式有三种：
- 构造函数注入
- 设值注入(Setter)
- 接口注入

其中接口注入是指在接口声明的方法中来传递对象，这些方法定义时使用的是抽象类型，运行时传入具体类型的对象。


> 思考： DIP原则和LSP原则的区别？

|设计原则|关注点|作用|
|---|---|---|
|DIP|模块间的依赖关系|减少模块间的耦合度，从而提高系统的灵活性和可维护性|
|LSP|类型继承中的兼容性|确保子类可以无缝替换父类，增强代码健壮性和可预测性|


#### CRP(合成复用原则)
在面向对象设计中，可以通过两种方法在不同的环境中**复用已有的设计和实现**：
- 组合/聚合关系
- 继承

合成复用原则(Composite Reuse Principle, CRP)又称为组合/聚合复用原则(Composition/Aggregate Reuse Principle, CARP)，其定义如下：
- 尽量使用对象**组合/聚合**关系（关联关系），而不是继承来达到复用的目的。

继承复用的主要问题在于继承会破坏系统的封装性，将基类的实现细节暴露给子类。所以这种复用又称**白箱**复用：
- 如果基类发生改变，那么子类的实现也不得不发生改变；
- 从基类继承而来的实现是静态的，不可能在运行时发生改变，没有足够的灵活性。

组合或聚合关系可以将`已有的对象`（也可称为`成员对象`）纳入到新对象中，使之成为`新对象`的一部分，因此新对象可以调用已有对象的功能，这样做可以使得成员对象的内部实现细节对于新对象不可见，所以这种复用又称为**黑箱**复用：
- 耦合度相对较低，成员对象的变化对新对象的影响不大，可以在新对象中根据实际需要有选择性地调用成员对象的操作；
- 可以在运行时动态进行，新对象可以动态地引用与成员对象类型相同的其他对象。

一般而言，如果两个类之间是**Has-A**的关系应使用组合或聚合，如果是**Is-A**关系可使用继承。

示例：假设我们的CRM系统有一个`CustomerDao`类，需要支持不同的数据库操作。我们可以使用组合/聚合关系来实现数据库连接`DBConnection`的复用，而不是通过继承。

![CRP原则UML类图](https://sustamp.github.io/assets/pictures/design-patterns/UML-CRP.png)


通过组合/聚合关系，`CustomerDao`可以动态地接受与成员对象`DBConnection`类型相同的其他对象，从而实现对不同数据库的切换。


#### LKP(最少知识原则)
迪米特法则（Law of Demeter, LoD）又称为最少知识原则(LeastKnowledge Principle, LKP)，其定义如下：
- 一个软件实体应当尽可能少地与其他实体发生相互作用。

如果一个系统符合LoD，那么当其中一个模块发生修改时，就会尽量少地影响其他模块，扩展会相对容易，这是对软件实体之间通信的限制，迪米特法则要求**限制**软件实体之间**通信**的**宽度**和**深度**。
- LoD可降低系统的耦合度，使类与类之间保持松散的耦合关系。

迪米特法则还有几种定义形式，包括：不要和“陌生人”说话、只与你的直接朋友通信等。朋友包括以下几类：
- 当前对象本身(this)；
- 以参数形式传入到当前对象方法中的对象；
- 当前对象的成员对象；
- 如果当前对象的成员对象是一个集合，那么集合中的元素也都是朋友；
- 当前对象所创建的对象。

迪米特法则要求我们在设计系统时，应该尽量减少对象之间的交互，如果两个对象之间不必彼此直接通信，那么这两个对象就不应当发生任何直接的相互作用，如果其中的一个对象需要调用另一个对象的某一个方法的话，可以通过第三者转发这个调用。简言之：
- 就是通过**引入**一个合理的**第三者**来降低现有对象之间的耦合度。

示例理解LoD：

CRM系统包含很多业务操作窗口，在这些窗口中，当一个按钮(Button)被单击时，对应的列表框(List)、组合框(ComboBox)、文本框(TextBox)、文本标签(Label)等都将发生改变，在初始设计方案中，界面控件之间的交互关系可简化为如图1所示结构：

![LoD重构前类图示意](https://sustamp.github.io/assets/pictures/design-patterns/UML-LoD-pre.jpg)

使用LoD进行重构后：

![LoD原则UML类图](https://sustamp.github.io/assets/pictures/design-patterns/UML-LoD.png)


## 创建型模式

### 简单工厂模式

#### 定义
简单工厂模式（Simple Factory Pattern）：
- 定义一个工厂类，它可以根据参数的不同返回不同类的实例，被创建的实例通常都具有共同的父类。

#### UML类图

![简单工厂模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Simple-Factory.drawio.png)

#### 结构
简单工厂模式的结构如下：
- 工厂类(Factory)：
  - 通过参数决定创建哪个具体产品。
- 抽象产品(Product)：
  - `抽象类`/`接口`
- 具体产品(ConcreteProduct)：
  - 抽象产品的实现类

#### 效果

优点：
- 实现了对象创建和使用的分离。工厂类包含必要的判断逻辑，可以决定在什么时候创建哪一个产品类的实例，客户端可以免除直接创建产品对象的职责
- 无须知道所创建的具体产品类的类名，只需要知道具体产品类所对应的参数即可.
- 通过引入配置文件，可以在不修改任何客户端代码的情况下更换和增加新的具体产品类，在一定程度上提高了系统的灵活性
  
缺点：
- 简单工厂类集中了`所有产品`的创建逻辑，职责过重，一旦不能正常工作，整个系统都要受到影响。
- 简单工厂模式由于使用了静态工厂方法，造成工厂角色无法形成基于继承的等级结构。
- 当系统中需要引入新产品时，这必定要修改工厂类的源代码，将违背“开闭原则”。

##### 具体应用
- Spring的BeanFactory和ApplicationContext就是简单工厂模式来创建Bean实例。

```java
ApplicationContext context = new ClassPathXmlApplicationContext("beans.xml");
MyService myService = context.getBean(MyService.class);
```


### 工厂方法模式
简单工厂模式在引入新产品时势必要修改工厂类的源码，如何实现增加新产品而不影响已有代码？工厂方法模式应运而生。

#### 定义
工厂方法模式（Factory Method Pattern）：
- 定义一个用于创建对象的接口，让子类决定将哪一个类实例化。

工厂方法模式让一个类的实例化延迟到其子类。

#### UML类图

![工厂模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Factory.drawio.png)

客户端的调用代码如下：

```java
public class Client {
    public static void main(String[] args) {
        Factory factory;
        factory = new FactoryA();//可以通过配置文件或其他方式进行实例化
        //工厂负责创建产品
        Product product = factory.createProduct();
        //使用产品
        product.doSomething();
    }
}
```

在某些情况下，比如业务方法单一时，该类图可以对客户端(Client)的调用进行简化：
- 隐藏(`private`)工厂 `Factory` 的 `createProduct()` 方法。
- 包含产品 `Product` 方法`doSomething()`。由具体工厂实现该方法完成具体产品的创建和使用。
- 客户端直接调用工厂暴露出来的产品方法`doSomething()`。

此时客户端调用代码就变为：

```java
public class Client {
    public static void main(String[] args) {
        Factory factory;
        factory = new FactoryA();//可以通过配置文件或其他方式进行实例化
        //使用产品方法
        factory.doSomething();
    }
}
```

#### 结构
- 抽象工厂(Factory)：
  - 抽象类或接口，定义一个创建对象的接口。
- 具体工厂(ConcreateFactory)：
  - 实现抽象工厂，创建并返回具体产品类的实例。
- 抽象产品(Product)：
  - 抽象类或接口。
- 具体产品(ConcreateProduct)：
  - 实现抽象产品。具体产品由具体工厂创建，二者为一对一关系。

抽象工厂也可以定义许多重载的工厂方法，包含不同的传参类型，以满足不同方式的创建需求:

```java
public interface IFactory {
    IProduct createProduct();
    IProduct createProduct(String param);
    IProduct createProduct(Object config);
}
```

#### 效果
优点：
1. 客户端只需要关心产品对应的具体工厂，无需关心创建细节和具体产品类。
2. 多态性。所有的具体工厂类都具有同一抽象父类，工厂可以自主确定创建何种产品对象。
3. 加入新产品时，无须修改抽象工厂和抽象产品提供的接口，无须修改其他的具体工厂和具体产品，只要添加新的具体工厂和具体产品，也无须修改客户端。

缺点：
- 每个工厂只生产一类产品，可能会导致系统中存在大量的工厂类，势必会增加系统的开销。

##### 具体应用
- Spring的`FactoryBean`或继承`AbstractFactoryBean`。

### 抽象工厂模式
#### 定义
抽象工厂模式（Abstract Factory Pattern）：
- 提供一个**创建一系列**相关或相互依赖**对象**的接口，而**无须指定**它们**具体的类**。

抽象工厂模式又称为Kit模式，它是一种对象创建型模式。

这里要引入2个概念：

![产品等级结构示意图](https://sustamp.github.io/assets/pictures/design-patterns/diagram-product-hierarchy.png)

- 产品等级结构：抽象产品和具体产品之间的**继承关系**，具体产品的风格各不相同。
- 产品族：**一组**相关或相互依赖的**产品**，这些产品具备**同一种风格**，可以协同工作。


示例：
- 产品族：
  - Windows组件库：WindowsButton、WindowsTextBox、WindowsLabel
  - 海尔产品族：海尔空调、海尔冰箱、海尔洗衣机。
  - 美的产品族：美的产品族：美的空调、美的冰箱、美的洗衣机。
- 产品等级结构：
  - 空调：格力空调、美的空调
  - 冰箱：海尔冰箱、美的冰箱
  - Button：WindowsButton、MacButton
  - TextBox：WindowsTextBox、MacTextBox


#### UML类图

![抽象工厂模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Abstract-Factory.drawio.png)


#### 结构
- 抽象工厂：
  - 声明一组用于创建一系列产品对象（产品族）的方法，每一个方法对应一个产品。
- 具体工厂：
  - 负责创建同一风格的一系列产品（产品族）。
- 抽象产品：
  - 产品族中一种产品，并声明产品所具有的业务方法。
- 具体产品：
  - 这种结构的产品的一种具体实现。


与工厂方法模式一样，抽象工厂模式也可为每一种产品提供一组重载的工厂方法，以不同的方式对产品对象进行创建。

#### 效果
抽象工厂的应用前提一般需要产品结构要稳定，设计完成之后，不会向系统中增加新的产品等级结构或者删除已有的产品等级结构。

因为当要增加一个新的产品结构 `IProductC` 时：
- 由于抽象工厂类 `IFactory` 目前没有 `createProductC()` 的方法，所以势必要修改抽象工厂的代码；
- 而后还要逐个修改具体工厂的实现方法；
- 此外还要修改客户端。

抽象工厂模式无法解决该问题，这也是抽象工厂模式最大的缺点。

综上，抽象工厂模式的主要缺点是：
- 当要增加新的产品结构时，会违反**开闭原则**。
  
优点：
- **易于拓展**：只需增加新的具体产品和对应的具体工厂即可，此时无需修改系统已有代码（配置文件调整具体工厂不算修改代码）。符合**开闭原则**。
- 当一个产品族中的多个对象被设计成一起工作时，它能够保证客户端始终只使用风格相同的同一个具体工厂所生产的对象。
- **高内聚、低耦合**：通过抽象工厂模式，客户端代码与具体的库实现解耦，只需要依赖抽象工厂和抽象产品。

##### 使用场景
- 当需要创建一系列相关的产品族时。
- 确保客户端始终使用风格相同的对象集。

##### 案例：不同数据库的切换和DAO的使用
假设我当前的业务系统是连接Oracle，Dao层的sql是针对oracle的语法编写的。而现在业务需要节约成本，使用数据库mysql作为业务库。那么业务系统可以使用何种设计模式可以避免对现有代码的更改，而又能让业务系统能针对不同数据库进行编程？

分析：
- 分析需求，我们存在一组不同的Dao对象的产品族。
  - `UserDao`：用于操作用户表的DAO对象，业务方法有：创建用户，查询用户。
  - `OrderDao`：操作订单表的DAO对象，业务方法有：创建订单，查询订单。
- 不同的数据库对它们的实现各不相同，因而形成了产品等级结构：
  - `UserDao`：`OracleUserDao`、`MysqlUserDao`。
  - `OrderDao`：`OracleOrderDao`、`MysqlOrderDao`。

这里我们采用**抽象工厂模式**进行改造，该模式可以提供创建一组的**DAO对象**的接口，而无须指定它们具体的实现类。

设计思路：
1. 设计抽象产品：每个Dao对象都是一个抽象产品：
   - `UserDao`
   - `OrderDao`
2. 定义具体产品：按照需求，我们现在有两种数据库类型，不同的数据库是不同风格的DAO产品：
   - `OracleUserDao`
   - `MysqlUserDao`
   - `OracleOrderDao`
   - `MysqlOrderDao`
3. 定义抽象工厂：`DaoFactory`，声明创建抽象Dao对象的接口：
   - `createUserDao()`
   - `createOrderDao()`
4. 实现具体工厂类：每种数据库对应具体的工厂类，负责创建该数据库风格的具体Dao产品。
   - `OracleDaoFactory`：实现`createUserDao()`返回`OracleUserDao`，实现`createOrderDao()`返回`OracleNewsDao`。
   - `MysqlDaoFactory`：创建`MysqlUserDao`、`MysqlNewsDao`。

客户端只需依赖抽象工厂和抽象产品的接口编程，无需关心具体的实现类。具体工厂负责获取到具体的Dao对象，从而实现对不同数据库的编程。

通过抽象工厂模式，未来要添加新的数据库支持时，无需修改现有代码，只需要添加新的具体工厂和具体Dao类即可，易于拓展，且无须修改现有代码，符合开闭原则。

定义抽象工厂和具体工厂：

```java
//抽象工厂
public interface DaoFactory {
    UserDao createUserDao();
    OrderDao createOrderDao();
}

//具体工厂
public class OracleDaoFactory implements DaoFactory {
    @Override
    public UserDao createUserDao() {
        return new OracleUserDao();
    }

    @Override
    public OrderDao createOrderDao() {
        return new OracleOrderDao();
    }
}

public class MysqlDaoFactory implements DaoFactory {

    @Override
    public UserDao createUserDao() {
        return new MysqlUserDao();
    }

    @Override
    public OrderDao createOrderDao() {
        return new MysqlOrderDao();
    }
}
```

定义抽象产品和具体产品：

```java
//抽象产品：UserDao
public interface UserDao {
    String addUser();
    Object queryUser();
}
//抽象产品：OrderDao
public interface OrderDao {
    String createOrder();
    Object queryOrder();
}

//具体产品：Oracle实现
public class OracleOrderDao implements OrderDao {

    @Override
    public String createOrder() {
        System.out.println("使用oracle的sql语句创建订单");
        return "订单号";
    }

    @Override
    public Object queryOrder() {
        System.out.println("使用oracle的sql语句查询订单");
        return "查到的订单";
    }
}

public class OracleUserDao implements UserDao {

    @Override
    public String addUser() {
        System.out.println("使用oracle的sql语句添加用户");
        return "用户id";
    }

    @Override
    public Object queryUser() {
        System.out.println("使用oracle的sql语句查询用户");
        return "查到的用户";
    }
}

//具体产品：Mysql实现
public class MysqlOrderDao implements OrderDao {
    @Override
    public String createOrder() {
        System.out.println("使用mysql的sql语句创建订单");
        return "订单号";
    }

    @Override
    public Object queryOrder() {
        System.out.println("使用mysql的sql语句查询订单");
        return "查到的订单";
    }
}

public class MysqlUserDao implements UserDao {
    @Override
    public String addUser() {
        System.out.println("使用mysql的sql语句添加用户");
        return "用户id";
    }

    @Override
    public Object queryUser() {
        System.out.println("使用mysql的sql语句查询用户");
        return "查到的用户";
    }
}
```

测试代码：

```java
class client{
    public static void main(String[] args) {
        DaoFactory daoFactory = new MysqlDaoFactory();//模拟使用配置文件或反射初始化工厂对象
		//创建相关数据库操作对象Dao
		UserDao userDao = daoFactory.createUserDao();
		OrderDao orderDao = daoFactory.createOrderDao();

		userDao.addUser();
		orderDao.createOrder();
		orderDao.queryOrder();
    }
}
```

输出：

```
使用mysql的sql语句添加用户
使用mysql的sql语句创建订单
使用mysql的sql语句查询订单
```


>思考：  
这个方案存在一个严重问题：虽然添加新的数据库类型时符合开闭原则并保证语法一致，但Dao层的对象是会随着业务迭代而需要新增的，这时候就不符合开闭原则，要怎么处理？

**解决方案1：利用Spring框架提供的依赖注入(DI)**

使用Spring的依赖注入来代替工厂模式完成对Dao对象的创建和注入，并根据`条件注入`的方式决定注入哪个Dao对象的具体实现类，这样可以就避免违背开闭原则。

改进思路：
- 在配置文件中添加一个配置属性`database.type`，其值决定数据库类型：
  - 比如：`database.type=mysql` 指定数据库为mysql。
- 给`Dao`的每个具体实现类打以下上注解，由Spring代替`DaoFactory`完成对象的创建和注入：
  - `@Repository`：表明该类作为一个组件，能够被Spring自动扫描和实例化为Bean，纳入Spring容器管理
  - `@ConditoinalOnProperty`：表明这个类是条件注解，根据配置的属性值来决定是否加载某个 Bean 或者配置类。

实现代码：

```
# 配置文件application.properties
# 指定数据库为mysql
database.type=mysql 
```


```java
@Repository
@ConditionalOnProperty(name = "database.type", havingValue = "mysql")
public class MysqlUserDao implements UserDao {
    //接口代码省略...
}

@Repository
@ConditionalOnProperty(name = "database.type", havingValue = "oracle")
public class OracleUserDao implements UserDao {
    //接口代码省略...
}

@Repository
@ConditionalOnProperty(name = "database.type", havingValue = "mysql")
public class MysqlOrderDao implements OrderDao {
    //接口代码省略...
}


//测试代码
class client{
    public static void main(String[] args) {
        // DaoFactory daoFactory = new MysqlDaoFactory();//模拟使用配置文件或反射初始化工厂对象
		//创建相关数据库操作对象Dao
		// UserDao userDao = daoFactory.createUserDao();
		// OrderDao orderDao = daoFactory.createOrderDao();
        UserDao userDao = ApplicationContextUtils.getBean(UserDao.class);
        OrderDao orderDao = ApplicationContextUtils.getBean(OrderDao.class);

		userDao.addUser();
		orderDao.createOrder();
		orderDao.queryOrder();
    }
}

```



### 单例模式
为了确保对象的唯一性，我们通常会用单例模式来设计。

#### 定义
单例模式（Singleton Pattern）的定义：
- 确保某一个类**只有一个实例**，而且**自行实例化**并向整个系统提供这个实例，这个类称为单例类，它提供**全局访问**的方法。

#### UML类图

![单例模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Singleton.drawio.png)

#### 结构
- 单例类Singleton，它的主要内容包括：
  - 私有的构造函数：`private Singleton()`。
  - 声明一个单例类Singleton的静态实例:`private static Singleton instance`。
  - 提供一个静态的工厂方法：`public static Singleton getInstance()`。


##### 1.饿汉单例模式

```java
public class EagerSingleton {
    private static final EagerSingleton instance = new EagerSingleton();
    private EagerSingleton() {}

    public static EagerSingleton getInstance() {
        return instance;
    }
    
}
```

饿汉式单例类不能实现延迟加载，不管将来用不用始终占据内存。

##### 2.懒汉单例模式

```java
public class LazySingleton {
    // volatile修饰的成员变量可以确保多个线程都能够正确处理
    private volatile static LazySingleton instance = null;
    private LazySingleton() {}

    public static LazySingleton getInstance() {
        // 使用双重检查判定锁DCL(Double-Check Locking)
        if (instance == null) {
            synchronized (LazySingleton.class) {
                if (instance == null) {
                    instance = new LazySingleton();
                }
            }
        }
        return instance;
    }
}

```

懒汉式单例类线程安全控制烦琐，而且性能受影响。

> 思考：为什么要加上 `volatile` 关键字?

`instance = new LazySingleton();` 不是一个原子操作。在JVM中，这条语句至少做了3件事：
1. 给Singleton的实例分配内存空间；
2. 调用Singleton()的构造函数，初始化成员字段；
3. 将singleton指向分配的内存空间(此时singleton就不是null了)
   

因为存在着指令重排序的优化，第2、3步的顺序是不能保证的，最后的执行顺序可能是1-2-3，也可能是1-3-2。

假如执行顺序是1-3-2时，`singleton!=null`，但没有初始化，其他线程判断通过直接返回instance并使用会因为没有初始化而报错。这就是**DCL失效**的问题，这种问题难以跟踪难以重现可能会隐藏很久。

JDK1.5之后，SUN官方调整了JVM，具体化了 `volatile` 关键字，就可以保证每次从主存中读取（这涉及到CPU缓存一致性问题），也可以**防止指令重排序**的发生，避免拿到未完成初始化的对象。

##### 3.使用静态内部类的单例模式

```java
public class Singleton{
    private singleton() {}

    // 定义单例类的静态内部类Holder
    // 然后在静态类部内创建单例对象，这样使得类的初始化延迟到子类中
    private static class SingletonHolder{
        private final static Singleton instance = new Singleton();
    }

    public static Singleton getInstance(){
        return SingletonHolder.instance;
    }

}
```

使用Initialization Demand Holder (IoDH)的技术能够将上述两种模式的优点合二为一，既可以实现延迟加载，又可以保证线程安全，不影响系统性能。

##### 4.使用枚举的单例模式

```java
public enum Singleton {
    INSTANCE;
}
```

使用枚举实现单例模式，代码简洁，同时实现懒加载和线程安全，也不会在序列化或反射时被破坏。

#### 效果
优点：
- 确保对象的唯一性。
- 节约系统资源。系统内存中只存在一个对象，一些需要频繁创建和销毁的对象无疑可以提高系统的性能。
- 实例数目可控。使用与单例控制相似的方法来获得指定个数的对象实例，既节省系统资源，又解决了单例单例对象共享过多有损性能的问题。

缺点：
- 没有抽象层，单例类拓展困难。
- 单例类的职责过重，在一定程度上违背了**单一职责原则**。单例类既充当了工厂角色，提供了工厂方法，同时又充当了产品角色，包含一些业务方法，将产品的创建和产品的本身的功能融合到一起。

### 原型模式
原型模式-对象的克隆。
#### 定义
原型模式（Prototype Pattern）定义如下：
- 使用原型实例指定创建对象的种类，并且通过拷贝这些原型创建新的对象。
  
原型模式的工作原理很简单：
- 将一个原型对象传给那个要发动创建的对象，这个要发动创建的对象通过请求原型对象拷贝自己来实现创建过程
- 创建克隆对象的工厂就是原型类自身，工厂方法由克隆方法来实现。


#### UML类图

![原型模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Prototype.drawio.png)

#### 结构
- 原型(Prototype)：
  - 它是`抽象类`或`接口`或`具体实现类`，声明克隆方法。
- 具体原型类(ConcretePrototype)：
  - 实现克隆方法，在克隆方法中返回自己的一个克隆对象。


##### 浅拷贝
浅克隆(ShallowClone)：
- 如果原型对象的成员变量是`值类型`，将复制一份给克隆对象。
- 如果原型对象的成员变量是`引用类型`，则将引用对象的**地址复制**一份给克隆对象，也就是说原型对象和克隆对象的成员变量指向相同的内存地址。

##### 深拷贝
深克隆(DeepClone)：
- 无论原型对象的成员变量是`值类型`还是`引用类型`，都将复制一份给克隆对象，深克隆将原型对象的所有引用对象也复制一份给克隆对象。


在Java语言中，如果需要实现深克隆，可以通过**序列化(Serialization)**等方式来实现。

序列化就是将对象写到流的过程。
- 写到流中的对象是原有对象的一个拷贝，而原对象仍然存在于内存中。
- 再从流里将其读出来，可以实现深克隆。

用Json工具类实现深拷贝：
- 将原对象进行`objToJson`转成json字符串。
- 然后再进行`jsonToObj`转成新对象

#### 效果
缺点：
- 每一个类配备一个克隆方法，而且该克隆方法位于一个类的内部，当对已有的类进行改造时，需要修改源代码，违背了**开闭原则**。
- 在实现深克隆时，当对象之间存在多重的嵌套引用时，每一层对象对应的类都必须支持深克隆，实现起来可能会比较麻烦。

> 思考：使用工具类完成对象的拷贝动作。  

```java
public class CopyUtils {
    public static <T> T deepCopy(T obj, Class<T> clazz) {
        //TODO： 深拷贝代码...
    }
}
```

优点：
- 对象实例复杂时，使用原型模式可以简化对象的创建过程，提高新实例的创建效率。
- 扩展性较好，由于在原型模式中提供了抽象原型类，在客户端可以针对抽象原型类进行编程，而将具体原型类写在配置文件中，增加或减少产品类对原有系统都没有任何影响。
- 深克隆的方式可以保存对象的状态，将对象复制一份并将其状态保存起来，以便在需要的时候使用（如恢复到某一历史状态），可辅助实现撤销操作。



## 结构型模式

### 适配器模式
适配器模式-不兼容结构的协调。

#### 定义
适配器模式（Adapter Pattern）：
- 将一个接口转换成客户希望的另一个接口，使接口不兼容的那些类可以一起工作。
  
适配器模式别名为包装器(Wrapper)，有两种实现类型：
- 类适配器模式：**类结构型**模式，适配器与适配者之间是继承（或实现）关系。
- 对象适配器模式：**对象结构型**模式。适配器与适配者之间是关联关系。

在实际开发中，对象适配器的使用频率更高。

类适配器的使用受到很多限制：
- Java、C#等语言不支持多重类继承。目标抽象类Target不是接口，而是一个类，就无法使用类适配器。
- 适配者Adapter为最终(Final)类，也无法使用类适配器。

#### UML类图

![适配器模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Adapter.drawio.png)

> 思考：
> 1. 在对象适配器中，一个适配器能否适配多个适配者？如果能，应该如何实现？如果不能，请说明原因。  
> 2. 在类适配器中，一个适配器能否适配多个适配者？如果能，应该如何实现？如果不能，请说明原因。

#### 结构
- **目标(Target)**：
  - 定义客户所需的目标和结构。可以是`接口`，`抽象类`或`具体类`。
- **适配器(Adapter)**: 
  - 作为转换器，调用`适配者`的接口或方法，将其结果和结构转换成符合`目标`的接口和结构。
- **被适配者(Adaptee)**：
  - 已经存在的对象。它本身具备已经定义好的接口和结构，但因为与`目标`期望结构不符，所以要被`适配器`适配，转换结果。


#### 效果
优点：
- 解耦：适配器模式将`目标`和`适配者`解耦，引入`适配器`来重用现有的`适配者`，无须修改原有结构。
- 增加了类的透明性和复用性：业务实现过程封装在`适配器`中，对客户端是透明的，且`适配者`不需改动，提高了复用性，可以被不同的系统或模块使用。
- 拓展性好：增加和更换适配器不需要修改原有代码。完全符合**开闭原则**。
- 一个对象适配器可以把多个不同的适配者适配到同一个目标。

缺点：
- 在适配器中更换适配者的某些方法会比较麻烦。
  - 可以先做一个适配者类的子类，将适配者类的方法置换掉，然后再把适配者类的子类当做真正的适配者进行适配，实现过程较为复杂。


### 桥接模式
桥接模式-处理多维度的变化

#### 定义
桥接模式（Bridge Pattern）：
- 将**抽象部分**与它的**实现部分**分离，使它们都可以独立地变化。
  
它是一种对象结构型模式，又称为柄体(Handle and Body)模式或接口(Interface)模式。

桥接模式的关键是识别出类所具有的两个独立变化的维度，分成**抽象部分**和**实现部分**，将这两个维度分离出来，使两者可以独立扩展，让系统更加符合**单一职责原则**。

与多层继承方案不同，它将两个独立变化的维度设计为两个独立的继承等级结构，并且在抽象层建立一个抽象关联，该关联关系类似一条连接两个独立继承结构的桥，故名桥接模式。

#### UML类图

![桥接模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Bridge.drawio.png)

java的jdbc的驱动程序就是桥接模式的典型应用：

![jdbc驱动程序UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Bridge-jdbc.drawio.png)

#### 结构
- **抽象部分**：通常是与类紧密相关的变化维度。
  - `抽象类`：抽象部分的抽象层，通常定义为抽象类。其中还维护了一个实现部分的接口对象，建立与实现部分的关联关系。
  - `具体扩充`：扩充抽象类，并实现其中的抽象业务方法，业务方法中还会调用实现部分的接口方法
- **实现部分**：通常是类的另一个变化维度。
  - `实现类`：实现部分的抽象层，通常定义为`接口`。
  - `具体实现`：实现维度的不同实现方式。

通常将与类的关系紧密的维度和业务方法设计为抽象部分，另一维度设计为实现部分。比如：
- 毛笔的型号是抽象部分。型号是毛笔固有维度，绘画是它的一个业务方法，各种型号的毛笔作为其子类并实现业务方法。
- 毛笔所用颜料是实现部分。将颜料作为另一个维度的抽象类或接口，由其子类实现具体的颜色，使用毛笔绘画时调用子类着色。


#### 效果
优点：
- 以 组合/聚合 取代 多层继承：
  - 不使用继承方案，减少了子类个数，并且使类的设计和实现分离，符合**单一职责原则**。
- 复用性高：
  - 以组合关系关联对实现类及其子类的使用，符合**合成复用原则**，**里氏替换原则**。
- 拓展性好：
  - 抽象部分和实现部分都是独立的继承体系，两者通过抽象层建立耦合关系，符合**依赖倒置原则**。变更新的实现不用修改原有代码，符合**开闭原则**。

缺点：
- 理解较难：桥接模式的关联关系在抽象层
- 需要经验积累：识别和建立系统中某两个独立变化的维度需要一定的经验。

> 思考： 桥接模式与策略模式有什么区别？

##### 具体应用
- jdk的`java.sql.DriverManager`。


### 代理模式
代理模式-真实对象的代理访问

#### 定义
代理模式（Proxy Pattern）：
- 给某一个对象提供一个代理或占位符，并由代理对象来控制对原对象的访问。

代理模式引入了一个新的代理对象，代理对象在客户端对象和目标对象之间起到中介的作用，它去掉客户不能看到的内容和服务或者增添客户需要的额外的新服务。

其核心是代理类，为了让客户端能够一致性地对待真实对象和代理对象，在代理模式中引入了抽象层。

#### UML类图

![代理模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Proxy.drawio.png)

#### 结构
- **抽象主题**：
  - 实现客户端一致调用的抽象层。声明了代理主题和真实主题共同的接口。
- **代理主题**：
  - 包含对真实主题的引用，从而可以操作真实主题的方法。并且可以在操作真实主题方法之前和之后增加一些额外的操作。
- **真实主题**：
  - 实际使用的业务对象和方法，只不过由代理主题负责调用。

##### 分类
代理模式根据其目的和实现方式不同可分为很多种类。

###### 1.远程代理
远程代理(Remote Proxy)为一个位于不同的地址空间的对象提供一个本地的代理对象，这个不同的地址空间可以是在同一台主机中，也可是在另一台主机中，远程代理又称为大使(Ambassador)。

###### 2.虚拟代理
虚拟代理(Virtual Proxy)是需要创建一个资源消耗较大的对象，先创建一个消耗相对较小的对象来表示，真实对象只在需要时才会被真正创建。

适用场景：
- 对象本身的复杂性或者网络等原因导致一个对象需要较长的加载时间。
  - 通常结合多线程技术，一个线程用于加载耗时较短的代理对象，其他线程用于加载真实对象。
  - 用代理对象代替真实对象初始化，大大加速了系统的启动时间。
  - 当需要使用真实对象时，再通过代理对象来引用，而此时真实对象可能已经成功加载完毕，可以缩短用户的等待时间。
- 当一个对象的加载十分耗费系统资源的时候，也非常适合使用虚拟代理。
  - 用占用资源较少的代理对象来代表真实对象,再通过代理对象来引用真实对象。
  - 为了节省内存，在第一次引用真实对象时再创建对象，以后每次访问时需要检测所需对象是否已经被创建。
  - 消耗一定的系统时间，但是可以节省内存空间，这是一种用时间换取空间的做法。


###### 3.保护代理
保护代理(Protection Proxy)控制对一个对象的访问，可以给不同的用户提供不同级别的使用权限。

###### 4.缓存代理
缓存代理(Caching Proxy)为某一个目标操作的结果提供临时的存储空间，以便多个客户端可以共享这些结果。

###### 5.智能引用代理
智能引用代理(Smart Reference Proxy)当一个对象被引用时，提供一些额外的操作，例如将对象被调用的次数记录下来等。


#### 效果
优点：
- 客户端针对抽象层编程，更换代理类无需修改已有代码，符合**开闭原则**。
- 在真实主题之间做了代理，一定程度上降低了真实对象的耦合度。
- 其他优势见代理模式的分类。

缺点：
- 通过代理对象访问真实对象，一定程度上会降低请求的处理速度。
- 代理模式通常会做其他额外功能，会增加一定的维护程度。

##### 具体应用
- SpringAop的切面编程主要使用了代理模式，来实现方法的拦截和增强功能，并不需要知道方法的细节。

### 装饰器模式
装饰器模式-动态拓展系统功能

#### 定义
装饰器模式（Decorator Pattern）定义：
- 在**不改变现有对象结构**的情况下，动态地给一个对象增加一些额外的职责，就增加对象功能来说，装饰模式比生成子类实现更为灵活。

装饰器模式是一种对象结构型模式。

#### UML类图

![装饰模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Decorator.drawio.png)


客户端的调用代码：

```java
class client {
    public static void main(String[] args) {
        Component component = new ConcreteComponent();
        Component decorator = new ConcreteDecoratorB(component);

        decorator.operation();
    }
}
```



#### 结构
- `抽象构件`：
  - 作为`具体构件`和`抽象装饰类`的共同**父类**，可以是`接口`或`抽象类`。声明具体构件的业务接口，使客户端能一致处理未被装饰和装饰之后的对象。
- `具体构件`：
  - `抽象构件`子类，具体实现的业务。
- `抽象装饰类`：
  - `抽象构件`子类，维护一个指向`抽象构件`的引用来调用构件的方法。
- `具体装饰类`：
  - `抽象装饰类`的子类，装饰构件，添加新的功能。


#### 效果
优点：
- 比采用继承方式拓展功能更为灵活
- 可以设计不同的装饰类，创造出不同行为的组合。
- 具体构件类和具体装饰类可以独立变化，符合开闭原则。

缺点：
- 装饰类会产生许多小对象，过渡使用会增加系统的复杂度。
- 如果装饰对象过多或过于复杂，排查问题需要逐级排查，较为繁琐，还可能会导致代码难以维护。
  

> 思考： 代理模式也能增加对象的额外功能，装饰模式与代理模式有什么区别？

- 代理模式是全权代理，真实对象不对外展示
- 装饰模式只是起到增强的作用，被装饰的类仍然可以对外提供服务。

##### 具体应用
- Spring框架中有不少地方使用了装饰器模式的原理：
  - 含有`-Wrapper`或`-Decorator`后缀的类，比如：`HttpServletRequestWrapper`。
  - `BeanPostProcessor`:对Bean实例进行增强。
  - `HandlerInterceptor`：对拦截器的增强。
- jdk的`InputStream`类下的`FileInputStream`、`BufferedInputStream`等也是装饰器模式。
  - 在不修改`InputStream` 代码的情况下扩展了它读取文件、增加缓存加快读取速度等功能。
- 数据源包装、IO流等。


### 外观模式
外观模式-易用的统一入口

#### 定义
外观模式（Facade Pattern）定义：
为子系统中的一组接口提供一个统一的入口。外观模式定义了一个高层接口，这个接口使得这一子系统更加容易使用。

外观模式又称为门面模式，它是一种对象结构型模式。外观模式是**迪米特法则**的一种具体实现，通过引入一个新的外观角色可以降低原有系统的复杂度，同时降低客户类与子系统的耦合度。

#### UML类图

![外观模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Facade.drawio.png)

#### 结构
- **外观角色**：
  - 提供一个统一的入口由客户端调用，代替其调用一系列子系统的业务方法。实现客户端与子系统的解耦。
- **子系统角色**：
  - 一个或多个完成业务的子系统角色，由外观角色统一调用。

#### 效果
优点：
1. 松耦合：由外观角色负责与子系统交互，降低了客户端与子系统之间的耦合，减少了客户端所需处理的对象数目。
2. 提高易用性：客户端只与外观角色交互，简化了客户端的代码。

缺点：
1. 限制了客户端对子系统对象的访问，降低了灵活性和可变性。

> 思考： 外观模式与代理模式有什么区别，它们的作用是什么？

##### 具体应用
- Spring的`JdbcTemplate`、`RestTemplate`使用了模板方法模式，也应用了外观模式简化复杂操作。



### 组合模式
组合模式-树形结构的处理

#### 定义
组合模式(Composite Pattern)：
- 组合多个对象形成树形结构以表示**整体-部分**关系的层次结构。
- 组合模式对单个对象（叶子）和组合对象（容器）的使用具有**一致性**。

组合模式又可称为整体-部分模式。

#### UML类图



#### 效果


## 行为性模式
### 模板方法模式
#### 定义
模板方法模式（Template Method Pattern）：
- 定义一个操作中算法的框架，而将**一些步骤延迟到子类**中。模板方法模式使得子类可以不改变一个算法的结构即可重定义该算法的某些特定步骤。

模板方法模式是基于继承的代码复用技术，它是一种类行为模式。其结构只存在于父类和子类之间的继承关系，是结构最简单的行为型设计模式。

#### UML类图

![模板方法模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Template-Method.drawio.png)

#### 结构
- **抽象模板类**：
  - 在抽象类中定义一系列基本操作，这些操作可以是具体的，也可以是抽象的。同时抽象类中实现一个模板方法，用于定义算法的基本框架，且包含一系列的基本操作。
- **具体子类**：
  - 继承抽象模板类，并实现抽象类中的抽象方法或重写父类模板中已实现的具体方法。

在父类模板中可能还会提供一些抽象的钩子方法，钩子方法可以使得子类能够控制父类的某些行为。

#### 效果
1. 优点：
   - 提高代码复用率。
   - 更换子类非常方便，符合开闭原则。
2. 缺点：
   - 每个方法的不同实现都需要提供一个新的子类，如果父类中可变的基本方法太多，将导致类的个数剧增，增加系统的复杂度，此时可以考虑使用**桥接模式**重新设计。

##### 使用场景
1. 模板方法是基于继承的代码复用技术，广泛应用于框架设计中，以确保通过父类控制处理流程的逻辑顺序（如框架的初始化、测试流程的设置等）。
2. 各子类的公共行为提取出来并集中到公共父类中以避免代码重复。
3. 需要通过子类控制父类算法中某个步骤是否执行，实现子类对父类的反向控制。


##### 具体应用
-  Spring中的`JdbcTemplate`和`RestTemplate`等模板类都是模板方法模式的典型应用。  


### 策略模式
策略模式-算法的封装与切换

#### 定义
策略模式（Strategy Pattern）定义：
- 定义一系列算法类（策略），将每一个算法封装起来，并让它们可以相互替换，策略模式让算法独立于使用它的客户而变化。

策略模式的主要目的是：
- 将算法的定义与使用分开。

它把算法的责任和算法本身分割开，委派给不同的对象管理。

  
#### UML类图

![策略模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Strategy.drawio.png)

> 思考：一个环境类Context能否对应多个不同的策略等级结构？如何设计？

#### 结构
- 环境类(Context)：
  - 它是使用算法的角色。在环境类中维持一个对抽象策略类的引用实例，用于定义所采用的策略。
- 抽象策略类(Strategy)：
  - 是所有策略类的父类，为算法声明抽象方法。它可以是`抽象类`,`接口`或`具体类`
- 具体策略类(ConcreteStrategy)：
  - 实现具体算法。

在策略模式中，对环境类和抽象策略类的理解非常重要，环境类是需要使用算法的类。在一个系统中可以存在多个环境类，它们可能需要重用一些相同的算法。

#### 效果
优点：
- 提供了对**开闭原则**的完美支持，用户可以在不修改原有系统的基础上选择算法或行为，也可以灵活地增加新的算法或行为。
- 使用策略模式可以避免多重条件选择语句。
- 提高算法复用性。由于将算法单独提取出来封装在策略类中，因此不同的环境类可以方便地复用这些策略类。

主要缺点：
-  客户端必须知道所有的策略类，并自行决定使用哪一个策略类。
-  策略模式将造成系统产生很多具体策略类，任何细小的变化都将导致系统要增加一个新的具体策略类。
-  无法同时在客户端使用多个策略类。也就是说，在使用策略模式时，客户端每次只能使用一个策略类，不支持使用一个策略类完成部分功能后再使用另一个策略类来完成剩余功能的情况。

##### 应用场景
1. 一个系统需要动态地在几种算法中选择一种。
2. 一个对象有很多的行为，如果不用恰当的模式，这些行为就只好使用多重条件选择语句来实现。
3. 不希望客户端知道复杂的、与算法相关的数据结构，在具体策略类中封装算法与相关的数据结构，可以提高算法的保密性与安全性。


### 观察者模式
观察者模式-对象间的联动
#### 定义
观察者模式（Observer Pattern）定义：
- 定义对象间的一种一对多依赖关系，一个或多个对象依赖于某一个对象，当这个对象的状态发生改变时，其相关依赖的对象都得到通知并被触发自动更新。

#### UML类图

观察者模式简单类图：

![观察者模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Observer.drawio.png)

发布订阅模式UML类图：

![发布订阅模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Publish-Subscribe.drawio.png)

#### 结构
观察者模式的基本结构是：
- `主题(Subject)`：
  - 它作为`被观察者`，是`观察者`的观察**目标**。持有观察者对象的引用，并提供注册、注销和通知观察者的接口。它可以是`接口`、`抽象类`或`具体类`。
- `具体主题(ConcreteSubject)`：
  - 存储实际状态的具体主题，当状态发生变化时，则触发通知其相关的观察者。
- `观察者(Observer)`：
  - 通常设计为`接口`，声明`update()`方法，表示当目标状态发生变化时产生的行为。
- `具体观察者(ConcreteObserver)`：
  - 具体实现更新逻辑。


发布订阅模式(Publichish-Subscribe Pattern)也是观察者模式的一种实现。其结构如下：
- `发布者(Publisher)`: 负责生产消息。
- `消息代理中介(Message Broker)`：管理订阅者列表，负责将`发布者`的消息分发给相应的`订阅者`，支持主题、异步处理、消息过滤和持久化。
- `订阅者(Subscriber)`：负责接收消息和后续处理。

发布订阅模式与观察者模式类似，但存在着一些差别：
- 观察者模式中`被观察者`本身负责了对`观察者`的管理和通知。
- 发布订阅模式在`发布者`与`订阅者`之间增加一个`中介者`，由`中介者`承担对`订阅者`的管理和通知，使得`发布者`与`订阅者`之间是解耦的。

#### 效果
优点：
- 主题与观察者行为的独立。主题不知道观察者的具体实现，只需调用它们的方法。两者可以独立变化。
- 支持广播通信：观察目标会向所有已注册的观察者对象发送通知，简化一对多系统设计的难度。
- 提高代码复用性：不同的主题可以使用相同的观察者，不同的观察者也可以订阅不同的主题。

缺点：
- **性能问题**：当观察者数量较多时，被观察者在状态改变时需要遍历所有观察者并调用它们的更新方法，这可能会导致性能瓶颈。特别是在高并发环境下，频繁的通知和更新操作可能会显著影响系统性能。
- **循环依赖**：观察者在更新时又触发了被观察者的状态变化，导致无限循环，可能导致系统崩溃。
- **依赖关系复杂化**：每个被观察者都需要维护一个观察者的列表，并在状态改变时通知所有观察者。

##### 应用场景
1. 观察者模式
   - 读者关注感兴趣的作者，当作者发布新作品时能收到通知。
   - 当前流行的MVC(Model-View-Controller)架构中也应用了观察者模式：
     - 模型(Model)：对应于观察目标。
     - 视图(View)：对应于观察者。
     - 控制器(Controller)。充当两者之间的中介者。当模型层的数据发生改变时，视图层将自动改变其显示内容
   
2. 发布订阅模式。
   - 系统可能根据业务会向不同的消息中间件(ibmmq/activemq/kafaka)发送消息，子系统订阅该消息中间件时可收到消息。
   - 系统可能有不同的业务信息生产者，比如订单信息生产者，支付信息生产者，物流信息生产者等，不同的子系统对接不同的生产者完成对应的后续功能。

> 习题：开发一个简单的股票监控应用程序，要求：当股票购买者所购买的某支股票价格发生变化时，该股票的所有股民都将收到通知（包括新价格）。

习题实现代码：

```java
//抽象主题(被观察者)：股票抽象类
public abstract class Stock {
    protected BigDecimal price = new BigDecimal("1");//初始1块钱

    protected List<StockBuyer> buyers = Lists.newArrayList();

    // 由子类具体实现，并调用notifyBuyers方法
    public abstract void setPrice(BigDecimal price);

    public synchronized void addBuyer(StockBuyer buyer) {
        if (!buyers.contains(buyer)){
            buyers.add(buyer);
        }
    }

    public synchronized void removeBuyer(StockBuyer buyer) {
        buyers.remove(buyer);
    }

    public void notifyBuyers(Object arg) {
        for (StockBuyer buyer : buyers) {
            buyer.receive(arg);
        }
    }
}

//具体主题(被观察者)：腾讯股票
public class TxStock extends Stock {

    public BigDecimal getPrice() {
        return this.price;
    }

    //具体主题实现价格变化时，通知股民
    @Override
    public void setPrice(BigDecimal price) {
        BigDecimal oldPrice = getPrice();
        BigDecimal growth =  price.subtract(oldPrice).multiply(new BigDecimal("100")).divide(oldPrice,2, RoundingMode.HALF_DOWN);
        this.price = price;
        //当涨幅低于0或者涨幅大于1%时，通知所有股民
        if(growth.compareTo(BigDecimal.ZERO) < 0 || growth.compareTo(new BigDecimal("0.01")) >= 0){
            String message = MessageFormat.format("之前价格：{0}，最新价格：{1}，涨幅:{2}", oldPrice.toString(), price.toString(), growth + "%");
            notifyBuyers(message);
        }
    }
}

//抽象观察者：股民抽象类
public interface IStockBuyer {
    void receive(Object arg);
}

//具体观察者：股民
public class StockBuyer implements IStockBuyer {

    private String name;

    public String getName() {
        return name;
    }

    public StockBuyer(String name){
        this.name = name;
    }

    @Override
    public void receive(Object arg) {
        System.out.println(this.name + "收到股票信息：" + arg);
    }
}

//测试代码
public class Client{
    public static void main(String[] args) {
        //股民
        StockBuyer zhangsan = new StockBuyer("张三");
        StockBuyer lisi = new StockBuyer("李四");
        StockBuyer wangwu = new StockBuyer("王五");
        //股票
        Stock txStock = new TxStock();
        //股票被股民购买
        txStock.addBuyer(zhangsan);
        txStock.addBuyer(lisi);
        txStock.addBuyer(wangwu);
        //价格发生变化
        txStock.setPrice(new BigDecimal(50));
        txStock.setPrice(new BigDecimal(51));
        txStock.setPrice(new BigDecimal(38));
        txStock.removeBuyer(wangwu);//不跟了
        txStock.setPrice(new BigDecimal(50));
        txStock.setPrice(new BigDecimal(52));
        txStock.setPrice(new BigDecimal(55));
        txStock.setPrice(new BigDecimal(55.5));
        txStock.setPrice(new BigDecimal(56.5));
    }
}
```

### 中介者模式
中介者模式-协调多个对象之间的交互
#### 定义
中介者模式（Mediator Pattern）：
- **用一个中介对象**来封装一系列的对象交互，中介者使各对象不需要显式地相互引用，从而使其耦合松散，而且可以独立的改变它们之间的交互。

中介者模式又叫调停者模式，是一种对象行为型模式。

> 思考：中介者模式和外观模式都符合迪米特法则，它们之间有什么区别？  


#### UML类图

![中介者模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Mediator.drawio.png)


#### 结构
- **抽象中介类**：
  - **核心类**，定义一些接口，用于各同事对象之间进行通信。
- 具体中介类：
  - 抽象中介类的具体实现，它维持了对各个`同事对象`或`组件对象`的引用，协调各对象的行为。
- 抽象同事类：
  - 定义各个同事类共有的方法，并声明一些抽象方法由子类实现。
  - 同时维持了一个对`抽象中介类`的引用，可让子类与中介者通信。
- 具体同事类：
  - 实现抽象同事类的方法，通过**调用中介者的方法**完成与其他同事类的通信。

#### 效果
优点：
1. 简化对象之间的交互，减少了类之间的耦合。
   - 通过引入中介者对象，将系统对象之间复杂联系的网状结构变成了以中介者为中心的星形结构。
   - 对象之间多对多的关系变成了一对多的关系，是**迪米特法则**的典型应用。
2. 集中管理。所有的交互逻辑都被封装在中介者类中，容易集中管理和修改。
3. 方便拓展。有新的同事类加入交互时，可以通过派生新的中介者类完成而不用修改原有代码，符合**开闭原则**。

> 思考：观察者模式也是定义一对多的依赖关系，中介者模式与观察者模式有什么区别？

缺点：
- 可能过于集中：中介者类包含了大量同事类的交互细节，可能会导致中介者类逻辑复杂，难以维护。

##### 使用场景
以下情况可以考虑使用中介者模式：
1. 系统各对象之间存在复杂的引用关系。
2. 需要集中管理对象之间的通信。
3. 多个对象之间需要进行通信，但不希望相互之间过于紧密耦合。
4. 系统中有多个对象协作完成某一任务。

##### 实践：聊天群功能
现在我们以聊天群来实现中介者模式的应用代码。
- 以聊天群作为中介者，参与聊天的用户作为同事类
  - 当其中一个人发送消息时，中介者联动其他同事类收到消息（行为的变化）。

具体代码如下：

```java
/**
 * 聊天中介者：抽象类
 */
public abstract class ChatMediator {
    /**
     * 提供发送消息的方法
     * @param msg 消息内容
     * @param colleague 发送消息的同事类
     */
    public abstract void sendMessage(String msg, ChatColleague colleague);

    /**
     * 提供加入聊天的方法（添加同事类）
     * @param colleague
     */
    public abstract void addUser(ChatColleague colleague);
}

/**
 * 群聊中介者。具体实现抽象中介者的方法
 */
public class GroupChatMediator extends ChatMediator {

    /**
     * 维护一个所有同事类的列表
     */
    protected List<ChatColleague> colleagues = Lists.newArrayListWithCapacity(0);

    @Override
    public void sendMessage(String msg, ChatColleague colleague) {
        for (ChatColleague c : colleagues) {
            if (!Objects.equals(c, colleague)) {
                c.receiveMessage(msg);
            }
        }
    }

    @Override
    public synchronized void addUser(ChatColleague colleague) {
        System.out.println(MessageFormat.format("【{0}】发送消息：{1}", colleague.getName(), msg));

        if (!colleagues.contains(colleague)){
            colleagues.add(colleague);
            // 添加同事类时，同时设置它的中介者
            colleague.setMediator(this);

            System.out.println(MessageFormat.format("【{0}】加入群聊。", colleague.getName()));
        }
    }
}

/**
 * 聊天同事类
 */
public abstract class ChatColleague {

    private String name;
    /**
     * 维持对中介者的引用
     */
    protected ChatMediator mediator;

    public ChatColleague(String name) {
        this.name = name;
    }

    public void setMediator(ChatMediator mediator) {
        this.mediator = mediator;
    }

    public String getName() {
        return this.name;
    }

    /**
     * 发送信息。通常是调用中介者的操作方法完成
     * @param msg 消息内容
     */
    public abstract void sendMessage(String msg);

    /**
     * 自用方法
     * @param msg
     */
    public abstract void receiveMessage(String msg);
}

/**
 * 聊天用户：实现聊天同事类的具体方法
 */
public class ChatUser extends ChatColleague {

    public ChatUser(String name) {
        super(name);
    }

    @Override
    public void sendMessage(String msg) {
        mediator.sendMessage(msg, this);
    }

    @Override
    public void receiveMessage(String msg) {
        System.out.println(MessageFormat.format("【{0}】收到消息：{1}", getName(), msg));
    }
}
```

客户端调用代码：

```java
class client{
    public static void main(String[] args) {
        // 聊天用户
		ChatColleague zhangSan = new ChatUser("张三");
		ChatColleague liSi = new ChatUser("李四");
		ChatColleague wangWu = new ChatUser("王五");

		// 群聊中介者
		ChatMediator chatMediator = new GroupChatMediator();
		// 加入到群聊的用户
		chatMediator.addUser(liSi);
		chatMediator.addUser(wangWu);
        chatMediator.addUser(zhangSan);

		// 有人发了消息
		zhangSan.sendMessage("你们好，我是张三。经常出现在罗老师案例中的那个张三");
    }
}
```

运行结果：

```
【李四】加入群聊。
【王五】加入群聊。
【张三】加入群聊。
【张三】发送消息：你们好，我是张三。经常出现在罗老师案例中的那个"张三"。
【李四】收到消息：你们好，我是张三。经常出现在罗老师案例中的那个"张三"。
【王五】收到消息：你们好，我是张三。经常出现在罗老师案例中的那个"张三"。
```


### 命令模式
命令模式-请求**发送者**与**接收者**的解耦
#### 定义
命令模式（Command Pattern）：
- 将一个请求封装为一个对象，从而让我们用不同的请求对客户进行参数化；
- 对请求排队或者记录请求日志，以及支持可撤销的动作。

命令模式可以使发送者与接收者之间没有直接引用关系，发送请求的对象只需知道如何发送请求，而不用知道如何完成请求。

#### UML类图

![命令模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Command.drawio.png)

#### 结构
- 调用者：
  - 请求发送者，只与抽象命令类存在关联关系，无需知道谁是接收者。
- **抽象命令类**：
  - 声明执行接口，用于调用接收者的相关操作。
- 具体命令类：
  - 实现抽象命令，与具体接收者存在引用关系，从而在实现接口时调用接收者的方法。
- 接收者：
  - 接收者执行具体的业务操作。

#### 效果
优点：
1. 减低系统耦合度。请求者和接收者完全解耦。
2. 添加新的命令很容易，不需修改现有代码，符合开闭原则。
3. 为请求的撤销(undo)和恢复(redo)提供了一种实现方案。
4. 可以较容易的设计一个命令队列或宏命令。

缺点：
- 可能会导致系统有过多的命令类。因为每一个接收者的调用操作都需要设计一个具体命令类。

##### 使用场景
1. 需要将请求和接收解耦时。
2. 系统需要在不同的时间指定请求、将请求排队和执行请求。
3. 系统需要支持命令的撤销和恢复操作时。
4. 系统需要将一组操作组合在一起形成宏命令。

### 责任链模式
责任链模式-请求的链式处理
#### 定义
责任链模式（Chain of Responsibility Pattern）：
- 避免请求发送者与接收者耦合在一起，让多个对象都有可能接收请求，将这些对象连接成一条链。将请求沿着这条链路传递，直到有对象可以处理它为止。

#### UML类图

![责任链模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-ChainOfResponsibility.drawio.png)


#### 结构
责任链模式的核心在于引入了抽象处理者。其结构如下：
- 抽象处理者：
  - 定义一个处理请求的接口，具体的处理方式由子类实现。
  - 维持一个继任者对象的引用。通过该引用可将处理者连成一条链路。
- 具体处理者：
  - 判断能否处理请求，不能处理时则传递给下一个继任者对象处理。

#### 效果
优点：
1. 逐级处理：请求会逐级传递给继任者，直到某个继任者处理或者请求被拒绝。
2. 灵活性：业务调整不会影响原有的逻辑，只需对新的链路环节进行调整。

缺点：
- 长链路可能会影响系统性能。
- 如果建链不当，可能会导致死循环。

##### 具体应用
- Spring的过滤器链和拦截器链用的就是责任链模式。

## 资料引用
[1] [《设计模式 Java版本》](https://www.bookstack.cn/books/design-pattern-java)