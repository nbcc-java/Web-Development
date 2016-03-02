## Scala 学习笔记--闭包##

###常见错误###
"-3+4".collect{case '+'=>1;case '-'=> -1}
>注意：collect方法用于`偏函数(partial function)`，那些没有对所有可能的输入值进行定义的函数（例如这里的case），它产出被定义的所有参数的函数值的集合。这里书写时，需要注意case 对偶值=>后的-1之间必须保持一个空格。

###`#::`语法###
`#::`操作符很像列表的`::`操作符，只不过他用来构建一个流

###match表达式###
```scala
var sign =...
val ch:Char=...

ch match{
	case '+' => sign = 1
	case '-' => sign = -1
	case _ => sign = 0
}

```
由于match是表达式，也可以写成
```scala
sign = ch match{
	case '+' => 1
	case '-' => -1
	case _ => 0
}
```
您还可以在模式中添加变量
```
str(i) match{
	case ch if Character.isDigit(ch)=>digit = Character.digit(ch,10)
	...
}
```
>Scala的常量通常都是大写字母开头，如果你有一个小写字母开头的常量，则需要将它包在反引号中：  

```scala
import java.io.File._
str match{
	case `pathSeparator` =>...
	...
}
```
###提取器###
>`提取器extractor`，带有从对象中提取值的unapply或unapplySeq方法的对象。unapply方法用于提取固定数量的对象，而unapplySeq提取的是一个序列，可长可短。    
* Array伴生对象就是一个提取器
* 正则表达式是另一个适合提取器的场景

