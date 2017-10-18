### 5、单例模式\(Singleton\)

单例模式，从字面上看就是一个实例的意思。所以它的定义就是确保某一个类只有一个实例，并且提供一个全局访问点。

单例模式具备如下几个特点：

1、只有一个实例。

2、能够自我实例化。

3、提供全局访问点。

所以说当系统中只需要一个实例对象或者系统中只允许一个公共访问点，除了这个公共访问点外，不能通过其他访问点访问该实例时，可以使用单例模式。

单例模式的主要优点就是节约系统资源、提高了系统效率，同时也能够严格控制客户对它的访问。也许就是因为系统中只有一个实例，这样就导致了单例类的职责过重，违背了“单一职责原则”，同时也没有抽象类，所以扩展起来有一定的困难。其UML结构图非常简单，就只有一个类：

[![](http://images.cnitblog.com/blog/381060/201310/08191350-7ffc1abdcf934de1abd3f7dcc683d992.png "单例模式")](http://images.cnitblog.com/blog/381060/201310/08191349-f6174c940aa44d86a765ac983778f699.png)

参与者：

Singleton：单例。

```php
<?php
/**
 * 设计模式之单例模式
 * $_instance必须声明为静态的私有变量
 * 构造函数必须声明为私有,防止外部程序new类从而失去单例模式的意义
 * getInstance()方法必须设置为公有的,必须调用此方法以返回实例的一个引用
 * ::操作符只能访问静态变量和静态函数
 * new对象都会消耗内存
 * 使用场景:最常用的地方是数据库连接。
 * 使用单例模式生成一个对象后，该对象可以被其它众多对象所使用。
 */

class man{

    //保存例实例在此属性中
    private static $_instance;

    //构造函数声明为private,防止直接创建对象
    private function __construct(){
        echo '我被实例化了';
    }

    //单例方法
    public static function getInstance(){
        var_dump(isset(self::$_instance));
        if(!isset(self::$_instance)){
            self::$_instance = new self();
        }else{
            return self::$_instance;
        }
    }

    //阻止用户复制对象实例
    private function __clone(){
        trigger_error('Clone is not allow', E_USER_ERROR);
    }

    function test(){
        echo 'Test';
    }
}

// 这个写法会出错，因为构造方法被声明为private
//$man = new man();

// 下面将得到Example类的单例对象
$test = man::getInstance();
$test = man::getInstance();
$test->test();

// 复制对象将导致一个E_USER_ERROR.
//$test_clone = clone $test;
```



