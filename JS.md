# JavaScript

Javascript是一种基于对象和事件驱动的，并具有安全性能的脚本语言。

JS对大小写敏感

JavaScript特点

- 向HTML网页中添加交互行为
- 脚本语言，语法与Java类似
- 解释型语言，边执行边解释
- 安全性：js不能访问本地磁盘
- 跨平台：浏览器中都具备js解析器

![image-20200921094452025](F:\md笔记文件\JavaScript组成.png)

DOM：文档对象模型   BOM：浏览器对象模型

js在HTML中的书写方式有两种：

1. 内部脚本

   定义<script>，标签体内就是js代码

2. 外部脚本

   定义<script>，通过src属性引入外部的js文件
   
   <script src="../js/demo.js" type="text/javascript" charset="utf-8"></script>
   
3. 内嵌脚本：在某一行/某一个元素中可以直接写JavaScript代码类似于：

   ```html
   <input type = "button" value="" onclick = "javascript:alert('demo')";
   ```

   注意这样书写的时候，如果外面写的是双引号，里面就必须得写单引号，或者外面写单引号，里面写双引号。

注意：

- <script>可以定义在html页面的任何地方。但是定义的位置会影响执行顺序。

- <script>可以定义多个

- <script>....</script>虽然可以放在任何地方，但需要保证这些代码在使用前已被读取并加载到内存即可。

JavaScript的执行原理

![image-20200921101233002](F:\md笔记文件\assets\JavaScript执行原理.png)

注释：

1. 单行注释：//注释内容
2. 多行注释：/**/

## **数据类型**：

1. 原始数据类型（基本数据类型）
   1. number：数字。整数/小数NaN(not a number  一个不是数字的数字类型)
   2. string：字符串。字符串“abc”|“a”|‘abc’
   3. boolean：true/false
   4. null：一个对象为空的占位符
   5. undefined：未定义。如果一个变量没有给初始化值，则会被默认赋值为undefined
   
   null：空值与undefined的值相等
   
   **注意：number、boolean、string是伪对象**
   
2. 引用数据类型：对象

   ```js
   //类似的
   var obj = new Object();
   ```

   

3. 类型转换：

   1. number\boolean转换string：toString();

   2. string\boolean转换number： parseInt();\parseFloat();boolean不能转。

      string 可以将数字字符串转换成number 如果“123a3sd5” 转成123强制转换。

   3. Boolean()：强转成布尔

   4. 数字强转成布尔：非零就是true，零就是false

   5. 字符串强转成布尔*非“”（空字符串）*就是true，*空字符串“”*就是false。

   6. Number()强转成数字：布尔转数字：true转成1，false转成0

   7. 字符串转数字：不能强转。

## 变量：

一小块存储数据的内存区域。
Java语言是强类型语言。
JS是弱类型语言。

强类型：在开辟变量存储空间时，定义了空间将来存储的数据的数据类型。只能存储固定类型的数据
弱类型：在开辟变量存储空间时，不定义空间将来存储的数据的数据类型，可以存放任意类型的数据。

- 语法：

```javascript
var 变量名 = 值
```

```js
//输出到页面上
var num = 1;
document.write(num);
```

## **运算符**：

typeof运算符判断类型并获取他的字符串形式

```js
var num = 1;
typeof(num);
```

特殊的：null类型的typeof返回的类型时object而并非null。

![image-20200921153511590](F:\md笔记文件\assets\运算符.png)

| 运算符 | 描述         | 例子    | 等同于       | 结果 | 十进制 |
| :----- | :----------- | :------ | :----------- | :--- | :----- |
| &      | 与           | 5 & 1   | 0101 & 0001  | 0001 | 1      |
| \|     | 或           | 5 \| 1  | 0101 \| 0001 | 0101 | 5      |
| ~      | 非           | ~ 5     | ~0101        | 1010 | 10     |
| ^      | 异或         | 5 ^ 1   | 0101 ^ 0001  | 0100 | 4      |
| <<     | 零填充左位移 | 5 << 1  | 0101 << 1    | 1010 | 10     |
| >>     | 有符号右位移 | 5 >> 1  | 0101 >> 1    | 0010 | 2      |
| >>>    | 零填充右位移 | 5 >>> 1 | 0101 >>> 1   | 0010 | 2      |

### 一元运算符：

#### delete

delete 运算符删除对以前定义的对象属性或方法的引用。

```js
var o = new Object;
o.name = "David";
alert(o.name);	
-->David
delete o.name;
alert(o.name);
-->undefined
```

delete 运算符不能删除开发者未定义的属性和方法。

```js
delete o.toString;//报错
```

即使 toString 是有效的方法名，这行代码也会引发错误，因为 toString() 方法是原始的 ECMAScript 方法，不是开发者定义的。

#### void

void 运算符对任何值返回 undefined。该运算符通常用于避免输出不应该输出的值。

```js
<a href="javascript:void(window.open('about:blank'))">Click me</a>
//这使 window.open() 调用返回 undefined，它不是有效值，不会显示在浏览器窗口中。
```

没有返回值的函数真正返回的都是 undefined。

#### 增量/减量运算符++ --

这个与java的++--效果是相同的。写在前面就先执行在调用，写在后面就先调用在执行。

### 位运算符

ECMAScript 整数有两种类型，即有符号整数（允许用正数和负数）和无符号整数（只允许用正数）。在 ECMAScript 中，所有整数字面量默认都是有符号整数。



### 赋值运算符

　　　　var x = 5;

### 算数运算符

+: 遇到字符串变成连接
-：先把字符串转成数字然后进行运算
*: 先把字符串转成数字然后进行运算
/: 先把字符串转成数字然后进行运算

### 逻辑运算符

**&&	||**

### 比较运算符

<	>	>=	<=	!=	==
**注意：===:全等：类型与值都要相等**

### 三元运算符：

```js
var c = a>b?1:10;
语法：
表达式?值1：值2;
```

判断表达式的值，如果true则取值1，如果是false则取值2；
有符号整数使用 31 位表示整数的数值，用第 32 位表示整数的符号，0 表示正数，1 表示负数。数值范围从 -2147483648 到 2147483647。

**JS中的一些特殊语法**：

语句以; 结尾。如果一行只有一条语句则;可以省略(不建议)

```js
var a= 3
alert(a)
```

变量的定义使用var关键字，也可以不使用

- 用：定义的变量是局部变量
- 不用：定义的变量是全局变量(不建议)

```js
b=4;
alert(b);
/*****************/
function fun(){
var a =4;
    c=4;
}
fun();
alert(a);
alert(b);
```

## **流程控制语句**：

- if...else...
- switch
  - 在java中，switch语句可以接受的数据类型：byte，int，char，枚举(1.5jdk)，string(1.7jdk)
  - 在javascript中，switch可以接受任意的原始数据类型
- while
- do...while
- for

用法基本和java相同

```js
//用javascript书写的一个小练习九九乘法表
<script type="text/javascript">
			for (var a=1;a<10;a++) {
				for(var b=1;b<a;b++){
					document.write("<div>");
					document.write(a + " * " + b +" = "+(a*b));
					document.write("</div>");
				}
				document.write("<br /><br />");
			}
		</script>
```

## 基本对象

### Array对象

- **Array对象**：一个数组对象

  1. 创建

     1. var arr = new Array(元素列表);

        ```js
        var arr = new Array(1,"abc",true);
        ```

     2. var arr = new Array(默认长度);

        ```js
        var arr = new Array(5);
        ```

     3. var arr = [元素列表];

        ```js
        var arr = [1,2,3,4]
        ```

  2. 方法

     - join(参数):将数组中的元素按指定的分隔符拼接成字符串。
     - push():向数组的尾部添加一个或多个元素。
   - sort():给数组排序。
  
3. 属性
  
   - length可以设置数组长度（基本没人用）
  
  4. 特点

   - ```js
       var arr = new Array();相当于创建了一个空的数组
     ```
  
   - 如果只有一个数字元素则代表这个数组的长度。
  
   - js中，数组元素的类型是可变的。
  
     - js中，数组长度是可变的。若没有给值，则是undefined
     
     - 数组下标也是从0开始

### Boolean对象

- Boolean：表示两个值：“true”或“false”

  1. 创建

     - 构造函数new Boolean(value);

     ```js
     var Boolean = new Boolean(true);
     ```

     - 转换函数Boolean(value);

     ```js
     Boolean(true);
     ```

     **参数** *value* **由布尔对象存放的值或者要转换成布尔值的值。**

  2. 方法

     1. toString();把逻辑值转换为字符串，并返回结果。
     2. valueOf();返回Boolean对象的原始值。

  3. 属性

  4. 特点

     - 其实就是个基本类型的包装类没有特别的特殊

### Date对象

- Date

  1. 创建

     1. new Date();

     ```js
     var date = new Date();
     ```

  2. 方法

     1. toLocalString：返回当前date对象对应的时间本地字符串格式
     2. getTime();获取毫秒值。返回当前时间对象描述的时间到1970年1月1日零点的毫秒值差。
     
  3. **注意**:如果要获取时间的年份使用的是**getFullYear()**;

### Math对象

- Math数学对象

  1. 创建

     - 特点：该Math对象不用创建，直接使用。类似的Math.方法名();

  2. 方法

     1. random():返回0-1之间的随机数（包含0不包含1）

     2. ceil(x);对数进行上舍入。类似：

        ```js
        Math.ceil(0.1) ==1;
        ```

     3. floor(x):对数进行下舍入。

        ```js
        Math.floor(1.9) ==1;
        ```

     4. round(x):把数四舍五入为最接近的整数

     5. abs():绝对值

     6. pow(x,y)：返回 x 的 y 次幂
  
  3. 属性
  
     1. PI：圆周率的兀

### Number对象

- Number:基本数据类型的包装类对象

  如果想要规定一个数后面有几位小数点可以使用toFixed()方法

  ```js
  //Example：
  var n = new Number(3456);
  alert(n.toFixed(2));
  ```

### String对象

- String：基本数据类型的包装类对象

  去某一字符串后面多少的字符可以使用slice()方法

  ```js
  //Example:
  var str = “32px”;
  var str1 = str.slice(-2);
  alert(str);
  alert(str1);
  -->32px
  -->px
  ```

### RegExp对象

- RegExp：正则表达式对象

  1. 正则表达式：定义字符串的组成规则

     1. 单个字符：[]

        如[a]表示：a;[ab]表示啊或者b;[a-z]表示a到z中的一个。特殊符号代表特殊含义的单个字符：

        - \d:单个数字[0-9]
        - \w单个单词字符[a-zA-Z0-9]

     2. 量词符号

        - ?:表示出现0次或1次

        - *:表示出现0次或多次

        - +:表示出现1次或多次

        - {m,n}:表示：m <= 数量 <= n

          m如果缺省：{,n}：表示最多n次；n如果缺省：{m,}：表示最少m次。

  2. 正则对象：

     1. 创建：

        1. var reg = new RegExp(“正则表达式”);

           ```js
           var reg = new RegExp("^\\w{,6}$");
           ```

        2. var reg = /正则表示/;(常用)

           ```js
           var reg = /^\w{,6}$/
           ```

     2. 方法：

        1. test(参数)：验证指定的字符串是否符合正则定义的规范

           ```js
           var reg = /^\w{6,12}$/;
           var username = "zhangsan";
           var flag = reg.test(username);
           alert(flag);
           -->true
           ```

### Global对象

- Global：全局对象，这个Global对象中封装的方法不需要对象就可以直接调用。 方法名();

  1. 方法

     1. encodeURI()：url编码

     2. decodeURI()：url解码

     3. endodeURIComponent()：url编码 编码的字符更多。可以编码的字符更多

     4. decodeURIComponent()：url解码

     5. 强制转换
      　　　　Number()
           　　　　String()
           　　　　Boolean()
  
     6. parseInt(str):
  
        ```js
        var str = "235abc";
        var number = parseInt(str);
        alert(number);
        -->235
        
        ```
  
      var str = "a235abc";
        var number = parseInt(str);
      alert(number);
        -->NaN
  
     7. isNaN():判断一个值是否是NaN**如果一个数字是NaN则返回false；不是则返回true**
  
      ```js
     
        NaN六亲不认，连自己都不认。NaN参与的==比较全部为false
        var a = NaN;
      document.write(a == NaN);
        document.write(isNaN(a));
      -->false
        -->true
      ```
     
     8. eval():将javaScript字符串转成JavaScript脚本代码来执行。
  
      ```js
     var jscode = "alert(123)";
      eval(jscode);
        -->123
      ```
     
  2. 编码
  
     - GBK编码：1个字节8个二进制位
       1个字节编译成两个数字，每个字节之间用%间隔。
     - 使用编码解码方法快速编译。

### **Function对象**

- **Function对象**：描述一个方法或函数的对象

  - 创建

    1. 对象函数

       var fun = new Function(形式参数列表，方法体);(不建议)

       ```js
       var fun = new function("a","b","alert(a);")
       ```

    2. 普通函数

       function 方法名称(形式参数列表){
       方法体
       }

       ```js
       function fun(a,b){
       alert(a+b);
       }
       ```

    3. 匿名函数

       var 方法名 = function(){

       方法体
       }

       ```js
       var fun = function(a,b){
       alert(a+b);
       }
       ```

  - 方法

  - 属性

    1. length属性：代表形参个数

  - 特点

    1. 方法定义时：形参的类型不用写

    2. 方法是一个对象，如果定义名称相同的方法，会覆盖。后面定义的方法对象会覆盖掉前面的方法

    3. 在js中方法的调用只与方法的名称有关，和参数列表无关。参数列表有多少都可以调用这个方法。

    4. 在方法声明中有一个隐藏的内置对象(数组),arguments,封装了所有的实际参数。（就是把所有的实际参数都放在一个数组里面）

       ```js
       //求任意个数个参数的和
       function add(){
           var sum =0;
           for(var i =0;i<arguments.length;i++){
               sum += arguments[i];
           }
           return sum;
       }
       ```

       

    5. 方法的返回值类型也是可以不用写，因为是弱类型所以都是var就不需要写。

  - 调用

    1. 方法名称(实际参数列表);

## **js的常用事件**

onclick:点击事件
onchange:域内容被改变的事件
onfoucus:获得焦点的事件
onblur:失去焦点的事件
onmouseover:鼠标悬浮的事件
onmouseout:鼠标离开的事件
onload:加载完毕的事件

## 事件的绑定方式

- 将事件和响应行为都内嵌到html标签中

  ```js
  <input type="button" value="button"  onclick="alert('xxx')"/>
  ```

- 将事件内嵌到html中而响应行为用函数进行封装

  ```js
  <input type="button" value="button" onclick="fn()" />
  <script type="text/javascript">
  function fn(){
  alert("yyy");
  }
  ```

- 将事件和响应行为 与html标签完全分离

  ```js
  <input id="btn" type="button" value="button"/>
  <script type="text/javascript">
  var btn = document.getElementById("btn");
  btn.onclick = function(){
  alert("zzz");
  };
  </script>
  ```

### **this关键字**

this经过事件的函数进行传递的是html标签对象

```js
<input id="btn" name="mybtn" type="button" value="button123" onclick="fn(this)"/>
<script type="text/javascript">
function fn(obj){
alert(obj.name);
}
</script>
```

### 阻止事件的默认行为

```js
IE：window.event.returnValue = false;
W3c: 传递过来的事件对象.preventDefault();
//ie：window.event.returnValue = false;
//W3c：传递过来的事件对象.preventDefault();
//W3c标准
if(e&&e.preventDefault){
alert("w3c");
e.preventDefault();
//IE标签
}else{
alert("ie");
window.event.returnValue = false;
}

//通过事件返回false也可以阻止事件的默认行为
<a href="demo11.html" onclick="return false">点击我吧</a>
```

### 阻止事件的传播

```js
IE：window.event.cancelBubble = true;
W3c: 传递过来的事件对象.stopPropagation();
if(e&&e.stopPropagation){
alert("w3c");
e.stopPropagation();
//IE标签
}else{
alert("ie");
window.event.cancelBubble = true;
}	
```

## BOM

![image-20200922161534860](F:\md笔记文件\assets\BOM对象.png)

BOM提供了独立于内容的、可以与浏览器窗口进行互动的对象结构。

BOM对象又包含DOM对象，但因为DOM对象特别重要，所以又细分了DOM对象。

![image-20200922093403733](F:\md笔记文件\assets\BOM模型.png)

功能：

- 弹出新的浏览器窗口
- 移动、关闭浏览器窗口以及调整窗口的大小
- 页面的前进、后退

### window窗口对象

常用属性：

| **属性名称** | **说   明**                           |
| ------------ | ------------------------------------- |
| **history**  | **有关客户访问过的****URL****的信息** |
| **location** | **有关当前** **URL** **的信息**       |

**语法**：window.属性名= "属性值"

实例：

```js
window.location="http://www.baidu.com" ; 
//表示跳转到百度首页
```

常用方法：

| **方法名称**                   | **说   明**                                                  |
| ------------------------------ | ------------------------------------------------------------ |
| **prompt( )**                  | **显示可提示用户输入的对话框**                               |
| **alert( )**                   | **显示带有一个提示信息和****一个****确定按钮的警示框**       |
| **confirm****( )**             | **显示一个****带有提示信息、确定和取消按钮的对话框**         |
| **close( )**                   | **关闭浏览器窗口**                                           |
| **open( )**                    | **打开一个新的浏览器窗口，加载给定** **URL** **所指定的文档** |
| **setTimeout****( )**          | **在指定的毫秒数后调用函数或计算表达式**                     |
| **set****I****nterval****( )** | **按照指定的周期（以毫秒计）来调用函数或表达式**             |

confirm()方法：语法：

```js
confirm("对话框中显示的纯文本");
/*Example；
<script type="text/javascript">
   var flag=confirm("确认要删除此条信息吗？");
    if(flag==true)
	      alert("删除成功！");
      else
	       alert("你取消了删除");
</script>
*/
```

alert( )：一个参数，仅显示警告对话框的消息，无返回值，不能对脚本产生任何改变
prompt( )：两个参数，输入对话框，用来提示用户输入一些信息，单击“取消”按钮则返回null，单击“确定”按钮则返回用户输入的值，常用于收集用户关于特定问题而反馈的信息
confirm( )：一个参数，确认对话框，显示提示对话框的消息、“确定”按钮和“取消”按钮，单击“确定”按钮返回true，单击“取消”按钮返回false，因此与if-else语句搭配使用。

弹框的方法：
提示框：alert("提示信息");
确认框：confirm("确认信息");
有返回值：如果点击确认返回true 如果点击取消 返回false
var res = confirm("您确认要删除吗？");
alert(res);
输入框：prompt("提示信息");
有返回值：如果点击确认返回输入框的文本 点击取消返回null
var res = prompt("请输入密码？");
alert(res);
open方法：
window.open("url地址");	
open("../jsCore/demo10.html");

控制台打印方法：

```js
Console.log(...);//括号中放想要打印在控制台的东西。
```



open()方法：语法：

```js
window.open("弹出窗口的url","窗口名称","窗口特征”);
```

属性：

| **属性名称**                          | **说   明**                                                  |
| ------------------------------------- | ------------------------------------------------------------ |
| **height、width**                     | **窗口文档显示区的高度、宽度。以像素计**                     |
| **left、top**                         | **窗口的****x坐标、y坐标****。****以像素计**                 |
| **toolbar=yes \| no \|1 \| 0**        | **是否显示浏览器的工具栏。黙认是****yes**                    |
| **scrollbars=yes \| no \|1 \| 0**     | **是否显示滚动条。黙认是****yes**                            |
| **location=yes \| no \|1 \| 0**       | **是否显示地址地段。黙认是****yes**                          |
| **status=yes \| no \|1 \| 0**         | **是否添加状态栏。黙认是****yes**                            |
| **menubar****=yes \| no \|1 \| 0**    | **是否显示菜单栏。黙认是****yes**                            |
| **resizable=yes \| no \|1 \| 0**      | **窗口是否可调节尺寸。黙认是****yes**                        |
| **titlebar****=yes \| no \|1 \| 0**   | **是否显示标题栏。黙认是****yes**                            |
| **fullscreen****=yes \| no \|1 \| 0** | **是否使用全屏模式显示浏览器。黙认是****no。处于全屏模式的窗口必须同时处于剧院模式** |

window对象不需要创建可以直接使用，window使用，window.方法名();
window可以省略，直接使用方法名();

### history历史记录对象

| **名称**      | **说   明**                                          |
| ------------- | ---------------------------------------------------- |
| **back()**    | **加载** **history** **对象列表中的前一个****URL**   |
| **forward()** | **加载** **history** **对象列表中的下一个****URL**   |
| **go()**      | **加载** **history** **对象列表中的某个具体****URL** |

![image-20200922103554072](F:\md笔记文件\assets\history.png)

### location地址栏对象

常用方法

| **名称**      | **说   明**                |
| ------------- | -------------------------- |
| **reload()**  | **重新加载当前文档**       |
| **replace()** | **用新的文档替换当前文档** |

常用属性

| **名称**     | **说   明**                                   |
| ------------ | --------------------------------------------- |
| **host**     | **设置或返回主机名和当前****URL****的端口号** |
| **hostname** | **设置或返回当前****URL****的主机名**         |
| **href**     | **设置或返回完整的****URL**                   |

### Navigator浏览器对象

基本不用了解

### screen显示器屏幕对象

基本不用了解

## DOM

HTML DOM模型结构化对象树：

![DOM HTML æ ](F:\md笔记文件\assets\HTML DOM树.gif)

功能：控制html文档的内容
代码：获取页面标签对象Element

```js
document.getElementById("Id值");
//通过元素的ID获取元素对象。
```

### 操作Element对象

- 修改属性值：

  1. 明确获取的对象是哪一个?
  2. 查看API文档，找其中有哪些属性可以设置

- 修改标签体内容

  ```js
  属性：对象.innerHTML = "Change"//Change为要修改的内容
  ```

  1. 获取元素对象
  2. 使用innerHTML属性修改标签体内容

W3C DOM 标准被分为 3 个不同的部分

- 核心DOM - 针对任何结构化文档的标准模型
  - Document：文档对象
    - 创建(获取)：在html dom模型中可以使用window对象来获取
      1. `window.document`
      2. `document`
    - 方法：
      1. 获取Element对象：
         - getElementById()：根据id属性值获取元素对象，id属性值唯一。
         - getElementsByTagName():根据元素名称获取元素对象们。返回值是一个数组。
         - getElementsByClassName():根据class属性值获取元素对象们，返回值是一个数组。
         - getElementsByName():根据name属性值获取元素对象们。
      2. 创建其他DOM对象：
         - createAttribute(name)
         - createComment()
         - createElement():创建一个Element对象
         - createTextNode()
    
  - Element：元素对象
    - 获取/创建：通过document对象获取或者创建对象。
    - 方法：
      - removeAttribute(name):删除属性
      - setAttribute():设置属性
      - createComment()
      - createElement()
      - createTextNode()
    
  - Attribute：属性对象
  
  - Text：文本对象
  
  - Comment：注释对象
  
  - **Node：节点对象，其他5个的父对象**
  
    - 特点：所有dom对象都可以被认为是一个节点
  
    - 方法：
  
      - CRUD dom树的方法：
  
        [^CRUD]: 增删改查
  
        - appendChild():向节点的子节点列表的结尾添加新的子节点。
        - removeChild():删除(并返回)当前节点的指定子节点。
        - replaceChild():用新节点替换一个子结点。
        - get....
  
    - 属性：parentNode 返回节点的父节点
- XML DOM -  针对XML文档的标准模型
- HTML DOM - 针对HTML文档的标准模型

#### 根据层级关系访问节点

节点对象代表文档树中的一个节点。

节点属性

| **属性名称**    | **描述**                                                   |
| --------------- | ---------------------------------------------------------- |
| parentNode      | 返回节点的父节点                                           |
| childNodes      | 返回子节点集合，childNodes[i]                              |
| firstChild      | 返回节点的第一个子节点，最普遍的用法是访问该元素的文本节点 |
| lastChild       | 返回节点的最后一个子节点                                   |
| nextSibling     | 下一个节点                                                 |
| previousSibling | 上一个节点                                                 |

```js
///Example：
var sonNode = document.getElementById("son");
var fatherNode = sonNode.parentNode;
//返回节点的父节点
如果要修改样式可以这样写
fatherNode.style.属性 = "样式";
HTML元素.style.样式属性＝"值";
//如果属性里面有-的话省略掉，类似于 font-size在js中设置样式时写成：fontsize
```

**注意**：childNodes有的浏览器会把空的空格也当成一个节点。推荐使用children
可以这样书写

> oNext = oParent.nextElementSibling || oParent.nextSibling   
> oPre = oParent.previousElementSibling || oParent.previousSibling  
> oFirst = oParent. firstElementChild  ||  oParent.firstChild   
> oLast = oParent.lastElementChild || oParent.lastChild 

element属性

| firstElementChild      | 返回节点的第一个子节点，最普遍的用法是访问该元素的文本节点 |
| ---------------------- | ---------------------------------------------------------- |
| lastElementChild       | 返回节点的最后一个子节点                                   |
| nextElementSibling     | 下一个节点                                                 |
| previousElementSibling | 上一个节点                                                 |

操作节点属性

语法：

```js
getAttribute("属性名")
setAttribute("属性名","属性值")
```

nodeName：节点名称
nodeValue：节点值
nodeType：节点类型

| **节点类型** | **NodeType****值** |
| ------------ | ------------------ |
| 元素element  | 1                  |
| 属性attr     | 2                  |
| 文本text     | 3                  |
| 注释comments | 8                  |
| 文档document | 9                  |

#### 创建节点

| **名称**                | **描述**                            |
| ----------------------- | ----------------------------------- |
| createElement( tagName) | 创建一个标签名为tagName的新元素节点 |
| A.appendChild( B)       | 把B节点追加至A节点的末尾            |
| insertBefore( A,B )     | 把A节点插入到B节点之前              |
| cloneNode(deep)         | 复制某个指定的节点                  |

#### 删除和替换节点

| **名称**                                | **描述**                   |
| --------------------------------------- | -------------------------- |
| removeChild( node)                      | 删除指定的节点             |
| replaceChild( newNode, oldNode)属性attr | 用其他的节点替换指定的节点 |

###### 补充：

超链接功能：

1. 可以被点击，样式改变
2. 点击后跳转到href指定的url

需求：保留功能，丢掉功能2

实现：

```js
href=“javascript:void(0)”;
```

### Document对象

常用属性：

| **名称**     | **说   明**                                                  |
| ------------ | ------------------------------------------------------------ |
| **referrer** | **返回载入当前文档****的****URL**获取关联页面（从哪跳转过来的页面） |
| **URL**      | **返回当前文档的****URL**                                    |

语法：

```js
document.referrer
document.URL
/*Example
function ud(){
		var ie = document.referrer;//获取关联页面（从哪跳转过来的页面）。
		if(ie.indexOf("xx.html")>=0){
			document.write("您是从xx.html跳转过来的");
			
		}else{
			document.write("宁不是从xx.html跳转过去，5秒后自动跳转");
			setTimeout(function(){
				location.href = "xx.html";
			},5000);//等待5秒后跳转到某页
		}
	}
*/
```

常用方法：

| **名称**                       | **说   明**                                                  |
| ------------------------------ | ------------------------------------------------------------ |
| **getElementById****()**       | **返回对拥有指定****id****的第一****个对象的引用**(对象id唯一) |
| **getElementsByName****()**    | **返回带有指定名称的对象的集合**（相同的name属性）           |
| **getElementsByTagName****()** | **返回带有指定标签名的对象的集合**（相同的元素）             |
| **write()**                    | **向文档写文本、****HTML****表达式或****JavaScript****代码** |

```js
function fun(){
var namenode = document.getElementById("Id值");
namenode.innerHTML;//innerHTML是用于获取这个Id里面所有元素的
}
```

```js
//Example
//获取指定某个父级元素里面的某种子元素
var father = document.getElementById("父级元素的id");
var son = father.getElementsByTagName("子元素的标签值");
```

定时器：
setTimeout(函数,毫秒值);

```js
setInterval(函数,毫秒值);//每隔一段时间执行一次。
setTimeout(函数,毫秒值);//隔一段时间执行一次，之后不再执行。
```

#### 清除函数

- [ ] clearTimeOut()

语法：clearTime(setTimeOut()返回的ID值)

```js
var  myTime＝setTimeout("disptime() ", 1000 );
clearTimeout(myTime)；
```

- [ ] clearInterval()

语法：clearIntercal(setInterval()返回的ID值)

```js
var  myTime＝setInterval("disptime() ", 1000 );
clearInterval(myTime)；

```

location	
location.href="url地址";

history
back();
forward();
go();

```HTML
<a href="demo7.html">后一页</a>
<input type="button" value="上一页" onclick="history.back()">
<input type="button" value="下一页" onclick="history.forward()">

<input type="button" value="上一页" onclick="history.go(-1)">
<input type="button" value="下一页" onclick="history.go(1)">
```

### style属性

HTML DOM

1. 标签体的设置和获取：innerHTML

2. 使用html元素对象的属性

3. 控制样式

   1. 使用元素的style属性镭射纸

   2. 提前定义好类选择器的样式，通过元素的className属性来设置其class属性值。

      ```js
      //Example
      div2.onclick = function(){
          div2.className = "newclass";
      }//newclass为一个class类样式。
      ```

      

HTML元素.style.样式属性＝"值"

```js
document.getElementById("titles").style.color="#ff0000"; 
document.getElementById("titles").style.fontSize="25px ";
```

注意：HTML元素. currentStyle.样式属性;这个currentStyle兼容IE浏览器

HTML中元素属性

| **属性**         | **描述**                                                   |
| ---------------- | ---------------------------------------------------------- |
| **offsetLeft**   | **返回当前元素左边界到它上级元素的左边界的距离，只读属性** |
| **offsetTop**    | **返回当前元素上边界到它上级元素的上边界的距离，只读属性** |
| **offsetHeight** | **返回元素的高度**                                         |
| **offsetWidth**  | **返回元素的宽度**                                         |
| **offsetParent** | **返回元素的偏移容器，即对最近的动态定位的包含元素的引用** |
| **scrollTop**    | **返回匹配元素的滚动条的垂直位置**                         |
| **scrollLeft**   | **返回匹配元素的滚动条的水平位置**                         |
| **clientWidth**  | **返回元素的可见宽度**                                     |
| **clientHeight** | **返回元素的可见高度**                                     |

![image-20200923110330985](F:\md笔记文件\assets\操作DOM对象.png)

## 事件

1. 事件
   - 功能：某些组件被执行了某些操作后，触发某些代码的执行。
2. 如何绑定事件
   1. 直接在html标签上，指定事件的属性(操作)，属性值就是js代码。
      1. onclick点击事件
   2. 获取js获取元素对象，指定事件属性

| **名称**    | **描述**                     |
| ----------- | ---------------------------- |
| onclick     | 当用户单击某个对象时调用事件 |
| onmouseover | 鼠标移到某元素之上           |
| onmouseout  | 鼠标从某元素移开             |
| onmousedown | 鼠标按钮被按下               |

* 常见的事件：
  1. 点击事件：
  	1. onclick：单击事件
  	2. ondblclick：双击事件
  2. 焦点事件
  	1. onblur：失去焦点
  	2. onfocus:元素获得焦点。
  3. 加载事件：
  	1. onload：一张页面或一幅图像完成加载。
  4. 鼠标事件：
  	1. onmousedown	鼠标按钮被按下。
  	2. onmouseup	鼠标按键被松开。
  	3. onmousemove	鼠标被移动。
  	4. onmouseover	鼠标移到某元素之上。
  	5. onmouseout	鼠标从某元素移开。

  5. 键盘事件：
      1. onkeydown	某个键盘按键被按下。	
      2. onkeyup		某个键盘按键被松开。
      3. onkeypress	某个键盘按键被按下并松开。
  6. 选择和改变
      1. onchange	域的内容被改变。
      2. onselect	文本被选中。
  7. 表单事件：
      1. onsubmit	确认按钮被点击。
      2. onreset	重置按钮被点击。

## JS面向对象

JS的属性不需要先声明有这个属性。可以直接创建并赋值。类似于

```js
var flower = new Object();
flower.name = "牵牛花";
flower.open = function(){
		alert("开花啦~@—_—@！");
	}
alert(flower.name);
flower.open();
```

**创建对象的第二种方式**（常用）

```js
var stu = {
    name:"tom",
    age:20,
    study:function(){
        alert(this.name+"好好学习！~~")
    }
}
//注意中间都不是用.而是:与键值对形式大致相同
```

### 构造函数：

```js
//Example：
function Person(name,age){
	this.name = name;
	this.age = age;
	this.info = function(){
		alert(this.age)
	}
}
//原型
//Person.prototype
Person.prototype.address = "江西";
Person.prototype.study = function(){
	alert("好好学习");
}
通过Person.prototype.属性/方法来添加这个Person属性或方法
```

js对象也可以继承。 

```js
子类.prototype = new 父类();
子类.prototype = 父类.prototype;
改变了父类的原型同时，子类的原型也会改变。因为是子类的原型指向父类的对象。
```

原型：类名.prototype指向它本身的类型。

```js
_proto_:是指向其父类对象
```

- [ ] 一个原型对象是另一个原型对象的实例
- [ ] 相关的原型对象层层递进，就构成了实例与原型的链条，就是原型链

要给原型增加属性首先必须得有属性，类似于要给一个继承的原型添加属性，必须先写继承语句。

#### 原型与构造函数之间的关系

![image-20200924143401655](F:\md笔记文件\assets\原型.png)

上图中调用man1.getFoot()经历的三个步骤：

- 搜索实例
- 搜索Man.prototype
- 搜索Humans.prototype

#### Object再原型链中的位置

![image-20200924150502777](F:\md笔记文件\assets\Object在原型链中的位置.png)

**注意：**

![image-20200924153411923](F:\md笔记文件\assets\原型的注意点.png)

如果这个里面是数组，如果一个对象添加或删除了数组里面的值。则同一个类的其他对象也会修改。写在原型里面也都会修改**如果非数组则不会。如果只是修改里面的值也不会。**

### 借用构造函数

```js
apply([thisOjb[,argArray]])
//中括号代表可写可不写
//Example：
类名.apply(this,[arg,arg,arg]);
```

```js
call([thisObj[,arg1[,arg2[,  [,argN]]]]])
//中括号代表可写可不写，arg代表参数
//Example:
类名.call(this,arg,arg);
```

调用一个对象的一个方法，以另一个对象替换当前对象。

组合继承：有时也叫做伪经典继承
将原型链和借用构造函数的技术组合到一块，发挥二者之长的一种继承模式
使用原型链实现对原型属性和方法的继承，而通过借用构造函数来实现对实例属性的继承

![image-20200924160103808](F:\md笔记文件\assets\原型对象.png)



# JQuery

jQuery由美国人John Resig于2006年创建
jQuery是目前最流行的JavaScript程序库，它是对JavaScript对象和函数的封装
它的设计思想是write less,do more。

示例：实现隔行变色只需一句代码：

```javascript
$("tr:even").css("background-color","#e8f0f2");
```

jQuery功能：

- 访问和操作DOM元素
- 控制页面样式
- 对页面事件进行处理
- 扩展新的jQuery插件
- 与Ajax技术完美结合

jQuery优势：

- 体积小，压缩后只有100KB左右
- 强大的选择器
- 出色的DOM封装
- 可靠的事件处理机制
- 出色的浏览器兼容性
- 使用隐式迭代简化编程
- 丰富的插件支持

jQuery可以进入以下网址获取http://jquery.com

| **名称**                                             | **大小**         | **说   明**                                                  |
| ---------------------------------------------------- | ---------------- | ------------------------------------------------------------ |
| **jquery-1.****版本号****.****js****（开发版）**     | **约****286KB**  | **完整无压缩版本，主要用于测试、学习和开发**                 |
| **jquery-1.****版本号****.****min.js****（发布版）** | **约****94.8KB** | **经过工具压缩或经过服务器开启****Gzip****压缩，主要应用于发布的产品和项目** |

```js
//jQuery弹出提示框
<script>
     $(document).ready(function() {
        alert("我欲奔赴沙场征战jQuery，势必攻克之！");
    });
</script>
```

$(document).ready()与window.onload类似，但也有区别.

| ** **        | **window.onload**                                            | **$(document).ready()**                                      |
| ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **执行时机** | ** ****必须等待网页中所有的内容加载完毕后（包括图片、****flash****、视频等）才能执行**** ** | **网页中所有****DOM****文档结构绘制完毕后即刻执行，可能与****DOM****元素关联的内容（图片、****flash****、视频等）并没有加载完** |
| **编写个数** | **同一页面不能同时编写多个**                                 | **同一页面能同时编写多个**                                   |
| **简化写法** | **无**                                                       | **$(function(){** **//****执行代码****}) ;**                 |

## jQuery语法结构

```js
$(selector).action() ;
工厂函数$()：将DOM对象转化为jQuery对象
选择器 selector：获取需要操作的DOM 元素
方法action()：jQuery中提供的方法，其中包括绑定事件处理的方法
```

- addClass( )方法为元素添加样式

  ```js
  jQuery 对象.addClass([样式名]);
  //Example：
  $("#current").addClass("current");  
  ```

- css( )方法设置元素样式

  ```js
  css("属性","属性值") ;//设置一个css属性
  css({"属性1":"属性值1","属性2":"属性值2"...}) ;//同时设置多个css属性
  //Example：
  $(this).css({"background":"#c81623"});
  ```

- show( )、hide( ) 方法设置元素的显示和隐藏

  ```js
  $(selector).show( );
  $(selector).hide( );
  //Example：
  $(".nav-top").show( );
  $("p").hide( );
  ```

鼠标移入移出添加/删除类样式的方法。

![image-20200925105136984](F:\md笔记文件\assets\鼠标移入移出的效果.png)

next()方法

获取同级其他元素的方法：

```js
$(this).siblings().action
```

用于筛选表达式,找到每个段落的后面紧邻的同辈元素。

```javascript
//Example：
<p>Hello</p><p>Hello Again</p><div><span>And Again</span></div>
$("p").next();//jQuery代码
--[ <p>Hello Again</p>, <div><span>And Again</span></div> ]  ///找到的结果
//Example2：
<p>Hello</p><p class="selected">Hello Again</p><div><span>And Again</span></div>
$("p").next(".selected");
--[ <p class="selected">Hello Again</p> ]///找到的结果
```

可以在此地址查看jQuery文档：https://jquery.cuishifeng.cn/

## JQuery代码风格

“$”等同于“jQuery”

```js
$(document).ready()=jQuery(document).ready()
$(function(){...})=jQuery (function(){...}) 
```

### 链式操作

对一个对象进行多重操作，并将操作结果返回给该对象。

```js
//Example：
$("h2").css("background-color","#ccffff").next().css("display","block");
```

### 隐式迭代

```js
//Example：
 $(document).ready(function() {
        $("li").css({"font-weight":"bold","color":"red"});
    });
```

### 添加注释

| **阶段**         | **说明**                                                     |
| ---------------- | ------------------------------------------------------------ |
| **开发阶段**     | **为代码添加注释，可以增加代码的可读性，能够让别人很容易的读懂你的代码，便于后期维护** |
| **维护阶段**     | **建议把关键的模块形成开发文档，便于后期维护，即便后期删除代码注释，也不影响后期维护** |
| **产品正式发布** | **建议删除注释，减少文件大小，加快下载速度，提高用户体验**   |

## DOM对象和jQuery对象

DOM对象：直接使用JavaScript获取的节点对象

```js
var objDOM=document.getElementById("title"); 

var objHTML=objDOM.innerHTML;  
```

 jQuery对象：使用jQuery包装DOM对象后产生的对象，它能够使用jQuery中的方法

```js
$("#title").html( );
等同于
document.getElementById("title").innerHTML;
```

DOM对象和jQuery对象分别拥有一套独立的方法，不能混用。

### DOM对象转jQuery对象

 使用$()函数进行转化：$(DOM对象)

```js
var txtName = document.getElementById("txtName"); //DOM对象
var $txtName =$(txtName);//jQuery对象
```

**注意**：

jQuery对象命名一般约定以$开头
在事件中经常使用$(this)，this是触发该事件的对象。

**jQuery对象是一个类似数组的对象，可以通过[index]的方法得到相应的DOM对象。**

```js
var $txtName = $ ("#txtName"); //jQuery对象
var txtName = $txtName[0]; //DOM对象
```

通过get(index)方法得到相应的DOM对象。

```js
var $txtName =$("#txtName"); //jQuery对象
var txtName =$txtName.get(0);//DOM对象
```

attr()方法用于修改属性。

offset():获取元素偏移

![image-20200925091455812](F:\md笔记文件\assets\jQuery.png)

jQuery中获取某一元素中的值通过.val()就能获取

```html
//Example:
<h2>hello!</h2>
$("h2").val();
-->hello!
```

补充：

div无法执行获取焦点事件。

## jQuery选择器

jQuery选择器类似于css选择器，用来选取网页中的元素

```js
$("h3").css("background","#09F");
```

获取并设置网页中所有<h3>元素的背景
“h3”为选择器语法，必须放在$()中
$(“h3”)返回jQuery对象
.css()是为jQuery对象设置样式的方法

同级其他元素选择器siblings()

```js
$(this).siblings()//不包含这个当前元素的其他元素
```

jQuery选择器功能强大，种类也很多，分类如下
通过CSS选择器选取元素
基本选择器
层次选择器
属性选择器
通过过滤选择器选择元素
基本过滤选择器
可见性过滤选择器

| **名称**         | **语法构成**                          | **描述**                                   | **示例**                                                     |
| ---------------- | ------------------------------------- | ------------------------------------------ | ------------------------------------------------------------ |
| **标签选择器**   | **element**                           | **根据给定的标签名匹配元素**               | **$("h2" )****选取所有****h2****元素**                       |
| **类选择器**     | **.class**                            | **根据给定的****class****匹配元素**        | **$(" .title")****选取所有****class****为****title****的元素** |
| **ID****选择器** | **#id**                               | **根据给定的****id****匹配元素**           | **$(" #title")****选取****id****为****title****的元素**      |
| **并集选择器**   | **selector1,selector2,...,selectorN** | **将每一个选择器匹配的元素合并后一起返回** | **$("div,p,.title" )****选取所有****div****、****p****和拥有****class****为****title****的元素** |
| **全局选择器**   | *****                                 | **匹配所有元素**                           | **$("\*"** **)****选取所有元素**                             |

标签选择器根据给定的标签名匹配元素

```js
//Example：
$(document).ready(function(){
    $("dt").click(function(){
        $("dd").css("display","block"); 
    });
    $("h1").css("color","blue");
})
```

类选择器根据给定的class匹配元素

```js
//Example：
$(".price").css({"background":"#efefef","padding":"5px"});
```

ID选择器根据给定的id匹配元素

```js
//Example：
$("#author").css("color","#083499");
```

并集选择器用来合并元素集合

```js
Example：
$(".intro,dt,dd").css("color","#ff0000");
```

全局选择器可以获取所有元素

```js
//Example：
$("*").css("font-weight","bold");
```

层次选择器通过DOM 元素之间的层次关系来获取元素

| **名称**           | **语法构成**            | **描述**                                                     | **示例**                                                     |
| ------------------ | ----------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **后代选择器**     | **ancestor descendant** | **选取****ancestor****元素里的所有****descendant****（后代）元素** | **$("#menu span" )****选取****#menu****下的****<span>****元素** |
| **子选择器**       | **parent>child**        | **选取****parent****元素下的****child****（子）元素**        | **$(" #menu>span" )****选取****#menu****的子元素****<span>** |
| **相邻元素选择器** | **prev+next**           | **选取紧邻****prev****元素之后的****next****元素**           | **$(" h2+dl " )****选取紧邻****<h2>****元素之后的同辈元素****<dl>** |
| **同辈元素选择器** | **prev~sibings**        | **选取****prev****元素之后的所有****siblings****元素**       | **$(" h2~dl " )****选取****<h2>****元素之后所有的同辈元素****<dl>** |

后代选择器用来获取元素的后代元素

```js
//Example：
$(".textRight p").css("color","red");
```

子选择器用来获取元素的子元素

```js
//Example：
$(".textRight>p").css("color","red");
```

相邻选择器用来选取紧邻目标元素的下一个元素

```js
//Example： 
$("h1+p").css(text-decoration","underline");
```

同辈选择器用来选取目标元素之后的所有同辈元素

```js
//Example：
$("h1~p").css("text-decoration","underline");
```

属性选择器通过HTML元素的属性来选择元素

| **语法构成**            | **描述**                                 | **示例**                                                     |
| ----------------------- | ---------------------------------------- | ------------------------------------------------------------ |
| **[attribute^=value]**  | **选取给定属性是以某些特定值开始的元素** | **$(" [href****^='en']"** **)****选取****href****属性值以****en****开头的元素** |
| **[attribute$=value]**  | **选取给定属性是以某些特定值结尾的元素** | **$(" [href****$='.jpg']"** **)****选取****href****属性值以****.jpg****结尾的元素** |
| **[attribute\*=value]** | **选取给定属性是以包含某些值的元素**     | **$(" [href\*** **='txt']"** **)****选取****href****属性值中含有****txt****的元素** |

属性选择器可以根据是否包含某属性来选取元素

```js
$("#news a[class]").css("background","#c9cbcb");
```

属性选择器可以根据属性的值来选取元素

```js
//Example：
$("#news a[class='hot']").css("background","#c9cbcb");
```

- 属性选择器可以指定属性值以指定值开头的元素

```js
//Example：a标签href属性值以www开头
$("#news a[href^='www']").css("background","#c9cbcb");
```

- 属性选择器可以指定属性值以指定值结尾的元素

```js
//Example:a标签href属性值以html结尾
$("#news a[href$='html']").css("background","#c9cbcb");
```

- 属性选择器可以指定属性值包含指定值的元素

```js
//Example:a标签href属性值包含“k2”的元素
$("#news a[href*='k2']").css("background","#c9cbcb");
```

not选择器:not(select)不选select的选择器

### 过滤选择器

- 通过特定的过滤规则来筛选出所需的元素
- 主要分类
  - 基本过滤选择器
  - 可见性过滤选择器
  - 表单对象过滤选择器
  - 内容过滤选择器、子元素过滤选择器……

| **语法**       | **描述**                                                     | **示例**                                                     |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **:eq(index)** | **选取索引等于****index****的元素（****index****从****0****开始）** | **$("li:eq(1)" )****选取索引等于****1****的****<li>****元素** |
| **:gt(index)** | **选取索引大于****index****的元素（****index****从****0****开始）** | **$(" li:gt(1)" )****选取索引大于****1****的****<li>****元素（注：大于****1****，不包括****1****）** |
| **:lt(index)** | **选取索引小于****index****的元素（****index****从****0****开始）** | **$(“li:lt(1)”** **)****选取索引小于****1****的****<li>****元素（注****：小于****1****，不包括****1****）** |
| **:header**    | **选取所有标题元素，如****h1~h6**                            | **$(":header" )****选取网页中所有标题元素**                  |
| **:focus**     | **选取当前获取焦点的元素**                                   | **$(":focus" )****选取当前获取焦点的元素**                   |
| **:animated**  | **选择所有动画**                                             | **$(":animated" )****选取当前所有动画元素**                  |

可见性过滤选择器

通过元素显示状态来选取元素

| **语法**     | **描述**               | **示例**                                 |
| ------------ | ---------------------- | ---------------------------------------- |
| **:visible** | **选取所有可见的元素** | **$(":visible" )****选取所有可见的元素** |
| **:hidden**  | **选取所有隐藏的元素** | **$(":hidden" )** **选取所有隐藏的元素** |

```js
//Example：
$("p:hidden").show();
$("p:visible").hide();
```

**选择器中的空格**
**选择器的书写规范很严格，多一个空格或少一个空格，都会影响选择器的效果**

```js
//Example1：
var $t_a = $(".test :hidden"); //带空格的jQuery选择器
//--》选取class为“test”的元素内部的隐藏元素
var $t_b = $(".test:hidden");  //不带空格的jQuery选择器
//--》选取隐藏的class为“test”的元素
```

**转义字符名的注意点**

![image-20200926103445785](F:\md笔记文件\assets\jQuery转义符.png)

![image-20200925174210060](F:\md笔记文件\assets\jQuery选择器.png)

## jQuery事件

jQuery事件是对JavaScript事件的封装，常用事件分类。

| 基础事件   | 复合事件     |
| ---------- | ------------ |
| 鼠标事件   | 鼠标光标悬停 |
| 键盘事件   | 鼠标连续点击 |
| window事件 |              |
| 表单事件   |              |

### 鼠标事件

鼠标事件是当用户在文档上移动或单击鼠标时而产生的事件。

| **方法**          | **描述**                                               | **执行时机**           |
| ----------------- | ------------------------------------------------------ | ---------------------- |
| **click( )**      | **触发或将函数绑定到指定元素的****click****事件**      | **单击鼠标时**         |
| **mouseover( )**  | **触发或将函数绑定到指定元素的****mouseover****事件**  | **鼠标指针移****过时** |
| **mouseout( )**   | **触发或将函数绑定到指定元素的****mouseout****事件**   | **鼠标指针移出****时** |
| **mouseenter**( ) | **触发或将函数绑定到指定元素的****mouseenter****事件** | **鼠标指针进入时**     |
| **mouseleave**( ) | **触发或将函数绑定到指定元素的****mouseleave****事件** | **鼠标指针离开时**     |

鼠标事件的区别

| **方法**         | **相同点**                   | **不同点**                                                   |
| ---------------- | ---------------------------- | ------------------------------------------------------------ |
| **mouseover( )** | **鼠标进入被选元素时会触发** | **鼠标在其被选元素的子元素上来回进入时：****触发****mouseover****( )****不触发****mouseenter** |
| **mouseenter()** |                              |                                                              |
| **mouseout( )**  | **鼠标离开被选元素时会触发** | **鼠标在其被选元素的子元素上来回离开时：****触发****mouseout****不触发****mouseleave** |
| **mouseleave()** |                              |                                                              |

### 键盘事件

用户每次按下或者释放键盘上的键时都会产生事件，常用键盘事件。

| **方法**        | **描述**                                     | **执行时机**           |
| --------------- | -------------------------------------------- | ---------------------- |
| **keydown( )**  | **触发或将函数绑定到指定元素的**keydown事件  | **按下键盘时**         |
| **keyup( )**    | **触发或将函数绑定到指定元素的**keyup事件    | **释放按键时**         |
| **keypress( )** | **触发或将函数绑定到指定元素的**keypress事件 | **产生可打印的字符时** |

```js
//Example1：
$("[type=password]").keyup(function () {
	$("#events").append("keyup");
      }).keydown(function (e) {
	$("#events").append("keydown");
      }).keypress(function () {
	$("#events").append("keypress");
     });
//Example2：
$(document).keydown(function (event) {
	 if (event.keyCode == "13") {
		alert("确认要提交么？");
	}
});
//当按下回车键时触发alert语句
//event代表这个事件对象可以有参可以不带参。
```



### 浏览器事件

语法

```js
 $(selector).resize( );
//调整窗口大小时，完成页面特效
```

### 绑定事件与移出事件

- 绑定事件

  - 语法：

    ```js
    bind(type,[data],fn);
    //type：事件类型，主要包括click、mouseover、mouseout等基础事件，此外，还可以是自定义事件
    //[data]：可选函数
    //fn：处理函数
    ```

  - 绑定单个事件

    ```js
     $(document).ready(function(){
    $(".on").bind("mouseover",function(){
    		$(".topDown").show();
    	});
    });
    ```

  - 绑定多个事件

    ```js
    $(".top-m .on").bind({
    	mouseover:function(){
    		$(".topDown").show();
    	},
    	mouseout:function(){
    		$(".topDown").hide();
    	}
    });
    ```

- 移出事件

  - 语法：

    ```js
    unbind([type],[fn])
    //[type]：事件类型，主要包括：blur、focus、click、mouseout等基础事件，此外，还可以是自定义事件
    //[fn]:处理函数
    ```

    当unbind()不带参数时，表示移除所绑定的全部事件。

### 复合事件

- hover()方法：相当于mouseover与mouseout事件的组合。

  - 语法：

    ```js
    hover(enter,leave);
    //enter：移入时函数
    //leave：移出时函数
    //Example：
    $(".top-m .on").hover(function(){
    	$(".topDown").show();
              },
             function(){
    	 $(".topDown").hide();
             }
    );
    ```

- toggle()方法：用于模拟鼠标连续click事件。

  - 语法：

    ```js
    toggle(fn1,fn2,...,fnN);
    //每次鼠标连续点击所触发的事件
    ```

  - 注意：

    toggle()方法不带参数，与show( )和hide( )方法作用一样。

- toggleClass( )可以对样式进行切换

  - 语法：

    ```js
    toggleClass(className);
    //Example：
    $("input").click(function(){$("p").toggleClass("red");})
    ```

- toggle( )和toggleClass( )总结

  - toggle( fn1,fn2...)实现单击事件的切换，无须额外绑定click事件
  - toggle( )实现事件触发对象在显示和隐藏状态之间切换
  - toggleClass( )实现事件触发对象在加载某个样式和移除某个样式之间切换

## jQuery动画效果

- 控制元素显示与隐藏
- 改变元素的透明度
- 改变元素高度
- 自定义动画

### 控制元素的显示与隐藏

**show()** 控制元素的显示，**hide( )**控制元素的隐藏。

```js
$(selector).show([speed],[callback])
$(selector).hide([speed],[callback])
//speed:可选。表示速度，默认为“0”，可能值：毫秒（如1000）、slow、normal、fast
//callback:可选。show函数执行完之后，要执行的函数
```

### 改变元素的透明度

**fadeIn()**和**fadeOut()**可以通过改变元素的透明度实现淡入淡出效果。

```js
$(selector).fadeIn([speed],[callback])
$(selector).fadeOut([speed],[callback])
//speed可选。表示速度，默认为“0”，可能值：毫秒（如1000）、slow、normal、fast
//callback:可选。show函数执行完之后，要执行的函数
```

### 改变元素的高度

**slideDown()** 可以使元素逐步延伸显示
**slideUp()**则使元素逐步缩短直至隐藏

```js
$(selector).slideUp ([speed],[callback])
$(selector).slideDown ([speed],[callback])
//Example：
$(document).ready(function() {
       $("h2").click(function(){
	   $(".txt").slideUp("slow");
	   $(".txt").slideDown("slow");
       });
 });
```

### 自定义动画

```js
$(selector). animate({params},speed,callback)
//params：必须，定义形成动画的CSS属性
```

![image-20200928095054035](F:\md笔记文件\assets\jQuery动画.png)

## DOM-操作

DOM操作分为三类

- DOM Core：任何一种支持DOM的编程语言都可以使用它，如getElementById()
- HTML-DOM：用于处理HTML文档，如document.forms
- CSS-DOM：用于操作CSS，如element.style.color="green"

JavaScript用于对(x)html文档进行操作，它对这三类DOM操作都提供了支持。

jQuery对JavaScript中的DOM操作进行了封装。

jQuery中的DOM操作

- 样式操作
- 内容及Value值操作
- 节点操作
- 节点属性操作
- 节点遍历
- CSS-DOM操作

“元素”和“节点”含义大同小异，不严格区分。

### 样式操作

使用css()为指定的元素设置样式值或获取样式值。

```js
css(name,value) ;
或
css({name:value, name:value,name:value…}) ;
//Example：
$(this).css("border","5px solid #f5f5f5");
或
$(this).css({"border":"5px solid #f5f5f5","opacity":"0.5"});
```

#### 追加样式

```js
$(selector).addClass(class);
或
$(selector).addClass(class1 class2 … classN);
//Example：
CSS：
.content {background-color:#FFFF00; }
.border {border:1px dashed #333; }
jQuery：
$("h2").mouseover(function() {
     $("p").addClass("content border");
});
```

#### 移出样式

```js
$(selector).removeClass("class") ;
或
$(selector).removeClass("class1 class2 … classN ") ;
//Example：
$("h2").mouseout(function() {
        $("p").removeClass("content");
});
```

#### 切换样式

toggleClass()：模拟了addClass()与removeClass()实现样式切换的过程。

```js
$(selector).toggleClass(class) ;
//Example：
$("h2").click(function() {
    $("p").toggleClass("content  border");
});
```

#### 判断是否还有指定样式

```js
$(selector). hasClass(class);
//Example：
$("h2").mouseout(function() {
      if($("p").hasClass("content ")) {
	$("p").removeClass("content ");
    }
});

```

### 内容及Value值操作

#### html代码操作

html()可以对HTML代码进行操作，类似于JS中的innerHTML。

```js
$("div.left").html();//获取元素中的HTML代码
或
 $("div.left").html("<div class='content'>…</div>");//设置元素中的html代码
```

#### 标签内容操作

text()可以获取或设置元素的文本内容。

```js
$("div.left").text();//获取元素中的文本内容
或
$("div.left").text("<div class='content'>…</div>");//设置元素中的文本内容
```

#### html()与text()

| **语法格式**       | **参数说明**                                | **功能描述**                                   |
| ------------------ | ------------------------------------------- | ---------------------------------------------- |
| **html( )**        | **无参数**                                  | **用于获取第一个匹配元素的**HTML内容或文本内容 |
| **html(content)**  | **content****为****元素的****HTML****内容** | **用于设置所有匹配元素的**HTML内容或文本内容   |
| **text( )**        | **无参数**                                  | **用于获取所有匹配元素的文本内容**             |
| **text (content)** | **content****为****元素的文本内容**         | **用于设置所有匹配元素的文本内容**             |

#### 属性值操作

val()可以获取或设置元素的value属性值。

```js
$(this).val();//获取元素的value属性值
或
$(this).val(value);//设置元素的value属性值
```

### 节点操作

查找节点:根据选择器来查找结点。

#### 创建节点

创建节点元素

工厂函数$()用于获取或创建节点

- $(selector)：通过选择器获取节点
- $(element)：把DOM节点转化成jQuery节点
- $(html)：使用HTML字符串创建jQuery节点

```js
var $newNode=$("<li></li>");
 var $newNode1=$("<li>你喜欢哪些冬季运动项目？</li>");
var $newNode2=$("<li title='last'>北京申办冬奥会是再合适不过了！</li>");
```

#### 插入节点

元素内部插入子节点

| **语法**               | **功能**                                                     |
| ---------------------- | ------------------------------------------------------------ |
| **append(content)**    | **$(**A).append(B)表示将B追加到A中如：$("ul").append($newNode1); |
| **appendTo(content)**  | **$(**A).appendTo(B)表示把A追加到B中如*：$newNode1.appendTo("ul"); |
| **prepend(content)**   | **$(**A). prepend (B)表示将B前置插入到A中如：$("ul"). prepend** **($newNode1);** |
| **prependTo(content)** | **$(**A). prependTo (B)表示将A前置插入到B中如：$newNode1. **prependTo ("ul");** |

元素外部插入同辈节点

| **语法**                  | **功能**                                                     |
| ------------------------- | ------------------------------------------------------------ |
| **after(content)**        | **$(A).after (B)**表示将B插入到A之后如：$("ul").after($newNode1); |
| **insertAfter(content)**  | **$(A). insertAfter (B)**表示将A插入到B之后如：$newNode1.insertAfter("ul"); |
| **before(content)**       | **$(A). before (B)**表示将B插入至A之前如：$("ul").before($newNode1); |
| **insertBefore(content)** | **$(A). insertBefore (B)**表示将A插入到B之前如：$newNode1.insertBefore("ul"); |

#### 删除节点

jQuery提供了三种删除节点的方法。

- remove()：删除整个节点

  ```js
  $(selector).remove([expr]);
  ```

- empty()：清空节点内容

  ```js
  $(selector).empty();
  ```

- detach()：删除整个节点，保留元素的绑定事件、附加的数据

#### 替换节点

replaceWith()和replaceAll()用于替换某个节点。

```js
//Example：replaceWith()
var $newNode1=$("<li>你喜欢哪些冬季运动项目？</li>");
$(".gameList li:eq(2)").replaceWith($newNode1);
```

```js
//Example:replaceAll()
$($newNode1).replaceAll(".gameList li:e
```

两者的关系类似于append()和appendTo().

#### 复制节点

clone()用于复制某个节点.

```js
$(selector).clone([Even[,deepEven]]) ;
//Even:一个布尔值（true 或者 false）指示事件处理函数是否会被复制。
//deepEven：一个布尔值，指示是否对事件处理程序和克隆的元素的所有子元素的数据应该被复制。
//Example：
$(".gameList li:eq(1)").click(function(){
$(this).clone(true).appendTo(".gameList");
})
$(".gameList li:eq(2)").click(function(){
$(this).clone(false).appendTo(".gameList");
})
```

### 属性操作

#### 获取与设置元素属性

attr()用来获取与设置元素属性。

```js
$(selector).attr([name]);//获取属性值
或
$(selector).attr({[name1:value1]…[nameN:valueN]}) ;//设置多个属性的值
//Example：
$(".contain img").attr({width:"200",height:"80"});
```

#### 删除元素属性

removeAttr()用来删除元素的属性。

```js
$(selector).removeAttr(name) ;
//Example：
$(".contain img").removeAttr("alt");
//删除元素的alt属性
```

### 节点遍历

#### 遍历子元素

children()方法可以用来获取元素的所有子元素。但不包含子元素的子元素。

```js
$(selector).children([expr]);
//Example：
var $section =$("section").children();//获取<section>的子元素，但不包含子元素的子元素
alert($section.length);
```

#### 遍历同辈元素

jQuery可以获取紧邻其后、紧邻其前和位于该元素前与后的所有同辈元素。

| **语法**             | **功能**                                                     |
| -------------------- | ------------------------------------------------------------ |
| **next([expr])**     | **用于获取紧邻匹配元素之后的元素****$("li:eq(1)").****next****().addClass("orange");** |
| **prev([expr])**     | **用于获取紧邻匹配元素之前的元素****$("li:eq(1)").****prev****().addClass("orange");** |
| **slibings([expr])** | **用于获取位于匹配元素前面和后面的所有同辈元素****$("li:eq(1)").****siblings****().addClass("orange");** |

#### 遍历前辈元素

jQuery中可以遍历前辈元素

- **parent()**：获取元素的父级元素

  ```js
  $("li:eq(1)").parent().addClass("orange");
  ```

- **parents()**：元素元素的祖先元素

  ```js
  $("li:eq(1)").parents().addClass("orange");
  ```

jQuery中提供了find()、filter()等节点操作方法。

#### 其他遍历方法

**each( )** ：规定为每个匹配元素规定运行的函数

```js
$(selector).each(function(index,element)) ;
//index：选择器的位置；element：当前的元素
//Example：
$("img").click(function(){
       $("li").each(function(){
           var str=$(this).text()+"<br>";
           $("section").append(str);
       })
});
```

end( )：结束当前链条中的最近的筛选操作，并将匹配元素集还原为之前的状态。

```js
//Example：
$(".contain :header").css({"background":"#2a65ba","color":"#ffffff"});
$(".gameList li").first().css("background","#b8e7f9").end().last().css ("background","#d3f4b5");
$(".gameList li:last").css("border","none");
```

### CSS-DOM操作

除css()外，还有获取和设置元素高度、宽度等的样式操作方法。

| **语法**                       | **功能**                                                     |
| ------------------------------ | ------------------------------------------------------------ |
| **css()**                      | **设置或返回匹配元素的样式属性**                             |
| **height([value])**            | **设置或返回匹配元素的高度**                                 |
| **width([value])**             | **设置或返回匹配元素的宽度**                                 |
| **offset([value])**            | **返回以像素为单位的****top****和****left****坐标。仅对可见元素有效** |
| **offsetParent****( )**        | **返回最近的已定位祖先元素。定位元素指的是元素的****CSS position****值被设置为****relative****、****absolute****或****fixed****的元素** |
| **position( )**                | **返回第一个匹配元素相对于父元素的位置**                     |
| **scrollLeft****([position])** | **参数可选。设置或返回匹配元素相对滚动条左侧的偏移**         |
| **scrollTop****([position])**  | **参数可选。设置或返回匹配元素相对滚动条顶**                 |

![image-20200929101937129](F:\md笔记文件\assets\jQuery_DOM.png)

## 表单效验

表单验证的作用：

- 减轻服务器的压力
- 保证输入数据符合要求

![image-20200929200438586](F:\md笔记文件\assets\BS请求.png)

常用的表单验证：

- 日期格式
- 表单元素是否为空
- 用户名和密码
- E-mail地址
- 身份证号码

验证表单元素步骤

1. 获得表单元素值
2. 使用JavaScript的一些方法对数据进行判断
3. 当表单提交时，触发事件，对获取的数据进行验证

### 表单选择器

表单选择器用于选取某些特定的表单元素，比如所有单选按钮或隐藏的元素。

| **语法**  | **描述**                                     | **示例**                                                     |
| --------- | -------------------------------------------- | ------------------------------------------------------------ |
| :input    | 匹配所有input、textarea、select和button 元素 | $("#myform :input")选取表单中所有的input、select和button元素 |
| :text     | 匹配所有单行文本框                           | $("#myform :text")选取email 和姓名两个input 元素             |
| :password | 匹配所有密码框                               | $("#myform :password" )选取所有<input type="password" />元素 |
| :radio    | 匹配所有单项按钮                             | $("#myform :radio")选取<input type="radio" />元素            |
| :checkbox | 匹配所有复选框                               | $(" #myform :checkbox " )选取<input type="checkbox " />元素  |
| :submit   | 匹配所有提交按钮                             | $("#myform :submit " )选取<input type="submit " />元素       |

| **语法** | **描述**                                    | **示例**                                                     |
| -------- | ------------------------------------------- | ------------------------------------------------------------ |
| :image   | 匹配所有图像域                              | $("#myform :image" )选取<input type=" image" />元素          |
| :reset   | 匹配所有重置按钮                            | $(" #myform :reset " )选取<input type=" reset " />元素       |
| :button  | 匹配所有按钮                                | $("#myform :button" )选取button 元素                         |
| :file    | 匹配所有文件域                              | $(" #myform :file" )选取<input type=" file " />元素          |
| :hidden  | 匹配所有不可见元素，或者type 为hidden的元素 | $("#myform :hidden" )选取<input type="hidden " />、style="display: none"等元素 |

**属性过滤选择器**

| **语法**  | **描述**                                                  | **示例**                                                     |
| --------- | --------------------------------------------------------- | ------------------------------------------------------------ |
| :enabled  | 匹配所有可用元素                                          | $(" #userform :enabled" )匹配form内部除编号输入框外的所有元素 |
| :disabled | 匹配所有不可用元素                                        | $(" #userform :disabled" )匹配编号输入框                     |
| :checked  | 匹配所有被选中元素（复选框、单项按钮、select 中的option） | $(" #userform :checked" )匹配“性别”中的“男”选项和“爱好”中的“编程”选项 |
| :selected | 匹配所有选中的option 元素                                 | $(" #userform :selected" ) 匹配“家乡”中的“北京”选项          |

### 字符串验证

#### 非空验证

```js
if (mail == "") {
     alert("Email不能为空");
     return false;
}
```

#### 字符串查找

indexOf()：查找某个指定的字符串值在字符串中首次出现的位置。

```js
var str="this is JavaScript";
var selectFirst=str.indexOf("Java");
var selectSecond=str.indexOf("Java",12);
```

#### 长度验证

length属性可以获取字符串长度。

```js
if(pwd.length<6){
    alert("密码必须等于或大于6个字符");
    return false;
}
```

#### 判断字符串是否有数字

使用for循环和substring()方法依次截断单个字符，再判断每个字符是否是数字。

```js
for (var i = 0; i < user.length; i++) {
    var j = user.substring(i, i + 1);//截取单个字符
    if (isNaN(j) == false) {
        alert("姓名中不能包含数字");
        return false;
    }
}
```

### 表单验证事件和方法

表单验证需要综合运用元素的事件和方法

| **类别**     | **名称**                                       | **描述**                                 |
| ------------ | ---------------------------------------------- | ---------------------------------------- |
| **事件**     | **onblur**                                     | **失去焦点，当光标离开某个文本框时触发** |
| **onfocus**  | **获得焦点，当光标进入某个文本框时触发**       |                                          |
| **方法**     | **blur()**                                     | **从文本域中移开焦点**                   |
| **focus()**  | **在文本域中设置焦点，即获得鼠标光标**         |                                          |
| **select()** | **选取文本域中的内容，突出显示输入区域的内容** |                                          |

#### 文本输入提示特效

1. 把错误信息显示在<span>中，然后使用html()方法，设置<span>和</span>之间的内容
2. 编写脚本验证函数
3. 鼠标失去焦点时（blur事件）调用验证函数

### 正则表达式

优点：

- 简洁的代码
- 严谨的验证文本框中的内容

#### 定义正则表达式

**普通方式**:var reg=/表达式/附加参数

```js
//Example：
var reg=/white/;
var reg=/white/g;
```

**构造函数**:var reg=new RegExp("表达式","附加参数");

```js
//Example:
var reg=new RegExp("white");
var reg=new RegExp("white","g");
```

**简单模式**:只能表示具体的匹配

```js
//Example:
var reg=/china/;
var reg=/abc8/;
```

**复合模式**:可以使用通配符表达更为抽象的规则模式

```js
var reg=/^\w+$/;
var reg=/^\w+@\w+.[a-zA-Z]{2,3}(.[a-zA-Z]{2,3})?$/;
```

### RegExp对象

regExp对象的方法：

| **方法** | **描述**                                                     |
| -------- | ------------------------------------------------------------ |
| **exec** | **检索字符中是正则表达式的区配，返回找到的值，并确定其位置** |
| **test** | **检索字符串中指定的值，返回****true****或****false**        |

RegExp对象的属性：

| **属性**       | **描述**                            |
| -------------- | ----------------------------------- |
| **global**     | **RegExp****对象是否具有标志****g** |
| **ignoreCase** | **RegExp****对象是否具有标志****i** |
| **multiline**  | **RegExp****对象是否具有标志****m** |

### String对象

| **方法**    | **描述**                           |
| ----------- | ---------------------------------- |
| **match**   | **找到一个或多个正则表达式的匹配** |
| **search**  | **检索与正则表达式相匹配的值**     |
| **replace** | **替换与正则表达式匹配的字符串**   |
| **split**   | **把字符串分割为字符串数组**       |

### 正则表达式符号

| **符号** | **描述**                                                   |
| -------- | ---------------------------------------------------------- |
| **/…/**  | **代表一个模式的开始和结束**                               |
| **^**    | **匹配字符串的开始**                                       |
| **$**    | **匹配字符串的结束**                                       |
| **\s**   | **任何空白字符**                                           |
| **\S**   | **任何非空白字符**                                         |
| **\d**   | **匹配一个数字字符，等价于****[0-9]**                      |
| **\D**   | **除了数字之外的任何字符，等价于****[^0-9]**               |
| **\w**   | **匹配一个数字、下划线或字母字符，等价于****[A-Za-z0-9_]** |
| **\W**   | **任何非单字字符，等价于****[^a-zA-z0-9_]**                |
| **.**    | **除了换行符之外的任意字符**                               |

| **符号**  | **描述**                                                     |
| --------- | ------------------------------------------------------------ |
| **{n}**   | **匹配前一项****n****次**                                    |
| **{n,}**  | **匹配前一项****n****次，或者多次**                          |
| **{n,m}** | **匹配前一项至少****n****次，但是不能超过****m****次**       |
| *****     | **匹配前一项****0****次或多次，等价于****{0,}**              |
| **+**     | **匹配前一项****1****次或多次，等价于****{1,}**              |
| **？**    | **匹配前一项****0****次或****1****次，也就是说前一项是可选的，等价于****{0,1}** |

### html5新增属性

| **属性**        | **描述**                                                     |
| --------------- | ------------------------------------------------------------ |
| **placeholder** | 提供一种提示（hint），输入域为空时显示，获得焦点输入内容后消失 |
| **required**    | 规定输入域不能为空                                           |
| **pattern**     | 规定验证input域的模式（正则表达式）                          |

### validityState对象

| **属性**     | **描述**                                                     |
| ------------ | ------------------------------------------------------------ |
| stepMismatch | 输入的值不符合step特性所推算出的规则。用于填写数值的表单元素可能需要同时设置min、max和step特性，这就限制了输入的值必须是最小值与step特性值的倍数之和。例如范围从0到10，step特性值为2，因为合法值为该范围内的偶数，其他数值均无法通过验证。如果输入值不符合要求，则stepMismatch属性返回true，否则返回false |
| customError  | 使用自定义的验证错误提示信息。使用setCustomValidity( )方法自定义错误提示信息：setCustomValidity(message)会把错误提示信息自定义为message，此时customError属性值为true；setCustomValidity("")会清除自定义的错误信息，此时customError属性值为false。 |

![image-20200929204526082](F:\md笔记文件\assets\表单验证.png)

###### 补充：

**获取select中被选中的option**需要使用:selected

```js
find("option:selected")//获取select标签选中的option
```

**设置option中的属性内容**会自动换成初始的值

```js
$("select").find("option:contains('初始值')").attr("selected",true);
```

**获取复选框的值**是用:checked

```js
//jquery获取复选框值    
var chk_value =[];//定义一个数组    
$('input[name="interest"]:checked').each(function(){//遍历每一个名字为interest的复选框，其中选中的执行函数    
chk_value.push($(this).val());//将选中的值添加到数组chk_value中 });
```



# Bootstrap

Bootstrap 是快速开发 Web 应用程序的前端工具包。它是一个 CSS，HTML 和 JS 的集合，它使用了最新的浏览器技术，给你的 Web 开发提供了时尚的版式，表单，buttons，表格，网格系统等等。

概念：Bootstrap其实就是一个前端开发的框架。

- 框架：一个半成品软件，开发人员可以在框架基础上，再进行开发，简化编码
- 好处：
  1. 定义了很多的css样式和js插件。我们开发人员可以直接使用这些样式和插件得到丰富的页面效果。
  2. 响应式布局。
     - 同一套页面可以兼容不同分辨率的设备。譬如：一套页面在手机端显示效果很好，换成pc端显示也很好。

快速入门：

1. 下载Bootstrap(在Bootstrap中文网可以下载)
2. 在项目中将这个解压的所有文件复制进入文件夹
3. 创建html页面，引入必要的资源文件 

```html
<!DOCTYPE html>
<html lang="zh-CN">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- 上述3个meta标签*必须*放在最前面，任何其他内容都*必须*跟随其后！ -->
    <title>Bootstrap 101 Template</title>

    <!-- Bootstrap -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css" rel="stylesheet">

    <!-- HTML5 shim 和 Respond.js 是为了让 IE8 支持 HTML5 元素和媒体查询（media queries）功能 -->
    <!-- 警告：通过 file:// 协议（就是直接将 html 页面拖拽到浏览器中）访问页面时 Respond.js 不起作用 -->
    <!--[if lt IE 9]>
      <script src="https://cdn.jsdelivr.net/npm/html5shiv@3.7.3/dist/html5shiv.min.js"></script>
      <script src="https://cdn.jsdelivr.net/npm/respond.js@1.4.2/dest/respond.min.js"></script>
    <![endif]-->
  </head>
  <body>
    <h1>你好，世界！</h1>

    <!-- jQuery (Bootstrap 的所有 JavaScript 插件都依赖 jQuery，所以必须放在前边) -->
    <script src="https://cdn.jsdelivr.net/npm/jquery@1.12.4/dist/jquery.min.js"></script>
    <!-- 加载 Bootstrap 的所有 JavaScript 插件。你也可以根据需要只加载单个插件。 -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/js/bootstrap.min.js"></script>
  </body>
</html>
```

**注意**：带min的都是压缩到了一行的，计算机读取起来比较快，提升用户体验。而原本的则方便我们阅读源码。一般导入的链接都是带min的。

## 响应式布局

- 同一套页面可以兼容不同分辨率的设备。

- 实现：依赖于栅格系统：将一行平均分为12个格子，可以指定元素占几个格子。

- 步骤：

  1. 定义容器。把行放到容器里面，相当于之前的table。

     > “行（row）”必须包含在 `.container` （固定宽度）或 `.container-fluid` （100% 宽度）中，以便为其赋予合适的排列（aligment）和内补（padding）。

     - 容器分类;
       1. container:两边有留白
       2. container-fluid:每一种设备都是100%宽度

  2. 定义行。相当于tr。行的样式用：row

     > 通过“行（row）”在水平方向创建一组“列（column）”。

  3. 定义元素。指定该元素在不同的设备上，所占的格子数目.样式：col-设备代号-格子数目。

     > 你的内容应当放置于“列（column）”内，并且，只有“列（column）”可以作为行（row）”的直接子元素。

     1. xs:超小屏幕 手机 (<768px):col-xs-12
     2. sm:小屏幕 平板 (>=768px)
     3. md:中等屏幕 桌面显示器(>=992px)
     4. lg:大屏幕 大桌面显示器(>=1200px)

* 注意：
		1. 一行中如果格子数目超过12，则超出部分自动换行。
		2. 栅格类属性可以向上兼容。栅格类适用于与屏幕宽度大于或等于分界点大小的设备。
		3. 如果真实设备宽度小于了设置栅格类属性的设备代码的最小值，会一个元素沾满一整行。

1. 全局CSS样式：
	* 按钮：class="btn btn-default"
	* 图片：
		*  class="img-responsive"：图片在任意尺寸都占100%
		*  图片形状
			*  <img src="..." alt="..." class="img-rounded">：方形
			*  <img src="..." alt="..." class="img-circle"> ： 圆形
			*  <img src="..." alt="..." class="img-thumbnail"> ：相框
	* 表格
		* table
		* table-bordered
		* table-hover
	* 表单
		* 给表单项添加：class="form-control" 
2. 组件：
	* 导航条
	* 分页条
3. 插件：
	* 轮播图

通过为“列（column）”设置 `padding` 属性，从而创建列与列之间的间隔（gutter）。通过为 `.row` 元素设置负值 `margin` 从而抵消掉为 `.container` 元素设置的 `padding`，也就间接为“行（row）”所包含的“列（column）”抵消掉了`padding`。

| 超小屏幕 手机 (<768px) | 小屏幕 平板 (≥768px)       | 中等屏幕 桌面显示器 (≥992px)                        | 大屏幕 大桌面显示器 (≥1200px) |            |
| :--------------------- | :------------------------- | :-------------------------------------------------- | :---------------------------- | ---------- |
| 栅格系统行为           | 总是水平排列               | 开始是堆叠在一起的，当大于这些阈值时将变为水平排列C |                               |            |
| `.container` 最大宽度  | None （自动）              | 750px                                               | 970px                         | 1170px     |
| 类前缀                 | `.col-xs-`                 | `.col-sm-`                                          | `.col-md-`                    | `.col-lg-` |
| 列（column）数         | 12                         |                                                     |                               |            |
| 最大列（column）宽     | 自动                       | ~62px                                               | ~81px                         | ~97px      |
| 槽（gutter）宽         | 30px （每列左右均有 15px） |                                                     |                               |            |
| 可嵌套                 | 是                         |                                                     |                               |            |
| 偏移（Offsets）        | 是                         |                                                     |                               |            |
| 列排序                 | 是                         |                                                     |                               |            |

# XML

- 概念：Extensible Markup Language 可扩展标记语言

  可扩展：标签都是自定义的。

- 功能

  - 存储数据
    1. 配置文件
    2. 在网络中传输

- xml与html的区别

  1. xml标签都是自定义的，HTML标签都是预定义的。
  2. xml的语法严格，html语法松散。
  3. xml是存储数据的，html是展示数据。

  w3c：万维网联盟

  xml用来和配置文件做对比

  ```xml
  //Example:
  存储name：张三  age：20 sex =男
  <?xml version='1.0'?><!--文档声明-->
  	<user id = "...">
  		<name>张三</name>
  		<age>20</age>
  		<sex>male</sex>
  	</user>
  ```

- 语法：

  - 基本语法：

    1. xml文档的后缀名.xml
    2. xml第一行必须定义为文档声明
    3. xml文档中有且仅有一个根标签
    4. 属性值必须使用引号(单双都可)引起来
    5. 标签必须正确关闭
    6. xml标签名称区分大小写

  - 快速入门：

    ```xml
    <?xml version='1.0'? encoding = 'gbk'><!--文档声明-->
    <users>
    	<user id = "1">
    		<name>张三</name>
    		<age>20</age>
    		<sex>male</sex>
    	</user>
    	<user id = "2">
    		<name>张三</name>
    		<age>20</age>
    		<sex>male</sex>
    	</user>
    </users>
    ```

    

  - 组成部分：

    1. 文档声明

       1. 格式：<?xml 属性列表?>

       2. 属性列表：

          version：版本号，必须的属性

          encoding：编码格式。告知解析引擎当前文档使用的字符串，默认值：ISO-8859-1

          standalone：是否独立 属性值：yes/no
          yes:不依赖其他文件
          no:依赖其他文件

    2. 指令(随便了解)：结合css的
       <?xml-style type="text/css" href =“demo.css" ?>

    3. 标签：标签名称自定义的

       1. 命名规则
          1. 名称可以含字母、数字以及其他的字符
          2. 名称不能以数字或者标点符号开始
          3. 名称不能以字符 “xml”（或者 XML、Xml）开始
          4. 名称不能包含空格

    4. 属性

       id属性值唯一

    5. 文本

       - CDATA区：在该区域中数据会被原样展示

         格式：

         ```xml
         <![CDATA[数据]]>
         ```

- 约束：规定xml文档的书写规则

  - 作为框架的使用者(程序员)
    1. 能够在xml中引入约束文档
    2. 能够简单的读懂约束文档

![image-20200927144032748](F:\md笔记文件\assets\xml文档约束.png)

- 分类：

  1. DID：一种简单的约束技术
  2. Schema：一种复杂的约束技术

- DTD：

  - 引入dtd文档到xml文档中

    - 内部dtd：将约束规则定义在xml文档中

    - 外部dtd：将约束的规则定义在外部的dtd文件中

      - 本地：

        ```xml-dtd
        <!DOCTYPE 根标签名 SYSTEM "dtd文件的位置">
        ```

      - 网络：

        ```xml-dtd
        <!DOCTYPE 根标签名 PUBLIC "dtd文件名字" "dtd文件的位置URL">
        ```

```xml-dtd
<!--Example -->
<!ELEMENT students (student+) >
<!ELEMENT student (name,age,sex)>
<!ELEMENT name (#PCDATA)>
<!ELEMENT age (#PCDATA)>
<!ELEMENT sex (#PCDATA)>
<!ATTLIST student number ID #REQUIRED>
```

dtd的一个缺陷：不能限制xml标签中的内容

- Schema
  - 文件后缀名为：.xsd
  - 引入：
    1.填写xml文档的根元素
    2.引入xsi前缀.  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    3.引入xsd文件命名空间.  xsi:schemaLocation="http://www.itcast.cn/xml  student.xsd"
    4.为每一个xsd约束声明一个前缀,作为标识  xmlns="http://www.itcast.cn/xml" 

```xml
<!--Xml Example:-->
<students   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xmlns="http://www.itcast.cn/xml"
xsi:schemaLocation="http://www.itcast.cn/xml  student.xsd">
```

```xml
<!--Example-->
<?xml version="1.0"?>
<xsd:schema xmlns="http://www.itcast.cn/xml"
        xmlns:xsd="http://www.w3.org/2001/XMLSchema"
        targetNamespace="http://www.itcast.cn/xml" elementFormDefault="qualified">
    <xsd:element name="students" type="studentsType"/>
    <xsd:complexType name="studentsType">
        <xsd:sequence>
            <xsd:element name="student" type="studentType" minOccurs="0" maxOccurs="unbounded"/>
        </xsd:sequence>
    </xsd:complexType>
    <xsd:complexType name="studentType">
        <xsd:sequence>
            <xsd:element name="name" type="xsd:string"/>
            <xsd:element name="age" type="ageType" />
            <xsd:element name="sex" type="sexType" />
        </xsd:sequence>
        <xsd:attribute name="number" type="numberType" use="required"/>
    </xsd:complexType>
    <xsd:simpleType name="sexType">
        <xsd:restriction base="xsd:string">
            <xsd:enumeration value="male"/>
            <xsd:enumeration value="female"/>
        </xsd:restriction>
    </xsd:simpleType>
    <xsd:simpleType name="ageType">
        <xsd:restriction base="xsd:integer">
            <xsd:minInclusive value="0"/>
            <xsd:maxInclusive value="256"/>
        </xsd:restriction>
    </xsd:simpleType>
    <xsd:simpleType name="numberType">
        <xsd:restriction base="xsd:string">
            <xsd:pattern value="heima_\d{4}"/>
        </xsd:restriction>
    </xsd:simpleType>
</xsd:schema> 
```

## 解析xml

解析：操作xml文档，将文档中的数据读取到内存中

 * 操作xml文档
     1. 解析(读取)：将文档中的数据读取到内存中
     	
     	2. 写入：将内存中的数据保存到xml文档中。持久化的存储
     	
     2. 解析xml的方式：

        1. DOM：将标记语言文档一次性加载进内存，在内存中形成一颗dom树
        	* 优点：操作方便，可以对文档进行CRUD的所有操作
        	* 缺点：占内存
        2. SAX：逐行读取，基于事件驱动的。
        	* 优点：不占内存。
        	* 缺点：只能读取，不能增删改

     3. xml常见的解析器：
             		1. JAXP：sun公司提供的解析器，支持dom和sax两种思想
                           		2. DOM4J：一款非常优秀的解析器
                       		3. Jsoup：jsoup 是一款Java 的HTML解析器，可直接解析某个URL地址、HTML文本内容。它提供了一套非常省力的API，可通过DOM，CSS以及类似于jQuery的操作方法来取出和操作数据。
                                 		4. PULL：Android操作系统内置的解析器，sax方式的。

     4. Jsoup：jsoup 是一款Java 的HTML解析器，可直接解析某个URL地址、HTML文本内容。它提供了一套非常省力的API，可通过DOM，CSS以及类似于jQuery的操作方法来取出和操作数据。
          * 快速入门：
              * 步骤：
                     		1. 导入jar包
                                   		2. 获取Document对象
                               		3. 获取对应的标签Element对象
                                         		4. 获取数据

     5. ```java
        //Example:
        //2.1获取student.xml的path
        	        String path = JsoupDemo1.class.getClassLoader().getResource("student.xml").getPath();
        	        //2.2解析xml文档，加载文档进内存，获取dom树--->Document
        	        Document document = Jsoup.parse(new File(path), "utf-8");
        	        //3.获取元素对象 Element
        	        Elements elements = document.getElementsByTag("name");
        System.out.println(elements.size());
        	        //3.1获取第一个name的Element对象
        	        Element element = elements.get(0);
        	        //3.2获取数据
        	        String name = element.text();
        	        System.out.println(name);
        ```

## 对象的使用：

  1. Jsoup：工具类，可以解析html或xml文档，返回Document
       * parse：解析html或xml文档，返回Document
       * parse(File in, String charsetName)：解析xml或html文件的。
       * parse(String html)：解析xml或html字符串
       * parse(URL url, int timeoutMillis)：通过网络路径获取指定的html或xml的文档对象
2. Document：文档对象。代表内存中的dom树
   * 获取Element对象
     * getElementById(String id)：根据id属性值获取唯一的element对象
     * getElementsByTag(String tagName)：根据标签名称获取元素对象集合
     * getElementsByAttribute(String key)：根据属性名称获取元素对象集合
     * getElementsByAttributeValue(String key, String value)：根据对应的属性名和属性值获取元素对象集合
3. Elements：元素Element对象的集合。可以当做 ArrayList<Element>来使用
4. Element：元素对象
   1. 获取子元素对象
      * getElementById(String id)：根据id属性值获取唯一的element对象
      * getElementsByTag(String tagName)：根据标签名称获取元素对象集合
      * getElementsByAttribute(String key)：根据属性名称获取元素对象集合
      * getElementsByAttributeValue(String key, String value)：根据对应的属性名和属性值获取元素对象集合
   2. 获取属性值
      * String attr(String key)：根据属性名称获取属性值
   3. 获取文本内容
      * String text():获取文本内容
      * String html():获取标签体的所有内容(包括字标签的字符串内容)
5. Node：节点对象
   * 是Document和Element的父类

1. 快捷查询方式：
     		1. selector:选择器
            * 使用的方法：Elements	select(String cssQuery)
            * 语法：参考Selector类中定义的语法

```java
//1.获取student.xml的path
		        String path = JsoupDemo6.class.getClassLoader().getResource("student.xml").getPath();
		        //2.获取Document对象
		        Document document = Jsoup.parse(new File(path), "utf-8");
		
		        //3.根据document对象，创建JXDocument对象
		        JXDocument jxDocument = new JXDocument(document);
		
		        //4.结合xpath语法查询
		        //4.1查询所有student标签
		        List<JXNode> jxNodes = jxDocument.selN("//student");
		        for (JXNode jxNode : jxNodes) {
		            System.out.println(jxNode);
		        }
		
		        System.out.println("--------------------");
		
		        //4.2查询所有student标签下的name标签
		        List<JXNode> jxNodes2 = jxDocument.selN("//student/name");
		        for (JXNode jxNode : jxNodes2) {
		            System.out.println(jxNode);
		        }
		
		        System.out.println("--------------------");
		
		        //4.3查询student标签下带有id属性的name标签
		        List<JXNode> jxNodes3 = jxDocument.selN("//student/name[@id]");
		        for (JXNode jxNode : jxNodes3) {
		            System.out.println(jxNode);
		        }
		        System.out.println("--------------------");
		        //4.4查询student标签下带有id属性的name标签 并且id属性值为itcast
		
		        List<JXNode> jxNodes4 = jxDocument.selN("//student/name[@id='itcast']");
		        for (JXNode jxNode : jxNodes4) {
		            System.out.println(jxNode);
		        }
```


