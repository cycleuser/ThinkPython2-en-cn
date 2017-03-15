Title: ThinkPython 双语学编程 Chapter 2  
Date: 2015-10-23  
Category: ThinkPython  
Tag: 双语,Python,ThinkPython

# Chapter 2  Variables, expressions and statements 变量，表达式，语句

One of the most powerful features of a programming language is the ability to manipulate variables. A variable is a name that refers to a value.

> 编程语言最强大的功能就是操作变量。变量就是一个有值的代号。

## 2.1  Assignment statements 赋值语句

An assignment statement creates a new variable and gives it a value:

> 赋值语句的作用是创建一个新的变量，并且赋值给这个变量：

```python
>>> message = 'And now for something completely different' 
>>> n = 17 
>>> pi = 3.141592653589793 
```

This example makes three assignments. The first assigns a string to a new variable named message; the second gives the integer 17 to n; the third assigns the \(approximate\) value of π to pi.

> 上面就是三个赋值语句的例子。第一个是把一个字符串复制给名叫message的新变量；第二个将n赋值为整数17；第三个把圆周率的一个近似值赋给了pi这个变量。

A common way to represent variables on paper is to write the name with an arrow pointing to its value. This kind of figure is called a state diagram because it shows what state each of the variables is in \(think of it as the variable’s state of mind\). Figure 2.1 shows the result of the previous example.

> 平常大家在纸上对变量赋值的方法就是写下名字，然后一个箭头指向它的值。这种图解叫做状态图，因为它能指明各个变量存储的是什么内容。下图就展示了上面例子中赋值语句的结果。

---

![Figure 2.1: State diagram.](http://7xnq2o.com1.z0.glb.clouddn.com/ThinkPython2.1.png)  
Figure 2.1: State diagram.

---

## 2.2  Variable names 变量名称

Programmers generally choose names for their variables that are meaningful—they document what the variable is used for.

> 编程的人总得给变量起个有一定意义的名字才能记得住，一般情况就用名字来表示这个变量的用途了。

Variable names can be as long as you like. They can contain both letters and numbers, but they can’t begin with a number. It is legal to use uppercase letters, but it is conventional to use only lower case for variables names.

> 变量名称你随便起多长都可以的。包含字母或者数字都行，但是不能用数字来开头。大写字母也能用，不过还是建议都用小写字母来给变量命名，这个比较传统哈。

The underscore character, \_, can appear in a name. It is often used in names with multiple words, such as your\_name or airspeed\_of\_unladen\_swallow.

> 变量名里面可以有下划线\_，一般在多个单词组成的变量名里面往往用到下划线，比如your\_name等等。

If you give a variable an illegal name, you get a syntax error:

> 你要是给变量起名不合规则，就会出现语法错误提示了：

```Python
>>> 76trombones = 'big parade' 
SyntaxError: invalid syntax 
>>> more@ = 1000000 
SyntaxError: invalid syntax 
>>> class = 'Advanced Theoretical Zymurgy' 
SyntaxError: invalid syntax 
```

76trombones is illegal because it begins with a number. more@ is illegal because it contains an illegal character, @. But what’s wrong with class?

> 第一个数字开头所以不合规则，第二个有非法字符@，第三个这个class咋不行呢？好奇吧？

It turns out that class is one of Python’s keywords. The interpreter uses keywords to recognize the structure of the program, and they cannot be used as variable names.

> 因为clas是Python里面的一个关键词啦。解释器要用关键词来识别程序的结构，这些关键词是不能用来做变量名的。

Python 3 has these keywords:

> 以下是Python3的关键词哈：

```Python
False      class      finally    is         
return None       continue   for        lambda     
try True       def        from   nonlocal   
while and        del        global     not        
with as         elif       if         or         
yield assert     else       import     pass 
break      except     in         raise 
```

You don’t have to memorize this list. In most development environments, keywords are displayed in a different color; if you try to use one as a variable name, you’ll know.

> 你不用去记忆这些哈。因为一般大多数的开发环境里面，关键词都会有区别于普通代码的颜色提示你，你要是用他们做变量名了，一看就会知道的。

## 2.3  Expressions and statements 表达式和语句

An expression is a combination of values, variables, and operators. A value all by itself is considered an expression, and so is a variable, so the following are all legal expressions:

> 表达式是数值,变量和操作符的组合。单个值本身也被当作一个表达式，变量也是如此，下面这些例子都是一些正确表达式：

```Python
>>> 42 
42 
>>> n 
17 
>>> n + 25 
42 
```

When you type an expression at the prompt, the interpreter evaluates it, which means that it finds the value of the expression. In this example, n has the value 17 and n + 25 has the value 42.

> 当你在提示符后面敲出一个表达式，解释器就判断一下，他会找到这个表达式的值。在本节的例子中，n的值是17，所以n+25就是42了。

A statement is a unit of code that has an effect, like creating a variable or displaying a value.

> 语句是一组具有某些效果的代码，比如创建变量，或者显示值。

```Python
>>> n = 17 
>>> print(n)
```

The first line is an assignment statement that gives a value to n. The second line is a print statement that displays the value of n.

> 上面第一个就是赋值语句，给n赋值。第二行是显示n的值。

When you type a statement, the interpreter executes it, which means that it does whatever the statement says. In general, statements don’t have values.

> 输入语句的时候，解释器会执行它，就是会按照语句所说的去做。一般语句是没有值的。

## 2.4  Script mode 脚本模式

So far we have run Python in interactive mode, which means that you interact directly with the interpreter. Interactive mode is a good way to get started, but if you are working with more than a few lines of code, it can be clumsy.

> 以上我们一直在用Python的交互模式，就是直接咱们人跟解释器来交互。开始学的时候这样挺好的，但如果你要想一次运行多行代码，这样就很不方便了。

The alternative is to save code in a file called a script and then run the interpreter in script mode to execute the script. By convention, Python scripts have names that end with .py.

> 所以就有另一种选择了，把代码保存成脚本，然后用脚本模式让解释器来运行这些脚本。通常Python脚本文件的扩展名是.py。

If you know how to create and run a script on your computer, you are ready to go. Otherwise I recommend using PythonAnywhere again. I have posted instructions for running in script mode at [http://tinyurl.com/thinkpython2e](http://tinyurl.com/thinkpython2e).

> 如果你知道怎么创建和运行脚本，那就尽管在自己电脑上尝试好了。否则我就建议你还是用PythonAnywhere。关于脚本模式的介绍我放到网上了，打开这个链接（[http://tinyurl.com/thinkpython2e）去看下哈。](http://tinyurl.com/thinkpython2e）去看下哈。)

Because Python provides both modes, you can test bits of code in interactive mode before you put them in a script. But there are differences between interactive mode and script mode that can be confusing.

> Python两种模式都支持，所以你可以先用交互模式做点测试，然后再写成脚本。但是两种模式之间有些区别的，所以可能也挺麻烦。  
> For example, if you are using Python as a calculator, you might type：  
> 举个例子哈，比如咱们把Python当计算器用，你输入以下内容：

```Python
>>> miles = 26.2 
>>> miles * 1.61 
42.182 
```

The first line assigns a value to miles, but it has no visible effect. The second line is an expression, so the interpreter evaluates it and displays the result. It turns out that a marathon is about 42 kilometers.

> 第一行给miles这个变量赋初值（译者注：26.2英里是马拉松比赛全程长度），但是看着没啥效果。第二行是一个表达式，解释器会计算这个表达式，然后把结果输出。结果就是把马拉松全程长度从英里换算成公里，答案是42公里哈。

But if you type the same code into a script and run it, you get no output at all. In script mode an expression, all by itself, has no visible effect. Python actually evaluates the expression, but it doesn’t display the value unless you tell it to:

> 不过你要是直接把这些代码存成脚本然后运行，是啥都看不到的，没有输出。在脚本模式表达式是没有明显效果的。Python确实会计算这些表达式，但不显示结果，想看到结果你就得告诉他输出一下：

```Python
miles = 26.2 
print(miles * 1.61) 
```

This behavior can be confusing at first.

> 这种情况开始还挺让人混乱的。

A script usually contains a sequence of statements. If there is more than one statement, the results appear one at a time as the statements execute.For example, the script:

> 脚本一般都是包含了一系列的语句。如果语句超过一条，每个语句执行的时候都会显示结果。比如下面这个：

```python
print(1) 
x = 2 
print(x) 
```

produces the output

> 输出的结果如下

```Python
1 
2 
```

The assignment statement produces no output.

> 赋值语句是不会有任何输出的。

To check your understanding, type the following statements in the Python interpreter and see what they do:

> 检查下你理解了没哈，把下面这些语句输入到Python解释器，看看会发生什么：

```Python
5 x = 5 x + 1 
```

Now put the same statements in a script and run it. What is the output? Modify the script by transforming each expression into a print statement and then run it again.

> 现在再把同样的语句输入到脚本中，然后用Python来运行一下。看看输出是啥样的？把脚本中的表达式修改一下，每一个都加一个打印语句再试试。

## 2.5  Order of operations 运算符优先级

When an expression contains more than one operator, the order of evaluation depends on the order of operations. For mathematical operators, Python follows mathematical convention. The acronym PEMDAS is a useful way to remember the rules:

> 表达式可能会包含不止一个运算符，这些不同的运算先后次序就是运算符的优先级。对于数学运算符来说，Python就遵循着数学上的规则。下面这个PEMDAS、是用来记忆这些优先规则的好方法：

* Parentheses have the highest precedence and can be used to force an expression to evaluate in the order you want. Since expressions in parentheses are evaluated first, 2 \*\* \(3-1\) is 4, and \(1+1\)\*\*\(5-2\) is 8. You can also use parentheses to make an expression easier to read, as in\(minute _ 100\) / 60, even if it doesn’t change the result.

  > 括号内的内容最优先，大家可以用括号来强制某系表达式有限计算。所以2\*\*（3-1）就等于4了，（1+1）\*\*（5-2）就是2的立方，等于8。使用括号也有助于让你的表达式读起来更好理解，比如\(minute _ 100\) / 60，这个也不影响计算结果，不过看起来易于理解。

* Exponentiation has the next highest precedence, so 1 + 2\*\*3 is 9, not 27, and 2 \* 3\*\*2 is 18, not 36.

  > 除了括号，所有运算符中，乘方最优先，所以1 + 2\*\*3的结果是9而不是27，2\*3\*\*2结果是18，而不是36。

* Multiplication and Division have higher precedence than Addition andSubtraction. So 2\*3-1 is 5, not 4, and 6+4/2 is 8, not 5.

  > 乘除运算比加减优先，译者认为大家都知道了，这个我就不细说了。

* Operators with the same precedence are evaluated from left to right \(except exponentiation\). So in the expression degrees / 2 \* pi, the division happens first and the result is multiplied by pi. To divide by 2 π, you can use parentheses or write degrees / 2 / pi.

  > 同类运算符从左往右来进行，乘方除外。这个也不细说了，很简单。

I don’t work very hard to remember the precedence of operators. If I can’t tell by looking at the expression, I use parentheses to make it obvious.

> 我不会花很大力气来记忆这些运算符的优先级。如果我记不起来，就用括号来让优先级明确一些就好了。

## 2.6  String operations 字符串操作

In general, you can’t perform mathematical operations on strings, even if the strings look like numbers, so the following are illegal:

> 一般情况下，咱们不能对字符串进行数学运算的，即使字符串看上去像是数字也不行，所以以下这些都是非法操作：

```Python
'2'-'1'    'eggs'/'easy'    'third'*'a charm' 
```

But there are two exceptions, + and \*.

> 不过+和\*可以用在字符串上面。

The + operator performs string concatenation, which means it joins the strings by linking them end-to-end. For example:

> +加号的意思就是字符串拼接了，会把两个字符串拼到一起，如下所示：

```Python
>>> first = 'throat' 
>>> second = 'warbler' 
>>> first + second 
throatwarbler 
```

The _ operator also works on strings; it performs repetition. For example,'Spam'_3 is 'SpamSpamSpam'. If one of the values is a string, the other has to be an integer.

> _星号也就是乘法运算符也可以用在字符串上面，效果就是重复。比如'Spam'_3 结果就是   
> 'SpamSpamSpam'，重复了三次。需要注意的是字符串必须用整数去乘。

This use of + and _ makes sense by analogy with addition and multiplication. Just as 4_3 is equivalent to 4+4+4, we expect 'Spam'\*3 to be the same as'Spam'+'Spam'+'Spam', and it is. On the other hand, there is a significant way in which string concatenation and repetition are different from integer addition and multiplication. Can you think of a property that addition has that string concatenation does not?

> 这种加法和乘法实际上就是拼接和重复的意思。就像4_3等同于4+4+4一样，'Spam'_3 也就等于'Spam'+’Spam’+’Spam'。另外一方面，字符串的拼接重复与整数的加法乘法也有显著区别。你能想到加法具有些特性是字符拼接所不具有的么？

## 2.7  Comments 注释

As programs get bigger and more complicated, they get more difficult to read. Formal languages are dense, and it is often difficult to look at a piece of code and figure out what it is doing, or why.

> 程序会越来越庞大，也越复杂了，读起来就会更难了。公式语言很密集，靠阅读来理解代码，总是很困难的。

For this reason, it is a good idea to add notes to your programs to explain in natural language what the program is doing. These notes are called comments, and they start with the \# symbol:

> 为了解决阅读的困难，咱们就可以添加一些笔记到代码中，把程序的功能用自然语言来解释一下。这种笔记就叫注释了，使用井号\#来开头的：

```Python
# compute the percentage of the hour that has elapsed percentage = (minute * 100) / 60 
```

In this case, the comment appears on a line by itself. You can also put comments at the end of a line:

> 注释可以另起一行，也可以放到行末尾：

```Python
percentage = (minute * 100) / 60     # percentage of an hour 
```

Everything from the \# to the end of the line is ignored—it has no effect on the execution of the program

> 井号\#后面的内容都会被忽略，因此不会影响程序的运行结果。

Comments are most useful when they document non-obvious features of the code. It is reasonable to assume that the reader can figure out what the code does; it is more useful to explain why.

> 一般注释都是用来解释代码的一些不明显的特性。一般情况下读代码的人应该能理解代码的功能是什么，所以用注释多是要解释这样做的目的是什么。

This comment is redundant with the code and useless:

> 这个注释就显然是多余的，根本没必要：

```Python
v = 5     # assign 5 to v 
```

This comment contains useful information that is not in the code:

> 这种注释包含了重要信息，就很重要了：

```python
v = 5     # velocity in meters/second.  
```

Good variable names can reduce the need for comments, but long names can make complex expressions hard to read, so there is a tradeoff.

> 变量命名得当的话，就没必要用太多注释了，不过名字要是太长了，表达式读起来也挺麻烦，所以就得权衡着来了。

## 2.8  Debugging 调试

Three kinds of errors can occur in a program: syntax errors, runtime errors, and semantic errors. It is useful to distinguish between them in order to track them down more quickly.

> 程序一般会有三种错误：语法错误，运行错误和语义错误。区分这三种错误有助于更快速地追踪错误。

* Syntax error:  
  “Syntax” refers to the structure of a program and the rules about that structure. For example, parentheses have to come in matching pairs, so\(1 + 2\) is legal, but 8\) is a syntax error.  
  If there is a syntax error anywhere in your program, Python displays an error message and quits, and you will not be able to run the program. During the first few weeks of your programming career, you might spend a lot of time tracking down syntax errors. As you gain experience, you will make fewer errors and find them faster.

  > 语法错误Syntax error:  
  > 语法是指程序的结构和规则。比如括号要成对用。如果你的程序有某个地方出现了语法错误，Python会显示出错信息并退出，程序就不能运行了。最开始学习编程的这段时间，你遇到的最常见的估计就是这种情况。等你经验多了，基本就犯的少了，而且也很容易发现了。

* Runtime error:  
  The second type of error is a runtime error, so called because the error does not appear until after the program has started running. These errors are also called exceptions because they usually indicate that something exceptional \(and bad\) has happened.  
  Runtime errors are rare in the simple programs you will see in the first few chapters, so it might be a while before you encounter one.

  > 运行错误Runtime error:  
  > 第二种错误就是运行错误，显而易见了，就是直到运行的时候才会出现的错误。这种错误也被叫做异常，因为一般表示一些意外的尤其是比较糟糕的情况发生了。

* Semantic error:  
  The third type of error is “semantic”, which means related to meaning. If there is a semantic error in your program, it will run without generating error messages, but it will not do the right thing. It will do something else. Specifically, it will do what you told it to do.  
  Identifying semantic errors can be tricky because it requires you to work backward by looking at the output of the program and trying to figure out what it is doing.

  > 语义错误Semantic error:  
  > 第三种就是语义错误，顾名思义，是跟意义相关。这种错误是指你的程序运行没问题，也不产生错误信息，但不能正确工作。程序可能做一些和设计目的不同的事情。发现语义错误特别不容易，需要你仔细回顾代码和程序输出，要搞清楚到底程序做了什么。

## 2.9  Glossary 术语列表

variable:  
A name that refers to a value.  
变量：有值的量。

> assignment:

A statement that assigns a value to a variable.

> 赋值：给一个变量赋予值。

state diagram:  
A graphical representation of a set of variables and the values they refer to.

> 状态图：图形化表征每个变量的值。

keyword:  
A reserved word that is used to parse a program; you cannot use keywords like if, def, and while as variable names.

> 关键词：系统保留的用于解析程序的词，不能用关键词当做变量名。

operand:  
One of the values on which an operator operates.

> 运算数：运算符来进行运算操作的数值。

expression:  
A combination of variables, operators, and values that represents a single result.

> 表达式：一组变量、运算数的组合，会产生单值作为结果。

evaluate:  
To simplify an expression by performing the operations in order to yield a single value.

> 求解：把表达式所表示的运算计算出来，得到一个单独的值。

statement:  
A section of code that represents a command or action. So far, the statements we have seen are assignments and print statements.

> 声明：一组表示一种命令或者动作的代码，目前我们了解的只有赋值语句和打印语句。

execute:  
To run a statement and do what it says.

> 运行：将一条语句进行运行。

interactive mode:  
A way of using the Python interpreter by typing code at the prompt.

> 交互模式：在提示符后输入代码，让解释器来运行代码的模式。

script mode:  
A way of using the Python interpreter to read code from a script and run it.

> 脚本模式：将代码保存成脚本文件，用解释器运行的模式。

script:  
A program stored in a file.

> 脚本：程序以文本形式存成的文件。

order of operations:  
Rules governing the order in which expressions involving multiple operators and operands are evaluated.

> 运算符优先级：不同运算符和运算数进行计算的优先顺序。

concatenate:  
To join two operands end-to-end.

> 拼接：把两个运算对象相互连接到一起。

comment:  
Information in a program that is meant for other programmers \(or anyone reading the source code\) and has no effect on the execution of the program.

> 注释：程序中用来解释代码含义和运行效果的备注信息，通常给阅读代码的人准备的。

syntax error:  
An error in a program that makes it impossible to parse \(and therefore impossible to interpret\).

> 语法错误：程序语法上的错误，导致程序不能被解释器解译，就不能运行了。

exception:  
An error that is detected while the program is running.

> 异常：程序运行的时候被探测到的错误。

semantics:  
The meaning of a program.

> 语义：程序的意义。

semantic error:  
An error in a program that makes it do something other than what the programmer intended.

> 语义错误：程序运行的结果和料想的不一样，没有完成设计的功能，而是干了点其他的事情。

## 2.10  Exercises 练习

### Exercise 1  练习1

Repeating my advice from the previous chapter, whenever you learn a new feature, you should try it out in interactive mode and make errors on purpose to see what goes wrong.

> 像上一章一样，按我建议的，不论学了什么新内容，你都试着在交互模式上故意犯点错误，看看会怎么样。

* We’ve seen that n = 42 is legal. What about 42 = n?
  > 我们都看到了n=42是可以的，那42=n怎么样？
* How about x = y = 1?
  > 再试试x=y=1呢？
* In some languages every statement ends with a semi-colon, ;. What happens if you put a semi-colon at the end of a Python statement?
  > 有的语言每个语句结尾都必须有个单引号或者分号，试试在Python句末放个会咋样？
* What if you put a period at the end of a statement?
  > 句尾放个句号试试呢？
* In math notation you can multiply x and y like this: x y. What happens if you try that in Python?
  > 数学上你可以把x和y相乘写成xy，Python里面你这么试试看？

### Exercise 2

Practice using the Python interpreter as a calculator:  
1.    The volume of a sphere with radius r is 4/3 π r3. What is the volume of a sphere with radius 5?  
2.    Suppose the cover price of a book is $24.95, but bookstores get a 40% discount. Shipping costs $3 for the first copy and 75 cents for each additional copy. What is the total wholesale cost for 60 copies?  
3.    If I leave my house at 6:52 am and run 1 mile at an easy pace \(8:15 per mile\), then 3 miles at tempo \(7:12 per mile\) and 1 mile at easy pace again, what time do I get home for breakfast?

> 把Python解释器当做计算器来做下面的练习：  
> 1.    球体体积是三分之四倍的圆周率乘以半径立方，求半径为5的球体体积。  
> 2.    假如一本书的封面标价是24.95美元，书店打六折。第一本运费花费3美元，后续每增加一本的运费是75美分。问买60本一共得花多少钱呢？  
> 3.    我早上六点五十二分出门离家，以8:15的节奏跑了一英里，又以7：12的节奏跑了三英里，然后又是8：15的节奏跑一英里，回到家吃饭是几点？



