## spring + springMVC + mybatis
[参考1.1](https://blog.csdn.net/qq_41541619/article/details/82459873#SpringMVC%20%E7%9A%84%E5%B7%A5%E4%BD%9C%E5%8E%9F%E7%90%86%C2%A0)  
[参考1.2](https://blog.csdn.net/qq_41541619/article/details/82459965)  
[参考2](https://www.jianshu.com/p/7b6a070119c7)  
### spring
- 谈谈你对Spring的理解
> 1.是一个[容器](https://blog.csdn.net/JavaTear/article/details/9089655)框架；  
> 2.非侵入式框架，框架不会影响或者改变我们原有的编码过程;  
> 3.是一个轻量级框架，可以自由选择Spring框架的全部或者一部分；  
> 4.是一个一站式框架，提供了各种各样的模块，支持开发；  
> 5.提供了对于持久层的支持；  
> 6.提供了web MVC框架；  
> 7.IOC/DI，控制反转/依赖注入；  

- **IOC控制反转** 解释一下
> 不是一种技术，而是一个面向对象编程的法则，”别找我，我会来找你“  
> 控制反转是从**容器**角度来说的，以前对象都是应用程序new出来的，对象之间的依赖也是应用程序自己创建的
从而导致类与类之间的高耦合，难于测试。现在，由Spring管理[bean](https://blog.csdn.net/qfikh/article/details/52664144)的生命周期以及bean之间的关系，降低了
业务对象替换的复杂性，提高了组件之间的解耦。  
> 对资源进行集中管理，实现了资源的可配置和易管理；  
> 隐藏细节，不用自己组装，我们只负责调用；

- DI依赖注入 解释一下
> 是从应用程序的角度来说的，即，应用程序Spring管理的bean以及bean之间的关系。Spring容器中有很多bean的实例，它
会将符合依赖关系的对象通过注入的方式进行关联，建立bean与bean之间的联系。  
> 常见的注入方式有：属性注入，构造器注入，数组注入，集合注入；

- **AOP**面向切面编程 解释一下
> 利用一种成为”横切“的技术，支持将公共业务提取出来（例如：安全/事务/日志）进行集中管理，面向核心业务编程，
只需关注业务本身，而不用去关注公共业务。使用AOP可以将那些与业务无关，却为业务模块所共同调用的逻辑或责任封装起来，
便于减少系统的重复代码，降低模块间的耦合度，并有利于未来的可操作性和可维护性  
> 例如数据库的事务管理，通过Spring管理事务可以把我们从事务管理中解放出来专注于业务逻辑；  
> Spring中实现AOP的方式有三种，分别是，基于AspectJ注解方式实现，基于Schema的xml配置、基于ProxyFactoryBean代理
是西安，但是底层都是基于动态代理实现的，动态代理有JDK动态代理和CGLIB动态代理，AOP默认使用的是JDK动态代理，当目标类
没有接口时，使用CGLIB动态代理，也可以在配置文件中配置proxy-target-class=true，只使用CGLIB动态代理。

- Spring中的设计模式
> 工厂模式：定义一个用于创建对象的接口，让子类决定实例化哪一个类，例如Spring中的FactoryBean接口；  
> 单例模式：保证一个类只有一个实例，并提供一个访问它的全局访问点；  
> 包装器模式：动态的给一个对象添加一些额外的职责，Spring中类名中带有”wrapper“和”decorator“；
> 代理模式：为其他对象提供一种代理以控制对这个对象的访问；  
> 适配器模式：将一个类的接口转换成客户希望的另外接口。Adapter模式使得原本由于接口不兼容而不能在一起工作的那些类可以一起关注；  
> 简单工厂模式：实质是一个工厂类根据传入的参数，动态决定应该创建哪一个产品类；  

### springMVC
- 谈谈对SpringMVC的理解
> 1.是一个基于MVC的web框架  
> 2.SpringMVC是Spring的一个模块，是Spring的子容器，子容器可以拿父容器的东西，但是父容器不能拿子容器的东西  
> 3.SpringMVC的前端控制器DispatcherServlet，用于分发请求，使开发变得简单
> 4.SpringMVC流程（重点）
> 5.SpringMVC三大组件  
      1）HandlerMapping：处理器映射器  
            用户请求路径到Controller方法的映射  
      2）HandlerAdapter：处理器适配器  
            根据handler(controlelr类）的开发方式（注解开发/其他开发） 方式的不同去寻找不同的处理器适配器  
      3）ViewResolver：视图解析器  
            可以解析JSP/freemarkerr/pdf等

### MyBatis
- JDBC编程有哪些不足之处，MyBatis是如何解决这些问题的？
> 数据库链接创建、释放频繁造成系统资源浪费从而影响系统性能，如果使用数据库链接池可解决此问题。
解决：在SqlMapConfig.xml中配置数据链接池，使用连接池管理数据库链接。

> Sql语句写在代码中造成代码不易维护，实际应用sql变化的可能较大，sql变动需要改变java代码。  
解决：将Sql语句配置在XXXXmapper.xml文件中与java代码分离。

> 向sql语句传参数麻烦，因为sql语句的where条件不一定，可能多也可能少，占位符需要和参数一一对应。
解决： Mybatis自动将java对象映射至sql语句。

> 对结果集解析麻烦，sql变化导致解析代码变化，且解析前需要遍历，如果能将数据库记录封装成pojo对象解析比较方便。  
解决：Mybatis自动将sql执行结果映射至java对象。
