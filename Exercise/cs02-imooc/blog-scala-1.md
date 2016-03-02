## Scala 学习笔记--基础##

###基本语法###
Scala有Byte,Char,Short,Int,Long,Float，Double和Boolean八种类型。但都是类，没有基本数据类型。

**1、算术和操作符重载**
>a 方法 b 是 a.方法(b)的一种简写
1 to 10 同1.to(10)，将产生1到10的Range类数。    

scala没有提供++/--操作符，因为Int类是不可变的，这样一个方法不能改变某个整数类型的值。Scala设计者认为不值得为少按一个键额外增加一个特例。

对于BigInt
```scala
val x:BigInt = 1234567890
x*x*x//将产生1881676371789154860897069000
```
**2、调用函数和方法**   
scala没有提供静态方法，但可以直接使用数学函数，只要import scala.math._
>在使用以scala.开头的包时，我们可以省去scala前缀。import math._等同于import scala.math._
scala提供了单例对象，通常一个类对应有一个伴生对象（companion object)，其方法跟Java静态方法一样。形式上也是采用`类名.方法名`的形式。

**3、apply方法**    
"Hello"(4) //将输出'o'
其实现原理是，在背后存在一个名为apply的方法   
def apply(n:Int):Char
也就是说，"Hello"(4)是如下语句的简写 "Hello".apply(4)
同样的例子还有BigInt("1234567890") 其实是BigInt.apply("1234567890")的一种简写；Array(1,4,9,16)返回一数组，其实用的就是伴生对象的apply方法。
>在调用scala方法的时候，如果该方法不带任何参数，则可以不使用圆括号如"Hello".distinct,一般来讲，没有参数且不改变当前对象的方法不带圆括号。

**4、Any和Unit**    
在Scala中，每个表达式都应该有某种值，如果在if/else表达式中返回不同的数据类型，则表达式if/else返回的是其公共的父类Any。如果else部分缺失了，那么有可能if语句没有返回值，这时候整个表达式的值可以使用Unit类，写作()，这是Scala中引入的类。
>也就是说，不带else的if语句等同于如下的写法
```scala
if(x>0) 1 else ()
```
这里的()可以表示"无有用值"的占位符。当成java和c++中的void

**5、语句终止**
如果单行中要写下多条语句，则需要以分号分隔。
如果在写较长语句需要用两行来写的话，需要确保第一行以一个不能用作语句结尾的符号结尾。通常可以选择操作符作为结尾。scala程序员更倾向使用Kernighan&Ritchie风格的花括号：
```java
if(n>0){
	r = r*n
	n-=1
}
```
**6、块表达式**
块中最后一个表达式的值是块的值，这个特性对某个val的初始化需要多步完成的情况很有用
val distance = {val dx = x-x0;val dy = y-y0;sqrt(dx*dx+dy*dy)}
一个赋值语句是没有值的，或者说，他们的值是Unit类型。也正是由于这个原因，不要将赋值语句串联起来
x=y=1 这里y=1的值是()，然后将赋值语句的Unit赋值给x.