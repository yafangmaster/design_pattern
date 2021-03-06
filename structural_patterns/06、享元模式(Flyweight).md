### 6、享元模式\(Flyweight\)

在一个系统中对象会使得内存占用过多，特别是那些大量重复的对象，这就是对系统资源的极大浪费。享元模式对对象的重用提供了一种解决方案，它使用共享技术对相同或者相似对象实现重用。

享元模式就是运行共享技术有效地支持大量细粒度对象的复用。系统使用少量对象,而且这些都比较相似，状态变化小，可以实现对象的多次复用。这里有一点要注意：享元模式要求能够共享的对象必须是细粒度对象。

享元模式通过共享技术使得系统中的对象个数大大减少了，同时享元模式使用了内部状态和外部状态，同时外部状态相对独立，不会影响到内部状态，所以享元模式能够使得享元对象在不同的环境下被共享。同时正是分为了内部状态和外部状态，享元模式会使得系统变得更加复杂，同时也会导致读取外部状态所消耗的时间过长。

[![](http://images.cnitblog.com/blog/381060/201310/08191406-1487fd3e50e847e4b090ad5993786f6d.png "享元模式")](http://images.cnitblog.com/blog/381060/201310/08191406-32f110ca782745c39c0de446985616aa.png)

参与者：

Flyweight: 抽象享元类。所有具体享元类的超类或者接口，通过这个接口，Flyweight可以接受并作用于外部专题。  
ConcreteFlyweight: 具体享元类。指定内部状态，为内部状态增加存储空间。  
UnsharedConcreteFlyweight: 非共享具体享元类。指出那些不需要共享的Flyweight子类。  
FlyweightFactory: 享元工厂类。用来创建并管理Flyweight对象，它主要用来确保合理地共享Flyweight，当用户请求一个Flyweight时，FlyweightFactory就会提供一个已经创建的Flyweight对象或者新建一个（如果不存在）。



