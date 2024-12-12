---
layout: post-custom
title: "设计模式"
---

## 概述
设计模式(Design Pattern)是一套被反复使用、多数人知晓的、经过分类编目的、代码设计经验的总结，使用设计模式是为了可重用代码、让代码更容易被他人理解并且保证代码可靠性。

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
在支持可维护性的同时，提高系统的可复用性是一个至关重要的问题，如何同时提高一个软件系统的**可维护性**和**可复用性**是面向对象设计需要解决的核心问题之一。

面向对象设计原则为支持可维护性复用而诞生，这些原则蕴含在很多设计模式中，它们是从许多设计方案中总结出的指导性原则。面向对象设计原则也是我们用于评价一个设计模式的使用效果的重要指标之一。

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

#### Single responsiblity principle（单一职责原则）
SRP是最简单的面向对象设计原则，它用于控制类的粒度大小，简单定义为：
- 一个类或模块应该只负责一个职责或功能。

> 一个类不能太累！

单一职责原则告诉我们：
- 在软件系统中，一个类（大到模块，小到方法）承担的职责越多，它被复用的可能性就越小。
- 而且一个类承担的职责过多，就相当于将这些职责耦合在一起，当其中一个职责变化时，可能会影响其他职责的运作，因此要将这些职责进行分离，将不同的职责封装在不同的类中，即将不同的变化原因封装在不同的类中。
- 如果多个职责总是同时发生改变则可将它们封装在同一类中。

#### Open-Closed principle（开闭原则）
对模块、类、方法拓展开放，对修改关闭。

#### Liskov substitution principle（里氏替换原则）
子类能够替换父类对象出现的任何地方，并且保证原来程序的逻辑行为不变。

#### Inteface segregation principle（接口隔离原则）
为各个类建立它们需要的专门接口，而不要试图去建立一个很庞大的接口供所有依赖它的类去调用。例如UserService接口有登录、查询、注册等一些列方法，而删除操作是慎重的，且可能是特定系统才拥有的功能，所以可以专门定义一个RestrictedUserService接口，专门实现删除功能。具体调用方可以根据实际需要实现各自需要的一个或一组接口。

#### Dependency inversion principle（依赖倒置原则）
- 高层模块不应依赖于底层模块，二者都应该依赖于抽象。即：高层模块和底层模块共同依赖同一个抽象，面向抽象类或接口编程。
- 抽象不应该依赖实现细节，细节应该依赖抽象。

传统的从上到下设计方式是逐级依赖，即高层模块->级模块->底层模块。这样高层模块就依赖底层模块了，当某一模块需要修改，可能牵一发而动全身，影响较多不易维护。

而**依赖倒置**，就是高层模块->抽象层<-底层模块，使得它们同依赖抽象层，这样减少了类之间的耦合性，不同模块都可独立针对接口/抽象进行并行开发，可维护性大大增加。

## 创建型模式（6）

### 工厂方法模式

### 单例模式

## 结构型模式（7）

### 适配器模式

### 外观模式

## 行为性模式（11）
### 策略模式

### 方法模板模式

### 观察者模式