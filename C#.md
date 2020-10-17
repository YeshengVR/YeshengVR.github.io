# C#

C#开发完整流程![](F:\md笔记文件\Unityimg\C#整体流程.jpg)

## .NET框架

要进行C#开发，须先了解.NET框架。C#程序必须在.NET Framework上运行。.NET框架为C#搭建了一个基础平台。提供的.NET类库，让应用程序能够访问运行时环境。.NET Framework主要包括两个组件：公共语言运行库(Common Language Runtime)CLR和.NET Framework类库(Class Library)CL。所以，如果要运行C#编写的程序，计算机上必须要.NET框架。

.NET dotnet 是微软新一代多语言的开发平台，用于构建和运行应用程序。

**Mono**

- Novell公司支持在其它操作系统下开发.NET程序的框架。
- Unity借助Mono实现跨平台，核心是.NET Framework 框架

```C#
//引入命名空间
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

//定义命名空间[类的住址]：对类进行逻辑上的划分，避免重名
namespace Day09_17
{
    //定义类
    class Program
    {
        //定义方法[做功能]
        static void Main(string[] args)
        {
            //输出语句Console:控制台
         Console.WriteLine("Hello,World!");
            //读取一行
            //暂停程序(按回车键继续)
         Console.ReadLine();
        }
    }
}

```

## C#规则

自上而下逐语句执行 与Java语法规则非常相似
在C#中Console是个类，类似于Java的类的定义。
类似于Console.Title的Title就是这个类的属性值，用于命名命令行窗口。

C#程序的入口也是Main()方法。

C#文件的后缀名为：**.cs**

命名空间[类的住址]：对类进行逻辑上的划分，避免重名

### 快捷键

Ctrl+A ； Ctrl+K+F自动对齐代码的快捷键（已自定义修改成Ctrl+Shift+K）
				Ctrl+K+C注释选中的代码(Ctrl+Shift+/)
				Ctrl+K+U取消注释(Alt+/)

