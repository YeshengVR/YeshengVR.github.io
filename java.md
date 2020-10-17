



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

###### 补充：

utf-8存储的是三个字节，一般的emoji表情是四个字节。char类型不能存储emoji表情，但String类型可以存储Emoji表情。

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

11、补充

Alt+Shift+M将一段代码快速封装成一个方法。

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

因为静态方法从程序开始运行后就已经分配了内存，也就是说已经写死了。所有引用到该方法的对象（父类的对象也好子类的对象也好）所指向的都是同一块内存中的数据，也就是该静态方法。子类中如果定义了相同名称的静态方法，并不会重写，而应该是在内存中又分配了一块给子类的静态方法，没有重写这一说，我们应该称之为隐藏。

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

1. **饿汉模式**：饿汉模式就是立即加载，一般情况下在调用newStudent方法之前就已经产生了实例，也就是在类加载的时候已经产生了。这种模式的缺点很明显，就是占用资源。当单例类很大的时候，其实我们是想使用的时候再产生实例。因此这种方式适合占用资源少，在初始化的时候就会被用到的类。
2. **懒汉模式**：懒汉模式也就是延迟加载，也叫懒加载。在程序需要用到的时候再创建实例，这样保证了内存不会被浪费。

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



| 多态，即为多种形态     |
| ---------------------- |
| **子类赋值给父类引用** |
| 子类重写父类的方法     |

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



## 7.13

Object类是公共的父类，是所有类的根类

java.lang包重点的类：

 Object/String/StringBuffer/StringBuilder/包装类

java.util包重点的类：

Date/Calendar/GregorianCalendar

java.text包

SimpleDateFormat/NumberFormat

java.lang包下放置了java开发中常用的类和接口，，所以为简化该包下类的使用，java.lang包下的类在使用时不需要导入这些类。

### Object类

toString()方法将一个对象转换为字符串，获取对象的字符串形式。

直接打印某个对象，实际上是打印那个对象的toString()方法

getClass()获取当前对象的完整类结构

#### Boolean equals(Object 0)详解

Object类的equals方法用于判断两个对象是否相等

Object类的equals方法的返回值为boolean的true和false

Object类的equals方法只有一种情况返回true：两个非空的引用变量01和02指向的是同一个对象时。 

equals第一步判断是否为null。

判断对象的类型，是继续，否则返回false

将类型向下转型，在和this比较所有属性是否相同

在方法内部this永远不可能是null

此方法被重写时，通常hashcode方法也要被重写。

#### hashcode() 

获取对象的哈希值[根据地址得到的一个int类型整数]

相同的属性值，他一定会有相同的哈希值

两个对象相等，则哈希值一定相等。，哈希值相等，对象不一定相等。

#### finalize()

当垃圾回收器确定不存在该对象的更多引用时，由对象的垃圾回收器调用此方法。

#### clone()

创建并返回对象的一个副本。

### String类

提供了开中常用的字符串处理方法

字符串是是常量    ，它的值创建之后就不可以再修改了。

String类常用构造方法
String() 无参构造方法
String(String str) 有一个字符串参数的构造方法
String(char[]ch) 有一个char类型数组参数的构造方法
String(byte[] b) 有一个byte数组参数的构造方法

字符串可以将字节数组转成字符数组。

> String类常用方法
>  int length() 求字符串值的字符个数
>  boolean equals(Object o) 比较两个字符串是否相同
>  String replace(char old,char n) 字符串替换
>  char charAt(int index) 返回指定字符串指定位置的字符
>  int compareTo(String s)按字典顺序比较字符串大小
>  boolean endsWith(String s) 比较字符串是否以指定的参数结尾
>  boolean beginsWith(String s)比较字符串是否以指定的参数开头
> String valueOf(int i)将基本数据类型转换为字符串

![](F:\md笔记文件\java\javaimg\String常用方法.png)

## 7.15

### StringBulider

String字符串是不可更改的，所以这时候就出现了StringBulider和String Buffer类。可以对字符串进行更改。

![](F:\md笔记文件\javaimg\String_insert.png)

insert方法可以对字符串进行增加字符的操作。

append方法可以将其他字符添加到此字符串中。

![](F:\md笔记文件\javaimg\StringBulider_append.png)

delete方法可以删除字符串中内容。

```java
public class TestString {

	public static void main(String[] args) {
		
		StringBuilder s = new StringBuilder("javadoc#h3h2%wda");
		s.insert(4, "who");
		System.out.println(s);
		s.delete(11, 15);//删除11~15位置的字符
		System.out.println(s);
	}
}

```

### 正则表达式

正则表达式一般以“^”开头，以“$”结尾

**String正则API** 

正则表达式可以去网上搜索现成的正则表达式大全。![](F:\md笔记文件\javaimg\正则表达式部分内容.png)

![](F:\md笔记文件\javaimg\正则部分内容.png)比较常用的有matches方法：matches(String regex)告知此字符串是否匹配给定的[正则表达式](../../java/util/regex/Pattern.html#sum)

split方法：split(String regx)根据给定[正则表达式](../util/regex/Pattern.html#sum)的匹配拆分此字符串。

replaceAll方法：replaceAll(String regex, String replacement)        使用给定的 replacement 替换此字符串所有匹配给定的[正则表达式](../../java/util/regex/Pattern.html#sum)的子字符串。

### 包装类

在进行类型转换的范畴内，有一种特殊的转换，需要将int这样的基本数据类型转换为对象。

所有基本类型都有一个与之对应的类，即为包装类。

包装类是不可变类，在构造了包装类对象后，不允许更改包装在其中的值。

包装类是final的，不能定义他们的子类。

![](F:\md笔记文件\javaimg\包装类.png)

**Number类主要方法**

- doubleValue()以double形式返回指定的数值
- intValue()以int形式返回指定的数值
- floatVlaue()以float形式返回指定的数值

**Integer常用功能**

1. -static int MAX_VALUE 值为2^31-1的常量，表示int类型的能表示的最大值
2. -static int MIN_VALUE 值为-2^31的常量，表示int类型的能表示的最小值

**Integer也有小整数池的概念（-128~127）在这个范围内，地址相同**

Integer的静态方法parseInt用于将字符串转换为int(如果字符串不是整数形式，则不能转换为int)

```java
String str ="123";
int value = Integer.parseInt(str);
System.out.println(value);
-->123
```

Double常用功能也有静态方法parseDouble(String s)作用和int类型相似，也是将字符串转换为一个新的double值。

获取Number类的对象所属类型

```java
对象名.getClass().getName()
    //获取对象的所属数据类型。
```

例：

```java
Number d = 123.45;
d.getClass().getName()
```



#### 自动装箱和拆箱操作

从java5.0版本以后加入了autoboxing功能

自动”拆箱“和”装箱“是依靠JDK5的编译器在编译期的“预处理”工作

```java
Integer a = 100; //自动装箱
/*普通将int类型数值赋值给Integer是肯定不可以的，这里面做了两个步骤，先转换为Integer类型，在装入Integer类型的 j对象中。*/
Integer b = 200; //自动装箱
Integer c = a + b; //拆箱再装箱
double d = c;  //自动拆箱
```

装箱和拆箱是”编译器“认可的，而不是虚拟机。编译器在生成类的字节码时插入必要的方法调用。

## 7.17~7~20

**什么是设计模式**

在编程过程中我们经常会遇到一些典型的问题或需要完成某种特定需求，而这些问题和需求前人也曾经遇到过，他们经过大量理论总结和实践验证之后优选出的代码结构、编程风格、以及解决问题的思考方式，这就是设计模式（Design pattern）。设计模式就像是经典的棋谱，不同的棋局，我们用不同的棋谱，免得我们自己再去思考和摸索。

### 模板设计模式

**为什么要使用模板方法设计模式**

在解决一些问题或者设计一个软件的时候，需要先定义一个模板，就相当于一种事先定义好的协议。

以后要做这系列的事情都按照这个模板来做。这样就实现统一化管理。

**如何实现模板方法设计模式**

定义一个抽象的父类做为模板，定义所有需要的方法

在父类中实现供外界调用的主方法，将方法声明为final

根据不同业务需求定义子类实现父类的抽象方法

### 组合设计模式

**什么时候用组合**

组合是一种实现代码复用的方式，当我们在定义一个类的时候需要用到另外一个类的方法时，就可以用组合。

**怎么用组合**

定义一个所需要的类类型的成员变量

通过构造函数进行装配，接收一个该类类型的对象，用成员变量引用

在需要使用另一个类的方法时通过成员变量访问

**组合的优点**

如果两个类没有父子关系，不合适用继承。

Java只支持单继承，组合不占用继承位置。

### 单例设计模式

**单态（单例）设计模式**

单态设计模式（Singleton pattern）就是要保证在整个程序中某个类只能存在一个对象，这个类不能再创建第二个对象。

**单例设计模式的写法**

私有化构造函数，阻止创建新对象。 

由于需要返回一个对象，那么我们就需要在类内部自己创建一个对象，并使用成员变量记住它。

由于该类不能创建对象，所以这个成员变量不能是普通的成员变量，需要静态，这样在类加载之后就可以创建一个唯一的对象了。

我们不希望其他类修改这个成员变量，所以将其私有。 

提供一个公有的方法用来获取唯一的一个对象。

这个方法由于需要在不创建对象的情况下使用，所以需要静态。

### Object类的使用

```java
Class class1 = 对象名.getClass();//获取对象类的完整结构--》完整类名
```

#### clone方法

当使用Object调用clone方法时，没有实现cloneable的话就会出异常CloneNotSupportedException。 

### 内部类

```java
外部类名.内部类名 对象名 = new 外部类名().new 内部类名();
```

在类里面定义的类称为内部类（Inner Class），内部类是外部类的一个成员。

类必须创建外部类对象才能使用。内部类可以访问外部类成员，因为在使用内部类时一定会有外部类对象，且只对应一个。

外部类不能访问内部类成员，

## 7.21

### StringBuffer

构造一个其中不带字符的字符串缓冲区，其初始容量为 16 个字符。线程安全的可变字符序列。一个类似于 [`String`](../../java/lang/String.html) 的字符串缓冲区。

```java
append方法
String对象.append("字符串");//将append方法里的字符串添加至String对象后面。
```

```java
delete方法
String对象.delete(start，end);//将String对象按照delete方法里的位置删除String对象字符。
```

```java
insert方法
String对象.insert(int offset,字符)//将字符插入到String对象的offset位置
```

**左闭右开**位置都是不包括第一个数，但包括最后一个数。

String类、StringBuffer和StringBulider的区别

1. String字符串是常量，一旦创建无法修改
2. StringBuffer和StringBulider是可变字符串，创建之后仍可以修改。
3. String Buffer是线程安全的，StringBulider是线程不安全的。

**indexOf方法如果没找到就是返回-1；如果找到就返回找到的数值下标**

### String和StringBuffer——字符串性能优化

关键点
1. 无论何时只要可能的话使用字符串字面量来常见字符串而不是使用new关键字来创建字符串。
2. 无论何时当你要使用new关键字来创建很多内容重复的字符串的话，请使用String.intern()方法。
3. +操作符会为字符串连接提供最佳的性能——当字符串是在编译期决定的时候。
4. 如果字符串在运行期决定，使用一个合适的初期容量值初始化的StringBuffer会为字符串连接提供最佳的性能。
### 包装类

```java
Integer.parseInt("123");//将括号中的字符串转换为int类型。
```

```java
//Integer类的基本用法
Integer s = new Integer(10);// int-->Integer
		int intValue = s.intValue();// Integer --> int
		
		Integer s1 = new Integer("12938");// String -->Integer
		String string = s1.toString();// Integer -->string
		
		int parseInt = Integer.parseInt("4299");// String -->int
		String valueOf = String.valueOf(parseInt);// int -->String
```

### Boolean包装类

boolean类型的包装类Boolean
Boolean用于将一个基本数据类型boolean值包装为对象
将boolean值转换为Boolean对象
Boolean b1 = new Boolean(true);//方法一
Boolean b2 = Boolean.valueOf(true);//方法二
将Boolean对象转换为boolean值
Boolean b =  new Boolean(true);
boolean b1 = b.booleanValue();//方法一 

### Character包装类

Character包装类除了提供以上char和Character相互转换的方法意外也提供了其他好用的方法。

字符包装类Character用于将char类型值包装为对象
将char值转换为Character对象
Character c1= new Character(‘A’);//方法一
Character c2 = Character.valueOf(‘A’);//方法二
将Character对象转换为char值
Character c1= new Character(‘A’);
char ch1 = c1.toString();//方法一
char ch2 = Character.toString(c1);//方法二

![](F:\md笔记文件\javaimg\Character包装类.png)

### Math类

![](F:\md笔记文件\javaimg\Math类.png)

### System类

System类代表运行时系统，提供了一些获取设置和获取当前系统运行环境的方法

**System有三个成员变量**：

1. in标准输入流
2. out标准输出流
3. err错误输出流

**System中的方法**

- System.arrayCopy()//快速复制数组的方法
- System.exit()//退出Java虚拟机的方法

### Scanner类的注意

**一段程序如果出现红色的报错信息是绝对不优秀的程序。**

如果使用控制台输入就用nextLine();

```java
//良好的程序不应该有红色报错信息
Scanner input = new Scanner(System.in);
		String s1 = input.nextLine();
		boolean matches = s1.matches("^[1-9][0-9]{1,2}$");
		if(matches){
			int parseInt = Integer.parseInt(s1);
			System.out.println(parseInt);
		}else{
			System.out.println("年龄只能是1~3的正整数");
		}
```

## 7.22

### Date类

Date类表示特定的时间，可以精确到毫秒。

Date类构造方法

Date()无参构造方法

Date(long time)有长整型参数的构造方法

**常用方法**

- long getTime();返回1970年1月1日00：00：00GMT以来此Date对象表示的毫秒数

- String toString();将Date对象转换为字符串，默认的转换格式为：dow mon dd hh:mm:ss zzz yyyy

### Calendar类

java.util.Date类中获取当前年、月、日和将时间格式化以及将字符串类型的日期转换为Date对象的方法都已经被废弃。

如果想要获取Date对象的年、月、日、星期等操作，需要使用Calendar类以及其子类完成。

Calendar是一个抽象类，他为获取和修改年、月、日、星期等日历字段提供了一系列的方法。

常用方法

Calendar getInstance();返回一个Calendar对象
void set(int field,int x);设置日历字段的值
void get(int field);获取某个日历字段的值
java.util.Date getTime();返回代表该日历对象的Date值 void setTime(java.util.Date date);使用指定的Date设置该日历对象

常用的日历字段

AM_PM 上午或者下午
YEAR 年 MONTH 月 DATE 日 HOUR 12小时制 HOUR_OF_DAY 24小时制 MINUTE 分钟 SECOND 秒 MILLISECOND 毫秒

```java
Calendar.getInstance().getTimeInMillis();//获取时间戳的方法，自1970年起到至今的总共毫秒数。
//一般用于判断一段时间的间隔时长
```

### GregorianCalendar类

GregorianCalendar是Calendar的一个直接子类。

提供了世界上大多数国家/地区使用的标准日历系统，及中国所谓的阳历或者公历

**常用方法**

boolean isLeapYear(int year) 判断指定年份是不是闰年
void add(int field ,int x)为指定的日历字段增加值

### text类

提供以与自然语言无关的方式来处理文本、日期、数字和消息的类和接口

java.text包常用类或者接口

DateFormat以及子类SimpleDateFormat

NumberFormat以及子类DecimalFormat

#### DateFormat类

DateFormat是一个抽象的时间格式化类

DateFormat是日期/时间格式化的抽象类，他以与语言无关的方式格式化并解析日期或时间。

DateFormat可帮助进行格式化并解析任何语言环境的日期。对于月、星期，甚至日历格式（阴历和阳历），其代码可完全与语言环境的约定无关。

在格式化和解析日期时间过程中，其子类SimpleDateFormat更为常用。

SimpleDateformat一般的对时间格式化

```java
//Date-->String
Date date = new Date();//时间
		SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss E a");//模式
		String time = sdf.format(date);
		System.out.println(time);
//String -->Date
		String t = "2020-07-23 09:27:58 星期四 上午";
		SimpleDateFormat sdf2 = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss E a");
		Date parse = sdf2.parse(t);
		
```

SimpleDateFormat类
是一个以与语言环境有关的方式来格式化和解析日期的具体类
它提供了格式化日期时间(日期时间字符串)和解析日期时间(字符串日期时间)的方法
**SimpleDateFormat构造方法**
SimpleDateFormat()
SimpleDateFormat(String pattern) 按照指定的模式创建SimpleDateFormat对象

![](F:\md笔记文件\javaimg\SimpleDateFormat.png)

NumberFormat

```java
		DecimalFormat df = new DecimalFormat("0,000.00");//强制保留俩位
		DecimalFormat df2 = new DecimalFormat("#,###.##");//最多保留两位
		df2.setMaximumFractionDigits(n);//小数位最多n位
		df2.setMinimumFractionDigits(m);//小数位最少m位
```

double类型在Java中是以科学计数法存放。

```java
//Number -->String
		double s = 123456789.73531141;
		DecimalFormat df4 = new DecimalFormat("#,###.##");
		String format = df4.format(s);
		
		// String -->Number
		String s1 = "123456789.122421";
		DecimalFormat df3 = new DecimalFormat("#,###.##");
		Number parse = df3.parse(s1);
```

NumberFormat是一个数字格式化抽象类
该类提供了格式化和解析数值的方法
**常用方法**
 String format(double d)将数字格式化为字符串
 Number parse(String s)将字符串解析为数字
 void  setMaximumFractionDigits(int newValue)设置最大小数位
 void  setMinimumFractionDigits(int newValue) 设置最小小数位
通常情况下会使用其子类DecimalFormat格式化或者解析数字

#### DecimalFormat类

DecimalFormat 是 NumberFormat 的一个具体子类，用于格式化十进制数字。该类设计有各种功能，使其能够解析和格式化任意语言环境中的数，包括对西方语言、阿拉伯语和印度语数字的支持。
**构造方法**
DecimalFormat()
DecimalFormat(String pattern)按照指定模式构建对象

![](F:\md笔记文件\javaimg\DecimalFormat.png)

## 7.23

### 异常

异常是程序在编译或者运行期间出现的意外。

![](F:\md笔记文件\javaimg\常见异常种类.png)

```java
//常见的运行时异常		
	public static void main(String[] args) throws Exception {
		//算术异常：ArithmeticException
		int a = 10/0;
		
		//数组下标越界异常：ArrayIndexOutOfBoundsException
		int[] arr = {1,2};
		arr[3] = 10;
		
		//空指针异常：NullPointerException
		String str = null;
		int length = str.length();
		
		//类型转换异常：ClassCaseException
		String s = (String)new Object();
		
		//数字格式化异常：NumberFormatException
		Integer i = new Integer("abc");
		
		//解析异常：ParseException
		SimpleDateFormat sdf = new SimpleDateFormat("yyyy");
		sdf.parse("sadaf");
		
		//非法的参数异常：IllegalArgumentException
		Date d = new Date();
		SimpleDateFormat sdfn = new SimpleDateFormat("awdawd");
		sdfn.format(d);
		
		//栈溢出异常：StackOverflowError
		t();//一般为递归没出口或循环有问题
		
	}
	public static void t(){
		int a = 10;
		t();
	}
```

#### Throwable类

Thorwable为所有异常类的父类

Exception的所有子类都是编译器异常。除了RuntimeException是运行期异常。

![](F:\md笔记文件\javaimg\Throwable异常.png)

#### 异常分类

检查异常也被称为编译器异常

1. 不可避免必须进行异常处理，要不然编译器报错
2. Exception以及它的子类（除去RuntimeException）

未检查异常也成为运行时异常

1. 可以避免，不需要处理
2. RuntimeException以及它的子类

Java编译器异常的处理方式有两种

- 使用try、catch、finally关键字捕获异常
- 使用thorows关键字声明抛出异常。

#### throws

通过throws关键字在方法头抛出异常

本身不处理异常，交给调用者处理异常

方法抛出了异常之后调用了方法之后，也要将调用的方法抛异常。

通过throws关键字可以在方法头抛出多个异常。

如果抛出了异常类型为Exception类型，那么在try   catch代码块中需要处理的异常类型也应该为Exception类型。

在开发中，可能需要自定义异常类
自定义异常根据继承的父类不同分为两类
继承自Exception的自定义异常
继承自RuntimeException的自定义异常
继承自Exception的自定义异常为编译期异常必须要进行处理
继承自RuntimeException的自定义异常为运行时异常不需要进行特别的处理。

#### try-catch

```java
try{
	//可能会出现异常的代码
    //如果异常，内部任何程序都不会执行、
   return;
 }catch(ParseException  e){
	//捕获执行的代码
 }finally{
	//不管是否发生异常都要执行的代码
   return;
 }

//类似实例
try{
	toDate();
 }catch(ParseException  e){
	e.printStackTrace();
 }
```

catch可以有多个

在try()括号中写下流，在执行完之后会自动关闭流通道。

## 7.27

### Random()类

```java
public int nextInt(int n)//返回一个伪随机数，范围在0和指定值n之间的int值
```

### 

### 集合框架

![](F:\md笔记文件\javaimg\集合图鉴.png)

![](F:\md笔记文件\javaimg\集合特点.png)

框架：通俗易懂的讲就是功能类

集合：有时又称为容器，简单地说它是一个对象，能将具有相性质的多个元素汇聚成一个整体

集合被用于存储、获取、操纵和传输聚合的数据。

在集合中添加基本数据类型，会变成包装类型。

集合框架（Collections Framework）是用来表现和操纵集合的一个统一的体系结构。所有的集合框架都包含以下内容：

接口：是代表集合的抽象数据类型。

实现：实际和接口的具体实现。本质上，他们是可重用的数据结构，是一些类。

算法：是在实现了集合接口的对象上执行的计算机的方法，如查找和排序。

![](F:\md笔记文件\javaimg\java集合框架.png)

#### Collection接口

| **基本操作**               |                                  |
| -------------------------- | -------------------------------- |
| int size()                 | 返回集合元素的个数               |
| boolean isEmpty()          | 判断集合是否包含集合元素         |
| boolean contains(Object o) | 判断集合中是否包含指定元素       |
| boolean add(E element)     | 向集合中添加指定元素             |
| boolean remove(Object o)   | 从集合中移除指定元素             |
| Iterator<E> iterator()     | 返回在集合元素上进行迭代的迭代器 |

| **批量操作**                              |                                  |
| ----------------------------------------- | -------------------------------- |
| boolean containAll(Collection<?> c)       | 集合中是否包含指定的所有集合元素 |
| boolean addAll(Collection<? extendsE> c ) | 向集合中添加指定集合的所有元素   |
| boolean removeAll(Collection<?> c)        | 从集合中移除指定集合的包含的元素 |
| void clear()                              | 移除集合中所有元素               |
| boolean retainAll(Collection<?> c)        | 保留集合中指定的元素             |

#### List接口

list接口是一个有序的集合，可以包含重复元素。

除了从Collection继承来的操作外，List接口还提供了以下按序列进行操作的方法。<数据类型>

| **按序列操作的方法**              |                                |
| --------------------------------- | ------------------------------ |
| E get(int index)                  | 返回集合中指定位置的元素       |
| int indexOf(Object o)             | 返回指定对象在集合中的索引位置 |
| List<E> subList(int from ,int to) | 从集合中截取子集合             |
| E remove(int index)               | 移除集合中指定位置的元素       |



#### ArrayList集合框架

ArrayList集合的意义和StringBuffer类的意义有点相似。

ArrayList集合糅合了数组的一些用法，使用无参的ArrayList构造方法时会自动创建长度为10的集合。可以添加不同的数据类型，会自动增长集合长度。

```java
//增加元素
ArrayList arr = new ArrayList();//创建对象
		arr.add("aa");//add方法可以添加字符串
		arr.add(10);//也可以添加基本数据类型
		arr.add(0, "bb");//在arr数组的指定位置添加数据
```

用第二种add方法的时候，切记第一个位置，的数组位置下标不能乱写，要注意不要引起下标越界异常。

```java
//删减元素
ArrayList arr = new ArrayList();//创建对象
		arr.remove(0);//直接在remove中写要删除的指定元素的下标
		arr.remove("aa");//删除遇到的第一个这个引用类型元素
		arr.remove(new Integer(10));//如果要删除某一个基本类型的数据，需要使用包装类来删除。

```

Ps:remove和clear删除方式都不能把集合变为null。

```java
//修改元素
ArrayList arr = new ArrayList();//创建对象
		arr.set(0,"AA");//用指定元素替换掉指定下标元素
```

```java
//查找元素
ArrayList arr = new ArrayList();//创建对象
		Object obj = arr.get(0);//获取指定下标元素
```

```java
//其他方法
arr.clear();//清空
boolean contains = arr.contains(10);//是否包含指定元素
boolean empty = arr.isEmpty();//判断是否为空集合
arr.subList(int from,int to)//生成一个子集合，从from下标开始一直到to下标结束。
Object[] array = arr.toArray();//将集合转为数组    
```

```java
//集合遍历
//遍历方案一
		for(int i = 0;i<arr.size();i++){
			Object o = arr.get(i);
			System.out.println(o);
		}
//遍历方案二
		for(Object 0:arr){
            System.out.println(o);
        }
//遍历方案三
Iterator iter = arr.iterator();//迭代器
while(iter.hasNext()/*判断有没有下一个元素*/){
    Object next =iter.next();
    System.out.println(next);
}
```

ArrayList：元素可以任意类型，可以重复，可以为null，有下标，有序【按照元素的存入顺序打印】。

LinkedList：元素可以任意类型，可以重复，可以为null，有下标，有序【按照元素的存入顺序打印】

不同：ArrayList内存空间连续，插入和删除慢，查找快。LinkedList内存空间不连续，通过双向链表来维护元素，插入和删除快，查找慢。

Vector：线程安全的。

#### Set接口

Set是一个不能包含重复元素的接口，是无序的，不能包含重复的

Set接口时Collection的子接口，增加了对add方法的限制，不允许有重复的元素。

| **基本操作**               |                                  |
| -------------------------- | -------------------------------- |
| int size()                 | 返回集合元素的个数               |
| boolean isEmpty()          | 判断集合是否包含集合元素         |
| boolean contains(Object o) | 判断集合中是否包含指定元素       |
| boolean add(E element)     | 向集合中添加指定元素             |
| boolean remove(Object o)   | 从集合中移除指定元素             |
| Iterator<E> iterator()     | 返回在集合元素上进行迭代的迭代器 |

| **批量操作**                              |                                  |
| ----------------------------------------- | -------------------------------- |
| boolean containAll(Collection<?> c)       | 集合中是否包含指定的所有集合元素 |
| boolean addAll(Collection<? extendsE> c ) | 向集合中添加指定集合的所有元素   |
| boolean removeAll(Collection<?> c)        | 从集合中移除指定集合的包含的元素 |
| void clear()                              | 移除集合中所有元素               |
| boolean retainAll(Collection<?> c)        | 保留集合中指定的元素             |

#### Map接口

Map是一种包含键值对的元素的集合。

Map不能包含重复的键。

每个键最多映射一个值。

```java

```

| **基本操作**                   | ** **                              |
| ------------------------------ | ---------------------------------- |
| V put(K key , V value)         | 将指定的值与映射中的指定键进行关联 |
| V get(Object key)              | 返回指定键所对应的映射值           |
| V remove(Object key)           | 如果存在一个键的映射关系，那么移除 |
| int size()                     | 返回此映射中键值映射关系的数量     |
| boolean isEmpty                | 判断此映射中是否包含映射关系       |
| boolean containKey(Object k)   | 判断映射中是否包含指定的键         |
| boolean containValue(Object v) | 判断映射中是否包含指定的值         |

| **批量操作和集合视图**                    | ** **                                       |
| ----------------------------------------- | ------------------------------------------- |
| void clear()                              | 清除映射中所有的映射关系                    |
| void putAll(Map<? extends K,? extends V>) | 将指定映射中的映射关系复制到当前映射中去    |
| Set<K>keySet                              | 返回此映射中包含的所有key的Set视图          |
| Collection<V>values                       | 返回此映射中包含的所有value的Collection视图 |
| Set<Map.Entry<K,V>> entrySet              | 返回此映射中包含的所有映射关系的Set视图     |

## 7.28

### HashSet

元素可以任意类型，不能重复的元素，可以为null，**没有下标**，无序[顺序和哈希码有关]

```java
Hash set = new HashSet();
//增
set.add("aaa");
set.add(10);
set.add(null);
//删
set.remove(10);
//改
m欸有直接修改的方法，可以删除要修改的元素再添加。
//查
boolean contains = set.contains(10);
```

```java
//其他方法
clear();//清空元素
//遍历元素
for(Object o:set){
    system.out.println(o);
}
Iterator iter = set.iterator();
		while(iter.hasNext()){
			Object next = iter.next();
			System.out.println(next);
		}
```

LinkedHashSet是HashSet的子类，基本和HashSet一样除了存储形式。**有序！**

//泛型：泛指一种类型<数据类型>

<T>:泛型接口

### TreeSet

TreeSet类型元素要一致类型。不能重复，不能为null，TerrSet集合必须放可以实现Comparable接口的类。否则会报空指针异常。一般这种集合都会写上泛型。

```java
//add方法放的元素必须是实现了Comparable接口的类
```

ps：Comparable此接口强行对实现它的每个类的对象进行整体排序。这种排序被称为类的*自然排序*，类的 `compareTo`  方法被称为它的*自然比较方法*。

TreeSet集合会自然排序好。

TreeSet的构造方法里还有可以传入一个comparator的子类比较器，TreeSet的比较方式就会根据写的比较器的方法来比较顺序。比较器的好处是，比较方法任意，可以方便更改。

### **Map**

#### HashMap

hashmap用键值进行存储。

HashMap：Key可以为任意类型,(HashMap的顺序是(无序的)，是根据哈希码排的.)不会重复，可以为null，Key就是自定义下标；Value可以任意类型，可以重复，可以为null，键值对性质，value跟着key走。

hashmap直接输出，与其他的集合输出不一样，其他的集合都是用[]括起来，而hashmap是用大括号，键和值之间用=号相连。

hashMap用键值没找到的话就会返回一个null。

Hashtable：同HashMap使用，但是Hashtable是线程安全的。

```java
		HashMap hm = new HashMap();
		//增
		hm.put("aa", "AA");
		hm.put("bb", "BB");
		hm.put(null, "CC");
		//删
		hm.remove(null);
		//改
		hm.put("aa", "hello,world!");
		//查
		hm.get("aa");
```

```java
//Map的遍历
//获取所有值得集合
		Collection<String> values = hm.values();
		for(String s:values){
			System.out.println(s);
		}
		
		Set<String> keySet = hm.keySet();
		Iterator<String> iterator = keySet.iterator();
		while(iterator.hasNext()){
			String next = iterator.next();
			String string = hm.get(next);
			System.out.println(string);
		}
		System.out.println(keySet.getClass());
		System.out.println("-----------------------");
		//Entry是Map的一个内部类
		Set<Map.Entry<String, String>> entrySet = hm.entrySet();
		for(Map.Entry<String, String> entry:entrySet){
			System.out.println(entry.getKey()+"="+entry.getValue());
```

#### TreeMap

融合了TreeSet和Map的特点，在添加时也会进行排序，是对键值进行排序。键值一定得是相同类型。

TreeMap:key类型要一致，不可以为null，不会重复，key是自定义下标。

## 7.29

```java
public File(String pathname)//通过将给定的路径名字符串转换为抽象路径名来创建新的File实例
public File(String parent,String child)//从父路径名字符串和子路径名字符串创建新的File实例。
public File(File parent,String child)//从父抽象路径名和子路径名字符串创建新的File实例。
```

一个File对象代表硬盘中实际存在的一个文件或者目录。

无论该路径下是否存在文件或者目录，都不影响File对象的创建。

```java
//获取功能的方法
public String getAbsolutePath()//返回此File的绝对路径名字符串
public String getPath()//将此File转换为路径名字符串
public String getName()//返回由此File表示的文件或目录的名称
public long length()//返回由此File表示的文件的长度
```

**绝对路径**：从盘符开始的路径，这是一个完整的路径。

**相对路径**：相对于项目目录的路径，这是一个便捷的路径，开发中经常使用。

```java
public class FilePath {
	public static void main(String[] args) {
// D盘下的bbb.java文件
	File f = new File("D:\\bbb.java");
	System.out.println(f.getAbsolutePath());
// 项目下的bbb.java文件
	File f2 = new File("bbb.java");
System.out.println(f2.getAbsolutePath());
	}
}
```

```java
//判断功能的方法
public boolean exists() ：此File表示的文件或目录是否实际存在。
public boolean isDirectory() ：此File表示的是否为目录。
public boolean isFile() ：此File表示的是否为文件。
//创建删除功能的方法
public boolean createNewFile() ：当且仅当具有该名称的文件尚不存在时，创建一个新的空文件。
public boolean delete() ：删除由此File表示的文件或目录。
public boolean mkdir() ：创建由此File表示的目录。
public boolean mkdirs() ：创建由此File表示的目录，包括任何必需但不存在的父目录。
```

## 7.29

### Queue和Stack ：队列和栈

队列：先进先出。

栈：后进先出。

**方法**

pop()移除堆栈顶部的对象，并作为此函数的值返回该对象。

List如果想要进行排序可以用Collections的sort方法

不过要排序的类必须实现Comparator类，或者通过比较器

```java
Collections.sort(list);//按list集合中元素的自然顺序排序(必须实现Comparator类)
//Collections.shuffle(list);
Collections.sort(list,c1);//按比较器的排序规则排序
Collections.binarySearch(list,V)//二分搜索法，调用此方法前，必须先进行升序排序。
```

###### 补充：可变参数

```java
public void add(int .... a){
	//在方法里面会把a当作int类型的数组；
    for(int i =0;i<a.length;i++){
	
    }//通过循环输出数组
}
```

```java
//Arrays
List<int[]> asList = Arrays.asList(new int[]{10,20,30});//基本数据类型转换成一个数组，存储在集合中以一个元素存在
List<String> asList = Arrays.asList(new String[]{"10","20","30"});//引用数据类型转换成一个数组，存储在集合中以对应个数个元素存在。
Arrays.copyOf(array,length);//复制一个数组array，设置他的长度为length。
```





### IO流File类

```java
public File(String pathname)//通过将给定的路径民字符串转换为抽象路径名来创建新的File实例
public File(String parent,String child)//从父路径名字符串和子路径名字符串创建新的File实例。
public File(File parent,String child)//从父抽象路径名和子路径名字符串创建新的File实例。
```

一个File对象代表硬盘中实际存在的一个文件或者目录。

无论该路径下是否存在文件或者目录，都不影响File对象的创建。

```java
//获取功能的方法
public String getAbsolutePath()//返回此File的绝对路径名字符串
public String getPath()//将此File转换为路径名字符串
public String getName()//返回由此File表示的文件或目录的名称
public long length()//返回由此File表示的文件的长度
```

**绝对路径**：从盘符开始的路径，这是一个完整的路径。

**相对路径**：相对于项目目录的路径，这是一个便捷的路径，开发中经常使用。

```java
public class FilePath {
	public static void main(String[] args) {
// D盘下的bbb.java文件
	File f = new File("D:\\bbb.java");
	System.out.println(f.getAbsolutePath());
// 项目下的bbb.java文件
	File f2 = new File("bbb.java");
System.out.println(f2.getAbsolutePath());
	}
}
```

```java
//判断功能的方法
public boolean exists() ：此File表示的文件或目录是否实际存在。
public boolean isDirectory() ：此File表示的是否为目录。
public boolean isFile() ：此File表示的是否为文件。
//创建删除功能的方法
public boolean createNewFile() ：当且仅当具有该名称的文件尚不存在时，创建一个新的空文件。
public boolean delete() ：删除由此File表示的文件或目录。
public boolean mkdir() ：创建由此File表示的目录。
public boolean mkdirs() ：创建由此File表示的目录，包括任何必需但不存在的父目录。
```

File类没有无参构造方法。

```java
File file = new File("lli.txt");
		boolean canExecute = file.canExecute();//是否可以执行
		boolean canRead = file.canRead();//是否可读
		boolean canWrite = file.canWrite();//是否可写
		boolean hidden = file.isHidden();//是否隐藏
//		file.delete();//删除文件
		file.deleteOnExit();//虚拟机退出时，删除文件
//		Thread.sleep(5000);
		boolean exists = file.exists();//文件或者文件夹是否存在
		String absolutePath = file.getAbsolutePath();//获取绝对路径
		String name = file.getName();//获取文件或目录的名称
		String parent = file.getParent();//父目录的路径名字符串
		File parentFile = file.getParentFile();//父目录的路径对象形式
		String path = file.getPath();//目录的路径名字符串
		boolean absolute = file.isAbsolute();//判断是否是绝对路径
		boolean file2 = file.isFile();//判断是否是文件
		boolean directory = file.isDirectory();//判断是否是文件夹
		long lastModified = file.lastModified();//最后一次修改的时间
		Date d = new Date(lastModified);
		long length = file.length();
		//只有文件夹可以使用，否则会报空指针异常
		String[] list = file.list();//文件夹的子级文件或文件夹【只有文件名】
		File[] listFiles = file.listFiles();//文件夹的子级文件或文件夹【全路径】
		file.setWritable(false);//设置只读模式
		
		//父级目录存在在可以创建文件
		file.createNewFile();//创建新的文件
		File parentFile2 = file.getParentFile();
		parentFile2.mkdir();//创建父级目录
		parentFile2.mkdirs();//创建所有父级目录
```

### 递归

通过自身调用自身

斐波那契数列

```java
public static int fbnq(int n){
	if(n==1||n==2){
		return 1;
	}
	return fbnq(n-1)+fbnq(n-2);
}
```

## 7.30

### 流

- 流是一组有序的，有起点和终点的字节集合，是对计算机中数据传输的总称或者抽象
- 即数据在两个设备间的传输称为流，流的本质是数据传输。
- 流序列中的数据可以是没有进行加工的原始数据（二进制字节数据）也可以是经过编码的符合某种格式的规定的数据，Java中提供了不同的流类对他们进行处理。

![](F:\md笔记文件\javaimg\IO流框架.png)

按照**流传输方向**不同	
输入流（InputStream）
输出流（OutputStream）
按照**处理数据类型**的不同
字节流
字符流
按照**流的基本功能**不同
节点流
过滤流

*ps：每次创建完流通道都得记得关闭通道。释放资源。*

#### 输入流

在Java中，程序可以打开一个输入流，输入流的信息源可以位于文件、内存或网络套接字（socket）等地方，信息源的类型可以是包括对象、字符、图像、声音在内的任何类型。一旦打开输入流后，程序就可从输入流串行的读数据。

![](F:\md笔记文件\javaimg\InputStream.png)

#### 输出流

类似的，程序也能通过打开一个输出流并顺序的写入数据来讲信息送至目的端。

![](F:\md笔记文件\javaimg\OutputStream.png)

#### 字节流

传输的数据单位是字节，意味着字节流能够处理任何一种文件

字节流的组成：

- 字节输入流inputStream
- 字节输出流 OutputStream

![](F:\md笔记文件\javaimg\Fileinput_output.png)

**FileInputStream常用方法**

构造方法
FileInputStream(String filename)
FileInputStream(File file)

常用方法
close() 
int read()
int read(byte[]b)
int read(byte[] bs, int off, int len)

**FileOutputStream常用方法**

常用构造方法
FileOutputStream(String path)
FileOutputStream(File file)
FileOutputStream(String path, boolean append)
FileOutputStream(File file, boolean append)
常用方法
close()
void write(int v)
void write(byte[] bs)
void write(byte[] bs, int off, int len) 

#### 字符流

字符编码
常见的 编码规范（字符集）
***ASCII***
***ISO-8859-1***
***GB2312***
***GBK***
***UTF-8***
乱码问题

字符流的组成

- **Reader**
- **Writer**

FileReader
FileReader(String  fileName)
close()
int read(char[] cbuf) 
 FileWriter
FileWriter(String fileName)
close()
write(String value)

**InputStreamReader和OutputStreamWriter**
特点：  
可以把一个字节流转换成一个字符流
 在转换时可以执行编码方式
**InputStreamReader**
InputStreamReader(InputStream  is)
InputStreamReader(InputStream  is   String charSet)
int read(char[] cbuf)

**OutputStreamWriter**
OutputStreamWriter(OutputStream  is) 
OutputStreamWriter(nOuputtStream  is   String charSet)
write(String value)

#### 过滤流

Data  Stream
DataInputStream
readXxx();
DataOutputStream
writeXxx();
 过滤流的开发步骤
创建节点流
基于节点流创建过滤流
读/写数据
关闭外层流

![](F:\md笔记文件\javaimg\过滤流.png)

**ObjectStream**

ObjectInputStream  
ObjectOutputStream
ObjectStream特点
writeObject()
readObject()
对象序列化

##### **transient**

序列化时注意事项

不要使用追加的方式写对象

如果一个对象的属性又是一个对象，则要求这个属性对象也实现了Serializable接口

#### 字符流过滤流

BufferedReader  
字符过滤流，提供了缓冲功能可以一行一行的读取内容
public String readLine()
完整的字符输入流的开发步骤
创建节点流
桥转换为字符流
在字符流的基础上封装过滤流
读/写数据
关闭外层流

#### 字符过滤流

PrintWriter
字符过滤流
提供了缓冲功能
可以一行一行的输出内容
println();
第一种用法

```java
//字符流过滤流
		String path ="D:"; 
		String child = "st";
		String child2 ="ad";
		File f = new File(path,child);//创建file对象
		FileInputStream fis = new FileInputStream(f);//创建字节流
		InputStreamReader isr = new InputStreamReader(fis);//创建字符流
		BufferedReader br = new BufferedReader(isr);//创建字符流的过滤流
		
		String readLine = null;
		while((readLine=br.readLine())!=null){
			System.out.println(readLine);
		}
	
		File f2 = new File(path,child2);
		FileOutputStream fos = new FileOutputStream(f);//创建字节流
		OutputStreamWriter osw = new OutputStreamWriter(fos);//创建字符流
		/*BufferedWriter bw = new BufferedWriter(osw);//创建字符流过滤流
		bw.write("\r\n");
		bw.newLine();
		bw.write("你好！");*/
		
		PrintWriter pw = new PrintWriter(osw);
		pw.println("你好");
		
		pw.flush();
		br.close();pw.close();
```

#### 对象流

序列化:串行化，持久化。

序列化就是有格式的二进制数据

如果想要保存对象流，将一个对象写入流通道中需要将对象先进行序列化通过实现Serializable接口。

调用writeObject的方法时候，不光本类需要实现序列化，本类里面的引用属性也要实现实例化。

## 8.4

### 多线程

**进程**

进程是一个正在执行的程序。

每一个进程都有一个执行顺序，该顺序是一个执行路径，或者叫一个控制单元。

**线程**

线程是一个独立的控制单元。

线程在控制着进程的执行。



**一个进程至少有一个线程**

Java VM 启动的时候会有一个进程java.exe。

该进程中至少一个线程负责Java程序的执行。而且这个线程运行的代码存在于main方法中，该线程称之为主线程。

扩展：其实更细节的说明虚拟机JVM,JVM启动不止一个线程，还有负责垃圾回收的线程。

如何在自定义代码中，自定义一个线程。

Java虚拟机允许应用程序并发的运行多个执行线程。

java已经提供了对线程这类事物的描述，是Thread类。

创建新执行线程有两种方法：

1. 将类声明为Thread的子类，该子类应重写Thread类的run方法，接下来分配并启动该子类的实例。

   ```java
   class PrimeThread extends Thread{
       long minPrime;
       PrimeThread(long minPrime){
           this.minPrime = minPrime;
       }
       public void run(){
           //compute primes larger than minPrime
           ...
       }
   }
   ```

   通过如下代码启动一个线程

   ```java
   PrimeThread p = new PrimeThread(143);
   p.start();
   ```

   第一步定义类继承Thead类

   第二步覆写Thead类中的run方法（目的：将自定义代码存储在run方法中，让线程运行）

   第三步调用线程的start方法（start方法：使线程开始执行，Java虚拟机调用该线程的run方法。）

2. 声明实现Runnable接口的类。该类实现run方法，然后可以分配该类的实例，在创建Thread时作为一个参数来传递并启动。

```java
class Prime implements Runnable{
    long minPrime;
    PrimeRun(long minPrime){
        this.minPrime = minPrime;
    }
    public void run(){
        //compute primes larger than minPrime
        ...
    }
}
```

通过如下代码启动一个线程

```java
PrimeRun p = new PrimeRun(143);
new Thead(p).start();
```

每次多线程运行结果都不同。

因为多个线程都获取cpu的执行权，cpu执行到谁，谁就运行。明确一点，在某一个时刻，只能有一个程序在运行（多核除外）

cpu在做着快速的切换，以达到看上去是同时运行的效果。 我们可以形象的把多线程的运行行为在互相抢夺cpu的执行权。

这就是多线程的一个特性：随机性。谁抢到谁执行，至于执行多长，cpu说的算。

###### 补充

多核编程有空可以了解一下。

## 创建线程-run和start特点

Thread类用于描述线程。

该类就定义了一个功能，用于存储线程要运行的代码，该存储功能就是run方法。

Thread类中的run方法用于存储线程要运行的代码。这是虚拟机定义的。

start方法是开启线程，执行线程中的run方法

单纯的run方法指的是调用这个方法，没有线程的特点。

## 多线程运行状态

![](F:\md笔记文件\javaimg\多线程运行状态.png)

![](F:\md笔记文件\javaimg\线程状态.png)

### 阻塞状态

阻塞状态/临时状态：具备运行资格，但没有执行权。

### 冻结状态

冻结状态：当一个线程碰到了sleep、wait 进入冻结状态，此状态放弃了执行资格。

wait()方法最好放在循环之中，否则可能造成**虚假唤醒状态**

没执行资格是冻结状态，有执行资格但没有执行权的就是临时状态，既有资格又有执行权就叫运行状态。

用sleep来控制多线程是非常不精确的。（例如，某一支线程需要另一个支线程的结果，用sleep控制不精确）这时候可以采用join来实现控制

## 多线程获取线程对象以及名称

线程都有自己默认的名称，Thread-编号，该编号从0开始。

### join方法

如果两个线程彼此调用对方的join方法程序就会一直运行不会结束，互相等待对方。

解决办法
public final void join(long millis) throws  InterruptedException

join：

```java

```

利用sleep方法对线程的控制是非常不精确的
join方法可以精确控制线程
join方法也会导致线程阻塞
特点：如果当前线程中调用了另外一个线程的 join方法，当前线程会立即阻塞，直到另外一个线程运行完成

可以通过getName()方法获取线程名称。

```java
Thread.currentThread()//返回对当前正在执行的线程对象的引用。因为是静态方法用类名.方法名就ok
Thread.currentThread().getName()//使用此方法获取当前线程的名称最为合适。实现Runable接口的线程用这种方法获取名字
```

设置线程的名称：可以通过setName或者带参的构造方法设置线程名称。

多线程设置优先级也不一定会是最先运行，只是概率更大。 

例：

```java
class Dicket extends Thread{
	private static int dickNum = 100;
	public Dicket(String name){
		super(name);
	}
	public Dicket(){
		
	}
	public void run(){

		while(dickNum!=0){
			if(dickNum>0){
				System.out.println(Thread.currentThread().getName()+"售卖了第"+dickNum--+"票");
			}
		}
	}
}
public class TestMain {

	public static void main(String[] args) {
		Dicket d1 = new Dicket("第1条线程开始：");
		Dicket d2 = new Dicket("第2条线程：");
		d1.start();
		d2.start();
//		d1.run();
		System.out.println("输出结束");
	}

}
```

## 创建线程-实现Runnable接口

创建线程的另一种方法是声明Runnable接口的类，该类实现run()方法。然后可以分配该类的实例，在创建Thread时作为一个参数来传递并启动。

Runnable接口应该由那些打算通过某一线程执行其实例的类来实现。类必须定义一个称为run的无参数方法。

```java
Thread(Runnable target){}//Thread创建对象的构造方法里面有一个可以传递实现Runnable接口类的子类
```

通过此方法可以使用多态来，实现多线程操作。

### 实现Runnable接口

第一步：定义类实现Runnable接口

第二步：覆盖Runnable接口中的run方法。（将线程要运行的代码存放在该run方法中）

第三步：通过Thread类建立线程对象。

第四步：将Runnable接口的子类对象作为实际参数传递给Thread类的构造函数。

第五步：调用Thread类的start方法开启线程并调用Runnable接口子类的run方法。

当一个类继承了一个父类，但是有部分代码想要被多线程操作，所以就提供了Runnable接口实现线程性，**避免了java单继承的局限性。在定义线程时，建议使用实现Runnable方式。**![](F:\md笔记文件\javaimg\Runnable接口的特殊.png)

## 两种方式的区别

继承Thread：线程代码存放在Thread子类run方法中

实现Runnable：线程代码存在接口子类的run方法中

## 多线程的运行相关安全问题

问题的原因：当多条语句在操作同一个线程共享数据时，一个线程对多条语句只执行了一部分，还没有执行完，另一个线程参与进来执行，导致共享数据的错误。

解决办法：对多条操作共享数据的语句，只能让一个线程都执行完，在执行过程中，其他线程不可以参与执行。

Java对于多线程的安全问题提供了专业的解决方式。——**同步代码块**

```java
synchronized(对象)//此对象可以使用object类的对象。当作标记位
{
    //需要被同步的代码(哪些语句需要被同步？就是对共享数据进行操作的语句！)
}
```

这个**synchronized**的对象可以理解为锁， 其他线程进入同步代码块会关上锁，其他线程进不来。当在其中的线程执行完同步代码块，才会在开锁，可以让其他线程进入。

持有锁的线程可以在同步中执行，没有持有锁的线程即使获取cpu的执行权，也进不去，因为没有获取锁。

同步的前提：

1. 必须要有两个或者两个以上的线程。
2. 必须是多个线程使用同一个锁。

必须保证同步中只能有一个线程在运行。不能将所有的代码都全部放入同步代码块，要不然的话就成为单线程模式了。

好处：解决了多线程的安全问题。

弊端：多个线程都要判断锁，较为消耗资源。

```java
class ThreadTest implements Runnable{
	private int tick = 100;
	Object obj = new Object();//这个对象是任意的，什么都想都可以。作为一个标记作用
	public void run(){
		while(true){
			synchronized(obj){
				if(tick>0){
					try {
						Thread.sleep(10);
					} catch (InterruptedException e) {
						e.printStackTrace();
					}
					System.out.println(Thread.currentThread().getName()+"卖出了第"+tick--+"张票");
				}
			}
		}
	}
	public static void main(String[] args) {
		ThreadTest t = new ThreadTest();
		Thread t1 = new Thread(t);
		Thread t2 = new Thread(t);
		Thread t3 = new Thread(t);
		t1.start();
		t2.start();
		t3.start();
	}
	
}
```

run方法不能使用throws抛出异常

如何查找安全问题

1. 明确那些代码是多线程运行代码
2. 明确共享数据
3. 明确多线程运行代码中那些是操作共享数据的。

**把synchronized放在方法修饰符上就可以实现同步函数了。**

synchronized得用在同步代码块上，将同步代码块的代码封装在方法上使用synchronized修饰。就是同步函数了

同步函数需要被对象调用，那么函数都有一个所属对象引用，就是this。所以同步函数使用的锁是this

同步函数用的锁是this

如果同步方法被静态修饰，则用的锁是Class。因为静态方法中不可以定义this。

```java
类名.class//该对象的类型是class
```

静态进内存时，内存中没有本类对象，但是一定有该类对应的字节码对象。

当使用多线程访问懒汉式单例模式，需要在静态创建单例模式 里加入synchronized同步代码，解决安全问题。

```java
class Single implements Runnable{

	private static Single s = null;
	private Single(){
		
	}
	public static Single getInstance(){
		if(s==null){
			synchronized(Single.class){
				if(s == null){
					s = new Single();
				}
			}
		}
		return s;
	}
	public void run(){
		System.out.println("启动线程"+Thread.currentThread().getName());
	}
}

//------------------------------------------

public class Main {

	public static void main(String[] args) {
		Single instance = Single.getInstance();
		Thread t1 = new Thread(instance,"a");
		Thread t2 = new Thread(instance,"b");
		Thread t3 = new Thread(instance,"c");
		t1.start();
		t2.start();
		t3.start();
	}

}

```

**并发存在资源竞争，并行不存在竞争。**

## 通过Callable和Future接口创建线程

从JAVA5开始，JAVA提供提供了Callable接口，该接口是Runnable接口的增强版，Callable接口提供了一个call()方法可以作为线程执行体，但call()方法比run()方法功能更强大。

1、call()方法可以有返回值；

2、call()方法可以声明抛出异常；

Callable接口是JAVA新增的接口，而且它不是Runnable接口的子接口，所以Callable对象不能直接作为Thread的target。还有一个原因就是：call()方法有返回值，call()方法不是直接调用，而是作为线程执行体被调用的，所以这里涉及获取call()方法返回值的问题。

JAVA5提供了Future接口来代表Callable接口里call()方法的返回值，并为Future接口提供了一个FutureTask实现类，该类实现了Future接口，并实现了Runnable接口，所以FutureTask可以作为Thread类的target

**1、boolean cancel(boolean mayInterruptIfRunning)：试图取消Future里关联的Callable任务；**

**2、V get()：返回Callable任务里call()方法的返回值，调用该方法将导致程序阻塞，必须等到子线程结束以后才会得到返回值；**

**3、V get(long timeout, TimeUnit unit)：返回Callable任务里call()方法的返回值。该方法让程序最多阻塞timeout和unit指定的时间，如果经过指定时间后，Callable任务依然没有返回值，将会抛出TimeoutException异常；**

**4、boolean isCancelled()：如果Callable任务正常完成前被取消，则返回true；**

**5、boolean isDone()：如果Callable任务已经完成， 则返回true；**

## 死锁

死锁：同步锁里面有同步锁。

```java
class DeadLock implements Runnable {
	private boolean flag;

	DeadLock(boolean flag) {
		this.flag = flag;
	}
	//死锁程序
	public void run(){
		if(flag){
			while(true){
				synchronized(MyLock.locka){
					System.out.println("if locka");
    				//MyLock.locka.wait();解决死锁
					synchronized(MyLock.lockb){
						System.out.println("if lockb");
					}
				}
			}
		}else{
			while(true){
				synchronized(MyLock.lockb){
					System.out.println("else lockb");
					synchronized(MyLock.locka){
						System.out.println("else locka");
                          //MyLock.locka.notifyAll();解决死锁
					}
				}
			}
		}
	}
}
//标记位
class MyLock {
	public static Object locka = new Object();
	public static Object lockb = new Object();
}
//主线程
public class DeadLockTestMain {

	public static void main(String[] args) {
		Thread t1 = new Thread(new DeadLock(true));
		Thread t2 = new Thread(new DeadLock(false));
		t1.start();
		t2.start();
	}

}
```

### 解决死锁

通过wait方法，让当前线程释放锁，并且进入阻塞状态。

再通过notifyAll/notify方法唤醒所有锁。

## 8.5

### 内部类

当某一个类只会被另外一个类使用的时候，可以使用内部类来使用。

#### 成员内部类

```java
public class 外部类名 {

	public int a;
	//成员内部类
	public class 内部类名{}
}
public static void main(String[] args) {
		Student stu = new Student();
		//声明内部类并且创建一个对象
		Student.Address add = stu.new Address();
	}
```



**this.成员属性**：指的是当前调用该方法的对象

**外部类名.this.成员属性**指的是当前内部类所依赖的外部类的对象

成员内部类不能有静态属性，如果设置为静态属性必须加上final修饰。

***ps： 只有成员属性能加权限修饰符，方法体里面的属性不能加权限修饰符。***

#### 局部内部类

```java
//局部内部类
	public void info(){
		int a =10;
		class T{
			public int a = 10;
			public void x(){
				int a = 5;
				System.out.println(a);//拿到x的方法里的a
				System.out.println(this.a);//拿到T里的成员属性a
				//要在这里拿info方法的a成员是拿不到的
			}
		}
		T t = new T();
		t.x();
	}
```

#### 静态内部类

```java
//静态内部类
	public static class School{
		public int a;
		public static String s;
		public final static String t = "school";
		
		public void info(){
			int a = 10;
			System.out.println(a);
			System.out.println(this.a);
			//静态成员无法访问外部的东西
//			System.out.println(Student.this.a);
		}
	}
```

#### **匿名内部类**

```java
//匿名内部类
		A a = new A(){//这是多态创建a对象
			//这是一个实现A接口的子实现类，因为这个类没有名字，所以是匿名内部类
			@Override
			public void a() {
				System.out.println("aaaaa");
			}
		};
		a.a();


int i =10;
		Student stu = new Student();
		stu.s(new A(){
			@Override
			public void a() {
				//可以直接获取i的值
				System.out.println(i);
				System.out.println("ssssssssssssss");
			}
		});
```

```java
public interface A {
	public void a();
}
public class Student {
	public void s(A a){
		
	}
}
```

匿名neibulei如果要用到外部的成员，必须得是常量。

### Lambda表达式

**匿名内部类和对象以及Lambda表达式创建线程的区别**

```java
Thread t1 = new Thread(new Run());
		t1.start();
		
		new Thread(new Runnable(){
			@Override
			public void run() {
				System.out.println(Thread.currentThread().getName()+"在匿名内部类中创建了一个新的线程！！！");
			}
		}).start();
//无参无返回值Lambda
		new Thread(()->{
			System.out.println(Thread.currentThread().getName()+"使用Lambda表达式创建了一个新的线程");
		}).start();
```

![](F:\md笔记文件\javaimg\Lambda表达式.png)

```java
//Lambda表达式（带参带返回值）
		Arrays.sort(p,(Person o1,Person o2)->{
			return o1.getAge()-o2.getAge();
		});
```



### 线程池

**Java中的线程池是运用场景最多的并发框架，几乎所有需要异步或并行执行的程序都可以使用线程池。**

【强制】创建线程或线程池时请指定有意义的线程名称，方便出错时回溯。

【强制】线程资源必须通过线程池提供，不允许在应用中自行显式创建线程。
说明： 使用线程池的好处是减少在创建和销毁线程上所花的时间以及系统资源的开销，解决资
源不足的问题。如果不使用线程池，有可能造成系统创建大量同类线程而导致消耗完内存或者
“过度切换”的问题。

【强制】线程池不允许使用 Executors 去创建，而是通过 ThreadPoolExecutor 的方式，这样
的处理方式让写的同学更加明确线程池的运行规则，规避资源耗尽的风险。
说明： Executors 返回的线程池对象的弊端如下：
1） FixedThreadPool 和 SingleThreadPool:
允许的请求队列长度为 Integer.MAX_VALUE，可能会堆积大量的请求，从而导致 OOM。
2） CachedThreadPool 和 ScheduledThreadPool:
允许的创建线程数量为 Integer.MAX_VALUE， 可能会创建大量的线程，从而导致 OOM。

#### 好处：

1. 降低资源消耗，通过重复利用机制已降低线程创建和销毁造成的消耗。
2. 提高响应速度，当任务到达时，任务可以不需要等到线程创建就能立即执行。
3. 提高线程的可管理性。线程是稀缺资源，如果无限制的创建，不仅会消耗系统资源，还会降低系统的稳定性，使用线程池可以统一分配、调优和监控。

**线程池的作用：**线程池是为突然大量爆发的线程设计的，通过有限的几个固定线程为大量的操作服务，减少了创建和销毁线程所需的时间，从而提高了效率。

如果一个线程的时间非常长，就没必要用线程池了，（不是不能做长时间操作，而是不宜。）况且还不能控制线程池中线程的开始，挂起，和中止。



#### **线程池的分类**

**ThreadPoolExecutor**

| 参数            | 说明                                                         |
| --------------- | ------------------------------------------------------------ |
| corePoolSize    | 核心线程数量，线程池维护线程的最少数量                       |
| maximumPoolSize | 线程池维护线程的最大数量                                     |
| keepAliveTime   | 线程池除核心线程外的其他线程的最长空闲时间，超过该时间的空闲线程会被销毁 |
| unit            | keepAliveTime的单位，TimeUnit中的几个静态属性：NANOSECONDS、MICROSECONDS、MILLISECONDS、SECONDS |
| workQueue       | 线程池所使用的任务缓冲队列                                   |
| threadFactory   | 线程工厂，用于创建线程，一般用默认的即可                     |
| handler         | 线程池对拒绝任务的处理策略                                   |

##### 1.corePoolSize

  线程池核心线程数，默认情况下，核心线程会在线程池中一直存活，即使它们处于闲置状态。如果ThreadPoolExecutor的allowCoreThreadTimeOut属性设置为true,那么闲置的核心线程在等待新任务到来时会有超时策略，这个时间间隔由keepAliveTime所指定的时长后，核心线程就会被终止。

##### 2.maximumPoolSize

线程池所能容纳的最大线程数，当活动线程达到这个数值后，后续的新任务将被阻塞。

##### 3.keepAliveTime

非核心线程闲置时的超时时长，超过这个时长，非核心线程就会被回收。当ThreadPoolExecutor的allowCoreThreadTimeOut属性设置为true时，keepAliveTime同样会作用于非核心线程。

##### 4.unit

keepAliveTime 参数的时间单位。

##### 5.workQueue

执行前用于保持任务的队列。此队列仅保持由 execute 方法提交的 Runnable 任务。

当线程池任务处理不过来的时候，可以***通过handler指定的策略进行处理，ThreadPoolExecutor提供了四种策略***：

1. ThreadPoolExecutor.AbortPolicy:丢弃任务并抛出RejectedExecutionException异常；也是默认的处理方式。
2. ThreadPoolExecutor.DiscardPolicy：丢弃任务，但是不抛出异常。
3. ThreadPoolExecutor.DiscardOldestPolicy：丢弃队列最前面的任务，然后重新尝试执行任务（重复此过程）
4. ThreadPoolExecutor.CallerRunsPolicy：由调用线程处理该任务

可以通过实现RejectedExecutionHandler接口自定义处理方式。

#### 添加执行任务

- submit() 该方法返回一个Future对象，可执行带返回值的线程；或者执行想随时可以取消的线程。Future对象的get()方法获取返回值。Future对象的cancel(true/false)取消任务，未开始或已完成返回false，参数表示是否中断执行中的线程
- execute() 没有返回值。

#### **线程池任务提交过程**

![](F:\md笔记文件\javaimg\线程池任务提交过程.png)

1. 如果此时线程池中的数量小于corePoolSize，即使线程池中的线程都处于空闲状态，也要创建新的线程来处理被添加的任务。
2. 如果此时线程池中的数量等于corePoolSize，但是缓冲队列workQueue未满，那么任务被放入缓冲队列。
3. 如果此时线程池中的数量大于等于corePoolSize，缓冲队列workQueue满，并且线程池中的数量小于maximumPoolSize，建新的线程来处理被添加的任务。
4. 如果此时线程池中的数量大于corePoolSize，缓冲队列workQueue满，并且线程池中的数量等于maximumPoolSize，那么通过 handler所指定的策略来处理此任务。
5. 当线程池中的线程数量大于 corePoolSize时，如果某线程空闲时间超过keepAliveTime，线程将被终止。这样，线程池可以动态的调整池中的线程数。

总结即：处理任务判断的优先级为 核心线程corePoolSize、任务队列workQueue、最大线程maximumPoolSize，如果三者都满了，使用handler处理被拒绝的任务。

**注意：**

1. 当workQueue使用的是无界限队列时，maximumPoolSize参数就变的无意义了，比如new LinkedBlockingQueue(),或者new ArrayBlockingQueue(Integer.MAX_VALUE);
2. 使用SynchronousQueue队列时由于该队列没有容量的特性，所以不会对任务进行排队，如果线程池中没有空闲线程，会立即创建一个新线程来接收这个任务。maximumPoolSize要设置大一点。
3. 核心线程和最大线程数量相等时keepAliveTime无作用.

#### 线程池关闭

1. shutdown() 不接收新任务,会处理已添加任务
2. shutdownNow() 不接受新任务,不处理已添加任务,中断正在处理的任务

#### 常用队列介绍

1. ArrayBlockingQueue： 这是一个由数组实现的容量固定的有界阻塞队列.
2. SynchronousQueue： 没有容量，不能缓存数据；每个put必须等待一个take; offer()的时候如果没有另一个线程在poll()或者take()的话返回false。
3. LinkedBlockingQueue： 这是一个由单链表实现的默认无界的阻塞队列。LinkedBlockingQueue提供了一个可选有界的构造函数，而在未指明容量时，容量默认为Integer.MAX_VALUE。

| 方法    | 说明                                                   |
| ------- | ------------------------------------------------------ |
| add     | 增加一个元索; 如果队列已满，则抛出一个异常             |
| remove  | 移除并返回队列头部的元素; 如果队列为空，则抛出一个异常 |
| offer   | 添加一个元素并返回true; 如果队列已满，则返回false      |
| poll    | 移除并返回队列头部的元素; 如果队列为空，则返回null     |
| put     | 添加一个元素; 如果队列满，则阻塞                       |
| take    | 移除并返回队列头部的元素; 如果队列为空，则阻塞         |
| element | 返回队列头部的元素; 如果队列为空，则抛出一个异常       |
| peek    | 返回队列头部的元素; 如果队列为空，则返回null           |

#### 线程池的四种创建方式

Java通过Executors（jdk1.5并发包）提供四种线程池，分别为：

**newCachedThreadPool**创建一个**可缓存线程池**，如果线程池长度超过处理需要，可灵活回收空闲线程，若无可回收，则新建线程。

```java
// 无限大小线程池 jvm自动回收
		ExecutorService newCachedThreadPool = Executors.newCachedThreadPool();
		for (int i = 0; i < 10; i++) {
			final int temp = i;
			newCachedThreadPool.execute(new Runnable() {
				@Override
				public void run() {
					try {
						Thread.sleep(100);
					} catch (Exception e) {
					}
					System.out.println(Thread.currentThread().getName() + ",i:" + temp);
				}
			});
		}
```

***总结:线程池为无限大，当执行第二个任务时第一个任务已经完成，会复用执行第一个任务的线程，而不用每次新建线程。***

**newFixedThreadPool** 创建一个**定长线程池**，可控制线程最大并发数，超出的线程会在队列中等待。

```java
ExecutorService newFixedThreadPool = Executors.newFixedThreadPool(5);
		for (int i = 0; i < 10; i++) {
			final int temp = i;
			newFixedThreadPool.execute(new Runnable() {
				@Override
				public void run() {
					System.out.println(Thread.currentThread().getId() + ",i:" + temp);
				}
			});
		}
```

***定长线程池的大小最好根据系统资源进行设置。如Runtime.getRuntime().availableProcessors()***

**newScheduledThreadPool** 创建一个**定长线程池**，支持定时及周期性任务执行。

```java
		ScheduledExecutorService newScheduledThreadPool = Executors.newScheduledThreadPool(5);
		for (int i = 0; i < 10; i++) {
			final int temp = i;
			newScheduledThreadPool.schedule(new Runnable() {
				public void run() {
					System.out.println("i:" + temp);
				}
			}, 3, TimeUnit.SECONDS);//表示延遲三秒執行
		}
```

**newSingleThreadExecutor** 创建一个**单线程化的线程池**，它只会用唯一的工作线程来执行任务，保证所有任务按照指定顺序(FIFO, LIFO, 优先级)执行。

```java
ExecutorService newSingleThreadExecutor = Executors.newSingleThreadExecutor();
		for (int i = 0; i < 10; i++) {
			final int index = i;
			newSingleThreadExecutor.execute(new Runnable() {
				@Override
				public void run() {
					System.out.println("index:" + index);
					try {
						Thread.sleep(200);
					} catch (Exception e) {
					}
				}
			});
		}
```

注意：结果依次输出，相当于顺序执行各个任务。

**线程池提交任务时的执行顺序如下：**

向线程池提交任务时，会首先判断线程池中的线程数是否大于设置的核心线程数，如果不大于，就创建一个核心线程来执行任务。

如果大于核心线程数，就会判断缓冲队列是否满了，如果没有满，则放入队列，等待线程空闲时执行任务。
如果队列已经满了，则判断是否达到了线程池设置的最大线程数，如果没有达到，就创建新线程来执行任务。
如果已经达到了最大线程数，则执行指定的拒绝策略。这里需要注意队列的判断与最大线程数判断的顺序。

## 8.6

### 反射

通过获取类的完整结构，从而创建对象调用方法。

```java
Student stu = new Student();
		//获取类的完整结构
		Class class1 = stu.getClass();
		//获取类的完整结构
		Class class2 = Student.class;
		//获取类的完整结构，
		Class c3 = Class.forName("com.classs.test1.Student");
		Object inse = c3.newInstance();//创建对象
		//获取类的完整结构，从而创建对象调用方法。
```

Field：属性

```java
//非私有属性获取
Field field = c3.getField("classmate");//通过名字获取属性
		String name = field.getName();//获取属性名
		String string = Modifier.toString(field.getModifiers());//返回属性的修饰符
		Class type = field.getType();//返回属性的类型
			
		System.out.println(field);
		System.out.println(string);
```

```java
//通过指定名字获取本类所有属性[包括私有]
		Field declaredField = c3.getDeclaredField("classmate");
		System.out.println(declaredField);
		//获取本类所有属性
		Field[] declaredFields = c3.getDeclaredFields();
		for (Field field : declaredFields) {
			System.out.println(field);
		}
```

```java
//获取方法
Class forName = Class.forName("com.classs.test1.Student");
		Object newInstance = forName.newInstance();
		Method method = forName.getMethod("setAge", int.class);
		Method m = null;
		Method[] declaredMethods = forName.getDeclaredMethods();
		for (Method method2 : declaredMethods) {
			String name = method2.getName();
			if("setAge".equals(name)){
				m = method2;
				break;
			}
		}
		Object invoke = m.invoke(newInstance, 20);
		System.out.println(((Student)newInstance).getAge());

```

```java
//获取无参构造方法
		Constructor declaredConstructor = c3.getDeclaredConstructor();
		//获取有参构造方法
		Constructor declaredConstructor2 = c3.getDeclaredConstructor(String.class,String.class,int.class);
		//无参构造对象
		Object newInstance = declaredConstructor.newInstance();
		//有参构造方法
		Object newInstance2 = declaredConstructor2.newInstance("aaa","1001",20);
		System.out.println(newInstance.getClass());
		System.out.println(newInstance2);
```

```java
		//获取内部类
		Class[] declaredClasses = c3.getDeclaredClasses();
		for (Class class1 : declaredClasses) {
			System.out.println(class1.getSimpleName());
		}

		//获取父类
		Class superclass = c3.getSuperclass();
		System.out.println(superclass);

		//获取父接口
		Class[] interfaces = c3.getInterfaces();
		for (Class class1 : interfaces) {
			System.out.println(class1.isInterface());
			System.out.println(class1);
		}
		//获取包名
		Package package1 = forName.getPackage();
```

### XML 可扩展标记语言

html为超文本标记语言，xml为可扩展标记语言。

html的标记已经定死了，xml可变。

XML的设计宗旨是传输数据，而非显示数据

XML标签没有被预定义，您需要自行定义标签

XML被设计为具有自我描述性。

XML不会做任何事情，XML被设计用来结构化，存储以及传输信息。

XML仅是纯文本

XML文档形成一种树结构。

### XML语法

所有XML元素都必须有关闭标签；

XML标签对大小写敏感

XML必须正确嵌套

XML必须有根元素

XML属性值必须加上双引号。

### DTD

DTD可定义XML文档构建模块，它使用一系列合法的元素来定义文档的结构。

```xml
<!DOCTYPE 根元素[
	<!ELEMENT 根元素(子级元素)>
	<!ELEMENT 子级元素(子级的子级元素)>
]>
```

```xml-dtd
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE students [
	<!ELEMENT students (student*) >
	<!ELEMENT student (id,name,age,address) >
	<!ELEMENT address (province,city,county) >
	<!ELEMENT id (#PCDATA) >
]>

<students>
	<student>
		<id>1001</id>
		<name></name>
		<age></age>
		<address>
			<province></province>
			<city></city>
			<county></county>
		</address>
	</student>
</students>
```

## 8.7

### json

json：一种数据的传输格式【将对象转字符串】

Object<-->String

**通过tojson方法可以进行转换Object-->String。**

**通过fromjson方法可以将String-->Object。**

Array<-->String

通过tojson方法可以进行转换Array-->String。

```java
ArrayList<String> fromjson = g.from(str, new TypeToken<ArrayList<String>>(){}.getType());
```

Collection<-->String

Map<-->String



如果是json解析的字符串输出会有双引号。直接输出字符串没有双引号。基本数据类型则不会有双引号。**在json格式中，字符串[包括字符]有双引号，基本数据类型没有。**如果是null则不写。Object是大括号包起来。

如果使数组就会在最外层为中括号。

## 8.10

### 泛型

泛型只起编译器作用，不起运行期作用。

在集合中定义了某个泛型类型后，这个集合只能装这个泛型的元素，其他元素会报错。

泛型的使用方式有三种：**泛型类，泛型接口，泛型方法**。泛型的声明：一般用单个大写字母来声明。无特殊意义，也无确定指向某种类型，但在其他地方规定了是什么类型后，就会只允许那种类型的使用。

#### 泛型类：

在实例化泛型类时，必须指明泛型类的泛型的具体类型。

泛型的类型参数只能是类类型（包括自定义类），不能是基本类型。定义的泛型类不一定是要传入泛型类型实参。

#### 泛型接口：

泛型接口与泛型类的定义及使用基本相同，泛型接口常被用在各种类的生产

未传入泛型实参，与泛型类的定义相同，在声明类的时候，需要将泛型的声明也一起加到类中。

#### 泛型方法：

泛型方法是在调用方法的时候指明泛型的具体类型。

泛型放在返回值类型前面，在修饰符后面。

泛型方法里的泛型和泛型类里的泛型不一样，不指代同一事物。

```java
//泛型方法的声明
public <T> void pro(Object obj){
	//数据处理
}
```

静态方法无法访问泛型类上的泛型

### 泛型通配符

同一种泛型可以对应多种版本，不同版本的泛型实例是不兼容的。

```java
<? extends 父类>//可以是父类或者父类的子类，的泛型写法。
<? super 子类>//泛型，一定是子类的父类。
```

在实例化时一定要明确指定某个类型。

### Lambda表达式

Lambda时匿名函数

接口中只有一个抽象方法的接口，称为**函数式接口**，可以用**@FunctionalInterface**注解来修饰。

(参数列表，对应的是接口中对应的抽象方法的参数列表) -> {对抽象方法的实现}

```java
Thread t = new Thread(new Runnable(){
system.out.println("Hello,World!!!");
})
//如果打括号里面语句只有一行，可以简写成如下表达式的模样。
Thread t = new Thread(()->system.out.println("Hello World!!"));
```

Java四大内置核心函数式接口

```java
Consumer<T> : 消费型接口（无返回值，有去无回）
         void accept(T t);
 Supplier<T> : 供给型接口
         T get();
         
 Function<T,R> : 函数型接口
        R apply(T t);
        
 Predicate<T> : 断言型接口
        boolean test(T t);
```

### 方法引用

![](F:\md笔记文件\javaimg\方法引用.png)

## 8.11

### Stream

Stream是java8中处理集合的关键抽象概念。

Stream API给操作集合带来了强大的功用，更简单易上手。

创建Stream

从一个数据源，如集合，数组中获取。

使用完得关闭Stream。

filter：过滤

Stream流不能有多个终止操作，（类似：forEach，count等等）

#### Stream中间操作：

filter：接受lambda，从流中排除某些操作。

limit(n)：截断流，使其元素不超过给定元素。(只要前n个元素)

sklp(n)：跳过元素，返回一个扔掉了前n个元素的流，若流中元素不足n个则返回一个空流。与limit(n)互补

distinct：筛选，tongguo流所生成元素的hashCode()和equals()去除重复元素。

##### 映射

map--接收Lambda，将元素转换成其他形式或提取信息。接收一个函数作为参数，该函数会被应用到每个元素上，并将其映射成一个新的元素。

![](F:\md笔记文件\javaimg\map&flatMap.png)

map在接收到流后，直接将Stream放入到一个Stream中，最终整体返回一个包含了多个Stream的Stream。

flatMap--接收一个函数作为参数，将流中的每个值都换成另一个流，然后把所有流连接成一个流

![](F:\md笔记文件\javaimg\map&flatMap2.png)

flatMap在接收到Stream后，会将接收到的Stream中的每个元素取出来放入一个Stream中，最后将一个包含多个元素的Stream返回

##### 排序

- sorted()--自然排序（Comparable）
- sorted（Comparator com）--定制排序（Comparator）

#### 终止操作--查找与匹配

· allMatch--检查是否匹配所有元素

· anyMatch--检查是否至少匹配一个元素

· noneMatch--检查是否没有匹配所有元素

· findFirst--返回第一个元素

· findAny--返回当前流中的任意元素

· count--返回流中元素的总个数

· max--返回流中最大值

· min--返回流中最小值

#### 收集

list和Stream可以互相转换。

## **注意**

**：方法里面不能new对象**

## 写在后面的补充：

### 并发程序

- 原子性：即一个操作或者多个操作 要么全部执行并且执行的过程不会被任何因素打断，要么就都不执行。
- 可见性：是指当多个线程访问同一个变量时，一个线程修改了这个变量的值，其他线程能够立即看得到修改的值。
- 有序性：即程序执行的顺序按照代码的先后顺序执行。

#### 指令重排序

指令重排序：一般来说，处理器为了提高程序运行效率，可能会对输入代码进行优化，它不保证程序中各个语句的执行先后顺序同代码中的顺序一致，但是它会保证程序最终执行结果和代码顺序执行的结果是一致的。

处理器在进行重排序时是会考虑指令之间的数据依赖性，如果一个指令Instruction 2必须用到Instruction 1的结果，那么处理器会保证Instruction 1会在Instruction 2之前执行。
**虽然重排序不会影响单个线程内程序执行的结果，但是多线程则会产生影响了**

并发程序正确地执行，必须要保证原子性、可见性以及有序性。

在Java里面，可以通过**volatile**关键字来保证一定的“有序性”（具体原理在下一节讲述）。另外可以通过synchronized和Lock来保证有序性，很显然，synchronized和Lock保证每个时刻是有一个线程执行同步代码，相当于是让线程顺序执行同步代码，自然就保证了有序性。

　　另外，**Java内存模型具备一些先天的“有序性”，即不需要通过任何手段就能够得到保证的有序性，这个通常也称为 happens-before 原则。如果两个操作的执行次序无法从happens-before原则推导出来，那么它们就不能保证它们的有序性，虚拟机可以随意地对它们进行重排序。**

#### happens-before原则（先行发生原则）：

- 程序次序规则：一个线程内，按照代码顺序，书写在前面的操作先行发生于书写在后面的操作
- 锁定规则：一个unLock操作先行发生于后面对同一个锁额lock操作
- volatile变量规则：对一个变量的写操作先行发生于后面对这个变量的读操作
- 传递规则：如果操作A先行发生于操作B，而操作B又先行发生于操作C，则可以得出操作A先行发生于操作C
- 线程启动规则：Thread对象的start()方法先行发生于此线程的每个一个动作
- 线程中断规则：对线程interrupt()方法的调用先行发生于被中断线程的代码检测到中断事件的发生
- 线程终结规则：线程中所有的操作都先行发生于线程的终止检测，我们可以通过Thread.join()方法结束、Thread.isAlive()的返回值手段检测到线程已经终止执行
- 对象终结规则：一个对象的初始化完成先行发生于他的finalize()方法的开始

### volatile

**volatile关键字的两层语义**

　　一旦一个共享变量（类的成员变量、类的静态成员变量）被volatile修饰之后，那么就具备了两层语义：

　　1）保证了不同线程对这个变量进行操作时的可见性，即一个线程修改了某个变量的值，这新值对其他线程来说是立即可见的。

　　2）禁止进行指令重排序。

volatile关键字禁止指令重排序有两层意思：

　　1）当程序执行到volatile变量的读操作或者写操作时，在其前面的操作的更改肯定全部已经进行，且结果已经对后面的操作可见；在其后面的操作肯定还没有进行；

　　2）在进行指令优化时，不能将在对volatile变量访问的语句放在其后面执行，也不能把volatile变量后面的语句放到其前面执行。

​		第一：使用volatile关键字会强制将修改的值立即写入主存；

　　第二：使用volatile关键字的话，当线程2进行修改时，会导致线程1的工作内存中缓存变量stop的缓存行无效（反映到硬件层的话，就是CPU的L1或者L2缓存中对应的缓存行无效）；

　　第三：由于线程1的工作内存中缓存变量stop的缓存行无效，所以线程1再次读取变量stop的值时会去主存读取。

　　那么在线程2修改stop值时（当然这里包括2个操作，修改线程2工作内存中的值，然后将修改后的值写入内存），会使得线程1的工作内存中缓存变量stop的缓存行无效，然后线程1读取时，发现自己的缓存行无效，它会等待缓存行对应的主存地址被更新之后，然后去对应的主存读取最新的值。

**使用volatile必须具备以下2个条件：**

　　1）对变量的写操作不依赖于当前值

　　2）该变量没有包含在具有其他变量的不变式中

## 策略模式

```java
//非策略模式代码
public void Share{
public void shareOptions(String option){
       if(option.equals("微博")){
           //function1();
           //...
      }else if(option.equals("微信")){
           //function2();
           //...
      }else if(option.equals("朋友圈")){
           //function3();
           //...
      }else if(option.equals("QQ")){
           //function4();
           //...
      }1
       //...
}
```

- [ ] 用于优化 if...else的模式使用起来非常优秀，而且省代码，后期优化非常方便。

```java
//定义策略接口
public interface DealStrategy{
   void dealMythod(String option);
}

//定义具体的策略1
public class DealSina implements DealStrategy{
   @override
   public void dealMythod(String option){
       //...
  }
}

//定义具体的策略2
public class DealWeChat implements DealStrategy{
   @override
   public void dealMythod(String option){
       //...
  }
}

//定义上下文，负责使用DealStrategy角色
public static class DealContext{
   private String type;
   private DealStrategy deal;
   public  DealContext(String type,DealStrategy deal){
       this.type = type;
       this.deal = deal;
   }
   public DealStrategy getDeal(){
       return deal;
   }
   public boolean options(String type){
       return this.type.equals(type);
   }
}

```

```java
public void Share{
   private static List<DealContext> algs = new ArrayList();
   //静态代码块,先加载所有的策略
   static {
       algs.add(new DealContext("Sina",new DealSina()));
       algs.add(new DealContext("WeChat",new DealWeChat()));
  }
public void shareOptions(String type){
       DealStrategy dealStrategy = null;
       for (DealContext deal : algs) {
           if (deal.options(type)) {
               dealStrategy = deal.getDeal();
               break;
          }  
      }
       dealStrategy.dealMythod(type);
  }
}
```

