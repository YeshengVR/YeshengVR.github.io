# java笔试面试题

## static

### 1.静态变量和实例变量的区别

静态变量也称作类变量，由static修饰，只能通过类来访问。实例变量没有static修饰符，只能通过实例对象来访问。

同一类的不同实例对象有自己的实例变量，但是他们共享同一个静态变量。当一个实例对象改变了它的实例变量时，并不会影响其他的实例对象。而一个实例对象如果修改了静态变量，则会影响其他的对象实例。

再java中类的静态变量在内存中只有一个，Java虚拟机在加载类的过程中为静态变量分配内存，静态变量位于方法区，被类的的所有实例共享。静态变量可以直接通过类名进行访问，其生命周期取决于类的生命周期。

而实例变量取决于类的实例，每创建一个实例，Java虚拟机就会为实例变量分配一次内存，实例变量位于堆区中，其生命周期取决于实例的生命周期。

### 2.是否可以从一个static方法内部发出对非static方法的调用？

不可以，如果静态方法内部包含对象的非静态方法的调用则不能保证对象初始化，所以不能在静态的方法里调用非静态的方法。

## java基础

### 1.描述一下JVM加载CLASS文件的原理机制？

JVM中类的装载是由ClassLoader和它的子类来实现的，JavaClassLoader是一个重要的Java运行时系统组件。它负责在运行时查找和装入类文件的类。

### 2.一个“.java”源文件中是否可以包括多个类（不是内部类）？有什么限制？

可以，必须只有一个类名与文件名相同。public的类必须和文件名相同，并且一个.java的源文件只能有一个公有的类。

### 3.javaGC流程

JavaGC机制，垃圾回收机制是Java与C++/C的主要区别之一。Java开发者一般不需要专门编写内存回收和垃圾清理代码，对内存泄露和溢出的问题，Java虚拟机中存在自动内存管理和垃圾清扫机制。该机制对JVM的内存进行标记，并确定那些内存需要回收，永不停息的自动回收内存，保证jvm中的内存空间。

GC机制的基本算法是：分代收集

方法区（永久代）：

　　永久代的回收有两种：常量池中的常量，无用的类信息，常量的回收很简单，没有引用了就可以被回收。对于无用的类进行回收，必须保证3点：

1. 类的所有实例都已经被回收
2. 加载类的ClassLoader已经被回收
3. 类对象的Class对象没有被引用（即没有通过反射引用该类的地方）

   永久代的回收并不是必须的，可以通过参数来设置是否对类进行回收。

## 运算符

### 1.&和&&的区别？

&是位运算符，表示按位与运算，&&是逻辑运算符，表示逻辑与（and）。是用&运算符进行判断比较时，如果第一个已经判断为不符合要求，他还是会继续判断&语句之后的判断语句。而&&运算符进行判断时，如果第一个判断已经为不符合要求，则不会继续惊醒判断，节省运行时间。

### 2.怎么样最有效率的方法算出2乘以几等于16？

2<<3

### 3.简述逻辑操作（&，|，^）与条件操作（&&，||）的区别。

区别主要答两点：

1. 条件操作只能操作布尔型的，而逻辑操作不仅可以操作布尔型的，还可以操作数值型。
2. 逻辑操作不会产生短路。

## 循环结构

### 1.在JAVA中，如何跳出当前的多重嵌套循环？

用break; return方法。

## 逻辑结构

### 1.Switch能否作用在Byte上，是否能作用在long上，是否能作用在String上？

switch(expr1)中，expr1是一个整数表达式。因此传递给switch和case语句的参数应该是int，short，char或者byte。long，String都不能做用于switch。

switch的运行效率比起if else效率更高。

## Math函数

### 1.Math.round(11.5)，Math.round(-11.5)等于多少？

Math.round(11.5) == 12

Math.round(-11.5) == -11

round方法返回与参数最接近的长整数，参数加1/2后求其floor。

## String函数

### 1.String是基本的数据类型嘛？

基本数据类型包括byte、short、int、long、float、double、char、boolean。

String不属于基本数据类型，它是一个对象，默认值为null，String类型是final的，因此是不可以继承这个类，不可以修改这个类。为了提高效率节省空间应该使用StringBuffer类。

### 2.String s = new String(“XYZ”);创建了几个String Object？

两个，String里面又是一个字符串。

### 3.数组有没有length()这个方法？String有没有length()这个方法?

数组有length属性，没有length方法。String有length()方法。

### 4.String 和 StringBuffer,StringBuilder的区别？

Java平台提供了两个类，String和StringBuffer，他们可以存储和操作字符串，既包含多个字符的字符数据。这个String类提供了数组不可改变的字符串。而这个String Buffer类提供的字符串进行修改。当你知道字符数据要改变的时候你就可以使用StringBuffer。可以使用StringBuffer来动态构造字符数据。StringBuffer线程是安全的，StringBulider是单线程使用的，相对效率高些。

### 5.是否可以继承String类？

String类是final类故不可以继承。

## 基本数据类型

### 1.short s1 = 1; s1 = s1+1;有什么错？short s1 = 1; s1+=1;有什么错？

short s1 = 1; s1 = s1+1;(s1+1运算结果是int型，需要强制转换类型)                 short s1 = 1; s1 += 1;(可以正确编译)

### 2.int 和Integer有什么区别？

java提供两种不同的类型：引用类型，和原始类型（或内置类型）。int是java的原始数据类型，Integer是java为int提供的封装类。Java为每个原始类型提供了封装类。

原始类型封装类如：boolean Boolean，char Character，byte Byte，short Short, int Integer, long Long, float Float,  double Double.引用类型和原始类型的行为完全不同，具有不同的语义。当引用数据类型和原始类型用作某个类的实例数据时所指定的缺省值为null，而原始类型实例变量的缺省值与他们的类型有关。

### 3.char型变量中能不能存储一个中文汉字？为什么？

能够定义成为一个中文的，因为java中以unicode编码，一个char占16个字节，所以放一个中文是没有问题的，一个汉字两个字节。 

## 数据结构

### HEAP 和STACK有什么区别。

栈是后进先出的线性表结构，存取速度比堆快。创建对象的时候new一个对象，引用存在栈上具体的内容存在堆上.

栈与堆都是Java用来在RAM中存放数据的地方，与C++不同，JAVA自动管理栈和堆，程序员不能直接的设置栈和堆。

JAVA的堆是一个运行时数据区，类的对象从中分配空间。这些对象通过new指令建立，他们不需要程序代码来显示的释放，堆是由垃圾回收来负责的，堆的优势是可以动态的分配内存大小，生存期也不必事先告诉编译器，因为他是在运行时动态分配内存的，Java的垃圾收集器会自动收走这些不再使用的数据，但缺点是，由于要在运行时动态分配内存，存取速度较慢。

栈的优势是：存取速度比堆快，仅次于寄存器，栈数据可以共享。但是缺点是，存在栈中的数据大小与生存期必须是确定的，缺乏灵活性。栈中主要存放一些基本类型的变量（int,short,long,byte,float,double,char,boolean）的对象句柄。

**只有通过new()方法才能保证每次都创建一个新的对象。** 

> String str1 = "abc"; 
>
> String str2 = "abc"; 
>
> System.out.println(str1==str2); //true 
>
> 可以看出str1和str2是指向同一个对象的。 
>
> String str1 =new String ("abc"); 
>
> String str2 =new String ("abc"); 
>
> System.out.println(str1==str2); // false 
>
> 用new的方式是生成不同的对象。每一次生成一个。 
>
> 因此用第一种方式创建多个”abc”字符串,在内存中其实只存在一个对象而已. 这种写法有利与节省内存空间. 同时它可以在一定程度上提高程序的运行速度，因为JVM会自动根据栈中数据的实际情况来决定是否有必要创建新对象。而对于String str = new String("abc")；的代码，则一概在堆中创建新对象，而不管其字符串值是否相等，是否有必要创建新对象，从而加重了程序的负担。 
>
> 另一方面, 要注意: 我们在使用诸如String str = "abc"；的格式定义类时，总是想当然地认为，创建了String类的对象str。担心陷阱！对象可能并没有被创建！而可能只是指向一个先前已经创建的对象。只有通过new()方法才能保证每次都创建一个新的对象。 

#### 申请后系统的响应：

**栈**：只要栈的剩余空间大于所申请空间，系统将为程序提供内存，否则将报异常提示栈溢出。

**堆**：首先应该知道操作系统有一个记录空闲内存地址的链表，当系统收到程序的申请时，会遍历该链表，寻找第一个空间大于所申请空间的堆结点，然后将该结点从空闲节点链表中删除，并将该节点的空间分配给程序，另外，对于大多数系统，会在这块内存空间中的首地址处记录本次分配的大小，这样代码中的delete语句才能正确的释放本内存空间。另外，由于找到的堆结点的大小不一定正好等于申请的大小，系统会自动的将多余的那部分重新放入空闲链表中。

#### 申请大小的限制

**栈**：在windows下，**栈是向低地址扩展的数据结构**，是**一块连续的内存的区域**。这句话的意思是栈顶的地址和栈的最大容量是系统预先规定好的，在WINDOWS下，栈的大小是2M（也可能是1M，他是一个编译时就确定的常数），**如果申请的空间超过栈的剩余空间时，将提示overflow**。因此，能从栈获得的空间较小。

**堆**：堆是**向高地址扩展的数据结构**，是**不连续的内存区域**。这是由于系统是用链表来存储的空间内存地址的，自然是不连续的，而链表的遍历方向是由低地址向高地址。**堆的大小受限于计算机系统中有效的虚拟内存**，由此可见，堆获得的空间比较灵活，也比较大。

#### 申请效率的比较

**栈**是由系统自动分配，速度较快。但程序员是无法控制的。

**堆**是由new分配的内存，一般速度比较慢，而且容易产生内存碎片，不过用起来最方便。

另外在WINDOWS下，最好的方式是用VirtualAlloc分配内存，他不是在堆，也不是在栈是直接在进程的地址空间中保留一块内存，虽然用起来最不方便，但是速度快，也最灵活。

#### 堆和栈中的存储内容

**栈**：在函数调用时，第一个进栈的是主函数中后的下一条指令（函数调用语句的下一条可执行语句）的地址，然后是函数的各个参数，在大多数的C编译器中，参数是由右往左入栈的，然后是函数中的局部变量。注意*静态变量是不入栈的*。当**本次函数调用结束后，局部变量先出栈，然后是参数，最后栈顶指针指向最开始存的地址**，也就是主函数的下一条指令，程序由该点继续运行。

**栈**：一般是在堆的头部用一个字节存放堆的大小，堆中的具体内容有程序员安排。

#### 存取效率的比较

存取效率的比较char s1[] = "aaaaaaaaaaa"; char *s2 = "bbbbbbbbbbb";  aaaaaaaaaaa是在运行时刻赋值的；而bbbbbbbbbbb是在编译时就确定的；但是，在以后的存取中，在栈上的数组比指针所指向的字符串(例如堆)快。 

## Object类

### 写CLONE()方法时，通常都有一行代码，是什么？

Clone有缺省行为，**super.clone();**她负责产生正确大小的空间，并逐位复制。

