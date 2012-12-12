## Forward

Objective C是C语言严格意义上的超集。Obj－C面向对象的特性继承自Smalltalk，基于消息机制而不是常见的对象方法调用，所以和C++,Java等面向对象的方式有很大的区别。

乔布斯被苹果扫地出门后创建的NEXTSTEP公司基于Obj-C搞了一套开发环境，后来被苹果收购之后，NEXTSTEP的人马和技术来到了苹果。原来的NEXTSTEP的框架该叫Cocoa。所以现在Cocoa框架里的东西，名字的前缀都是NS。

## Cocoa
[Objective-C新特性](
http://blog.devtang.com/blog/2012/08/05/use-modern-objective-c/)

## 面向对象

ObjC的实例变量只能通过方法访问。

id类型是ObjC通用的指针类型，定义为一个指向对象的指针，也是方法默认的返回类型。

每一个对象都有一个isa变量指向它的Class，Class本身定义为指向对象的指针，所以isa通常是指：指向对象的指针。

id是可以指向任何对象的。ObjC是同态类型，对象类型也是可以动态绑定的。

## 内存管理

ObjC内存管理有三种形式

* Automatic Reference Counting (ARC)编译器自动计数对象的引用管理内存
* Manual reference counting 手动管理
* Garbage collection　垃圾收集。iOS设备不支持。

##　消息传递

ObjC的面向对象继承自SmallTalk，是比较独特的消息传递方式而不是常见的方法调用。消息传递的表达式是：

	[receiver message];
	
消息接收者是对象，而消息是方法的名称和参数表.ObjC采用 named parameters，或者叫keyword arguments，即列出所有的参数名称和参数。
	
	[myRectangle setOriginX: 30.0 y: 50.0]; 
	
类似于下面的参数表是允许的，但是风格不推荐。
	
	[myRectangle setOrigin:30.0 :50.0];
	
ObjC也支持边长参数表

	￼[receiver makeGroup:group, memberOne, memberTwo, memberThree];
	
方法调用可以嵌套，同时也可以用`.`操作符来访问可以访问的属性·

## 动态绑定

方法调用和消息传递的区别在于，方法调用在编译的时候混合进代码里，而消息传递在运行的时候才确定

## Catalog

分类可以扩展类。

	@interface ClassName (catalog)
	@end
	
	
	@impelement ClassName (catalog)
	@end
	
分类不能添加实例变量

Obj-C里面没有共有方法，可以通过定义一个分类，在分类中扩展的方法就是私有的。


## Protocol

协议类似于Java中的interface，是多个类共享的一个方法列表。

	@interface  ClassName : SuperClass <Protocol>
	
然后在实现部分完成方法。

多个协议可以用`,`分开。`<protocol1 protocol2>`



##dot操作符

点操作符是`[]`的语法糖。	


## 构造函数和析构函数

构造函数要自己显示调用，析构函数`delloc`会在对象销毁的时候自动调用

Obj-C规定在nil对象上调用方法是不执行任何操作，所以释放成员变量后将指针设为nil是一个好主意。

### GC

在垃圾回收环境中不会用到dealloc方法，而是在对象销毁的时候自动调用finalize方法

### Strong 和　Weak



## property

	@property (getter=getPubStr,setter=setPubStr:,nonatomic, retain) NSString* pubStr;
	
###  assign、retain 或者 copy

用来定义该属性 setter 方法的赋值类型。assign是简单赋值；retain在赋值时会保留传入参数。copy是深拷贝。默认是assign。

assign 就是简单的变量赋值,这种类型一般适用于 基础数据类型 （如:NSInteger）、C数据类型（如:int, float, double, char等）还有 委托（delegate）。

	self.content = paramContent; 

使用retain的话，此属性在赋值的时候，先release之前的值，然后再赋新值给属性，引用再加1。说的更彻底一点儿就是它只是指针之间的浅复制，将参数的引用release掉，让属性的引用计数+1.对象还是原先的值，只是引用计数先-1再+1.只是指针的赋值。
	
	- (void)setContent:(NSString *)paramContent
	{
    	[paramContent autorelease];
    	self.content = [paramContent retain];
	}
	
使用copy与使用retain的区别应该就是，copy是深复制。copy没有增加引用计数，是分配一块新的内存来放置参数值。

	- (void)setContent:(NSString *)paramContent
	{
	    [paramContent autorelease];
	    self.content = [paramContent copy];
	}
	
	
- 使用assign: 对基础数据类型 （NSInteger，CGFloat）和C数据类型（int, float, double, char, 等等）
- 使用copy： 对NSString
- 使用retain： 对其他NSObject和其子类
	
### readwrite,readonly
设置可供访问级别
### atomic、nonatomic

atomic是Obj-C使用的一种线程保护技术，基本上来讲，是防止在写未完成的时候被另外一个线程读取，造成数据错误。而这种机制是耗费系统资源的，所以在iPhone这种小型设备上，如果没有使用多线程间的通讯编程，那么nonatomic是一个非常好的选择。


### dynamic 和　synthesize

使用dynamic，编译器会期望你为属性手动些存储器方法

默认的存储器方法约定应该是`setVariableName`和`VariableName`

### Xcode 4.4

http://stackoverflow.com/questions/3802851/objective-c-synthesize-property-name-overriding

	@synthesize dummyLabel = _dummyLabel;
	
	self._dummyLabel is undefined, however _dummyLabel is not.
	
	You can only use dot syntax for synthesized properties.
	
	self.dummyLabel  //works
	self._dummyLabel //does not work
	dummyLabel       //does not work
	_dummyLabel      //works

## Class

NSObject是所有类的根类

在头文件定义的都是公共的（方法 or 变量）

在m文件里面定义的都是私有的（方法 or 变量）


## Protocol

	@protocol BaseballPlayer
	-(void)drawHugeSalary;
	@optional
	-(void)slideHome;
	-(void)catchBall;
	@required
	-(void)swingBat;
	@end
	
因此，一个采用BaseballPlayer协议的类有两个要求实现的方法：-drawHugeSalary和-swingBat,还有3个不可选择实现的方法：slideHome,catchBall和throwBall。





### Blocks

### GCD

### KVC KVO

## 宏

小技巧

输出变量值的宏

	#define LOGVAR(var) NSLOG(@"%s: %@", #var, var);

其中#var会自动调用字符串化函数

## Exception

	@try {
	}
	@catch (NSException *e) {
	}
	@finally {
	}
### NSError

## 多线程　


