### 04、建造者模式\(Builder\)

对于建造者模式而已，它主要是将一个复杂对象的构建与表示分离，使得同样的构建过程可以创建不同的表示。适用于那些产品对象的内部结构比较复杂。

建造者模式将复杂产品的构建过程封装分解在不同的方法中，使得创建过程非常清晰，能够让我们更加精确的控制复杂产品对象的创建过程，同时它隔离了复杂产品对象的创建和使用，使得相同的创建过程能够创建不同的产品。但是如果某个产品的内部结构过于复杂，将会导致整个系统变得非常庞大，不利于控制，同时若几个产品之间存在较大的差异，则不适用建造者模式，毕竟这个世界上存在相同点大的两个产品并不是很多，所以它的使用范围有限。其UML结构图：

![](http://images.cnitblog.com/blog/381060/201310/08191342-1fb6ec5ff4734e7baaa87bb950cd8385.jpg)

参与者：

Builder：抽象建造者。它声明为创建一个Product对象的各个部件指定的抽象接口。  
ConcreteBuilder：具体建造者。实现抽象接口，构建和装配各个部件。  
Director：指挥者。构建一个使用Builder接口的对象。它主要是用于创建一个复杂的对象，它主要有两个作用，一是：隔离了客户与对象的生产过程，二是：负责控制产品对象的生产过程。  
Product：产品角色。一个具体的产品对象。

```php
<?php 
/**
* chouxiang builer
*/
abstract class Builder
{
  protected $car;
  abstract public function buildPartA();
  abstract public function buildPartB();
  abstract public function buildPartC();
  abstract public function getResult();
}

class CarBuilder extends Builder
{
  function __construct()
  {
      $this->car = new Car();
  }
  public function buildPartA(){
      $this->car->setPartA('发动机');
  }

  public function buildPartB(){
      $this->car->setPartB('轮子');
  }

  public function buildPartC(){
      $this->car->setPartC('其他零件');
  }

  public function getResult(){
      return $this->car;
  }
}

class Car
{
  protected $partA;
  protected $partB;
  protected $partC;

  public function setPartA($str){
      $this->partA = $str;
  }

  public function setPartB($str){
      $this->partB = $str;
  }

  public function setPartC($str){
      $this->partC = $str;
  }

  public function show()
  {
      echo "这辆车由：".$this->partA.','.$this->partB.',和'.$this->partC.'组成';
  }
}

class Director
{
  public $myBuilder;

  public function startBuild()
  {
      $this->myBuilder->buildPartA();
      $this->myBuilder->buildPartB();
      $this->myBuilder->buildPartC();
      return $this->myBuilder->getResult();
  }

  public function setBuilder(Builder $builder)
  {
      $this->myBuilder = $builder;
  }
}

$carBuilder = new CarBuilder();
$director = new Director();
$director->setBuilder($carBuilder);
$newCar = $director->startBuild();
$newCar->show();
```



