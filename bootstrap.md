doitian 1楼, 2天前  喜欢 
block 没设定宽度是不能 margin auto 来居中的，一个简单的办法是 display: table

PS:

display: table
width: auto
margin-left: auto
margin-right: auto
 
panywhang 2楼, 2天前  喜欢 
<center></center>

 
QueXuQ 3楼, 2天前  喜欢 
#2楼 @panywhang 二楼什么状况？？
#1楼 @doitian 哦。是在span12里面的div设置为display: table吗？

 
QueXuQ 4楼, 2天前  喜欢 
哥们，本贴出现bug了。@Rei @huacnlee

 
serco 5楼, 2天前  喜欢 
#4楼 m@QueXuQ 我来测试下新功能 原来真是bug。。。

 
doitian 6楼, 1天前  喜欢 
#3楼 @QueXuQ 可以加个 class

.center {
  width: auto;
  display: table;
  margin-left: auto;
  margin-right: auto;
}
.text-center {
  text-align: center;
}


<div class="center">
  pla pla pla
</div>
 
chucai 7楼, 1天前  喜欢 
这里有一个居中的实列
http://twitter.github.com/bootstrap/examples/marketing-narrow.html