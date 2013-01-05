# Java 其实是深受Objective-C影响 #

...而不是C++


http://cs.gmu.edu/~sean/stuff/java-objc.html


不久之前，和James Gosling一起作为Java主要设计者的Patrick Naughton，写了这篇文章。Objective-C是NeXTSTEP和MacOS X上C语言面向对象的一个发展，并且也可以用gcc。




Tom Gall  写道:
> Sean Luke 写道:
>> Blair MacIntyre (bm@renoir.cs.columbia.edu) 写道:

>>> BZZT.  错，Java受许多语言的影响，最重要的是 Modula-3 and C++.

>> 当然，说它受NewtonScript影响是没意义的
>> but it's even goofier to say that Java was based on .但是，说Java是基于Modula-3和C++的更傻。

Java的符号或许像C++，但是从语言层面上它并不像C++。Java的主要的是动态绑定和单继承，类对象，并且广泛的运行时系统。

 C++ and Modula-3像其他面向对象的语言一样，理这个模型差很远。

Java是Smalltalk以及其他相关语言上的语义派生出来的，NeXT的Objective-C与Java有惊人的相似支出：单继承，动态绑定，动态加载，类对象，接口，并且方法作为数据存储（Java的反射库的风格），纯虚函数，凡是你能说出来的… 真可怕。
 
这些离奇额巧合不过是设计的事实。我记得我的Java历史，打算从Sun卷铺盖走人，跳槽到NeXT。他岑推荐和一样在。叫他离开，记录下他在离开Sun之前，对于Sun的一些观点是错误的。并没有离开，并且成为了最早的Oak成员。我想他和NeXTSTEP的密切关系，并且从那里近距离接触到了Objective-C（NeXTSTEP的主要语言）


我不再常看usenet了（从comp.graphics在80年代的黄金时代过去之后），但是我偶然在Excite Live（一个很酷的服务）接触到了这篇文章 
...

正如它揭露的，Sean和Tom都是完全正确的。通常的，这种传闻都是完全错误的。但在这件事情中，这是正确的。当我离开Sun跳槽到NeXT的时候，我认为Objective-C是从切片面包以来最酷的东西，并且我讨厌C++。

所以，当我开始设计Java的时候，自然受Obj-C很大影响。
 James Gosling,比我年长许多，有许多关于 SmallTalk and Simula68,的经验 ，所以我们大方的借鉴了这些。

 另一个影响是，我们当时有许多在NeXT工作的朋友，他们觉得黑色的方块（ 指NeXT的工作站的独特造型  http://cultureandcommunication.org/deadmedia/index.php/NeXT_Step#.E2.80.9CThe_Cube.E2.80.9D  ）没前途了。

 Bruce Martin 当时工作在 NeXTStep 486 port, Peter King, Mike Demoney, and John
Seamons  工作在秘密的（并且从未发售的） NRW (NeXT RISC
Workstation, 88110???).  他们都在 late '92 - early '93 after加入了我们。我们写了Oak的第一个版本。我十分确定Java的接口是直接从前NeXT的工程师设计的 Obj-C的protocol上直接抄的...许多奇怪的原始类型包装类，如 Integer 和Number came 来自 Lee Boynton一个NeXT的搞Obj-C类库的讨厌int和float类型的家伙。

另一个有趣的旁注，（没有打破我第一次（也是最后一次）公布在），

Another interesting side-note, (so as not to break any rules on my first
[and last]-ever posting to comp.sys.newton), John Seamons, (who happened
to be Andy Bechtolsheim's roommate at Stanford and largely reponsible for
the first ever port of Unix to the SUN-0) once did a port of Oak (Java)
to the Newton.  We were in the midst of trying to do a deal with 3DO to
run as their OS/API, and we didn't have any 3DO dev systems on hand, so
John took apart an Apple Newton 100 and wired it up to a bunch of logic
analyzers, reverse engineered the interfaces and actually got some of the
original Star7 demo to run on this machine.  After the 3DO deal tubed, I
think most of the code was lost to history...  last I heard, John was out
in Aspen working for wnj, so you never know.

Sigh... we sure knew how to have fun in those days...

-Patrick

-------------
Patrick Naughton
President and CTO
Starwave Corporation
http://www.starwave.com/people/naughton

