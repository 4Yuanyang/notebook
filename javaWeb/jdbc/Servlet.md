# 简介

> - Servlet是Java提供的一门==动态==web资源开发技术
> - Servlet是JavaEE规范之一，其实就是一个接口，将来我们需要定义Servlet类实现Servlet接口，并由web服务器运行Servlet

# Servlet入门操作

> **1、创建web项目，导入Servlet依赖坐标**
>
> <img src="D:\software\Typora_imgs\QQ_1742110951136.png" alt="QQ_1742110951136" style="zoom: 67%;" />
>
> **2、创建：定义一个类，实现Servlet接口，并重写接口中所有方法，并在service方法中输入一句话**
>
> <img src="D:\software\Typora_imgs\QQ_1742111420628.png" alt="QQ_1742111420628" style="zoom: 80%;" />
>
> <img src="D:\software\Typora_imgs\QQ_1742111451098.png" alt="QQ_1742111451098" style="zoom:67%;" />
>
> **3、配置：在类上使用@WebServlet注解，配置该Servlet的访问路径**
>
> <img src="D:\software\Typora_imgs\QQ_1742111475994.png" alt="QQ_1742111475994" style="zoom: 75%;" />
>
> **4、访问：启动Tomcat，浏览器输入URL访问该Servlet**
>
> ![QQ_1742111710095](D:\software\Typora_imgs\QQ_1742111710095.png)
>
> 记得加上url访问，在控制台才会输入
>
> <img src="D:\software\Typora_imgs\QQ_1742111744044.png" alt="QQ_1742111744044" style="zoom:50%;" />

# Servlet执行流程

> 1、Servlet由谁创建？Servlet方法由谁调用？
>
> - Servlet由web服务器创建，Servlet方法由web服务器调用
>
> 2、服务器怎么知道Servlet中一定有service方法？
>
> - 因为我们自定义的Servlet，必须实现Servlet接口并复写其方法，而Servlet接口中有service方法
>
> `http://localhost:8080/webdemo4/demo1`
>
> 其中通过`http://localhost:8080`找到tomcat服务器，
> 而`webdemo4`就是web项目，
> 通过`demo1`访问到当前的Servlet对象

# Servlet生命周期

> - Servlet运行在Servlet容器(Web服务器)中，其生命周期由容器来管理，分为四个阶段：
>   ==1、加载和实例化==：默认情况下，当Servlet第一次被访问时，由容器创建Servlet实例.
>   ==2、初始化==：在Servlet实例化后，容器将调用Servlet的==init()==方法初始化这个对象，完成一些如加载配置文件、创建连接等初始化工作。`只调用一次`。
>   ==3、请求处理==：==每次==请求Servlet时，Servlet容器都会调用Servlet的==service()==方法对请求进行处理
>   ==4、服务终止==：当需要释放内存或者容器关闭时，容器就会调用Servlet实例的==destory()==方法完成资源的释放。在destroy()方法调用之后，容器会释放这个Servlet实例，该实例随后会被java的垃圾回收器回收。
>
>   > 可以通过在WebServlet注解中设置loadOnStartup参数来指定Servlet的加载顺序：
>   > 	负整数：第一次被访问时创建Servlet实例，默认-1.
>   > 	0或正整数：服务器启动时创建值越小，越先加载。

# Servlet方法介绍

> - 初始化方法，在Servlet被创建时执行，只执行一次
>   `void init(ServeltConfig config)`
> - 提供服务方法，每次Servlet被访问，都会调用该方法
>   `void service(ServletRequest req, SerletResponse res)`
> - 销毁方法，当Servlet被销毁，调用该方法。在内存释放或服务器关闭时销毁Servlet
>   `void destory()`
> - 获取ServletConfig对象
>    `ServletConfig getServletConfig()`
> - 获取Servlet信息
>   `String getServletInfo()`

# Servlet体系结构

> ![QQ_1742130282211](D:\software\Typora_imgs\QQ_1742130282211.png)
>
> <img src="D:\software\Typora_imgs\QQ_1742130287384.png" alt="QQ_1742130287384" style="zoom:50%;" />
>
> `在Http常见的有get和post两种（总共7种）请求处理`
>
> `get`：在网页直接通过输入url的方式是get提交
>
> `post`：在网页中通过表单（action="项目目录下的Servlet资源路径" method="post"）请求Servlet
>
> > ~~~java
> > @WebServlet("/demo4")
> > public class ServletDemo4 extends HttpServlet {
> >     @Override
> >     protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
> >         System.out.println("get ...");
> >     }
> >     @Override
> >     protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
> >         System.out.println("post ...");
> >     }
> > }
> > 
> > ~~~
> >
> > 通过==get==：
> >
> > ​	直接在浏览器输入url路径即可：
> >
> > <img src="D:\software\Typora_imgs\QQ_1742131577513.png" alt="QQ_1742131577513" style="zoom:50%;" />
> >
> > <img src="D:\software\Typora_imgs\QQ_1742131600637.png" alt="QQ_1742131600637" style="zoom:67%;" />
> >
> > 通过==post==：
> >
> > ​	需要通过网页表单，如下所示：
> >
> > <img src="D:\software\Typora_imgs\QQ_1742131933853.png" alt="QQ_1742131933853" style="zoom:50%;" />
> >
> > <img src="D:\software\Typora_imgs\QQ_1742131956863.png" alt="QQ_1742131956863" style="zoom:67%;" />
> >
> > ~~~html
> > <!DOCTYPE html>
> > <html lang="en">
> > <head>
> >     <meta charset="UTF-8">
> >     <title>a</title>
> > </head>
> > <body>
> >     <form action="/webdemo3_war/demo4" method="post">
> >         <input name="userName" placeholder="Enter your name" required>
> >         <input type="submit" value="提交">
> >     </form>
> > </body>
> > </html>
> > ~~~
>
> **1、HttpServlet中为什么要根据请求方式不同，调用不同方法？**
>
> **2、如何调用？**
>
> **以下模拟HttpServlet实现：**
>
> > ~~~java
> > package com.xyy.web;
> > 
> > import javax.servlet.*;
> > import javax.servlet.http.HttpServletRequest;
> > import java.io.IOException;
> > 
> > public class MyHttpServlet implements Servlet {
> > 
> >     @Override
> >     public void service(ServletRequest req, ServletResponse res) throws ServletException, IOException {
> >         HttpServletRequest request = (HttpServletRequest)req;
> >         String method = request.getMethod();
> >         if("GET".equals(method)) {
> >             doGet(req, res);
> >         }else if("POST".equals(method)) {
> >             doPost(req, res);
> >         }
> >     }
> > 
> >     @Override
> >     public void init(ServletConfig servletConfig) throws ServletException {
> > 
> >     }
> > 
> >     @Override
> >     public ServletConfig getServletConfig() {
> >         return null;
> >     }
> > 
> >     @Override
> >     public String getServletInfo() {
> >         return null;
> >     }
> > 
> >     @Override
> >     public void destroy() {
> > 
> >     }
> >     protected void doGet(ServletRequest request, ServletResponse response) {
> > 
> >     }
> >     protected void doPost(ServletRequest request, ServletResponse response) {
> > 
> >     }
> > }
> > 
> > ~~~
> >
> > 
>

# urlPattern配置

> - Servlet要想被访问，必须配置其访问路径（==urlPattern==）
>
>   1、一个Servlet，可以配置多个urlPattern
>   `@WebServlet(urlPatterns = {"/demo1", "/demo5"})`
>   2、urlPattern配置规则
>   	1、精确匹配
>   	2、目录匹配
>   	3、扩展名匹配
>   	4、任意匹配
>
> ![QQ_1742175605527](D:\software\Typora_imgs\QQ_1742175605527.png)
>
> > @WebServlet(urlPatterns = {"/demo6", "/demo3"}) 精确匹配
> > @WebServlet(urlPatterns = {"/user/*"}) 目录匹配，即目录中包含统配符
> > @WebServlet(urlPatterns = {"*.do"}) 后缀名匹配 ，这种情况不能加/，否则会报错
> > @WebServlet(urlPatterns = {"/"}) //统配符有两种，/*优先级比/要高。
>
> 

# XML配置Servlet

> ~~~xml
> <!DOCTYPE web-app PUBLIC
>  "-//Sun Microsystems, Inc.//DTD Web Application 2.3//EN"
>  "http://java.sun.com/dtd/web-app_2_3.dtd" >
> 
> 
> <web-app>
>   <display-name>Archetype Created Web Application</display-name>
>   <!--
>   Servlet 全类名
>   -->
>   <servlet>
>     <servlet-name>demo7</servlet-name>
>     <servlet-class>com.xyy.web.ServletDemo7</servlet-class>
>   </servlet>
> 
>   <!--
>      Servlet 访问路径
>   -->
>   <servlet-mapping>
>     <servlet-name>demo7</servlet-name>
>     <url-pattern>/demo7</url-pattern>
>   </servlet-mapping>
> </web-app>
> 
> ~~~
>
> 以前老版的配置，了解即可，多用注解

# Request

> **1、Request请求体系**
>
> 
>
> <img src="D:\software\Typora_imgs\QQ_1742177408157.png" alt="QQ_1742177408157" style="zoom: 43%;" />
>
> > ServletRequest和HttpServletRequest都是接口，实现类由Tomcat来创建。
> >
> > Tomcat解析请求，将其包装成一个Request。使用Request对象，可以查阅JavaEEAPI中的HttpServletRequest接口，因为是实现了HttpServletRequest接口。
>
> **2、Request获取请求数据**（了解）
>
> > GET和POST方式区别：
> >
> > > GET:
> > > 	请求参数在请求行中，所以获取参数通过getQueryString方法来获取相关参数
> > >
> > > POST：
> > > 	请求参数单独放在请求体中，通过流的方式获取相关参数（字节流和字符流，纯文本用字符流，文件、图片用字节流即可）
> >
> > ![QQ_1742258314783](D:\software\Typora_imgs\QQ_1742258314783.png)
> >
> > ~~~java
> > //请求行
> > String getMethod(): 获取请求方式：GET
> > String getContextPath(): 获取虚拟目录（项目访问路径）：/Webdemo3
> > StringBuffer getRequestURL(): 获取URL（统一资源定位符）:http://localhost:8080/webdemo3/req1
> > String getRequestURI(): 获取URI（统一资源标识符）：/webdemo3/req1
> > String getQueryString(): 获取请求参数（GET方式）： username=zhangsan
> > ~~~
> >
> > ==Request通用方式获取请求参数==
> >
> > - 请求参数获取方式：
> >
> >   ![QQ_1746583756227](./imgs/QQ_1746583756227.png)
> >   
> >   - GET方式：`String getQueryString()`
> >   - Post方式：`ServletInputStream getInputStream()`
> >
> >   GET请求方式和POST请求方式 区别主要在于获取请求参数的方式不一样，是否可以提供一种==统一==获取请求参数的方式，从而==统一==doGet和doPost方法内的代码？
> >   
> >   > Request提供了几个方便的方法：
> >   >
> >   > `Map<String, String[]> getParameterMap()：获取所有参数的Map集合`
> >   > 其中value值是String[]的原因：是因为Request帮我们封装好了，对一一个key可能存在多个value，所以就用数组来继承key相同的value，比如复选框中选多个。
> >   >
> >   > `String[] getParameterValues(String name)：根据名称获取参数值（数组）`
> >   >
> >   > `String getParameter(String name)：根据名称获取参数值（单个）`
> >   >
> >   > ~~~java
> >   > //1、获取所有参数的Map集合
> >   > Map<String, String[]> map = req.getParameterMap();
> >   > for(Map.Entry<String, String[]> entry : map.entrySet()) {
> >   >     String key = entry.getKey();
> >   >     String[] value = entry.getValue();
> >   >     System.out.print(key + " : ");
> >   >     for (String s : value) {
> >   >         System.out.print(s + " ");
> >   >     }
> >   >     System.out.println();
> >   > }
> >   > System.out.println("-------------");
> >   > //2、获取单个参数，明确该参数只对应一个value，才能使用该方法
> >   > String name = req.getParameter("userName");
> >   > System.out.println("userName : " + name);
> >   > System.out.println("-------------");
> >   > 
> >   > //3、获取多个参数，明确该参数对应多个value，才能使用该方法
> >   > String[] hobbies = req.getParameterValues("hobby");
> >   > System.out.print("hobby : ");
> >   > for (String s : hobbies) {
> >   >     System.out.print(s + " ");
> >   > }
> >   > System.out.println();
> >   > ~~~
> >   >
> >   > ==该代码放在doGet和doPost中都能够正确实现。==

# 快速创建Servlet以及修改模版

> **快速创建**
>
> <img src="D:\software\Typora_imgs\QQ_1742261601392.png" alt="QQ_1742261601392" style="zoom:50%;" />
>
> <img src="D:\software\Typora_imgs\QQ_1742261614015.png" alt="QQ_1742261614015" style="zoom:43%;" />
>
> **修改模版**
>
> ![QQ_1742261470386](D:\software\Typora_imgs\QQ_1742261470386-1742261489805-5.png)

# Request请求参数中乱码问题

## POST

> POST获取请求参数是通过流来进行的，Tomcat在进行编码时采用的是ISO-8859-1，但是html中编码格式为UTF-8
>
> 所以解决POST乱码这需要改变流的编码方式：`request.setCharacterEncoding("UTF-8")//设置字符输入流的编码`
>
> ~~~java
> @WebServlet("/URLRequest1")
> public class URLRequest1 extends HttpServlet {
>     @Override
>     protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
>         Map<String, String[]> map = request.getParameterMap();
>         for(Map.Entry<String, String[]> entry : map.entrySet()) {
>             String key = entry.getKey();
>             String[] values = entry.getValue();
>             System.out.print(key + ": ");
>             for(String value : values) {
>                 System.out.print(value + " ");
>             }
>             System.out.println();
>         }
>     }
> 
>     @Override
>     protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
>         doGet(request, response);
>     }
> }
> ~~~
>
> > 以下问题是在修改了表单中name，改成中文"姓名"后，就会出现如下问题:
> >
> > <img src="D:\software\Typora_imgs\QQ_1742264185495.png" alt="QQ_1742264185495" style="zoom:50%;" />
>
> ==解决方案==：`request.setCharacterEncoding("UTF-8);`
>
> ~~~java
> @WebServlet("/URLRequest1")
> public class URLRequest1 extends HttpServlet {
>     @Override
>     protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
>         request.setCharacterEncoding("UTF-8");
>         Map<String, String[]> map = request.getParameterMap();
>         for(Map.Entry<String, String[]> entry : map.entrySet()) {
>             String key = entry.getKey();
>             String[] values = entry.getValue();
>             System.out.print(key + ": ");
>             for(String value : values) {
>                 System.out.print(value + " ");
>             }
>             System.out.println();
>         }
>     }
> 
>     @Override
>     protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
>         doGet(request, response);
>     }
> }
> 
> ~~~
>
> <img src="D:\software\Typora_imgs\QQ_1742264285306.png" alt="QQ_1742264285306" style="zoom:50%;" />
>
> 

## GET

> GET请求方式与POST不同，POST是通过流来进行读写，GET则是通过方法getQueryString方法进行获取请求参数
>
> 乱码原因：浏览器不支持中文，浏览器进行中文字符串进行URL编码（UTF-8），tomcat接收到的数据进行URL解码（ISO-8859-1），编码解码格式不一致，导致乱码。
>
> <img src="D:\software\Typora_imgs\QQ_1742264597985.png" alt="QQ_1742264597985" style="zoom:50%;" />
>
> **URL编码**
>
> 1、将字符串按照编码方式转为二进制
>
> 2、每个字节转为2个16进制数并在前边加上%
>
> ==解决方式==：
>
> 1、先对乱码数据进行编码：转为字节数组
> byte[] bytes = "乱码参数".getBytes(StandardCharsets.ISO_8859_1);
>
> 2、对字节数组解码，转为字符串。
> "乱码参数" = new String(bytes, StandardCharsets.UTF-8)
>
> ==以下为演示如何解决乱码问题。==
>
> ~~~java
> public void test() throws UnsupportedEncodingException {
>     String name = "向远洋";
>     String encode = URLEncoder.encode(name, "utf-8");
>     System.out.println("浏览器URL编码后的name: " + encode);
> 
>     String decode = URLDecoder.decode(encode, StandardCharsets.ISO_8859_1);
>     System.out.println("tomcat服务器URL解码后的name: " + decode);
> 
>     //解决tomcat服务器解码乱码问题
>     byte[] bytes = decode.getBytes(StandardCharsets.ISO_8859_1); //不管是utf-8还是ISO_8859_1，底层的byte数组都是一样的
>     String newDecode = new String(bytes, StandardCharsets.UTF_8);
>     System.out.println("解决乱码后的参数：" + newDecode);
> 
>     }
> ~~~
>
> > ==Tomcat8.0之后，已将GET请求乱码问题解决，设置默认的解码方式为UTF-8==

# Request请求转发

> - **请求转发（forward）**：一种在服务器内部的资源跳转方式
>
> - 实现方式：
>   `req.getRequestDispatcher("资源B路径").forward(req, resp);`
>
> - 请求转发资源间共享数据：使用Request对象
>
>   - void setAttribute(String name, Object o):存储数据到request域中
>   - ObjectgetAtrribute(String name)：根据key，获取值
>   - void removeAttribute(String name)：根据key，删除该键值对
>
> - 请求转发特点：
>
>   - 浏览器地址栏路径不发生变化
>   - 只能转发到当前服务器的内部资源
>   - 一次请求，可以在转发的资源间使用request共享数据
>
>   ==以下为从RequestForward1跳转到RequestForward2的测试：==
>
> ~~~java
> @WebServlet("/RequestForward1")
> public class RequestForward1 extends HttpServlet {
>     /*
>     用来测试从ReqeustForward1页面跳转到RequestForward2页面的Servlet
>      */
>     @Override
>     protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
>         System.out.println("RequestForward1 servlet is running");
>         //共享数据
>         String name = "向远洋";
>         request.setAttribute("name", name);
>         //转发到RequestForward2页面
>         request.getRequestDispatcher("/RequestForward2").forward(request, response);
>     }
> 
>     @Override
>     protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
>         doGet(request, response);
>     }
> }
> 
> ~~~
>
> ~~~java
> @WebServlet("/RequestForward2")
> public class RequestForward2 extends HttpServlet {
>     @Override
>     protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
>         System.out.println("RequestForward2 servlet is running");
>         //测试共享数据
>         Object name = request.getAttribute("name");
>         System.out.println(name);
>     }
> 
>     @Override
>     protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
>         doGet(request, response);
>     }
> }
> ~~~
>
> 



# Response设置响应数据功能介绍

> - 响应数据分为3部分
>
>   - 1、响应行：`HTTP/1.1  200  OK`
>
>     > `void setStatus(int sc)`:设置响应头键值对，sc为状态码
>
>   - 2、响应头：`Content-Type：text/html`
>
>     > `void setHeader(String name, String value)`：设置响应头键值对
>
>   - 3、响应体：`<html><head></head><body></body></html>`
>
>     > `PrintWriter getWriter()`:获取字符输出流
>     >
>     > `ServletOutputStream getOutputStream()`：获取字节输出流
>
>     



# Response完成重定向

> <img src="D:\software\Typora_imgs\QQ_1742287922632.png" alt="QQ_1742287922632" style="zoom: 67%;" />
>
> ### **实现方式一&简化操作：**
>
> ```java
> protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
>     System.out.println("res1");
>     /*response.setStatus(302);
>     response.setHeader("location", "/webdemo3_war/res2");*/
> 
>     //简化方式只需要一行代码
>     response.sendRedirect("http://www.baidu.com");
> }
> ```
>
> ### ==请求转发和重定向的区别==
>
> <img src="D:\software\Typora_imgs\QQ_1742292894842.png" alt="QQ_1742292894842" style="zoom:50%;" />
>
> 

# 路径问题

> - ### 明确路径谁使用？
>
>   - `浏览器使用`：需要加虚拟目录（项目访问路径）
>   - `服务端使用`：不需要加虚拟目录
>
>   > 举例：
>   >
>   > < a href = '路径' >  浏览器访问，需要加虚拟目录
>   >
>   > < form action = '路径' > 同样也是浏览器访问，需要加虚拟目录
>   >
>   > req.getRequestDispatcher("路径")  服务器内部转发，不加虚拟目录
>   >
>   > resp.sendRedirect("路径") 浏览器访问，需要加虚拟目录 
>
>   <img src="D:\software\Typora_imgs\QQ_1742293717991.png" alt="QQ_1742293717991" style="zoom:50%;" />
>
>   ### 虚拟目录动态获取
>
>   1、通过getContextPath方法获取虚拟目录
>
>   `String contextPath = request.getContextPath();`
>
>   2、拼接路径，找到要访问的资源
>
>   `response.sendRedirect(contextPath + "/resp")`
>
>   ~~~java
>   String contextPath = request.getContextPath();
>   response.sendRedirect(contextPath + "/res2");
>   ~~~
>
>   

# Response响应字符数据&字节数据

## 字符数据

> ### 使用
>
> - 通过Response对象获取字符输出流
>   `PrintWriter writer = response.getWriter();`
> - 写数据（向浏览器写数据）
>   `writer.write("<h1>hello</h1>");`
>   `writer.wite("你好世界");`
>
> ### 注意
>
> - 该流==不需要关闭==，随着响应结束，response对象销毁，由服务器关闭
> - ==中文数据乱码==：原因通过Response获取的字符输出流默认编码：ISO-8859-1
>   `response.setContentType("text/html;charset=utf-8");` 是专门用来设置ContentType的方法
>   也可以使用`response.setHeader("Content-Type", "text/html; charset=UTF-8");`注意字符串之间用==;==隔开，同样text/html是用来标记写入的文本中有html文本，可以解析html，不加上则会当做纯文本打印。
>
> 
>
> ~~~java
> @Override
> protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
> //1、获取字符输入流
> //        response.setContentType("text/html; charset=UTF-8"); 
>     response.setHeader("Content-Type", "text/html;charset=UTF-8");
>     PrintWriter writer = response.getWriter();
>     writer.write("你好，世界!");
>     //2、设置响应头信息
>     writer.write("<h1>hello, world!</h1>");
> }
> ~~~
>
> 浏览器中打印信息如下：
>
> <img src="D:\software\Typora_imgs\QQ_1742296345914.png" alt="QQ_1742296345914" style="zoom:50%;" />
>
> <img src="D:\software\Typora_imgs\QQ_1742296367553.png" alt="QQ_1742296367553" style="zoom:70%;" />、
>
> 

## 字节数据

> ### 使用
>
> - 通过Response对象获取字节输入流
> - outputStream.write(字节数据);
>
> ### IOUtils工具类使用
>
> - 导入坐标
>
>   > <dependency>
>   >   <groupId>commons-io</groupId>
>   >   <artifactId>commons-io</artifactId>
>   >   <version>2.6</version>
>   > </dependency>
>
> - 使用
>   `IOUtils.copy(输入流, 输出流);`
>
> ~~~java
> protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
>     response.setContentType("video/mp4;charset=UTF-8");
>     FileInputStream fis = new FileInputStream("C:\\Users\\86188\\Videos\\美女打游戏.mp4"); //cdl镁铝
>     ServletOutputStream output = response.getOutputStream();
>     /* 纯练习字节流，但是以后直接就通过下面的工具类进行拷贝，比如文件图片视频等
>     byte[] buffer = new byte[1024];
>     int len = 0;
>     while((len = fis.read(buffer)) != -1) {
>         output.write(buffer, 0, len);
>     }
>     fis.close();
>     */
>     IOUtils.copy(fis, output); //使用IOUtils工具类
>     fis.close();
> }
> ~~~
>
> 



















