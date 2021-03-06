### 03、工厂方法模式\(Factory Method\)

作为抽象工厂模式的孪生兄弟，工厂方法模式定义了一个创建对象的接口，但由子类决定要实例化的类是哪一个，也就是说工厂方法模式让实例化推迟到子类。

工厂方法模式非常符合“开闭原则”，当需要增加一个新的产品时，我们只需要增加一个具体的产品类和与之对应的具体工厂即可，无须修改原有系统。同时在工厂方法模式中用户只需要知道生产产品的具体工厂即可，无须关心产品的创建过程，甚至连具体的产品类名称都不需要知道。虽然他很好的符合了“开闭原则”，但是由于每新增一个新产品时就需要增加两个类，这样势必会导致系统的复杂度增加。其UML结构图：

[![](http://images.cnitblog.com/blog/381060/201310/08191345-b284145d01324a29a331abbe0285df33.png "工厂方法模式")](http://images.cnitblog.com/blog/381060/201310/08191344-c19aecfcfd1a4a63bb7a2aa698cb25c7.png)

参与者：

Product：抽象产品。所有的产品必须实现这个共同的接口，这样一来，使用这些产品的类既可以引用这个接口。而不是具体类 。

ConcreteProduct：具体产品。

Creator：抽象工厂。它实现了所有操纵产品的方法，但不实现工厂方法。Creator所有的子类都必须要实现factoryMethod\(\)方法。

ConcreteCreator：具体工厂。制造产品的实际工厂。它负责创建一个或者多个具体产品，只有ConcreteCreator类知道如何创建这些产品。

```php
<?php 
interface Animal{
  public function run();
  public function say();
}
class Cat implements Animal
{
  public function run(){
      echo "I ran slowly <br>";
  }
  public function say(){
      echo "I am Cat class <br>";
  }
}
class Dog implements Animal
{
  public function run(){
      echo "I'm running fast <br>";
  }
  public function say(){
      echo "I am Dog class <br>";
  }
}
abstract class Factory{
  abstract static function createAnimal();
}
class CatFactory extends Factory
{
  public static function createAnimal()
  {
      return new Cat();
  }
}
class DogFactory extends Factory
{
  public static function createAnimal()
  {
      return new Dog();
  }
}

$cat = CatFactory::createAnimal();
$cat->say();
$cat->run();

$dog = DogFactory::createAnimal();
$dog->say();
$dog->run();
```



