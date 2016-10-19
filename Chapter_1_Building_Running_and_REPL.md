## 编译、运行以及REPL ##

第一章，就是花一点时间熟悉如何编译和运行clojure程序，通过使用Read-Eval-Print_Loop（REPL，也就是读取->计算->打印->循环）来体验即刻运行代码的乐趣。首先，我会简单介绍clojure语言本身。然后讲一下clojure的事实上的标准编译工具Leiningen。学完本章，你将会掌握如下技能：

* 使用Leiningen创建一个Clojure工程
* 把工程打包成一个可执行的jar文件
* 执行jar文件
* 在Clojure REPL中执行代码

### 什么是Clojure ###

提到Clojure这个词的时候，需要记住，它可能代指两个不同的概念，Clojure语言本身和Clojure编译器。Clojure语言本身是一门偏重于函数式编程的Lisp方言，其语法和语义并不依赖于编译器如何实现，是一个语言层面的概念。而Clojure编译器就是一个可执行的jar包，clojure.jar，接收以Clojure语法写成的代码，把这些代码编译成JVM可识别的字节码。你会发现，大家会用Clojure这个词来指代语言本身，也可能指代编译器。如果不提前说明这一点，你可能会有些疑惑，但如果你已经了解了，这其实是很简单且容易区分的两个概念。

这种语言和编译器的区别对Clojure来说非常必要，不像其他编译型语言，Ruby、Python、C等，Clojure是一种托管语言。程序在JVM上执行，依赖于JVM来实现如线程和垃圾回收等特性。Clojure还有给予其他运行时的编译实现，如Javascript和Microsoft Common Language Runtime，不过，本书只涉及JVM实现。

我们稍后会研究Clojure和JVM的关系，但首先你需要理解下面几个概念：

* JVM进程执行Java字节码
* Java编译器把Java源码编译成Java字节码
* Jar包就是Java字节码
* Java程序一般以Jar包形式发布
* Java程序Clojure.jar读取Clojure源码，生成Java字节码
* Java字节码由加载了Clojure.jar的JVM执行

Clojure的版本在不断演进。当前最新版是1.7.0。如果你看到本书时，Clojure的版本已经更新，没有关系，因为本书只关注Clojure的基础部分，这部分一般不会有大的更改。

到此，你已经认识了Clojure，那我们就先干一个小的Clojure程序吧！


### Leiningen ###


