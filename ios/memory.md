[OBjective-C 内存管理](http://www.cnblogs.com/zilongshanren/archive/2011/08/08/2131236.html)

http://www.cnblogs.com/zhuqil/archive/2011/03/16/1986420.html


* 手把手教你ARC——ARC入门和使用  http://www.onevcat.com/2012/06/arc-hand-by-hand/


1. alloc, allocWithZone,new(带初始化)
   为对象分配内存，retainCount为“1”，并返回此实例

2. release
   retainCount 减“1”，减到“0”时调用此对象的dealloc方法

3. retain
   retainCount 加“1”

4. copy,mutableCopy
   复制一个实例，retainCount数为“1”，返回此实例。所得到的对象是与其它上下文无关的，独立的对象(干净对象)。

5. autorelease
   在当前上下文的AutoreleasePool栈顶的autoreleasePool实例添加此对象，由于它的引入使Objective-C（非GC管理环境）由全手动内存管理上升到半自动化。


http://www.cocoachina.com/bbs/read.php?tid=1848

		举个例子可能更好理解点 
		NSString *pt = [[NSString alloc] initWithString:@"abc"]; 
		上面一段代码会执行以下两个动作 
		1 在堆上分配一段内存用来存储@"abc"  比如：内存地址为：0X1111 内容为 "abc" 
		2 在栈上分配一段内存用来存储pt  比如：地址为：0Xaaaa 内容自然为0X1111   
		下面分别看下assign retain copy 
		assign的情况：NSString *newPt = [pt assing];    
		此时newPt和pt完全相同 地址都是0Xaaaa  内容为0X1111  即newPt只是pt的别名，对任何一个操作就等于对另一个操作。 因此retainCount不需要增加。 
		retain的情况：NSString *newPt = [pt retain];    
		此时newPt的地址不再为0Xaaaa，可能为0Xaabb 但是内容依然为0X1111。 因此newPt 和 pt 都可以管理"abc"所在的内存。因此 retainCount需要增加1   
		copy的情况：NSString *newPt = [pt copy];  
		此时会在堆上重新开辟一段内存存放@"abc" 比如0X1122 内容为@"abc 同时会在栈上为newPt分配空间 比如地址：0Xaacc 内容为0X1122 因此retainCount增加1供newPt来管理0X1122这段内存 