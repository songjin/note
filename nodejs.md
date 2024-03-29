
这里假定你有过Web后端的开发经验，无论是PHP, Python, Ruby还是Java。

1. 学习JavaScript
接触过前端JavaScript开发的同学可以跳过这一部分，只需要确认你已经掌握了闭包和原型。

学习JavaScript我推荐以下书籍:
《JavaScript高级程序设计》
这是一本这样的书：有人说它不适合入门，有人说它是入门的不二选择。总之它确实是从基础讲起，更重要的是，它是本好书。值得注意的是书中有些内容是和前端开发相关的，大可以略过不看。
《JavaScript语言精粹》
依然是本好书，没啥可说的。

2. 学习HTTP
相信Web后端开发者对HTTP都很熟悉，但仍然还是觉得顺便提一下比较好。

3. 学习node.js
node.js现在的中文资料不多，而且node.js的更新速度很快，所以看英文资料会比较好。
node.js的官网是http://nodejs.org。学习node.js要先从官网下载安装node。官网页面下面有一个很不错的例子，用6行代码实现一个Web Server，这个当做node.js的”Hello World”很合适。需要说明的是，node.js写的Web Server是可以在生产环境下使用的，并且性能颇高。

之后推荐阅读The Node Beginner Book，讲的很通俗易懂（在页面上方可以选择中文版哦）。

接下来是最重量级的两个页面：Felix’s Node.js Beginners Guide 和 Felix’s Node.js Style Guide。Felix是谁：

Hi, I am Felix Geisendörfer, an early node.js core contributor and co-founder of transloadit.com.

另外有闲的同学可以看看小羞怯同学Ryan Dahl(node.js的创造者)的演讲视频Introduction to Node.js with Ryan Dahl （如果你感兴趣，这是我在YouTube上完整看过的唯一一个正经的视频…）。

最后，node.js官方文档是你开发过程中会反复查阅的最重要的文档，相信我，你离不开它的。

自问自答
Q: 有这么多东西要看，什么时候才能开发呢？
A: 取决于你，我建议在看完Felix’s Node.js Beginners Guide中The module system一节后就可以开始动手写小网站了，比如留言板，论坛什么的。其余的教程可以一边写一边看。

Q: 用框架吗？用什么框架？
A: 先不用框架写一个小网站，注意一定要是小网站。然后你会感叹node.js写个网站好麻烦。这时你可以使用Express框架。学习Express的方法：看官网的Guide，然后看例子，同时对照着例子查看官网的API，最后看Express的源代码（这一步最好不要省略，这不仅能帮你理解Express，也能让你学到很多node.js的技巧，而且代码很短的哦）。

等等，还有一个Express的超赞教程：Let’s Make a Web App: Nodepad，不过教程中用的Express是2.*版本，现在已经是3.0了，有些地方有所区别，不过问题不大。
