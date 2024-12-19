---
layout: post-custom
title: "设计模式"
---

## 概述
设计模式(Design Pattern)是一套被反复使用、多数人知晓、经过分类的、代码设计经验的总结，使用设计模式是为了可重用代码、让代码更容易被他人理解并且保证代码可靠性。

设计模式的出现可以让我们站在前人的肩膀上，通过一些成熟的设计方案来指导新项目的开发和设计，以便于我们开发出具有更好的灵活性和可扩展性，也更易于复用的软件系统。

设计模式的组成要素一般包含：
- 模式名称
- 问题
- 目的
- 解决方案
- 效果

**模式名称(Pattern Name)** 通过一两个词来描述模式的问题、解决方案和效果，以便更好地理解模式并方便开发人员之间的交流，绝大多数模式都是根据其功能或模式结构来命名的。

**问题(Problem)** 描述了应该在何时使用模式，它包含了设计中存在的问题以及问题存在的原因。

**解决方案(Solution)** 描述了一个设计模式的组成成分，以及这些组成成分之间的相互关系，各自的职责和协作方式，通常解决方案通过`UML类图`和`核心代码`来进行描述。

**效果(Consequences)** 描述了模式的**优缺点**以及在使用模式时应权衡的问题。

常用设计模式一览表：

|类型|模式名称|学习难度|使用频率|
|-|-|-|-|
|创建型模式 Creational Pattern|单例模式 Singleton Pattern|★☆☆☆☆|★★★★☆|
|Creational Pattern|简单工厂模式 Simple Factory Pattern|★★☆☆☆|★★★☆☆|
|Creational Pattern|工厂方法模式 Factory Method Pattern|★★☆☆☆|★★★★★|
|Creational Pattern|抽象工厂模式 Abstract Factory Pattern|★★★★☆|★★★★★|
|Creational Pattern|原型模式 Prototype Pattern|★★★☆☆|★★★☆☆|
|Creational Pattern|建造者模式 Builder Pattern|★★★★☆|★★☆☆☆|
|结构型模式 Structural Pattern|	适配器模式 Adapter Pattern|★★☆☆☆|★★★★☆|
|Structural Pattern|桥接模式 Bridge Pattern|★★★☆☆|★★★☆☆|
|Structural Pattern|组合模式 Composite Pattern|★★★☆☆|★★★★☆
|Structural Pattern|装饰模式 Decorator Pattern|★★★☆☆|★★★☆☆|
|Structural Pattern|外观模式 Façade Pattern|★☆☆☆☆|★★★★★|
|Structural Pattern|享元模式 Flyweight Pattern|★★★★☆|★☆☆☆☆|
|Structural Pattern|代理模式 Proxy Pattern|★★★☆☆|★★★★☆|
|行为型模式 Behavioral Pattern|职责链模式 Chain of Responsibility Pattern|★★★☆☆|★★☆☆☆|
|Behavioral Pattern|命令模式 Command Pattern|★★★☆☆|★★★★☆|
|Behavioral Pattern|解释器模式 Interpreter Pattern|★★★★★|★☆☆☆☆|
|Behavioral Pattern|迭代器模式 Iterator Pattern|★★★☆☆|★★★★★|
|Behavioral Pattern|中介者模式 Mediator Pattern|★★★☆☆|★★☆☆☆|
|Behavioral Pattern|备忘录模式 Memento Pattern|★★☆☆☆|★★☆☆☆|
|Behavioral Pattern|观察者模式 Observer Pattern|★★★☆☆|★★★★★|
|Behavioral Pattern|状态模式 State Pattern|★★★☆☆|★★★☆☆|
|Behavioral Pattern|策略模式 Strategy Pattern|★☆☆☆☆|★★★★☆|
|Behavioral Pattern|模板方法模式 Template Method Pattern|★★☆☆☆|★★★☆☆|
|Behavioral Pattern|访问者模式 Visitor Pattern|★★★★☆|★☆☆☆☆|

## 面向对象设计原则
面向对象设计需要解决的核心问题之一是如何同时提高一个软件系统的：
- **可维护性**
- **可复用性**

面向对象设计原则为支持可维护性复用而诞生，这些原则蕴含在很多设计模式中，它们是从许多设计方案中总结出的指导性原则。

面向对象设计原则也是我们用于评价一个设计模式的使用效果的重要指标之一。

### SOLID-CL设计原则
最常见的7种面向对象设计原则如下表所示:

|设计原则|定义|使用频率|
|---|---|---|
|单一职责原则 (Single Responsibility Principle, SRP)|一个类只负责一个功能领域中的相应职责|★★★★☆|
|开闭原则 (Open-Closed Principle, OCP)|软件实体应对扩展开放，而对修改关闭|★★★★★|
|里氏代换原则 (Liskov Substitution Principle, LSP)|所有引用基类对象的地方能够透明地使用其子类的对象|★★★★★|
|接口隔离原则 (Interface Segregation Principle, ISP)|使用多个专门的接口，而不使用单一的总接口|★★☆☆☆|
|依赖倒转原则 (Dependence Inversion Principle, DIP)|抽象不应该依赖于细节，细节应该依赖于抽象|★★★★★|
|合成复用原则 (Composite Reuse Principle, CRP)|尽量使用对象组合，而不是继承来达到复用的目的|	★★★★☆|
|迪米特法则 (Law of Demeter, LoD)|一个软件实体应当尽可能少地与其他实体发生相互作用|	★★★☆☆|

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
- 例如：我喜欢动物，那我一定喜欢狗，因为狗是动物的子类；但是我喜欢狗，不能据此断定我喜欢动物，因为我并不喜欢老鼠，虽然它也是动物。

**里氏代换原则**是**实现开闭原则**的重要方式之一，由于使用基类对象的地方都可以使用子类对象，因此在程序中尽量使用基类类型来对对象进行定义，而在运行时再确定其子类类型，用子类对象来替换父类对象。

使用LSP要注意如下几个问题：
- 尽量把父类设计为`抽象类`或`接口`，子类实现父类的所有方法。
- 增加新功能可以通过增加新的子类来实现，而无须修改原有子类的代码。

在CRM(Customer Relationship Management)系统中，客户（Customer）可以分为VIP客户和普通客户，系统需要提供一个发送Email的功能。以下是UML类图示意：

![LSP原则UML类图](https://sustamp.github.io/assets/pictures/design-patterns/UML-LSP.png)

- 将`Customer`作为父类，`VIPCustomer`和`CommonCustomer`作为子类。
- 邮件发送`EmailSender`接受父类对象`Customer`作为参数，根据LSP原则，必然也能接受子类对象。

#### ISP(接口隔离原则)
ISP(Interface Segregation Principle)定义：
- 使用多个专门的接口，而不使用单一的总接口，即客户端不应该依赖那些它不需要的接口

为各个类建立它们需要的专门接口，而不要试图去建立一个很庞大的接口供所有依赖它的类去调用。

举个例子，在CRM系统中，客户数据显示模块具备如下功能：
- 从文件中读取数据
- 将数据转换为XML格式
- 图表显示
- 文字报表
  
用UML类图示意如下：
![ISP原则UML类图](https://sustamp.github.io/assets/pictures/design-patterns/UML-ISP.png)


#### DIP(依赖倒置原则)
如果说开闭原则是面向对象设计的目标的话，那么依赖倒转原则就是面向对象设计的主要实现机制之一。它是**系统抽象化**的具体实现。

DIP(Dependency Inversion Principle)原则核心思想是：
- 高层模块不应该依赖底层模块，二者都应该依赖**抽象**。
- 抽象不依赖细节，细节应该依赖于**抽象**。

换言之：
- 针对`接口`编程，而不是针对实现编程。

DIP要求我们在程序代码中传递参数时或在关联关系中，尽量引用层次高的抽象层类。即：
- 使用`接口`和`抽象类`进行`变量类型声明`、`参数类型声明`、`方法返回类型声明`，以及`数据类型的转换`等，而不要用具体类来做这些事情。


举例：司机需要不同的驾照才可以驾驶不同的载具，用UML类图表示DIP原则如下：

![DIP原则UML类图](https://sustamp.github.io/assets/pictures/design-patterns/UML-DIP.png)


传统的从上到下设计方式是逐级依赖，即`高层模块` -> `次级模块` -> `底层模块`。这样高层模块就依赖底层模块了，当某一模块需要修改，可能牵一发而动全身，影响较多不易维护。

而**依赖倒置**，就是`高层模块` -> `抽象层` <- `底层模块`，使得它们同依赖抽象层，这样减少了类之间的耦合性，不同模块都可独立针对`接口` / `抽象类`进行并行开发，可维护性大大增加。


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




## 创建型模式（6）

### 简单工厂模式

#### 定义
简单工厂模式(Simple Factory Pattern)：
- 定义一个工厂类，它可以根据参数的不同返回不同类的实例，被创建的实例通常都具有共同的父类。

#### UML类图

![简单工厂模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Simple-Factory.drawio.png)

#### 结构
简单工厂模式的结构如下：
- 工厂类(Factory)：通过参数决定创建哪个具体产品。
- 产品角色(Product)：抽象类/接口
- 具体产品(ConcreteProduct)

#### 效果
优点：
- 实现了对象创建和使用的分离。工厂类包含必要的判断逻辑，可以决定在什么时候创建哪一个产品类的实例，客户端可以免除直接创建产品对象的职责
- 无须知道所创建的具体产品类的类名，只需要知道具体产品类所对应的参数即可.
- 通过引入配置文件，可以在不修改任何客户端代码的情况下更换和增加新的具体产品类，在一定程度上提高了系统的灵活性
  
缺点：
- 简单工厂类集中了`所有产品`的创建逻辑，职责过重，一旦不能正常工作，整个系统都要受到影响。
- 简单工厂模式由于使用了静态工厂方法，造成工厂角色无法形成基于继承的等级结构。
- 当系统中需要引入新产品时，这必定要修改工厂类的源代码，将违背“开闭原则”。

如何实现增加新产品而不影响已有代码？工厂方法模式应运而生。

### 工厂方法模式
#### 定义
工厂方法模式(Factory Method Pattern)：
- 定义一个用于创建对象的接口，让子类决定将哪一个类实例化。

工厂方法模式让一个类的实例化延迟到其子类。

#### UML类图

![工厂模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Factory.drawio.png)

按照该类图，客户端的使用代码如下：

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
- 抽象工厂(Factory)：抽象类或接口，定义一个创建对象的接口。
- 具体工厂(ConcreateFactory)：实现抽象工厂，创建并返回具体产品类的实例。
- 抽象产品(Product)：抽象类或接口。
- 具体产品(ConcreateProduct)：实现抽象产品。具体产品由具体工厂创建，二者为一对一关系。

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

### 抽象工厂模式
#### 定义
抽象工厂模式(Abstract Factory Pattern)：
- 提供一个**创建一系列**相关或相互依赖**对象**的接口，而无须指定它们具体的类。

抽象工厂模式又称为Kit模式，它是一种对象创建型模式。

#### UML类图

![抽象工厂模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Abstract-Factory.drawio.png)


#### 结构
- 抽象工厂：声明一组用于创建一系列产品结构的方法，每一个方法对应一个的产品结构。
- 具体工厂：具体实现抽象工厂，生成一系列相同风格的具体产品。
- 抽象产品：每一个产品结构都是一个抽象类或接口，并声明产品所具有的业务方法。
- 具体产品：实现对应产品结构的业务方法。

与工厂方法模式一样，抽象工厂模式也可为每一种产品提供一组重载的工厂方法，以不同的方式对产品对象进行创建。

#### 效果
抽象工厂的应用场景是：
- 产品结构要稳定，设计完成之后，不会向系统中增加新的产品等级结构或者删除已有的产品等级结构。

因为当要增加一个新的产品结构 `IProductC` 时：
- 由于抽象工厂类 `IFactory` 目前没有 `createProductC()` 的方法，所以势必要修改抽象工厂的代码；
- 而后还要逐个修改具体工厂的实现方法；
- 此外还要修改客户端。

抽象工厂模式无法解决该问题，这也是抽象工厂模式最大的缺点。

综上，抽象工厂模式的主要缺点是：
- 当要增加新的产品结构时，会违反**开闭原则**。
  
优点：
- 对已有产品结构的进行产品风格的新增和拓展很方便，只需增加新的具体产品和对应的具体工厂即可，此时无需修改系统已有代码（Client通过配置文件配置具体工厂不算修改代码），符合**开闭原则**。
- 当一个产品族中的多个对象被设计成一起工作时，它能够保证客户端始终只使用风格相同的同一个具体工厂所生产的对象。


### 单例模式
为了确保对象的唯一性，我们通常会用单例模式来设计。

#### 定义
单例模式(Singleton Pattern)的定义：
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
原型模式(Prototype Pattern)定义如下：
- 使用原型实例指定创建对象的种类，并且通过拷贝这些原型创建新的对象。
  
原型模式的工作原理很简单：
- 将一个原型对象传给那个要发动创建的对象，这个要发动创建的对象通过请求原型对象拷贝自己来实现创建过程
- 创建克隆对象的工厂就是原型类自身，工厂方法由克隆方法来实现。


#### UML类图

![原型模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Prototype.drawio.png)

#### 结构
- 原型(Prototype)：它是`抽象类`或`接口`或`具体实现类`，声明克隆方法。
- 具体原型类(ConcretePrototype)：实现克隆方法，在克隆方法中返回自己的一个克隆对象。


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



## 结构型模式（7）

### 适配器模式
适配器模式-不兼容结构的协调。

#### 定义
适配器模式(Adapter Pattern)：
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

> 思考1：在对象适配器中，一个适配器能否适配多个适配者？如果能，应该如何实现？如果不能，请说明原因。  
> 思考2：在类适配器中，一个适配器能否适配多个适配者？如果能，应该如何实现？如果不能，请说明原因。

#### 结构
- **目标(Target)**：定义客户所需的目标和结构。可以是`接口`，`抽象类`或`具体类`。
- **适配器(Adapter)**: 作为转换器，调用`适配者`的接口或方法，将其结果和结构转换成符合`目标`的接口和结构。
- **被适配者(Adaptee)**：已经存在的对象。它本身具备已经定义好的接口和结构，但因为与`目标`期望结构不符，所以要被`适配器`适配，转换结果。


#### 效果
优点：
- 解耦：适配器模式将`目标`和`适配者`解耦，引入`适配器`来重用现有的`适配者`，无须修改原有结构。
- 增加了类的透明性和复用性：业务实现过程封装在`适配器`中，对客户端是透明的，且`适配者`不需改动，提高了复用性，可以被不同的系统或模块使用。
- 拓展性好：增加和更换适配器不需要修改原有代码。完全符合**开闭原则**。
- 一个对象适配器可以把多个不同的适配者适配到同一个目标。

缺点：
- 在适配器中更换适配者的某些方法会比较麻烦。
  - 可以先做一个适配者类的子类，将适配者类的方法置换掉，然后再把适配者类的子类当做真正的适配者进行适配，实现过程较为复杂。


### 组合模式
组合模式-树形结构的处理

#### 定义

### 装饰模式
装饰模式-拓展系统功能

#### 定义



## 行为性模式（11）
### 策略模式
策略模式-算法的封装与切换

#### 定义
策略模式(Strategy Pattern)定义：
- 定义一系列算法类（策略），将每一个算法封装起来，并让它们可以相互替换，策略模式让算法独立于使用它的客户而变化。

策略模式的主要目的是：
- 将算法的定义与使用分开。

它把算法的责任和算法本身分割开，委派给不同的对象管理。

  
#### UML类图

![策略模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Strategy.drawio.png)

> 思考：一个环境类Context能否对应多个不同的策略等级结构？如何设计？

#### 结构
- 环境类(Context)：它是使用算法的角色。在环境类中维持一个对抽象策略类的引用实例，用于定义所采用的策略。
- 抽象策略类(Strategy)：是所有策略类的父类，为算法声明抽象方法。它可以是`抽象类`,`接口`或`具体类`
- 具体策略类(ConcreteStrategy)：实现具体算法。

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


### 模板方法模式
#### 定义
模板方法模式(Template Method Pattern)定义：
- 定义一个操作中算法的框架，而将一些步骤延迟到子类中。模板方法模式使得子类可以不改变一个算法的结构即可重定义该算法的某些特定步骤。



### 观察者模式
观察者模式-对象间的联动
#### 定义
观察者模式(Observer Pattern)定义：
- 定义对象间的一种一对多依赖关系，一个或多个对象依赖于某一个对象，当这个对象的状态发生改变时，其相关依赖的对象都得到通知并被触发自动更新。

#### UML类图

观察者模式简单类图：

![观察者模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Observer.drawio.png)

发布订阅模式UML类图：

![发布订阅模式UML类图](https://sustamp.github.io/assets/pictures/design-patterns/Pattern-Publish-Subscribe.drawio.png)

#### 结构
观察者模式的基本结构是：
- `主题(Subject)`：它作为`被观察者`，是`观察者`的观察**目标**。持有观察者对象的引用，并提供注册、注销和通知观察者的接口。它可以是`接口`、`抽象类`或`具体类`。
- `具体主题(ConcreteSubject)`：存储实际状态的具体主题，当状态发生变化时，则触发通知其相关的观察者。
- `观察者(Observer)`：通常设计为`接口`，声明`update()`方法，表示当目标状态发生变化时产生的行为。
- `具体观察者(ConcreteObserver)`：具体实现更新逻辑。


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


## 资料引用
[1] [《设计模式 Java版本》](https://www.bookstack.cn/books/design-pattern-java)