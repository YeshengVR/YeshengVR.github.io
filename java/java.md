# JAVA笔记

## 6.22

### java的运行规则

先获取java文件再通过编译器转为class文件，通过类加载器将文件加载到jvm虚拟机中，再通过虚拟机满足底层操作系统的支持。来实现Java文件在各个系统的运行。![](F:\md笔记文件\javaimg\java运行机制.jpg)

###### 补充：

- ###### **JVM垃圾回收机制**

垃圾回收器（GC）是JVM自带的一个线程，用于回收没有任何引用指向的对象。

java程序员不用担心内存管理，因为垃圾收集器会自动进行回收管理。

```java
Cell c = new Cell();
c = null;
//不在指向刚分配的对象空间，成员变量失效
```



- **Java程序的内存泄露问题**

内存泄漏是指，不再使用的内存没有被及时的回收，严重的内存泄漏会因过多的内存占用而导致程序的崩溃。

GC线程判断对象是否可以回收的依据是该对象是否有引用指向，因此，当确定该对象不再使用时，应该及时将其引用设置为null。

- **System.gc()方法**

GC的回收对程序员来说是透明的，并不一定一发现有无引用的对象，就立刻回收。

一般情况下，当我们需要GC线程即可回收无用对象时，可以调用System.gc()方法。

System.gc()用于建议虚拟机马上调度GC线程回收资源，具体的实现策略取决于不同的JVM系统

## 6.23

### 数据类型

byte：字节类型（计算机中的内存单位）1个字节-128~127 -2^7~2^7

short：短整型	2个字节	-32768~32767	-2^15~2^15

int：integer整数	4个字节	-21亿~21亿 	-2^31~2^31（整数默认是int类型）

long： 长整型	8个字节	很大	-2^63~2^63（末尾加L）

float：单精度浮点类型	4个字节，小数点后八位有效位（后面几位可能丢失精度）（末尾加F）

double：双精度浮点类型	8个字节，小数点后十六位有效位（小数默认是double类型）

char：charactor 字符	2个字节 	0~65536

boolean： 布尔	1个字节 	true|false

计算机中最小的存储数据的单位 byte（字节）----8位二进制

byte<short<int<long<float<double

char<int<long<float<doublue

类型自动向上转换，小范围类型变量赋值给大范围类型变量

类型强制向下转换，大范围类型变量赋值给小范围类型变量(小数强转整数，取整数部分。)

```java
int x =10;
byte y =(byte)x;
System.out.println(y);
```

## 6.24

### 算术运算符

```java
//算术运算符：+-*/% ++ --
```

```java
int a=13;
int b=5;
int c=a+b;
c = a-b;
c = a*b;
c = a/b;//int类型中，两个整数相除，结果取整，不进行四舍五入
```

![](F:\md笔记文件\javaimg\算术运算符.jpg)

不同类型的数据参与运算，低类型的的数据会向上转型。

++（--）在前面先自增（自减）再运算；++（--）在后面，先运算再自增（自减）

### 赋值运算符

```java
//int a = 3;赋值运算符 = += -= *= 
```

![](F:\md笔记文件\javaimg\赋值运算符.jpg)

### 比较运算符

< ,>, ==,<=,>=

### 逻辑运算符

逻辑运算符：&and 并且；|or 或者；!not 非。

逻辑运算符，两边都是布尔值。![](F:\md笔记文件\javaimg\逻辑运算符.jpg)

&：两边都为true，则为true  （&第一个条件即为false时，两边条件都会运行；&&第一个条件即为false时，后面条件忽略，不运行。）

|：两边只要有一边为true，则为true（|第一个条件即为true时，两边条件都还会运行；||第一个条件即为true时，后面条件忽略，不运行。）

^:两边相同则为false，否则为true

!:结果取反



### 位运算符

```java
//位运算符：&(与) |(或) ^(异或) ~(取反) <<(无符号左移) >>(无符号右移) >>>(带符号右移)
```



负数在内存上是需要先反码再补码显示的。

正数在内存上不需要进行反码补码操作，可以直接二进制显示的。（正数取反得出负数需要进行-1再反码的操作，显示出来。）



优先级：算术运算符，比较运算符，逻辑运算符，赋值运算符

## 6.28

### 选择分支结构

if(){}else{}



```java
//双分支结构
		if(a>0){
			System.out.println("出去玩");
		}else{
			System.out.println("吃香蕉");
		}
```

```java
//多选择分支结构
if(age<18){
			System.out.println("好好学习！");
		}else if(age<30){
			System.out.println("好好工作！")

		}else if(age<60){
			System.out.println("好好享福");

		}else{
			System.out.println("好好养老")；
		}
```

while(){}循环结构（先判断在执行）

```java
while(i<10){
	System.out.println("haohaoxuexi!");
    i++;
}
```

do{}while();循环结构（先执行在判断）

```java
do{
			System.out.println(n);
			n++;
		}while(n<=10);
```

for(){}循环结构（先判断在执行）

```java
for(int i=1;n<=10;n++){
			System.out.printlnl("i");
		}
```

for each循环：for each循环从1开始而不是从0开始

```
    for (变量类型 新变量名:数组名)  
        System.out.println(新变量名);

```

```java
int[] a = {1, 3, 8};
for (int element: a)
	System.out.println(element);
//打印输出a的每一个元素(优势)这个循环应该被读作“循环a中的每一个元素”(for each element in a)。当然，传统的for循环也可以获得的同样的效果，但是需要花费精力去关心下标的起始值和终止值。
```



### Scanner扫描器

## 6.30

### 数组

数组不能删除元素也不能添加元素，开始是多少元素就一直是多少元素。

```java
public class Array01{

	public static void main(String[] args){
		//数组的声明
		int[] arr0 ={0,3,6,12,24};//声明一个长度为五,直接赋值好的数组。
		int[] arr1 = new int[5];//开辟5个int类型的数组空间,默认值为0
		String[] arr2 = new String[3];//null是引用数据类型的值
		int[] arr3 = new int[]{1,20,30};
		//二维数组
		int[][] arr4 ={{1},{2,3},{4,5,6}};
		int a= arr4[1][0];
		System.out.println("a="+a);
	}
}
```

int类型数组 未声明数组元素的值，则默认值为0

double类型	默认值为0.0

char类型	默认值为0所对应的字符（也就是空格）

String类型	默认值为null（null是引用数据类型的值）

数组的初始化包括**申明，创建，初始化**

```java
int[][] a = new int[10][]
//第一个中括号时数组的长度，第二个是元素的长度
```

​	

### 冒泡排序

冒泡排序，依次获取数组中的每一个元素，和他相邻的元素比较，交换位置进行排序。

```java
public class classtest5{

	public static void main(String[] args){
		int[] arr={5,6,10,33,99,61,86,22};
		//冒泡排序
		for(int i=0;i<=arr.length-1;i++){
            //设置判断标记
			boolean flag=true;
            //交换元素位置
			for(int j=0;j<arr.length-1;j++){
				if(arr[j]<arr[j+1]){
					arr[j]=arr[j+1]+arr[j];
					arr[j+1]=arr[j]-arr[j+1];
					arr[j]=arr[j]-arr[j+1];
					//执行循环则代表位置不同进行了比较
					flag = false;
				}
			}
			if(flag){
				break;
			}
		}
		System.out.println("比较后的数据显示结果为");
		for(int k=0;k<arr.length;k++){
			System.out.print(arr[k]+">");
		}
		System.out.println("");
	}
}
```

选择排序：依次获取数组中的每个元素，和她后面的所有元素比较，小的调换位置。

```java
//选择排序
public class choosetest {

	public static void main(String[] args) {
		int[] array = {5,6,10,33,99,61,86,22};
		for (int i = 1; i < array.length; i++) {
			int index = 0;
			//第一个元素和第零个元素进行比较进行依次比较，找出最大的元素
			for (int j = 1; j <= array.length - i; j++) {
				if (array[j] > array[index]) {
					index = j;
				}
			}
			//将找出的最大的值和最后一个数字置换位置
           			int temp = array[array.length - i];
            			array[array.length - i] = array[index];
            			array[index] = temp;

		}
		//循环a中的每一个元素,然后打印值
		for (int i : array) {
			System.out.print(i + " ");
		}
	}
}
```

## 7.1

package命名方式一般以com.项目名.模块名

### eclipse快捷键

eclipse    Alt+/   快捷键/提示键			ctrl+/	注释快捷键

“syso” +alt+/   输出语句快捷键



**1、打开资源的快捷键**

CTRL + SHIFT + R打开所有类型文件，不包括 JAR 包

CTRL + SHIFT + T打开 Java 类型文件，包括 JAR 包

**2、查找资源的快捷键**

CTRL + F查找当前编辑器内容

CTRL + H查找所有文件内容

CTRL + SHIFT + G快速查找所有引用的地方

**3、代码整理的快捷键**

CTRL + SHIFT + F格式化代码

CTRL + SHIFT + O去除没有用到的引用

CTRL + SHIFT + M导入需要的类引用

**4、重命名的快捷键**

ALT + SHIFT + R重命名

CTRL + SHIFT + X转换大写

CTRL + SHIFT + Y转换小写

**5、切换编辑器的快捷键**

CTRL + E显示所有打开的编辑器列表

CTRL + SHIFT + E显示更详细的所有打开的编辑器列表

ALT + 左右方向键回到上一次/下一次编辑所在的代码

**6、快速处理行的快捷键**

CTRL + D删除当前行

CTRL + SHIFT + 上下方向键向上/下复制当前行

ALT + 上下方向键向上/下替换行

**7、类继承关系的快捷键**

CTRL + T显示当前类继承关系列表

F4打开当前类继承关系对话框

CTRL + SHIFT + H打开指定的类继承关系对话框

**8、快速修复的快捷键**

CTRL + 1快速修复问题

**9、重构的快捷键**

ALT + SHIFT + L提取出局部变量

ALT + SHIFT + M提取出方法

ALT + SHIFT + C修改当前方法构造

**10、添加注释的快捷键**

CTRL + /用行注释注释当前行或者选择的行

CTRL + SHIFT + C和上面一样

CTRL + SHIFT + /用块注释注释选择的行

### 类是大量对象共性的抽象

类是客观事物在人脑中的主观反映

类是创建对象的模板

类是对象的描述，对象是该类的实例

类体由两部分构成

1成员变量；2成员方法

方法构建方式：

语法：修饰符	返回值类型	方法名（[形参1],[形参2]....）{//方法体}

方法的调用：

[返回值类型 变量名 = ]对象名.方法名([实参1],[实参2]...)

```java
public void eat(){
	System.out.println("");
}
```

有返回值的方法需要用变量来接取他的返回值

```java
public int add(int a,int b){
		return a+b;
	}
	public double add(double a,double b){
		return a+b;
	}
```

方法的重载，两个方法名相同，参数不同。

方法的重载是：两个相同的方法名，不同的参数。

声明一个新的对象是开辟一个新的空间

#### this

在方法中如果要访问属性需要用this.***如果没有用this.则会调用局部变量

在方法内部可以通过this关键字调用其他方法

调用当前方法的引用

### 构造方法

构造对象的方法

构造方法不需要写返回值类型（其他方法都需要写返回值类型）

构造方法的名字和类名一致

构造方法的作用1是用来创建对象作用2是给属性初始化

通过new运算符，调用构造方法

如果没有显示的写一个构造方法，则系统会给一个默认的无参构造方法。

```java
public class method {

	public method(){
		
	}//构造方法
}
```

注意：在构造方法里面，this指当前创建的对象。

在一个构造方法中调用其他构造方法，只能在第一行。只能一次

```java
	public method(String name){
		this(20);//在构造方法中第一行调用其他构造方法。
		this.name=name;
	}
	public method(int age){
		this.age=age;
	}
}
```

形参传递中，基本数据类型传递是值传递。![](F:\md笔记文件\javaimg\带参构造方法应用类型的两种写法.png)

引用数据类型传参是引用传递

引用存储的是对象内存空间的首地址

（指针------引用-----地址）

![](F:\md笔记文件\javaimg\方法区，堆栈.jpg)

有参构造方法给你所有的属性初始化，（在设置一大批同样的对象时使用非常方便）

###### 补充

构造器最大bai的用处就是在创建对象时执行初始化，du当创建一个对象时，系zhi统会为这个对象dao的实例进行默认的初始化。如果想改变这种默认的初始化，就可以通过自定义构造器来实现。

## 7.6

### static修饰符

**static修饰的变量的方法，子类不会继承。**因为静态方法从程序开始运行后就已经分配了内存，也就是说已经写死了。所有引用到该方法的对象（父类的对象也好子类的对象也好）所指向的都是同一块内存中的数据，也就是该静态方法。子类中如果定义了相同名称的静态方法，并不会重写，而应该是在内存中又分配了一块给子类的静态方法，没有重写这一说，我们应该称之为隐藏。

static修饰符可以放在public修饰符前面也可以放在后面，一般放在public修饰符后面

static修饰符是静态修饰符

被static修饰的属性，则变成了共享属性，也叫类成员属性[静态属性]。[类一旦被加载进虚拟机中，类成员就已经存在，此时可能还没有创建对象。]

普通成员依赖于对象存在，类成员依赖于类而存在。（类成员可以在未创建对象时就直接用类名调用）

静态方法

被static修饰的方法不能使用this关键字（因为静态方法依赖于类存在，而this关键字的作用是当前对象的某一属性，所以逻辑上通不过。）被static修饰是共享方法，也叫类方法，静态方法。

static不能用来修饰构造方法，这样没有意义，还会报错。

在静态方法中不能访问实例成员，可以访问类成员。通过以下两种形式来访问。

```
类名.类成员
类名.类方法
```

在实例方法（构造出了对象之后的方法）中，可以访问所有成员[实例成员和类成员]。

 static一个很重要的用途就是实现单例设计模式 

#### 静态导包

用import static 代替import静态导入包

import static com…..ClassName. * ;这里的多了个static，还有就是类名ClassName后面多了个.* ，意思是导入这个类里的静态方法。当然，也可以只导入某个静态方法，只要把 .* 换成静态方法名就行了。然后在这个类中，就可以直接用方法名调用静态方法，
| **static修饰的成员变量和方法，从属于类**   |
| ------------------------------------------ |
| **普通变量和方法从属于对象**               |
| **静态方法不能调用非静态成员，编译会报错** |
| **static不允许用于修饰局部变量**           |



###### 补充

```java
//静态代码块
static{
    //被类加载进虚拟机中就立刻执行，只会执行一次（一般用来初始化资源）
	System.out.println("静态代码块");
}
//动态代码块
{
    //每创建一个对象则执行一次
    System.out.println("动态代码块");
}

```

创建对象时，动态代码块比构造方法先执行。（因为动态代码块一般是用来初始化资源）动态代码块并非一直最先执行，会先执行动态代码块之前的代码。 

static块可以置于类中的任何地方，类中可以有多个static块。在类初次被加载的时候，会按照static块的顺序来执行每个static块，并且只会执行一次。 

```java
public class Test extends Base{

    static{
        System.out.println("test static");
    }

    public Test(){
        System.out.println("test constructor");
    }

    public static void main(String[] args) {
        new Test();
    }
}

class Base{

    static{
        System.out.println("base static");
    }

    public Base(){
        System.out.println("base constructor");
    }
}
```

```java
//输出结果
base static
test static
base constructor
test constructor
```



### final修饰符

final修饰符可以放在public修饰符前面也可以放在后面，一般放在public修饰符后面。

final：最终的

被final修饰的属性，一定要初始化。

注意：如果某一个属性被final修饰了，建议也被static修饰

被final修饰的属性变成常量。

*常量的名字推荐全部大写*

final修饰类，这个类就不能被继承

final修饰方法，子类继承方法就不可被重写。





### 封装

public：公开的，公共的。（权限修饰符）

被public修饰的成员是公开的，在任何地方都可以访问

private：私有，私密

封装就是对属性的私有化

把客观事物封装成抽象的类，并且类可以把自己的属性和方法只让可信的类或者对象访问。

一般会给私有属性提供get和set方法用以访问私有属性，方法可以对数据进行处理，而直接访问数据不会进行数据处理。

 **私有构造类，阻止实例的生成** 

***单例模式***

```java
public class Student {

//	private static Student stu;
	private static Student stu2 = new Student();//饿汉模式
	private Student(){
		
	}
	public static Student newStudent(){
		//懒汉模式
		/*if(stu == null){
			stu = new Student();
		}*/
//		return stu;
		return stu2;
	}
}

```



## 7.7

###### 补充

return语句是一个方法的最后一步。

return 可以直接

```java
return this;//返回这个对象
```



### 继承

**extends**关键字：继承，扩展

```java
子类 extends 父类
```

一个新的类可以由现有的类派生，这样的一个过程就叫继承。

子类[subclass]父类[superclass]

子类一旦继承父类，则会继承父类所有非私有成员。（实际上子类也会继承父类的私有成员，只是无法直接访问。通过get，set方法间接继承父类私有成员）

子类是父类的扩展

构造方法无法被继承

Java中的继承时单继承，也就是一个类只能有一个父类（以防止两个父类方法一样，造成调用时产生二异性）。

如果一个类没有显示的继承某一个类，那么它就有一个默认的父类时java.lang.Object类（所以object类也称之为根类）

### 权限修饰符

![](F:\md笔记文件\javaimg\修饰符.png)

```java
import com.zet.demo.Person
    //com.zet.demo.Person称作完全类名
```

public：任何地方都可以访问，所有子类都可以继承

private：只能在本类内部访问，子类无法直接继承

(default)：默认的  没写修饰符的时候，只能在本类和同包的其他类中访问

protected：只能在本类和同包的其它类中访问，所有子类都可以继承

类只能被public和默认的方式修饰类，一般全都是用public

private 一般修饰属性，public一般修饰方法。

### 方法重写

子类从父类继承的某个实例方法无法满足子类的功能需求时，需要在子类中对该实例方法进行更改，重新实现，这样的过程叫重写，也叫覆写。

方法的重写前提是子类继承父类的方法。

方法重写：子类重写父类的方法。

```java
//方法的注解
@Override  //重写父类的方法
```

子类重写方法的访问修饰范围必须大于或者等于父类的修饰范围

方法的返回值类型要一样

> 一般在重写的方法上要写一句@Override，以方便观察阅读



### super

super代表的是父类对象

super使用方式：

与this关键字的使用方法相似

1.super.属性名 用于在子类中调用父类同名实例变量

2.super([参数列表])用于在子类的构造方法中调用父类的构造方法

![](F:\md笔记文件\javaimg\superthis.png)

this.指的是当前对象的引用。

super指的是当前调用该方法对象的父类对象

super和this只能在方法里使用。只要能使用this就能使用super。

super不能直接访问private的方法，因为方法封装，不可见。

构造方法中，默认第一行是super();必定调用父类构造方法初始化。

## 7.8

### 多态



| 多态，即为多种形态 |
| ------------------ |
| 子类赋值给父类引用 |
| 子类重写父类的方法 |

```java
父类 对象名 = new 子类
```

多态的含义：允许不同类的对象对同一消息做出响应。即同一消息可以根据发送对象的不同而采用多种不同的行为方式。（发送消息就是函数调用）

多态前提：继承，向上转型，方法重写（有意义的多态需要重写方法）

```java
实现多态的技术称为：动态绑定（dynamic binding），是指在执行期间判断所引用对象的实际类型，根据其实际的类型调用其相应的方法。
```

多态的作用：

提高代码的可重用性

降低模块之间的耦合度



### 抽象

抽象方法：

```java
修饰符 abstract 返回值类型 方法名(参数列表);
```

因为抽象方法无法确定具体执行的功能，所有抽象方法没有方法体，需要在小括号后面直接加上分号。方法只声明没有方法体。

如果一个类有抽象方法，则该类也一定是抽象类。

没有方法体的方法称之为抽象方法

抽象方法要abstract关键字修饰，抽象类也需要用abstract修饰。

抽象类不可以创建对象，但是可以作为引用。（类似于多态）抽象类有构造方法。

如果一个类是抽象类，不一定有抽象方法

```java
//抽象方法
public abstract 返回值类型 方法名();
```



```java
//子类的创建
抽象类 对象名 = new 抽象类的子类();
```

子类继承了父类的抽象方法，想要让子类不是抽象类，就将继承的父类的抽象方法重写成实例方法。

如果一个类全是抽象方法，就是接口。

## 7.9

### 接口

一个类全是抽象方法，则称为接口。接口是极端的抽象类

interface关键字 接口的关键字。

```java
public interface 类名
```

接口里面只能有抽象方法，抽象方法里的abstract关键字可以省略。

接口只能用public 修饰，不写public时，默认权限修饰符为public。

接口里面只能有静态常量。没有变量，所以创建成员属性时必须赋值。

接口没有构造器，因为他失去了构造方法中的两种作用，初始化和创建对象。

**implements**实现接口方法

子类继承普通类或者抽象类，使用extends，但如果是实现（继承）接口，则使用implements。

实现接口的子类需要重写接口里面的抽象方法。

继承是单继承，接口可以多实现。（因为接口都没有方法体，所以同名方法无所谓，都没有方法体。）

子类可以继承一个父类的同时，实现多个接口。

接口和接口之间可以多继承。

接口在高版本中有新特性：

> 可以通过default 来写默认权限的普通方法
>
> 也可以通过static来写静态的普通方法



接口不要写普通方法，就全都写抽象方法。

### 包

包时Java用于提供访问保护和命名空间管理的方式

包是用来将java中类和接口等进行分类管理的工具

类导入的语法

import 包名.类名；//导类

import 包名.*；//导入包里的类

如果需要用到其他包的类，一定要用到导包

### instanceof运算符

instanceof用来判断某个对象是不是某个类的实例

```java
对象名 instanceof 类名
```

```java
if(animal instanceof Dog){
	Dog d = (Dog)animal;//强制向下转型
    d.dogeat();//调用dog类的普通方法
}else if(animal instanceof Cat){
	Cat c = (Cat)animal;//强制向下转型
    c.cateat();//调用cat类的普通方法
}
```

向下转型 强制转型方法和普通基本类型转型语法是一样的。

## 7.10

### 代理模式

代理（Proxy）是一种设计模式，提供了间接对目标对象进行访问的方式，即通过代理对象访问目标对象。这样可以在目标对象实现的功能上增加额外的功能补充，及扩展目标对象的功能。

好处：可以不改动原有代码，进行功能扩充。

#### **静态代理模式**

```java
// 接口
    interface IStar {
        void sing();
    }

    // 真实对象
    class LDHStar implements IStar {
        @Override
        public void sing() {
            System.out.println("刘德华唱歌");
        }

    }

    // 代理类需要有真实对象的控制权 (引用)
    class ProxyManger implements IStar {
        
        // 真实对象的引用
        private IStar star;
        
        public ProxyManger() {
            super();
        }

        public ProxyManger(IStar star) {
            super();
            this.star = star;
        }
        
        @Override
        public void sing() {　　　　　　System.out.println("唱歌前准备");    　　　 star.sing();   　　　　System.out.println("善后工作");        }
    }
class Test{
public static void main(String[] args) {
            // 创建明星对象
            IStar ldh = new LDHStar();
            ProxyManger proxy = new ProxyManger(ldh);
            proxy.sing();
        }
}
```

代理类需要有真实对象的控制权，所以在代理类里需要创建一个被代理的对象获取对象控制权。

静态代理总结:
***优点：***

可以做到在不修改目标对象的功能前提下,对目标功能扩展.
***缺点:***

因为代理对象需要与目标对象实现一样的接口,所以会有很多代理类,类太多.同时,一旦接口增加方法,目标对象与代理对象都要维护.

#### **动态代理**

动态代理的主要特点就是能够在程序运行时JVM才为被代理对象生成代理对象。

动态代理也叫做JDK代理也是一种接口代理，JDK中生成代理对象的代理类就是Proxy，所在包为java.lang.reflect

动态代理，代理对象不需要实现接口，被代理对象一定要实现接口，否则不能用动态代理。

代理对象的生成，是利用JDK的API，动态的内存中构建代理对象（需要我们指定创建代理对象/目标对象实现的接口的类型）

动态代理也叫做：JDK代理，接口代理。

static Object newProxyInstance(ClassLoader loader, 
      Class[] interfaces,InvocationHandler h )

 

注意该方法是在Proxy类中是静态方法,且接收的三个参数依次为:

1. ClassLoader loader,:指定当前目标对象使用类加载器,获取加载器的方法是固定的
2. Class[] interfaces,:目标对象实现的接口的类型,使用泛型方式确认类型
3. InvocationHandler h:事件处理,执行目标对象的方法时,会触发事件处理器的方法,会把当前执行目标对象的方法作为参数传入

#### **Cglib代理模式**

1.需要引入cglib的jar文件,但是Spring的核心包中已经包括了Cglib功能,所以直接引入spring-core-3.2.5.jar即可.

2.引入功能包后,就可以在内存中动态构建子类

3.代理的类不能为final,否则报错

4.目标对象的方法如果为final/static,那么就不会被拦截,即不会执行目标对象额外的业务方法.



## 7.12

Object类是公共的父类