### 02、抽象工厂模式\(Abstract Factory\)

所谓抽象工厂模式就是她提供一个接口，用于创建相关或者依赖对象的家族，而不需要明确指定具体类。他允许客户端使用抽象的接口来创建一组相关的产品，而不需要关系实际产出的具体产品是什么。这样一来，客户就可以从具体的产品中被解耦。它的优点是隔离了具体类的生成，使得客户端不需要知道什么被创建了，而缺点就在于新增新的行为会比较麻烦，因为当添加一个新的产品对象时，需要更加需要更改接口及其下所有子类。其UML结构图如下：

![](http://images.cnitblog.com/blog/381060/201310/08191340-e13eefcde4ee4e029ee5df41067866dd.png)

参与者：

AbstractFactory：抽象工厂。抽象工厂定义了一个接口，所有的具体工厂都必须实现此接口，这个接口包含了一组方法用来生产产品。

ConcreteFactory：具体工厂。具体工厂是用于生产不同产品族。要创建一个产品，客户只需要使用其中一个工厂完全不需要实例化任何产品对象。

AbstractProduct：抽象产品。这是一个产品家族，每一个具体工厂都能够生产一整组产品。

Product：具体产品。

```php
<?php
/**
 * 抽象产品A
 */
interface AbstractProductA {

    /**
     * 取得产品名
     */
    public function getName();
}

/**
 * 抽象产品B
 */
interface AbstractProductB {

    /**
     * 取得产品名
     */
    public function getName();
}

/**
 * 具体产品Ａ1
 */
class ProductA1 implements AbstractProductA {
    private $_name;

    public function __construct() {
        $this->_name = 'product A1';
    }

    public function getName() {
        return $this->_name;
    }
}


/**
 * 具体产品Ａ2
 */
class ProductA2 implements AbstractProductA {
    private $_name;

    public function __construct() {
        $this->_name = 'product A2';
    }

    public function getName() {
        return $this->_name;
    }
}


/**
 * 具体产品B1
 */
class ProductB1 implements AbstractProductB {
    private $_name;

    public function __construct() {
        $this->_name = 'product B1';
    }

    public function getName() {
        return $this->_name;
    }
}

/**
 * 具体产品B2
 */
class ProductB2 implements AbstractProductB {
    private $_name;

    public function __construct() {
        $this->_name = 'product B2';
    }

    public function getName() {
        return $this->_name;
    }
}
/**
 * 抽象工厂
 */
interface AbstractFactory {
    /**
     * 创建等级结构为A的产品的工厂方法
     */
    public function createProductA();

    /**
     * 创建等级结构为B的产品的工厂方法
     */
    public function createProductB();

}

/**
 * 具体工厂1
 */
class ConcreteFactory1 implements AbstractFactory{

    public function createProductA() {
        return new ProductA1();
    }

    public function createProductB() {
        return new ProductB1();
    }
}


/**
 * 具体工厂2
 */
class ConcreteFactory2 implements AbstractFactory{

    public function createProductA() {
        return new ProductA2();
    }

    public function createProductB() {
        return new ProductB2();
    }
}




/**
 * 客户端
 */
class Client {

    /**
     * Main program.
     */
    public static function main() {
        self::run(new ConcreteFactory1());
        self::run(new ConcreteFactory2());
    }

    /**
     * 调用工厂实例生成产品，输出产品名
     * @param $factory AbstractFactory 工厂实例
     */
    public static function run(AbstractFactory $factory) {
        $productA = $factory->createProductA();
        $productB = $factory->createProductB();
        echo $productA->getName(), '<br />';
        echo $productB->getName(), '<br />';
    }

}

Client::main();

//打印数据
//product A1
//product B1
//product A2
//product B2
?>
```



