# PHP设计模式

设计模式之间的关系：

![](http://images.cnitblog.com/blog/381060/201310/08191337-82dda0937819464bbb7746583e264171.jpg)

设计模式总概况：![](http://images.cnitblog.com/blog/381060/201310/08191339-2b14278bb9a54d1798b6fc28b6370bc5.jpg)

## 一、设计原则

### 1、单一职责原则

一个类，只有一个引起它变化的原因。应该只有一个职责。每一个职责都是变化的一个轴线，如果一个类有一个以上的职责，这些职责就耦合在了一起。这会导致脆弱的设计。当一个职责发生变化时，可能会影响其它的职责。另外，多个职责耦合在一起，会影响复用性。例如：要实现逻辑和界面的分离。

### 2、开闭原则（Open Close Principle）

开闭原则就是说**对扩展开放，对修改关闭**。在程序需要进行拓展的时候，不能去修改原有的代码，实现一个热插拔的效果。所以一句话概括就是：为了使程序的扩展性好，易于维护和升级。想要达到这样的效果，我们需要使用接口和抽象类，后面的具体设计中我们会提到这点。

### 3、里氏代换原则（Liskov Substitution Principle）

里氏代换原则\(Liskov Substitution Principle LSP\)面向对象设计的基本原则之一。 里氏代换原则中说，任何基类可以出现的地方，子类一定可以出现。 LSP是继承复用的基石，只有当衍生类可以替换掉基类，软件单位的功能不受到影响时，基类才能真正被复用，而衍生类也能够在基类的基础上增加新的行为。里氏代换原则是对“开-闭”原则的补充。实现“开-闭”原则的关键步骤就是抽象化。而基类与子类的继承关系就是抽象化的具体实现，所以里氏代换原则是对实现抽象化的具体步骤的规范。

### 4、依赖倒转原则（Dependence Inversion Principle）

所谓依赖倒置原则（Dependence Inversion Principle）就是要依赖于抽象，不要依赖于具体。简单的说就是要求对抽象进行编程，不要对实现进行编程，这样就降低了客户与实现模块间的耦合。

实现开闭原则的关键是抽象化，并且从抽象化导出具体化实现，如果说开闭原则是面向对象设计的目标的话，那么依赖倒转原则就是面向对象设计的主要手段。

### 5、接口隔离原则（Interface Segregation Principle）

这个原则的意思是：使用多个隔离的接口，比使用单个接口要好。还是一个降低类之间的耦合度的意思，从这儿我们看出，其实设计模式就是一个软件的设计思想，从大型软件架构出发，为了升级和维护方便。所以上文中多次出现：降低依赖，降低耦合。

### 6、合成复用原则（Composite Reuse Principle）

合成复用原则就是指在一个新的对象里通过关联关系（包括组合关系和聚合关系）来使用一些已有的对象，使之成为新对象的一部分；新对象通过委派调用已有对象的方法达到复用其已有功能的目的。简言之：要尽量使用组合/聚合关系，少用继承。

### 7、迪米特法则（最少知道原则）（Demeter Principle）

为什么叫最少知道原则，就是说：一个实体应当尽量少的与其他实体之间发生相互作用，使得系统功能模块相对独立。也就是说一个软件实体应当尽可能少的与其他实体发生相互作用。这样，当一个模块修改时，就会尽量少的影响其他的模块，扩展会相对容易，这是对软件实体之间通信的限制，它要求限制软件实体之间通信的宽度和深度。

## 二、创建型模式

在软件工程中，创建型模式是处理对象创建的设计模式，试图根据实际情况使用合适的方式创建对象。基本的对象创建方式可能会导致设计上的问题，或增加设计的复杂度。创建型模式通过以某种方式控制对象的创建来解决问题。

创建型模式由两个主导思想构成。一是将系统使用的具体类封装起来，二是隐藏这些具体类的实例创建和结合的方式。

创建型模式又分为对象创建型模式和类创建型模式。对象创建型模式处理对象的创建，类创建型模式处理类的创建。详细地说，对象创建型模式把对象创建的一部分推迟到另一个对象中，而类创建型模式将它对象的创建推迟到子类中。

### [1、抽象工厂模式\(Abstract Factory\)](https://github.com/yafangmaster/design_pattern/blob/master/creational_patterns/01、抽象工厂模式%28Abstract Factory%29.md)

### [2、建造者模式\(Builder\)](https://github.com/yafangmaster/design_pattern/blob/master/creational_patterns/02、建造者模式%28Builder%29.md)

### [3、工厂方法模式\(Factory Method\)](https://github.com/yafangmaster/design_pattern/commit/30fc6707054c3326c71b390efaf4f51a2db95337)

### [4、原型模式\(Prototype\)](https://github.com/yafangmaster/design_pattern/blob/master/creational_patterns/04、原型模式%28Prototype%29.md)

### [5、单例模式\(Singleton\)](https://github.com/yafangmaster/design_pattern/blob/master/creational_patterns/05、单例模式%28Singleton%29.md)

## 三、结构型模式

结构型模式主要是用于处理类或者对象的组合，它描述了如何来类或者对象更好的组合起来，是从程序的结构上来解决模块之间的耦合问题。它主要包括适配器模式、桥接模式、组合模式、装饰模式、外观模式、享元模式、代理模式这个七个模式。

### [1、适配器模式\(Adapter\)](https://github.com/yafangmaster/design_pattern/blob/master/structural_patterns/01%E3%80%81%E9%80%82%E9%85%8D%E5%99%A8%E6%A8%A1%E5%BC%8F%28Adapter%29.md)

### [2、桥接模式\(Bridge\)](https://github.com/yafangmaster/design_pattern/blob/master/structural_patterns/02%E3%80%81%E6%A1%A5%E6%8E%A5%E6%A8%A1%E5%BC%8F%28Bridge%29.md)

### [3、组合模式\(Composite\)](https://github.com/yafangmaster/design_pattern/blob/master/structural_patterns/03%E3%80%81%E7%BB%84%E5%90%88%E6%A8%A1%E5%BC%8F%28Composite%29.md)

### [4、装饰者模式\(Decorator\)](https://github.com/yafangmaster/design_pattern/blob/master/structural_patterns/04%E3%80%81%E8%A3%85%E9%A5%B0%E8%80%85%E6%A8%A1%E5%BC%8F%28Decorator%29.md)

### [5、外观模式\(Facade\)](https://github.com/yafangmaster/design_pattern/blob/master/structural_patterns/05%E3%80%81%E5%A4%96%E8%A7%82%E6%A8%A1%E5%BC%8F%28Facade%29.md)

### [6、享元模式\(Flyweight\)](https://github.com/yafangmaster/design_pattern/blob/master/structural_patterns/06%E3%80%81%E4%BA%AB%E5%85%83%E6%A8%A1%E5%BC%8F%28Flyweight%29.md)

### [7、代理模式\(Proxy\)](https://github.com/yafangmaster/design_pattern/blob/master/structural_patterns/07%E3%80%81%E4%BB%A3%E7%90%86%E6%A8%A1%E5%BC%8F%28Proxy%29.md)



