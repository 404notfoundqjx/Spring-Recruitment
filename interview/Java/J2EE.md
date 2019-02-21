## [极客学院-面试题](http://wiki.jikexueyuan.com/project/java-interview-bible/servlet-jsp.html)
## [CSDN-面试题 详细](https://blog.csdn.net/u013361361/article/details/20956411)
## 什么是servlet
- 服务器端的applet（小程序）；
- 从客户端接收请求，执行某种作业，返回结果；  
基本流程：客户端 web服务器 servlet；
## 为什么要使用servlet
- java的平台无关性
- 持久连接。对于客户端的每次请求不用重启
- java的可扩展性，健壮，面向对象
- 安全，只有web服务器能调用servlet
## forward和sendRedirect区别是什么
-（在web服务器端工作）forward仅是容器中控制权的转向，在客户端浏览器地址栏中不会显示
转向后的地址，（Servletengine会传递HTTP请求从当前的Servlet到
另外一个Servlet）
浏览器发出一次HTTP请求，跟更加高效，也有助于隐藏实际的链接地址
-（在浏览器工作）后者是完全的跳转，浏览器将会得到跳转的地址，浏览器发出两次HTTP请求
## 什么是JSP
- 在html里加java代码，第一次访问时会编译成一个servlet
## JSP和Servlet有哪些相同点和不同点，他们之间的联系是什么
- 本质上是Servlet，
- 主要区别在于Servlet的应用逻辑在Java文件中，并且完全从表示层中的HTML里分离开来  
而JSP的情况是，Java和HTML组合成一个扩展名为.jsp文件
- JSP侧重于视图（动态页面），Servlet主要控制逻辑（业务流程）
