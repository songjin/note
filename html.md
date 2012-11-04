  
  
  
基本元素

* a
* q, blockquote（引用）
* br（换行）
* hr(水平线)
* code
* ul(有序)
* ol（无序）
* pre（预格式化文本）
* p

  
块元素：换行
内联元素：不换

<>&字符转义

### a
	<a id="xx">fadfasf</a>
	<a href="index.html#xx">fadsfd</a>
	<a target="_blank" href….</a> 在新窗口打开
	
### img
	<img src="xxx"  alt="fsda"　width="34" height="32" > alt 是描述
	
### Meta

	<meta http-equiv="Content-Type" content="text/html; charset=utf8" />
	
	
## CSS
p {
	backgroud-color: red;
	border: 1px soild gray;　边框
	font-family: 
	border-bottom: 			下划线
}

p.green {

}

.green   class选择

\#dasf		id选择

<p class="green hello"></p>  元素可以有多个class
### font

* font-size: 12px　140% 1.2em  xx-small x-small medium large xx-large
* color :red
* font-weight: bold normal
* font-style: italic
* text-decoration: underline 下划线

* line-height: 1.6em 行距


### font-family

* sans-serif　没有衬线，屏幕上更易读
* serif　有衬线，一般用于印刷
* monospace　　等宽
* cuisice　类似手写　　一般用于标题
* fantasy　　有装饰的字体，不常见 

### color
* background-color: rgb(204,12,255) rgb(10%, 34%, 3%) ##cc6600


### box

内容边上的是补白，边框里面，补白外面的是边界

* background-image: url(xxx)

* 边框 
	- border
	- border-color
	- border-width
	- border-style: soild double ...
* 补白
	- padding: 23px; 四周　
	- padding-left
	
* 边界
	- margin: 32px;
* 内容

### div 与　span

div是块元素　　

span是内联元素

### short
	padding-top: 23px 
	
	padding-left…
	
	margin也是，不用每个方向都写
	
	margin　　３px, 32px, 32px, 3px
	
	按照上右下左的顺序写
	
	或者写成两个，上下，左右
	
	background-color:fda
	
	background-image: da
	
	=> background: white url(dfasf) repeat-x;
	
	字体：
	
	font：样式-大小-family
	
	
### 伪类

能定义样式，但不是真的类

a:link

a:visited

a:hover （光标停在上面）

first-child 元素第一个孩子

\#fdsa a.link 嵌套使用伪类和类，改变类里面的伪类元素



###　漂移

	#amazing {
		width: 200px; （必须有宽度）
		float: right;
	}
		
