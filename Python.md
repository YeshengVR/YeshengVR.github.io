# Python

## day_01

### 变量

python是弱类型函数，所赋的值的是什么，便是什么类型。

### print（）函数

 print(*objects, sep=’ ‘, end=’\n’, file=sys.stdout, flush=False) 

参数： objects – 复数，表示可以一次输出多个对象。输出多个对象时，需要用 sep –, 分隔。用来间隔多个对象，默认值是一个空格。

end – 用来设定以什么结尾。默认值是换行符 \n，我们可以换成其他字符串。

file –要写入的文件对象。 

flush – 输出是否被缓存通常决定于 file，但如果 flush 关键字参数为 True，流会被强制刷新。
返回值：无。

print(‘’)

print(“”)

print(“‘

......

’‘’)    #类似于html的pre标签，是预处理标签。保留原有格式。

```python
a = '老baby'
b = '请告诉我你的愿望'
c = '我会帮你完成的，小可爱。'
print('芙蓉姐姐告诉%s,\"这是一次历练%s.\"60岁耿叔告诉%s' % (a,b,c))
```

格式化输出%s，%d，%f（五舍六入的方式，取舍数值）

```python
movie = '唐人街探案3'
ticket = 52.8
rount = 42
total = ticket*rount
message ='''电影：%s票价：%f人数：%d总价：%.1f'''% (movie, ticket, rount, total) 
print(message)

电影：唐人街探案3
票价：52.800000
人数：42
总价：2217.6

```

#### format格式化输出

```python
movie = '唐人街探案3'
ticket = 52.8
rount = 42
total = ticket*rount
message = '今天是{}电影，票价{}一张，一场可容纳人数{},总共票价{}'.format(movie,ticket,rount,total)
print(message)

今天是唐人街探案3电影，票价52.8一张，一场可容纳人数42,总共票价2217.6
```

用法和直接使用%s....之类的相同

### input()函数

```python
name =input()
print(name)

wad
wad
name =input('请输入名字:') #阻塞式
print(name)

请输入名字:dwa
dwa
```

输入类型函数，获取键盘输入内容。标准的输入流

input输入的都算作str字符串类型。

```python
print('''************************
捕鱼达人
************************''')
username = input('请输入参与游戏用户名：')
password = input('请输入密码：')
print('欢迎%s加入游戏'% username)
coins = input('请充值')
coins = int(coins)     #input输出的都是str字符串类型，要想使用需要先转换类型。
print('%s充值成功，当前游戏币有%d'%(username,coins))

************************
        捕鱼达人
************************

请输入参与游戏用户名：xiaozhu
请输入密码：xiaozhu
欢迎xiaozhu加入游戏
请充值500
xiaozhu充值成功，当前游戏币有500
```

### 赋值运算符

```python
name = 'admin'
name1 = name
print(id(name),name)
print(id(name1),name1)
name2 = 'admin'
print(id(name2),name)
name1 = 'admin'
print(id(name1),name)
name1 = 'admin1'
print(id(name1),name1)
1893948308528 admin
1893948308528 admin
1893948308528 admin
1893948308528 admin
1893948323888 admin1
```

常量赋值给变量时，新增一个地址。增加内存空间。重复的常量值付给不同的变量时，不增加新的内存空间，套用时节省内存空间。

新的常量赋值给以往的变量时，还是会增加一个地址。

新增地址与新增的常量相关，和变量无关。（变量类似于C的指针）

*常量池，地址*

### 算术运算符

算术运算符支持数学应用，不支持字符串。字符串只可识别‘+=’符号（因为，字符串有一个+的连接符号）

```python
a = input()
b = input()
a = int(a)
b = int(b)
result = a*b
print('乘法运算：',result)
result = a/b
print('除法运算：',result)
result = a**b
print('幂法运算：',result)
result = a//b
print('整除运算：',result)
result = a%b
print('求余运算：',result)
3
4
乘法运算： 12
除法运算： 0.75
幂法运算： 81
整除运算： 0
求余运算： 3
```

+= ，-=，*=，/=，**，//，%....的算术运算符用于math

### 关系运算符

```python
n1 =input('请输入第一个数：')
n2 =input('请输入第二个数：')
result = n1>n2
print('n1>n2:',result)
result = n1 == n2
print('n1==n2:',result)
password = 'hello123456789'
true_password = 'hello123456789'
result = password == true_password
print('password == true_password:',result)
username =input('请输入用户名：')
print(username+'您好！')
true_password =input('请再输入以便确认密码')
if true_password == password:
    print('密码正确！！！')
else:    
    print('密码错误！！！')
请输入第一个数：asd
请输入第二个数：asd
n1>n2: False
n1==n2: True
password == true_password: True
请输入用户名：
您好！
请再输入以便确认密码hello123456789
密码正确！！！
```

每一次创建的python函数都是新创建一个独立的常量池，地址

```python
>>> money=20000
>>> id(money)
2973351261104
>>> salary=20000
>>> id(salary)
2973321381072
>>> a=6
>>> id(a)
140706620210400
>>> b=6
>>> id(b)
140706620210400
```

#### 小整数对象池/大整数对象池

python中有《小整数》概念，当常数为【-5，256】时，python自动分配好了地址。在交互式系统里面另一个python函数中调用不用开辟一个新的常量地址池。当新建一个大于256的常量时，都会新增一个地址。

### 逻辑运算符

and 逻辑与     都为真：true

or 逻辑或        有一个为真：true

not 逻辑非      都为真：false

逻辑运算符的结果也是返回true/false。

```python
n1 = 8
n2 = 5
n3 = 3
result = n1>=(n2+n3) and n1>n2
print(result)result = n1>=(n2+n3) or n1>n2print(result)result = not n1>n2print(result)
True
True
False
```

## day_02

### 进制

8个二进制位bit构成1个字节byte

二进制，八进制，十进制，十六进制互转

八进制0o开头，里面数字不能超过8

十六进制0x开头，里面数值不超过16

a 10; b 11; c  12; d  13; e  14; f 15

*例：0o6430转二进制*

   *6      4      3      0*

*110   100   011  000*        

*110100011000就是0o6430的二进制数值*

#### 位运算

```python
 	print(5 & 3)
    #按位与    0101
    #         0011
    #         0001
    # 只有两者都是1才取1
    print(5 | 3)
    #按位或    0101
    #         0011
    #         0111
    #两者任意一个为1取1
    print(-5)
    #取反操作
    #         0101
    #         1010
    #都不为1时取1
    print(3^5)
	#异或     0011 0101
	#         0110
	#相同为0，不同为1
	print(2<<1)
	#左移1位  （位数不够，末尾补零）
	#等同于第一个数乘以（2的第二位数次方）
	#       0000 0010
	#       0000 0100
	print(2>>1)
	#右移1位   （位数不够，补符号位）
	#       0000 0010
	#       0000 0001
    1
	7
	-5
	6
	4
	1
```

##### 三目运算符

```python
a = 6
b = 5
result = (a+b) if a<b else (b-a) #三目运算符标识
print(result)
```

### 运算符优先级

> 排序
>
> **
>
> ！
>
> +，-
>
> *，/ ，//，%
>
> << ，>>
>
> &
>
> ^
>
> |
>
> ==，!=，>，>=，<，<=
>
> is，is not
>
> not
>
> and
>
> or

### 条件语句

条件语句用来判断

if else

```python
username =''
if username:
    print('欢应进入！！！')
print(username+'你好！')
你好！
```

python判断的变量是‘’（空字符串），0，none默认是false

python如果变量有值，认为是true。

### random随机数

import random

#### random猜数字

```python
import random
print(random.randint(1,100))

ran = random.randint(1,100)
my = input()
my = int(my)
print(ran)
if ran == my:
    print('恭喜你猜对了！！！')
elif ran>(my-10) and ran<(my+10):
    print('很接近了，下次努力吧！')
else:
    print('很遗憾你猜错了！！')
```

### for循环语句

#### range()

使用系统给定range() 完成范围指定

range的循环从0开始到给定的数值停止，不包括给定的数值。

```python
print(range(4))

for i in range(3):
    print('hello!',i)

range(0, 4)
hello! 0
hello! 1
hello! 2
```

```python
name = "赵文卓"
skills = '大威天龙'
for i in range(5):
    print('{}使出了第{}次{}，打死了{}个敌人'.format(name,i+1,skills,i+1))
赵文卓使出了第1次大威天龙，打死了1个敌人
赵文卓使出了第2次大威天龙，打死了2个敌人
赵文卓使出了第3次大威天龙，打死了3个敌人
赵文卓使出了第4次大威天龙，打死了4个敌人
赵文卓使出了第5次大威天龙，打死了5个敌人
```

如果range传递的是两个参数，则从第一个参数开始循环，递增到第二个参数-1。	如果第二个参数小于第一个参数，则不打印。（不会报错）

如果给定的是三个参数，range（start，end，step）

start开始的数，end结束的数，step步长，循环每次间隔几个数。

##### pass语句

只要有缩进的内容还不确定的时候，此时为了保证语法的正确性，就可以使用pass占位。

> ctrl+c：中断输入

pass语句一般用于整体写作代码时，先写出大体框架，用pass语句占位，等之后细写功能时再把pass语句去掉。（与html先写大体框架，再细写功能一样。）

##### break语句

break语句用于跳出本次循环

```python
#----*-登陆模块案例-*----
for i in range(3):
    username=input('请输入用户名：')
    password=input('请输入密码：')
    if username == 'Amy' and password == '123456789':
        print('登陆成功！，欢迎进入系统！！')
        print('*'*9,'爸爸欢迎你','*'*9)
        break
    else:
        print('用户名或密码错误，登录失败，请重新输入！')
#range的范围正常执行完毕，而没有异常break跳出，就可以执行else#range的范围正常执行完毕，而没有异常break跳出，就可以执行else
else:print('错误次数达到三次，请稍后再登陆！！！')

```

### while循环语句

```python
i=0
while i<10:
    print(i)
    i += 1
```

while语句一般用于死循环。

```python
while True:
	pass
```

## day_03

在字符串当中‘’‘

三引号占用的内存空间与单双引号的不同（即使内容相同，除非三引号的内容没有换行，全部都在一行上。）

input输入的都是字符串类型

```python
print(s1 == s2) # ==比较的是内容
print(s1 is s2) # is比较的是地址
```

常量赋值 is比较 地址是true；input输入底层做了处理，所以最后的地址都不会相同。（内容都相同的情况下比较地址值）

### in运算符

```python
name='steven'
result ='t' in name #返回值是布尔类型 true false    判断t是否在name里面
print(result)
```

in    在.....里面

not   in     不在........里面

### 字符串的格式化

% 字符串的格式化

在print输出语句开头写r则会保留原格式，不发生转义，没有r则发生转义

```python

name ='steven'
print(r'%s说：\'哈哈哈\''% name)
print('%s说：\'哈哈哈\''% name)

steven说：\'哈哈哈\'
steven说：'哈哈哈'
```

[]         [ : ] 

通过方括号可以结合位置获取字母

下标都通过0开始

```python
filename =‘picture.png’
print(filename[0:7])
```

[:]只要省略的是后面的，表示一直取到字符串的末尾

只要省略的是前面的，表示从第一个一直取到给定的位置。

[:-值]取负值指的是最后一个数字为-1，-2以此类推。从第几号值往前推

