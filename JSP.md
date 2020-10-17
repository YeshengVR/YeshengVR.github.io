# Tomcat

- web相关概念：

  1. 软件架构

     1. C/S：客户端/服务器端

     2. B/S：浏览器/服务器端

        服务器可以简单地理解为：可以通过域名来访问到这个。

  2. 资源分类

     1. 静态资源：所有用户访问后，得到的效果都一样的，称为静态资源

        如：html,css,javascript

        静态资源可以直接被浏览器解析

     2. 动态资源：每个用户访问相同资源后，得到的结果可能不一样，称为动态资源。

        如：servlet/jsp，php，asp....

        动态资源被访问时是先转化为静态资源在解析。

  3. 网络通信三要素

     1. IP：电子设备(计算机)在网络中的唯一标识。
     2. 端口:应用程序在计算机中的唯一标识。(0~65536)将来自己写的程序端口号推荐不要写1024以内的。因为很有可能被操作系统占用了。
     3. 传输协议：数据传输的规则。
        1. 基础协议：
           1. TCP:安全协议，三次握手。速度稍慢
           2. UDP：不安全协议，有可能丢失数据。速度快

![image-20200926105627425](F:\md笔记文件\assets\Web概念.png)

- web服务器软件：Tomcat

  - 服务器：安装了服务器软件的计算机
  - 服务器软件：接受用户的请求，处理请求，作出响应。
  - web服务器软件：接受用户的请求，处理请求，作出响应。

  再web服务器软件中，可以部署web项目，让用户通过浏览器来访问这些项目。

  - 常见的java相关的web服务器软件：
    - webLogic：Oracle公司，大型的javaEE服务器，支持所有的JavaEE规范，收费的。
    - WebSphere：IBM公司，大型的JavaEE服务器，支持所有的JavaEE规范，收费的。
    - JBoss：JBoss公司的，大型的JavaEE服务器，支持所有的JavaEE规范，收费的。
    - Tomcat：Apache基金组织，中小型的Java EE服务器，仅仅支持少量的Java EE规范servlet/jsp。开源的，免费的。
  - JavaEE：java语言在企业级开发中使用的技术规范的总和，一共规定了13项大的规范。

安装地址：https://tomcat.apache.org/

![image-20201007132549906](F:\md笔记文件\assets\tomcat路径.png)

| **目录**     | **说明**                                                     |
| ------------ | ------------------------------------------------------------ |
| **/bin**     | **存放各种平台下用于启动和停止****Tomcat****的脚本文件**     |
| **/conf**    | **存放****Tomcat****服务器的各种配置文件**                   |
| **/lib**     | **存放****Tomcat****服务器所需的各种****JAR****文件**        |
| **/logs**    | **存放****Tomcat****的日志文件**                             |
| **/temp**    | **Tomcat****运行时用于存放临时文件**                         |
| **/**webapps | **当发布**Web**应用时，默认情况下会将**Web**应用的文件存放于此目录中** |
| **/work**    | **Tomcat****把由****JSP****生成的****Servlet****放于此目录下** |

启动Tomcat：
通过bin目录下的startup.bat,双击运行该文件即可。
访问：http://localhost:8080 访问自己的Tomcat
			http://其他人的IP:8080 访问其他人的Tomcat  端口号也是8080的情况下。

## 可能遇到的问题

### cmd窗口一闪而过

原因：没有正确配置JAVA_HOME环境变量
解决方案：正确配置JAVA_HOME环境变量

### 启动报错

1. 暴力：站到占用的端口号，并且找到对应的进程，杀死该进程

   通过cmd命令查找PID

   ```cmd
   netstat -ano
   ```

   再关闭掉这个pid对应的程序

2. 温柔：修改自身的端口号

   conf目录的server文件找到。

   ![image-20201007134836957](F:\md笔记文件\assets\tomcat端口号.png)

   ![image-20201007134909587](F:\md笔记文件\assets\tomcat端口号2.png)

   修改端口号 port就是默认端口号。

   一般会将tomcat的默认端口号修改为80，80端口号是http协议的默认端口号。
   **好处**：在访问时，就不用输入端口号。

   一般的网站都是将端口号设置为80.

关闭

1. 正常关闭：
   1. 双击bin目录下的shutdown.bat关闭
   2. 直接按下Ctrl+C
2. 强制关闭：点击启动窗口的x

## 配置

### 部署项目的方式

1. 直接将项目放到webapps目录下即可。

   /Demo：项目的访问路径--》虚拟目录
   简化部署：将项目打成一个war包，再将war包放置到webapps目录下。彼时，这个war包会自动解压缩。

2. 配置conf/server.xml文件

   在<Host>标签体中配置

   ```xml
   <!--Example-->
   <context docBase = "D:\hello" path = "/Demo" />
   ```

   docBase:项目存放的路径

   path：虚拟目录

3. 在conf\Catalina\localhost创建任意名称的xml文件。在文件中编写

   ```xml
   <!--Example-->
   <context docBase = "D:\hello" />
   ```

   虚拟目录：xml文件的名称。
   **最推荐的方式！！！**

### 静态项目和动态项目：

目录结构

- java动态项目的目录结构：

  --项目的根目录
  --web.xml:web项目的核心配置文件
  --classes目录：放置字节码文件的目录
  --lib目录：放置以来的jar包

将Tomcat集成到IDEA中，并且创建JavaEE的项目，部署项目。

### 部署web项目

1.  Window -> Preferences ->
MyEclipse -> Servers -> Tomcat
2.  选择Tomcat版本及安装路径
3.  设置为可用状态（Enable）
4.  指定Tomcat运行Java的运行
    环境

### 部署Web项目

1.  单击MyEclipse菜单栏上的部署图标
2.  选择需要部署的项目
3.  选择Tomcat服务器并确认



# Jsp

JSP (Java Server Pages)：在HTML中嵌入Java脚本代码。

JSP本质就是servlet。

Jsp在服务端运行。服务端的脚本语言。

Jsp的page指令：通过设置内部的多个属性定义整个页面的属性。

```jsp
<%@ page 属性1="属性值" 属性2="属性值1,属性值2"… 
                   属性n="属性值n"%>
```

| **属性**        | **描述**                                     | **默认值**                    |
| --------------- | -------------------------------------------- | ----------------------------- |
| **language**    | **指定****JSP****页面使用的脚本语言**        | **java**                      |
| **import**      | **通过该属性来引用脚本语言中使用到的类文件** | **无**                        |
| **contentType** | **用来指定****JSP****页面所采用的编码方式**  | **text/html,** **ISO-8859-1** |

JSP中的声明：

```jsp
常见的用于声明一个方法
<%! Java代码%>
```

**方法声明后可在页面中多处调用。**

JSP注释

```jsp
<%-- JSP注释--%>
<% //单行注释 %> 
<%  /*多行注释 */ %>
```

![image-20201008152350012](F:\md笔记文件\assets\jsp页面元素.png)

JSP执行过程

![image-20201008155715178](F:\md笔记文件\assets\JSP执行过程.png)

## 运行Web程序时常犯的错误

- 未启动Tomcat

  检查Tomcat服务能否正确运行

- 未部署Web应用

  检查Web应用是否正确部署

- URL输入错误

  检查URL

- 目录不能被应用

  检查文件的存放位置

**web程序的调试与排错**

页面报错：400以上一般是路径有问题类似404，405...
500以上一般是代码出现问题类似500....
WEB-INF下的文件不允许直接访问

![image-20201008163554539](F:\md笔记文件\assets\tomcat总结与jsp.png)

## JSP数据交互

### JSP内置对象

JSP内置对象是web容器创建的一组对象

```jsp
<%// Example %>
<%
        int[ ] value = { 60, 70, 80 };
        for  (int i : value) {
                out.print(i);
        } 
%>
```

没有声明和创建，却也可以使用out对象。

```jsp
<%=表达式%>  ==  <% out.print(表达式)%>
//其实这两种是同一种方式。
```

常用的jsp内置对象

- out
- request
- response
- session
- application
- exception
- page
- config
- pageContext

#### out对象

输出对象：数据到客户端输出，用于输出JSP页面的信息，提供print（）方法和println（）方法。

#### request对象

request对象主要用于处理客户端请求。

![image-20201008165011750](F:\md笔记文件\assets\request请求.png)

request对象常用方法：

| **方法名称**                                                | **说明**                                                     |
| ----------------------------------------------------------- | ------------------------------------------------------------ |
| **String** **getParameter**(String name)                    | **根据表单组件名称获取提交数据**                             |
| **String[ ]** **getParameterValues**(String name)           | **获取表单组件对应多个值时的请求数据**                       |
| **void** **setCharacterEncoding**(String **charset**)       | **指定每个请求的编码**                                       |
| **RequestDispatcher** **getRequestDispatcher**(String path) | **返回一个RequestDispatcher对象，该对象的forward( )方法用于转发请求** |

###### 获取数据时解决中文乱码问题

在页面设置支持中文字符的字符集，如：UTF-8；

在Tomcat目录结构\conf\server.xml中设置字符集
<Connector  port="8080"  protocol="HTTP/1.1"
connectionTimeout="20000"
redirectPort="8443"  URIEncoding="UTF-8"
/>

#### response对象

response对象用于响应客户请求并向客户端输出信息。

![image-20201008170549618](F:\md笔记文件\assets\response对象.png)

**页面重定向**：

- void sendRedirect(String location)
- 客户端将重新发送请求到指定的URL

页面重定向不携带请求数据。

**使用转发取代重定向实现页面跳转**

##### 请求的转发

- 转发的作用
  - 在服务器端，将请求发送给服务器上的其他资源，以共同完成一次请求的处理。
- 转发的实现
  - RequestDispatcher对象的forward()方法

```jsp
<%//Example %>
<%
RequestDispatcher rd = request.getRequestDispatcher("welcome.jsp");
rd.forward(request, response);
%>
```

在多个页面交互过程中，请求中的数据可以共享。

转发和重定向的路径都是从当前**页面**的根路径下开始找。

| 转发                                                         | 重定向                                                     |
| ------------------------------------------------------------ | ---------------------------------------------------------- |
| 转发是在服务器端发挥作用，将同一请求在服务器资源之间进行传递 | 重定向是在客户端发挥作用，通过发送一个新的请求实现页面转向 |
| 客户端浏览器的地址栏不会显示转向后的地址                     | 在地址栏中可以显示转向后的地址                             |

##### 会话

一个会话就是在一段时间内，一个客户端与Web服务器的一连串相关的交互过程。

#### session对象

session对象常用方法：

| **方法名称**                                        | **说明**                                     |
| --------------------------------------------------- | -------------------------------------------- |
| **String** **getId**()                              | **获取sessionid**                            |
| **void** **setMaxInactiveInterval**(int interval)   | **设定session的非活动时间**                  |
| **int** **getMaxInactiveInterval**()                | **获取session的有效非活动时间(以秒为单位)**  |
| **void invalidate**()                               | **设置session对象失效**                      |
| **void** **setAttribute**(String key, Object value) | **以key/value的形式保存对象值**              |
| **Object** **getAttribute**(String key)             | **通过key获取对象值**                        |
| **void** **removeAttribute**(String key)            | **从session中删除指定名称(key)所对应的对象** |

session与窗口的关系：

- 每个session对象都与一个浏览器窗口对应，重新开启一个浏览器窗口，可以重新创建一个session对象(不同版本浏览器可能有所差别)
- 通过超链接打开的新窗口，新窗口的session与其父窗口的session相同。

##### session对象的失效

- 手动设置失效：invalidate()

- 超时失效

  - 通过setMaxInactiveInterval()方法，单位是秒

  ```jsp
  <%//Example%>
  <%
  session.setAttribute("login","admin"); 
  session.setMaxInactiveInterval(600); 
  response.sendRedirect("admin.jsp");
  %>
  ```

  - 通过设置项目的web.xml或Tomcat目录下的/conf/web.xml文件，单位是分钟。

  ```xml
  <session-config>
      <session-timeout>10</session-timeout>
  </session-config>
  ```

当session对象失效，传的值就没了。

#### application对象

应用程序对象：表示整个服务器，所有客户端使用的application都是同一个；用于实现了用户间数据恭喜概念股，可存放全局变量。

#### exception对象

异常对象：表示错误页面处理操作，作用域：page。

#### page对象

页面对象：如同this一样，表示JSP整个页面。

#### config对象

配置对象：作用域：page，获取服务器配置信息，去初始化参数，初始化参数在web.xml中配置。

#### pageContext对象

页面上下文对象：作用域page；可以访问其他八个对象。

#### include指令

可以将一些拱形的内容写入一个单独的文件中，然后通过include指令引用该文件

```jsp
<%//Example%>
--loginControl.jsp
<%
String login = (String) session.getAttribute("login");
if (login == null) {
　　response.sendRedirect("index.jsp");
	return;
} %>
--后台其他页面中引用文件
<%@  include file="loginControl.jsp" %>
```

![image-20201008182626932](F:\md笔记文件\assets\jsp对象总结.png)

**base标签：设置当前所有的请求路径的基路径**

```jsp
<%
String path = request.getContextPath();
String basePath = request.getScheme()+"://"+request.getServerName()+":"+request.getServerPort()+path+"/";
%>
<base href ="<%=basepath%>">
```

## JSP中四大作用域

| **名称**                  | **说 明**                                                 |
| ------------------------- | --------------------------------------------------------- |
| **page****作用域**        | **在一个页面范围内有效，通过****pageContext****对象访问** |
| **request****作用域**     | **在一个服务器请求范围内有效**                            |
| **session****作用域**     | **在一次会话范围内容有效**                                |
| **application****作用域** | **在一个应用服务器范围内有效**                            |

### pageContext

**页面域**：页面作用域仅限于当前页面对象，可以近似于理解为java的this对象，离开当前JSP页面(无论是redirect还是forward)，则pageContext中的所有属性值就会丢失。

### request

**请求域**：请求作用域是同一个请求之内，在页面跳转时，如果通过forward方式跳转，则forward目标页面仍然可以拿到request中的属性值。如果通过redirect方式进行页面跳转，由于redirect相当于重新发出的请求，此种场景下，request中的属性值会丢失。

### session

**会话域**：会话作用域是在一个会话的的生命周期内，会话失效，则session中的数据也随之丢失。

### application

**应用域**：应用作用域是最大的，只要服务器不停止，则application对象就一直存在，并且为所有会话所共享。

application实现用户之间的数据共享

application对象的常用方法

| **方法名称**                                                 | **说 明**                               |
| ------------------------------------------------------------ | --------------------------------------- |
| **void** **setAttribute****(String key,**		  **Object value)** | **以****key/value****的形式保存对象值** |
| **Object** **getAttribute****(String key)**                  | **通过****key****获取对象值**           |
| **String** **getRealPath****(String path)**                  | **返回相对路径的真实路径**              |

```jsp
<!--Example统计网站访问次数的实现-->
-------统计页----------
 <%
	Integer count = (Integer) application.getAttribute("count");
	if (count != null) {
		count = 1 + count;
	} else {
		count = 1;	 	
	}
	application.setAttribute("count", count);
%>
-------显示页-----------
<%
	Integer i = (Integer) application.getAttribute("count");
	out.println("您好，您是第 " + i + " 位访问本网站的用户");
%>
```

![image-20201012093102896](F:\md笔记文件\assets\作用域.png)

## cookie

cookie是Web服务器保存在客户端的一系列文本信息。

cookie的作用

- 对特定对象的追踪
- 实现各种个性化服务
- 简化登录

安全性能

- 容易泄露信息

创建cookie对象

```java
//创建cookie对象
Cookie newCookie = new Cookie(String key, String value);
//写入cookie
response.addCookie(newCookie);
//读取cookie
  Cookie[] cookies = request.getCookies();

```

cookie对象的常用方法

| **方法名称**                                   | **说 明**                                            |
| ---------------------------------------------- | ---------------------------------------------------- |
| **void** **setMaxAge****(****int** **expiry)** | **设置****cookie****的有效期，以秒为单位**           |
| **void** **setValue****(String value)**        | **在****cookie****创建后，对****cookie****进行赋值** |
| **String** **getName****()**                   | **获取****cookie****的名称**                         |
| **String** **getValue****()**                  | **获取****cookie****的值**                           |
| **int** **getMaxAge****()**                    | **获取****cookie****的有效时间，以秒为单位**         |

### cookie与session对比

| session                          | cookie                     |
| -------------------------------- | -------------------------- |
| 在服务端保存用户信息             | 在客户端保存用户信息       |
| session中保存的是Object类型      | cookie保存的是string类型   |
| 随会话的结束而将共存储的数据销毁 | cookie可以长期保存在客户端 |
| 保存重要的信息                   | 保存不重要的用户信息       |

###### web.xml

**配置tomcat启动时打开的首页**

![img](F:\md笔记文件\assets\tomcat启动页.jpg)

文件上传

表单属性里要写入enctype = "multipart/form-data"。

method必须得为post。

```html
enctype = "multipart/form-data"
<!--Example-->
<form action ="" method="post" enctype="multipart/form-data">
    <input type="file" name = "file">
    <input type="submit" name = "submit">
</form>
```



# Servlet

servlet：server applet

概念：运行在服务器端的小程序
servlet就是一个接口，定义了Java类被浏览器访问到tomcat识别的规则。
将来我们自己定义一个类，实现servlet接口，复写方法。

快速入门：

1. 创建Java EE项目

2. 定义一个类，实现servlet接口

   ```java
   public class servletDemo implements Servlet
   ```

3. 实现接口中的抽象方法

4. 配置servlet

   在web.xml中配置

   ```xml
   <!--Example-->
   <servlet>
           <servlet-name>demo01</servlet-name><!--demo01:为输入网址时的地址-->
           <servlet-class>com.web.servlet.servletDemo</servlet-class>
       </servlet>
       <servlet-mapping>
           <servlet-name>demo01</servlet-name>
           <url-pattern>/demo01</url-pattern>
       </servlet-mapping>
   <!--输入类似路径就可以访问了：http://localhost:8080/JSP10_10_war_exploded/demo01-->
   ```

5. 执行原理

   1. 当服务器接收到客户端浏览器的请求后，会解析请求URL路径，获取访问的Servlet的资源路径
   2. 查找web.xml文件，是否有对应的<url-pattern>标签体内容。
   3. 如果有，则在找到对应的<servlet-class>全类名。
   4. tomcat会将字节码文件加载进内存，并且创建其对象。
   5. 调用其方法。

## servlet的生命周期

1. 被创建：执行init方法，只执行一次。

   - Servlet默认情况下，第一次被访问时，Servlet被创建

   - 可以配置指定创建时间

     第一次被访问时，创建
         <load-on-startup>的值为负数；默认值为-1。
     在服务器启动时，创建
         <load-on-startup>的值为0或正整数。

   Servlet的init方法，只执行一次，说明一个Servlet在内存中只存在一个对象，Servlet是单例的。

   多个用户同时访问时，可能存在线程安全问题。

   解决方法：尽量不要在Servlet中定义成员变量，即使定义了成员变量，也不要对其修改值。

2. 提供服务：执行service方法，执行多次。

   每次访问Servlet时，Service方法都会被调用一次。

3. 被销毁：执行destory方法，只执行一次。

   Servlet被销毁时执行。服务器关闭时，Servlet被销毁。
   只有服务器正常关闭时，才会执行destory方法。

剩余两个方法用的不多：

```java
/**
     * 获取ServletConfig对象
     * @return  Servlet元素对象
     */
    @Override
    public ServletConfig getServletConfig() {
        return null;
    }
    
/**
     * 获取Servlet的一些信息，版本，作者等等...
     * @return
     */
    @Override
    public String getServletInfo() {
        return null;
    }
```

## Servlet3.0

好处：支持注解配置，可以不需要web.xml

步骤：

1. 创建JavaEE项目，选择Servlet的版本3.0以上，可以不创建web.xml

2. 定义一个类，实现Servlet接口

3. 复写方法

4. 在类上使用@webServlet注解，进行配置

   ```java
   @WebServlet("资源路径")
   ```

   可以配置多个url

如果只需要写一个urlPatterns的话那可以省略不用写，直接写资源路径就可以了。

## Servlet体系结构

![image-20201014085504572](F:\md笔记文件\assets\Servlet体系结构.png)

- **GenericServlet**：

  将Servlet接口中其他的方法默认空实现，只将service()方法作为抽象。
  将来定义Servlet类时，可以继承GenericServlet，实现service()方法即可。

- **httpServlet**：

  对http协议的一种封装，简化操作

  1. 定义类继承HttpServlet
  2. 复写doGet/doPost方法

## Servlet相关配置

1. urlpartten：Servlet访问路径

   1. 一个Servlet可以定义多个访问路径：

      ```java
      //Example:
      @WebServlet({“/d4”,”/dd4”,”/ddd4”})
      ```

   2. 路径定义规则：

      1. /xxx
      2. /xxx/xxx





