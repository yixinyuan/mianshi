# mianshi
安卓面试总结
1. Java基础 String a = "aa";与String a = new String("aa");  在内存中的区别？
	String a = new String("aa")，代表在堆内存中，创建了一个字符串对象，变量a指向该对象，
	而该对象又指向在常量池中的字符串常量。
	而String a = "aa"代表直接由变量a指向常量池中的字符串，省去了中间的堆内存中的对象，
	因为new对象时，都会在堆中创建对象。
	http://www.360doc.com/content/13/1028/08/13253385_324696458.shtml

2. Java设计模式
	http://www.cnblogs.com/maowang1991/archive/2013/04/15/3023236.html

3. Android设计模式
	http://blog.csdn.net/bboyfeiyu/article/details/44563871
	
4. 单点登录
	1.api请求中后台返回特定code
	2.推送
	3.使用第三方的监听器

5. Android抗并发

6. Android属性动画

7. 用java语言写出1 1 2 3 5 8 13 21 34 55 89 144
	public int fun(n){
	   if (n == 1) 
		 return 1;
		else if(n==2)
		 return 1;
		else if (n>2)
		 return fun(n) + fun(n-1);
	}

8. java读取文件内容，并压缩
	String a = "ddddaffffaaaaaaaaa";
	压缩结果：d4a1f4a9;
	
9. Android中MVC的应用
	http://www.cnblogs.com/John-Chen/p/4458823.html
	
	View：自定义View或ViewGroup，负责将用户的请求通知Controller，并根据model更新界面；
　　Controller：Activity或者Fragment，接收用户请求并更新model；
　　Model：数据模型，负责数据处理相关的逻辑，封装应用程序状态，响应状态查询，通知View改变，
	对应Android中的datebase、SharePreference等。

10. Android自定义控件绘制流程
	http://www.cnblogs.com/PDW-Android/p/3796748.html

11. Android事件分发机制
	http://www.cnblogs.com/sunzn/archive/2013/05/10/3064129.html

12. Android内存OOM的原因、及解决方案

12.1 android开发之避免使用枚举
	http://blog.csdn.net/warden032/article/details/52452035
	1）枚举会增加dex文件大小
	2）枚举会增加dex文件方法数量
	3）枚举会增加内存的使用
		一旦引用该枚举的时候，就会触发虚拟机加载该枚举类，并且实例化所有的枚举项，并且这些枚举实例的内存无法回收，而且枚举是单例，如果自定义的枚举类中包含了大块内存的引用，也可能会带来内存泄露。
	4）枚举会增加字符串常量
	5）枚举会增加函数调用时间
	总结：
		在Android开发上，由于设备内存和安装程序大小的限制，不管是从文件大小、内存使用量还是性能等角度考虑，使用枚举都不是一个好的选择，尤其是大型的App。对于主Dex文件的模块代码，以及高频率函数中，我们应该尽可能的不使用枚举。在其他int常量能够满足需求的情况下，也最好选用int常量的方式来实现相关的功能，避免对文件大小，方法数量，内存，性能产生不利的影响。

13. Android service的启动方式和区别
	start和bind是否可以同时调用？？？？
	https://my.oschina.net/tingzi/blog/376545
	
14. Android进程间通讯的几种方式？
	通过Intent在Activity、Service或BroadcastReceiver间进行进程间通信，可通过Intent传递数据
	AIDL方式
	Messenger方式
	利用ContentProvider
	Socket方式
	基于文件共享的方式

15. 安卓多线程间通信和多进程之间通信有什么不同?分别怎么实现?
	http://www.cnblogs.com/yangtao1995/p/6079067.html

15. Android 多线程及线程通信
	http://blog.csdn.net/zzj1881/article/details/8690589

16. handle机制？
	Handler是一个消息分发对象，而消息分发，依赖于消息循环，也就是looper。
	再一个线程中，looper阻塞线程，等待消息构成循环，有了消息，分配到对应的handler，让他进一步分发处理。

17. static的理解？
	1）static方法
	static方法一般称作静态方法，由于静态方法不依赖于任何对象就可以进行访问，因此对于静态方法来说，是没有this的，因为它不依附于任何对象，既然都没有对象，就谈不上this了。并且由于这个特性，在静态方法中不能访问类的非静态成员变量和非静态成员方法，因为非静态成员方法/变量都是必须依赖具体的对象才能够被调用。
	2）static变量
	static变量也称作静态变量，静态变量和非静态变量的区别是：静态变量被所有的对象所共享，在内存中只有一个副本，它当且仅当在类初次加载时会被初始化。而非静态变量是对象所拥有的，在创建对象的时候被初始化，存在多个副本，各个对象拥有的副本互不影响。
	3）static代码块
	tatic关键字还有一个比较关键的作用就是 用来形成静态代码块以优化程序性能。static块可以置于类中的任何地方，类中可以有多个static块。在类初次被加载的时候，会按照static块的顺序来执行每个static块，并且只会执行一次。
	
	注意：
		1.static关键字并不会改变变量和方法的访问权限
		2.静态成员变量虽然独立于对象，但是不代表不可以通过对象去访问，所有的静态方法和静态变量都可以通过对象访问（只要访问权限足够）。
		3.static是不允许用来修饰局部变量
		
	http://www.cnblogs.com/starhu/p/5150241.html

18. Java内存机制？
	http://blog.csdn.net/heirenheiren/article/details/7337402

19. Android dvm的进程和Linux的进程, 应用程序的进程是否为同一个概念?
	DVM指 dalivk 的虚拟机。每一个 Android 应用程序都在它自己的进程中运行，都拥有一个独立的 Dalvik 虚拟机实例。而每一个 DVM 都是在 Linux  中的一个进程，所以说可以认为是同一个概念。 
	
20.  在Activity之间使用Intent传值和Bundle传值的区别和方式？
	http://blog.csdn.net/plussoft/article/details/9114819

21. activity和fragment的区别？
	http://www.tuicool.com/articles/3QvMRfz

21.2 fragment的优缺点
	http://blog.csdn.net/ttkatrina/article/details/51793682

22. 线程池理解
	http://www.cnblogs.com/whgw/archive/2011/09/28/2194776.html
	  假设一个服务器完成一项任务所需时间为：T1 创建线程时间，T2 在线程中执行任务的时间，T3 销毁线程时间。
    
    如果：T1 + T3 远大于 T2，则可以采用线程池，以提高服务器性能。
                一个线程池包括以下四个基本组成部分：
                1、线程池管理器（ThreadPool）：用于创建并管理线程池，包括 创建线程池，销毁线程池，添加新任务；
                2、工作线程（PoolWorker）：线程池中线程，在没有任务时处于等待状态，可以循环的执行任务；
                3、任务接口（Task）：每个任务必须实现的接口，以供工作线程调度任务的执行，它主要规定了任务的入口，任务执行完后的收尾工作，任务的执行状态等；
                4、任务队列（taskQueue）：用于存放没有处理的任务。提供一种缓冲机制。
                
    线程池技术正是关注如何缩短或调整T1,T3时间的技术，从而提高服务器程序性能的。它把T1，T3分别安排在服务器程序的启动和结束的时间段或者一些空闲的时间段，这样在服务器程序处理客户请求时，不会有T1，T3的开销了。

    线程池不仅调整T1,T3产生的时间段，而且它还显著减少了创建线程的数目，看一个例子：

    假设一个服务器一天要处理50000个请求，并且每个请求需要一个单独的线程完成。在线程池中，线程数一般是固定的，所以产生线程总数不会超过线程池中线程的数目，而如果服务器不利用线程池来处理这些请求则线程总数为50000。一般线程池大小是远小于50000。所以利用线程池的服务器程序不会为了创建50000而在处理请求时浪费时间，从而提高效率。
	

23. sleep和wait的区别？
	sleep方法有：sleep(long millis)，sleep(long millis, long nanos)，调用sleep方法后，当前线程进入休眠期，暂停执行，但该线程继续拥有监视资源的所有权。到达休眠时间后线程将继续执行，直到完成。若在休眠期另一线程中断该线程，则该线程退出。
	wait方法有：wait()，wait(long timeout)，wait(long timeout, long nanos)，调用wait方法后，该线程放弃监视资源的所有权进入等待状态；
	wait()：等待有其它的线程调用notify()或notifyAll()进入调度状态，与其它线程共同争夺监视。wait()相当于wait(0)，wait(0, 0)。
	wait(long timeout)：当其它线程调用notify()或notifyAll()，或时间到达timeout亳秒，或有其它某线程中断该线程，则该线程进入调度状态。
	wait(long timeout, long nanos)：相当于wait(1000000*timeout + nanos)，只不过时间单位为纳秒

24. Android开发过程中遇到的问题
	http://www.jianshu.com/p/6e3ba6b71313
	
25. Application context和Activity context的区别
	http://blog.csdn.net/vincent_czz/article/details/8663871
	
26. Android数据库两个操作同时进行
	一个操作未完成，进行下一个操作，怎么处理

27. handler机制
	http://blog.csdn.net/itachi85/article/details/8035333

28. Android中asyncTask与handler的区别
	http://blog.csdn.net/onlyonecoder/article/details/8484200/
	
29. activity启动模式
	http://www.cnblogs.com/meizixiong/archive/2013/07/03/3170591.html
	
30. 安卓listview和recyclerview的不同
	http://www.tuicool.com/articles/aeeaQ3J

31. fastjson和gson的却别？
	http://www.cnblogs.com/whoislcj/p/5468420.html

32. volley的优缺点？
	http://blog.csdn.net/fenggit/article/details/50727831
	
