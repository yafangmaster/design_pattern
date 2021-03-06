### 3、组合模式\(Composite\)

组合模式组合多个对象形成树形结构以表示“整体-部分”的结构层次。它定义了如何将容器对象和叶子对象进行递归组合，使得客户在使用的过程中无须进行区分，可以对他们进行一致的处理。

在使用组合模式中需要注意一点也是组合模式最关键的地方：叶子对象和组合对象实现相同的接口。这就是组合模式能够将叶子节点和对象节点进行一致处理的原因。

虽然组合模式能够清晰地定义分层次的复杂对象，也使得增加新构件也更容易，但是这样就导致了系统的设计变得更加抽象，如果系统的业务规则比较复杂的话，使用组合模式就有一定的挑战了。

[![](http://images.cnitblog.com/blog/381060/201310/08191402-304eb9222e934734a9bf8ce2a85fbe0c.jpg "组合模式")](http://images.cnitblog.com/blog/381060/201310/08191402-ad0213120a1845b9b8564af6e00c1c1b.jpg)

参与者：

Component ：组合中的对象声明接口，在适当的情况下，实现所有类共有接口的默认行为。声明一个接口用于访问和管理Component子部件。  
Leaf：叶子对象。叶子结点没有子结点。  
Composite：容器对象，定义有枝节点行为，用来存储子部件，在Component接口中实现与子部件有关操作，如增加\(add\)和删除\(remove\)等。

### 



