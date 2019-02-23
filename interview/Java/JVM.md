## [JVM面试的问题](https://www.zhihu.com/question/27339390)
### 类加载机制
- 类加载器有哪些？分别加载哪些类？
> 启动：负责加载/lib下的类库，例如rt.jar  
> 扩展：负责加载/lib/ext下的类库  
> 应用程序（系统）：程序员写的代码就由它来加载

- 类加载器的父子关系是怎样的？
> 从上往下依次：启动-扩展-应用程序-自定义

- 什么是双亲委派模型？
如果一个类加载器收到了**类加载**的请求，它首先不会自己去尝试加载这个类，
而是把请求委托给**父加载器**去完成（调用父加载器的loadclass()），依次向上，因此所有类加载请求最终都应该被传递到顶层的**启动类加载器**中，
只有当父加载类在它的搜索范围中没有找到所需的类时，即无法完成该加载，子加载器才会尝试自己去加载该类（调用自己的findclass()）。

- 为什么要使用双亲委派模型？
> 主要是为了安全性，避免用户自己编写的类动态替换java的一些核心类，比如String
> 同时也避免了类的重复记载，因为JVM中区分不同类，不仅仅是根据类名，相同的class文件被不同的ClassLoader加载就是不同类；
- 如何自定义自己的类加载器，自己的类加载器和Java自带的类加载器关系如何处理？
> 继承ClassLoader，并重写findClass方法（相对于重写loadclass来说简单，还能避免覆盖默认加载器的父类委托、缓存机制）

### GC
- 什么时候一个对象会被GC？为什么要在这种时候对象才会被GC？
> 程序员不能具体控制时间，系统在不可预测的时候/调用System.gc()函数的时候；  
> Eden区满了minor gc，升到老年代的对象大于老年代剩余空间full gc，或者小于HandlePromotionFailure参数被
强制full gc；  
> gc与非gc时间耗时超过了GCTimeRatio的限制引发OOM（OOM触发条件）；  
> 调优诸如通过NewRatio控制新生代老年代比例、通过MaxTenuringThreshold控制进入老年前生存次数延迟full gc（降低GC的调优策略）

- 对什么东西GC
> 超出了作用域或引用计数为空的对象；  
> 从gc root开始搜索找不到的对象，而且经过一次标记、清理，仍然没有复活的对象；

- 如何回收？
> 删除不使用的对象，回收内存空间；  
> 运行默认的finalize，当然程序员想立刻调用就dispose调用以释放资源如文件句柄；  
> JVM用from survivor、to survivor对它进行标记清理，对象序列化后也可以使它复活；

- GC策略都有哪些分类？这些策略分别有什么优势？都适用于什么场景？
> [分代策略](http://shiyanjun.cn/archives/397.html)  

### 内存
- JVM内存分为哪几个部分，这些部分分别存储哪些数据？
[jvm内存分布](https://blog.csdn.net/qq_24499615/article/details/80012470)

- 一个对象从创建到销毁是怎么在这些部分里存活和转移的？
> [参考1](https://www.imooc.com/article/6319)  
> [参考2](https://blog.csdn.net/zhengzhb/article/details/7517213)

- 内存的哪些部分会参与GC的回收？
> Java堆与方法区（对方法区垃圾回收不是必要的）

- Java的内存模型是怎么设计的？为什么？结合内存模型的设计谈谈volatile关键字的作用？
[JMM](https://www.hollischuang.com/archives/2550)

## 一些网站
[Java类加载器（自定义类加载器）](https://blog.csdn.net/luochoudan/article/details/50789043)  
[类加载机制](http://www.importnew.com/23742.html)  
[GC有关面试题](https://blog.csdn.net/cy609329119/article/details/51771953)  
