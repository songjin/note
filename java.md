# Java 笔记

### Java特点

* cross-platform （JVM的优秀）
* OOP
* GC
* Speed（相对于Python　Ruby）
* 学习资源
* 强类型，静态
* Android

### main

	public static void main(String[] args)
	
### Type
	
* boolean 与　int不相容
* primitive：
 	- boolean
 	- char (16)
 	- byte (8)
 	- short (16)
 	- int (32)
 	- long (64)
	- float (32)
	- double (64)
* 初始值
	-　int, char : 0
	- boolean :false
	- 引用: null
* All operate of the Object is refrence
* ==
	- 比较基类
	- 比较引用是否链接到同一个对象
	
	
### Control　Flow
* for(int type: typeSet) {}

### OO
* ArrayList<class> myList = new ArrayList<class> ()
* import
* extends
* private  delfault protected public (public会被继承，pravite不会)

* the refrence can be the father class  e.g. `Animal[1] = new Dog()`, `Animal[1].eat` calls `Dog.eat()`
* 参数和返回类型也可以用负父类
* 重载方法　参数和return类型都要相同，而且不能降低权限
* 抽象类
	`abstract xxx classname`  不能被new
* 抽象方法　`public abstract xxx` 没有实体
* Object　Class的方法：　equal　,getClass, toString, hashCode
* 根据引用来判断methon调用而不是Objective类型
* inferface　接口类似于１００％的抽象类
* public inferface Pet{}
* public class Dog extends Cannie implements Pet {}
* heap 里面只有对象，局部变量，方法调用，原始类型，引用都在stack里面，实例变量在对象所属的堆空间上
* 构造函数　覆盖
* 构造很熟　super　编译器会给无参数的构造函数加上super，有参数要自己super(arg)
* this对自身的引用，与super不能同时用

* 静态方法（类方法））
* static
* 静态变量
* final



	
