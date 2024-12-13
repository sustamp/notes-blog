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

#### 效果
优点：
1. 客户端只需要关心产品对应的具体工厂，无需关心创建细节和具体产品类。
2. 多态性。所有的具体工厂类都具有同一抽象父类，工厂可以自主确定创建何种产品对象。
3. 加入新产品时，无须修改抽象工厂和抽象产品提供的接口，无须修改其他的具体工厂和具体产品，只要添加新的具体工厂和具体产品，也无须修改客户端。

缺点：
- 每个工厂只生产一类产品，可能会导致系统中存在大量的工厂类，势必会增加系统的开销。



### 单例模式

## 结构型模式（7）

### 适配器模式

### 外观模式

## 行为性模式（11）
### 策略模式

### 方法模板模式

### 观察者模式



## 资料引用
[1] [《设计模式 Java版本》](https://www.bookstack.cn/books/design-pattern-java)