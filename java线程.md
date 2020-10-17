# 线程

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

### 阻塞状态

阻塞状态/临时状态：具备运行资格，但没有执行权。

### 冻结状态

冻结状态：当一个线程碰到了sleep、wait 进入冻结状态，此状态放弃了执行资格。

没执行资格是冻结状态，有执行资格但没有执行权的就是临时状态，既有资格又有执行权就叫运行状态。

## 多线程获取线程对象以及名称

线程都有自己默认的名称，Thread-编号，该编号从0开始。

可以通过getName()方法获取线程名称。

```java
Thread.currentThread()//返回对当前正在执行的线程对象的引用。因为是静态方法用类名.方法名就ok
Thread.currentThread().getName()//使用此方法获取当前线程的名称最为合适。
```

设置线程的名称：可以通过setName或者带参的构造方法设置线程名称。



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

