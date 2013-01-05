VB是Visual Basic。已经非常过时了。。。

我们高中数学课本的教材上是BASIC语言，也就是类型VB的东西。

VB以前很成功，因为很简单。。。你想做一个按钮，想画图一样拖一个就醒了

但是，如果你想点击按钮会有反应，还是要写代码。。

大致的类型可以参考我之前高二写过的文章<http://www.cnblogs.com/oa414/archive/2011/01/24/1943414.html>

C语言是比较底层的， 和机器关系比较密切，所以工科（特别是机械电子计算机相关的）学生基本必学，一些理科学生也要学（主要是80年代比较火。。而中国计算机教育普通停留在。。。）

C语言很好很重要，你用的操作系统什么都是用它写的，所以像我这种学计算机的必须要好好学。。。

但是因为对初学者不太友好。。。而且大部分人不会去写操作系统。。。所以我个人不太建议非计算机专业入门学习

C语言输出一句话是这样的

	#include <stdio.h>
	
	int main(int argc, const char *argv[])
	{
	    printf("hello world\n);    
	    return 0;
	}
	
感觉好麻烦对吧。。。

如果你学了C，你就会知道，C语言中把一个数加1可以这样写

	a = a + 1；
	
也可以这样写

	a++；
	
然后明白C++是什么了吧。。。C++是C语言的超集，或者说C是C++的子集。。但是因为C++多了一些东西，风格和C语言还是有区别的。

这是C++的版本。。。

	#include <iostream>
	using namespace std;
	int main(int argc, const char *argv[])
	{
	    cout << "hello worrd" << endl;
	    return 0;
	}
	
Java的话，用的更多。。。Java是爪哇岛。。盛产咖啡。。。当时一群工程师看着桌上的咖啡，。。。就把新搞出的东西叫Java了。。。


我现在经常写Java。。因为开发安卓的软件是用Java的。。。

	public class t{
	    public static void main (String[] args) {
	        System.out.printf("hello world");
	    }
	}

其实有其他的语言，比如一个叫Python的，既流行。。。又简单。。。
	
	print "hello world"
	
但是中国计算机等级考试什么的没有。。。。。大学基本不会交。。。。。

但是科学计算确实用的很多。因为方便一些非计算机专业的科学家，工程师用计算机模拟实验。。

如果不是计算机专业。。C/C++/Java确实很少。。。金融行业可能会用到C++、Java。。。。


<b>我个人的看法是。千万不要学VB（或许应付考试确实简单。。。），个人偏好C、Java。。。（如果想方便做出一些东西，Java更合适，理解计算机的话，C更方便）</b>


	