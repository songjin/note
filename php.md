


## 框架

PHP入门门槛低，框架一堆堆。原因分析：http://www.iteye.com/topic/1071177

###框架比较

- http://www.cnbeta.com/articles/190452.htm
- http://www.zhihu.com/question/19611667

### Zend

[Zend Framewrok](http://framework.zend.com)

[Zend Framework手册 中文版]( http://phpeye.com/zf/index.html)

### CI

 - http://codeigniter.org.cn
 
 - PHP 敏捷开发框架 CodeIgniter - 快速 Web 应用开发详解
 
 - [CodeIgniter for Rapid PHP Application Development](http://www.amazon.com/CodeIgniter-Rapid-PHP-Application-Development/dp/1847191746)

### ThinkPHP
 国产框架 http://www.thinkphp.cn

###CakePHP
 据说最像Rails http://cakephp.org
### symfony2




## 第一印象

<?php

?>

需要加分号

##类型
###基础类型

四种基础类型bool,int,float,string

boolean型：FALSE =  FALSE和0，0.0，NULL

php没有整除，需要round()或者类型转换(int)

###String:

- 单引号，输出原始的
- <<<'SIGN' SIGN
- 双引号里面的会被转义
- <<<SIGN  SIGN 

后两种里面的变量会被求值

###数组

array(  key =>  value
     , ...
     )
 
 
###对象

<?php
class foo
{
    function do_foo()
    {
        echo "Doing foo."; 
    }
}

$bar = new foo;
$bar->do_foo();
?>


##变量

引用赋值

$bar = &$foo;

变量默认是FALSE，0，NULL

变量的作用域在其上下文环境

global 关键字或者$GLOBALS[]数组可以显示声明全局变量

static 关键字可以声明静态变量。其值在其作用域内不会丢失

可变变量：
$a = 'hello';
$$a = 'world';
这时候$a = 'hello'
$hello = 'world'

PHP之外的变量

	<form action="foo.php" method="POST">
	    Name:  <input type="text" name="username"><br />
	    Email: <input type="text" name="email"><br />
	    <input type="submit" name="submit" value="Submit me!" />
	</form>
	
	
	<?php
在PHP中显示
	
	
	// 自 PHP 4.1.0 起可用
	   echo $_POST['username'];
	   echo $_REQUEST['username'];
	   
	   import_request_variables('p', 'p_');
	   echo $p_username;
	// PHP 6以后将无效。自 PHP 5.0.0 起，这些较长的预定义变量
	// 可用 register_long_arrays 指令关闭。
	
	   echo $HTTP_POST_VARS['username'];
	
	// 如果 PHP 指令 register_globals = on 时可用。不过自
	// PHP 4.2.0 起默认值为 register_globals = off。
	// 不提倡使用/依赖此种方法。
	
	   echo $username;
	?>
	
define("name","something")可以定义常量

预定义常量

	__LINE__	 文件中的当前行号。
	__FILE__	 文件的完整路径和文件名。如果用在被包含文件中，则返回被包含的文件名。自 PHP 4.0.2 起，__FILE__ 总是包含一个绝对路径（如果是符号连接，则是解析后的绝对路径），而在此之前的版本有时会包含一个相对路径。
	__DIR__	 文件所在的目录。如果用在被包括文件中，则返回被包括的文件所在的目录。它等价于 dirname(__FILE__)。除非是根目录，否则目录中名不包括末尾的斜杠。（PHP 5.3.0中新增） =
	__FUNCTION__	 函数名称（PHP 4.3.0 新加）。自 PHP 5 起本常量返回该函数被定义时的名字（区分大小写）。在 PHP 4 中该值总是小写字母的。
	__CLASS__	 类的名称（PHP 4.3.0 新加）。自 PHP 5 起本常量返回该类被定义时的名字（区分大小写）。在 PHP 4 中该值总是小写字母的。
	__METHOD__	 类的方法名（PHP 5.0.0 新加）。返回该方法被定义时的名字（区分大小写）。
	__NAMESPACE__	 当前命名空间的名称（大小写敏感）。这个常量是在编译时定义的（PHP 5.3.0 新增）
	
	
	
===类型和对象一致的时候才True，==会自动转换类型，有点像JavaScript

错误控制运算符：@expression 中expression产生的错误会被忽略

字符串连接运算符是 .

检测对象类型instanceof

##控制流

elseif === else if 

if ($a == 5):
    echo "a equals 5";
    echo "...";
elseif ($a == 6):
    echo "a equals 6";
    echo "!!!";
else:
    echo "a is neither 5 nor 6";
endif;


while ($i <= 10):
    print $i;
    $i++;
endwhile;


for (expr1; expr2; expr3):
    statement;
    ...
endfor;

$arr = array(1, 2, 3, 4);
foreach ($arr as &$value) {
    $value = $value * 2;
}
//

break后面加数字表示跳出几重循环

$i = 0;
while (++$i) {
    switch ($i) {
    case 5:
        echo "At 5<br />\n";
        break 1;  /* 只退出 switch. */
    case 10:
        echo "At 10; quitting<br />\n";
        break 2;  /* 退出 switch 和 while 循环 */
    default:
        break;
    }
}

continue后面也可以加数字

declare(ticks=N) 每N条低级语句执行之后就会执行declare语句块的指令

declare(ticks=2) {
    for ($x = 1; $x < 50; ++$x) {
        echo similar_text(md5($x), md5($x*$x)), "<br />;";
    }
}

require和include都是包含文件，如果文件出错require停止执行而include继续

require_once()和include_once作用相同，但是不会重复包含

##函数

function foo($arg_1, $arg_2, ..., $arg_n)
{
    echo "Example function.\n";
    return $retval;
}



所有的函数和类都有全局作用域

通过引用传递参数

function add_some_extra(&$string)

指定默认参数的值

	function makecoffee($type = "cappuccino")

从函数返回一个引用

	<?php
	function &returns_reference()
	{
	    return $someref;
	}
	
	$newref =& returns_reference();
	?>


变量可以作为函数或类
	
	$func = 'foo';
	$func();        // This calls foo()
	
	$foo = new Foo();
	$funcname = "Variable";
	$foo->$funcname();   // This calls $foo->Variable()

PHP也支持匿名函数


##面向对象

extends继承

$this

const 声明类常量
Class::constName调用

__autoload 函数，它会在试图使用尚未被定义的类时自动调用。


	<?php
	function __autoload($class_name) {
	    require_once $class_name . '.php';
	}
	
	$obj  = new MyClass1();
	$obj2 = new MyClass2();
	?>

构造函数与析构函数
	
		function __construct() {
	       print "In constructor\n";
	       $this->name = "MyDestructableClass";
	   }
	
	   function __destruct() {
	       print "Destroying " . $this->name . "\n";
	   }
   
重载方法

	  // 覆盖父类中的方法
	    public function myFunc()
	    {
	        // 但仍然可以调用已被覆盖的方法
	        parent::myFunc();
	        echo "OtherClass::myFunc()\n";
	    }


和Java一样，有abstract，static，public，private，protected，interface声明

类似Ruby，有魔术方法

	public void __set ( string $name , mixed $value )
	public mixed __get ( string $name )
	public bool __isset ( string $name )
	public void __unset ( string $name )
	在给未定义的变量赋值时，__set() 会被调用。
	
	读取未定义的变量的值时，__get() 会被调用。
	
	当对未定义的变量调用isset() 或 empty()时，__isset() 会被调用。
	
	当对未定义的变量调用unset()时，__unset() 会被调用。
		
	public mixed __call ( string $name , array $arguments )
	public static mixed __callStatic ( string $name , array $arguments )
	当调用一个不可访问方法（如未定义，或者不可见）时，__call() 会被调用。
	
	当在静态方法中调用一个不可访问方法（如未定义，或者不可见）时，__callStatic() 会被调用。
	
	$name参数是要调用的方法名称。$arguments参数是一个数组，包含着要传递给方法的参数。

对象可以迭代自己的属性

 	foreach($this as $key => $value) {
           print "$key => $value\n";
       }
       
       
对象复制
 
 	$copy_of_object = clone $object;

对象比较

当使用对比操作符(==)比较两个对象变量时，比较的原则是：如果两个对象的属性和属性值 都相等，而且两个对象是同一个类的实例，那么这两个对象变量相等。

而如果使用全等操作符(===)，这两个对象变量一定要指向某个类的同一个实例（即同一个对象）。


序列化
 
 

	$a = new A;
	  $s = serialize($a);
	  // 把变量$s保存起来以便文件page2.php能够读到
	  file_put_contents('store', $s);
	
	// page2.php:
	  
	  // 要正确了解序列化，必须包含下面一个文件
	  include("classa.inc");
	
	  $s = file_get_contents('store');
	  $a = unserialize($s);
	
	  // 现在可以使用对象$a里面的函数 show_one()
	  $a->show_one();
  
##命名空间
  
PHP 在 5.3.0 以后的版本开始支持命名空间。
只有三种类型的代码受命名空间的影响，它们是：类，函数和常量。
定义命名空间

  namespace MyProject;
  
子命名空间
  
  namespace MyProject\Sub\Level;
同一文件可定义多命名空间，用namespace：或者namespace{}，但不推荐

命名空间用\分割

__	NAMESPACE__的值是包含当前命名空间名称的字符串

关键字 namespace 可用来显式访问当前命名空间或子命名空间中的元素。它等价于类中的 self 操作符。

别名，导入：

use My\Full\Classname as Another;

// 下面的例子与 use My\Full\NSname as NSname 相同
use My\Full\NSname;

在名称前加上前缀 \ 表示该名称是全局空间中的名称

###异常处理

类似Java
	<![CDATA[
	<?php
	function inverse($x) {
	    if (!$x) {
	        throw new Exception('Division by zero.');
	    }
	    else return 1/$x;
	}
	
	try {
	    echo inverse(5) . "\n";
	    echo inverse(0) . "\n";
	} catch (Exception $e) {
	    echo 'Caught exception: ',  $e->getMessage(), "\n";
	}
	
	// Continue execution
	echo 'Hello World';
	?>
	
###引用

PHP 的引用允许用两个变量来指向同一个内容。意思是，当这样做时：

	<?php
	$a =& $b;
	?>
	
	unset可以取消引用和内容的绑定
	unset($a);

在一个对象的方法中，$this 永远是调用它的对象的引用。


##在所有作用域中均可以用的变量

$GLOBALS
$_SERVER
$_GET
$_POST
$_FILES
$_COOKIE
$_SESSION
$_REQUEST
$_ENV
$_COOKIE
$php_errormsg 前一个错误信息
$HTTP_RAW_POST_DATA — 原生POST数据
$http_response_header — HTTP 响应头

###魔术引号

魔术引号（Magic Quote）是一个自动将进入 PHP 脚本的数据进行转义的过程。最好在编码时不要转义而在运行时根据需要而转义。

对初学者很有用 魔术引号在 PHP 中用来实现避免初学者的代码更危险。尽管 SQL 注入在魔术引号打开的情况下仍然有可能实现，但起码系统的风险减少很多了。
方便使用 当向数据库中插入数据时，魔术引号所做的就是自动对所有的 GET、POST、COOKIE 数据运用 addslashes() 函数。




###隐藏 PHP

一般而言，通过隐藏的手段提高安全性被认为是作用不大的做法。但某些情况下，尽可能的多增加一份安全性都是值得的。

一些简单的方法可以帮助隐藏 PHP，这样做可以提高攻击者发现系统弱点的难度。在 php.ini 文件里设置 expose_php = off ，可以减少他们能获得的有用信息。

另一个策略就是让 web 服务器用 PHP 解析不同扩展名。无论是通过 .htaccess 文件还是 Apache 的配置文件，都可以设置能误导攻击者的文件扩展名：

Example #1 把 PHP 隐藏为另一种语言
##### 使PHP看上去像其它的编程语言
AddType application/x-httpd-php .asp .py .pl
或者干脆彻底隐藏它：
Example #2 使用未知的扩展名作为 PHP 的扩展名
##### 使 PHP 看上去像未知的文件类型
AddType application/x-httpd-php .bop .foo .133t
或者把它隐藏为 HTML 页面，这样所有的 HTML 文件都会通过 PHP 引擎，会为服务器增加一些负担：
Example #3 用 HTML 做 PHP 的文件后缀
##### 使 PHP 代码看上去像 HTML 页面
AddType application/x-httpd-php .htm .html
要让此方法生效，必须把 PHP 文件的扩展名改为以上的扩展名。这样就通过隐藏来提高了安全性，虽然防御能力很低而且有些缺点。
 