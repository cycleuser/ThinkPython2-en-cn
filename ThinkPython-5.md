Title: ThinkPython 双语学编程 Chapter 5 
Date: 2015-10-29
Category: ThinkPython
Tag: 双语,Python,ThinkPython

#Chapter 5  Conditionals and recursion 条件循环
The main topic of this chapter is the if statement, which executes different code depending on the state of the program. But first I want to introduce two new operators: floor division and modulus.
>本章的主题是if语句，就是条件判断，会对应程序的不同状态来执行不同的代码。但首先我要介绍两种新的运算符：floor（地板除法，舍弃小数位）和modulus（求模，取余数）


##5.1  Floor division and modulus 地板除和求模

The floor division operator, //, divides two numbers and rounds down to an integer. For example, suppose the run time of a movie is 105 minutes. You might want to know how long that is in hours. Conventional division returns a floating-point number:
>floor除法，中文有一种翻译是地板除法，挺难听，不过凑活了，运算符是两个右斜杠：//，与传统除法不同，地板除法会把运算结果的小数位舍弃，返回整值。例如，加入一部电影的时间长度是105分钟。你可能想要知道这部电影用小时来计算是多长。传统的除法运算如下，会返回一个浮点小数：

```Python
>>> minutes = 105 
>>> minutes / 60 
1.75 
```
But we don’t normally write hours with decimal points. Floor division returns the integer number of hours, dropping the fraction part:
>不过一般咱们不写有小数的小时数。地板除法返回的就是整的小时数，舍弃掉小数位：

```Python
>>> minutes = 105 
>>> hours = minutes // 60 
>>> hours 
1 
```

To get the remainder, you could subtract off one hour in minutes:
>想要知道舍弃那部分的长度，可以用分钟数减去这么一个小时，然后剩下的分钟数就是了：

```Python
>>> remainder = minutes - hours * 60 
>>> remainder
45 
```


An alternative is to use the modulus operator, %, which divides two numbers and returns the remainder.
>另外一个方法就是使用求模运算符了，百分号%就是了，求模运算就是求余数，会把两个数相除然后返回余数。

```Python
>>> remainder = minutes % 60 
>>> remainder 
45 
```

The modulus operator is more useful than it seems. For example, you can check whether one number is divisible by another—if x % y is zero, then x is divisible by y.
>求模运算符的作用远不止如此。比如你可以用求模来判断一个数能否被另一个数整除——比如x%y如果等于0了，那就是意味着x能被y整除了。

Also, you can extract the right-most digit or digits from a number. For example, x % 10 yields the right-most digit of x (in base 10). Similarly x % 100yields the last two digits.
>另外你也可以从一个数上取最右侧的一位或多位数字。比如，x%10就会得出x最右边的数字，也就是x的个位数字。同样的道理，用x%100得到的就是右面两位数字了。


If you are using Python 2, division works differently. The division operator, /, performs floor division if both operands are integers, and floating-point division if either operand is a float.
>如果你用Python2的话，除法是不一样的。在两边都是整形的时候，常规除法运算符/就会进行地板除法，而两边只要有一侧是浮点数就会进行浮点除法。




##5.2  Boolean expressions 布尔表达式
A boolean expression is an expression that is either true or false. The following examples use the operator ==, which compares two operands and produces True if they are equal and False otherwise:
>布尔表达式是一种非对即错的表达式，只有这么两个值，true（真）或者false（假）。下面的例子都用了双等号运算符，这个运算符会判断两边的值是否相等，相等就是True，不相等就是False：

```Python
>>> 5 == 5 
True 
>>> 5 == 6 
False 

```

True and False are special values that belong to the type bool; they are not strings:
>True和False都是特殊的值，属于bool布尔类型；它们俩不是字符串：
```Python
>>> type(True) 
<class 'bool'> 
>>> type(False) 
<class 'bool'> 
```

The == operator is one of the relational operators; the others are:
>双等号运算符是关系运算符的一种，其他关系运算符如下：

```Python
x != y	# x is not equal to y  		二者相等     
x > y	# x is greater than y  		前者更大     
x < y	# x is less than y    		前者更小  
x >= y	# x is greater than or equal to y 大于等于      
x <= y	# x is less than or equal to y 	小于等于
```


Although these operations are probably familiar to you, the Python symbols are different from the mathematical symbols. A common error is to use a single equal sign (=) instead of a double equal sign (==). Remember that = is an assignment operator and == is a relational operator. There is no such thing as =< or =>.
>虽然这些运算符你可能很熟悉了，但一定要注意Python里面的符号和数学上的符号有一定区别。常见的错误就是混淆了等号=和双等号==。一定要记住单等号=是一个赋值运算符，而双等号==是关系运算符。另外要注意就是大于等于或者小于等于都是等号放到大于号或者小于号的后面，顺序别弄反。




##5.3  Logical operators 逻辑运算符

There are three logical operators: and, or, and not. The semantics (meaning) of these operators is similar to their meaning in English. For example, x > 0 and x < 10 is true only if x is greater than 0 and less than 10.
>逻辑运算符有三种：且，或以及非。这三种运算符的意思和字面意思差不多。比如x>0且x<10，仅当x在0到10之间的时候才为真。

n%2 == 0 or n%3 == 0 is true if either or both of the conditions is true, that is, if the number is divisible by 2 or 3.
>n%2 == 0 或 n%3 == 0，只要条件有一个成立就是真，就是说这个可以被2或3整除就行了。

Finally, the not operator negates a boolean expression, so not (x > y) is true if x > y is false, that is, if x is less than or equal to y.
>最后说这个非运算，是针对布尔表达式的，非（x>y）为真，那么x>y就是假的，意味着x小于等于y。

Strictly speaking, the operands of the logical operators should be boolean expressions, but Python is not very strict. Any nonzero number is interpreted as True:
>严格来说，逻辑运算符的运算对象应该必须是布尔表达式，不过Python就不太严格。任何非零变量都会被认为是真：
```Python
>>> 42 and True 
True 
```

This flexibility can be useful, but there are some subtleties to it that might be confusing. You might want to avoid it (unless you know what you are doing).
>这种灵活性特别有用，不过有的情况下也容易引起混淆。建议你尽量不要这样用，除非你很熟练了。



##5.4  Conditional execution 条件执行

In order to write useful programs, we almost always need the ability to check conditions and change the behavior of the program accordingly.Conditional statements give us this ability. The simplest form is the if statement:
>有用的程序必然要有条件检查判断的功能，根据不同条件要让程序有相应的行为。条件语句就让咱们能够实现这种判断。最简单的就是if语句了：


```Python
if x > 0:
	print('x is positive') 
```




The boolean expression after if is called the condition. If it is true, the indented statement runs. If not, nothing happens.
>if后面的布尔表达式就叫做条件。如果条件为真，随后缩进的语句就运行。如果条件为假，就不运行。

if statements have the same structure as function definitions: a header followed by an indented body. Statements like this are called compound statements.
>if语句与函数定义的结构基本一样：一个头部，后面跟着缩进的语句。这样的语句叫做复合语句。

There is no limit on the number of statements that can appear in the body, but there has to be at least one. Occasionally, it is useful to have a body with no statements (usually as a place keeper for code you haven’t written yet). In that case, you can use the pass statement, which does nothing.
>复合语句中语句体内的语句数量是不限制的，但至少要有一个。有的时候会遇到一个语句体内不放语句的情况，比如空出来用来后续补充。这种情况下，你就可以用pass语句，就是啥也不会做的。


```Python
if x < 0:
	pass          # TODO: need to handle negative values! 
```



##5.5  Alternative execution 选择执行

A second form of the if statement is “alternative execution”, in which there are two possibilities and the condition determines which one runs. The syntax looks like this:
>if语句的第二种形式就是『选择执行』，这种情况下会存在两种备选的语句，根据条件来判断执行哪一个。语法如下所示：

```Python
if x % 2 == 0:
	print('x is even') 
else:
	print('x is odd')
```


If the remainder when x is divided by 2 is 0, then we know that x is even, and the program displays an appropriate message. If the condition is false, the second set of statements runs. Since the condition must be true or false, exactly one of the alternatives will run. The alternatives are called branches, because they are branches in the flow of execution.
>如果x除以2的余数为0，x就是一个偶数了，程序就会显示对应的信息。如果条件不成立，那就运行第二条语句。这里条件非真即假，只有两个选择。这些选择也叫『分支』，因为在运行流程上产生了不同的分支。




##5.6  Chained conditionals 链式条件

Sometimes there are more than two possibilities and we need more than two branches. One way to express a computation like that is a chained conditional:
>有时我们要面对的可能性不只有两种，需要更多的分支。这时候可以使用连锁条件来实现：

```Python
if x < y:     
	print('x is less than y') 
elif x > y:     
	print('x is greater than y') 
else:     
	print('x and y are equal') 
```

elif is an abbreviation of “else if”. Again, exactly one branch will run. There is no limit on the number of elif statements. If there is an else clause, it has to be at the end, but there doesn’t have to be one.
>elif是『else if』的缩写。这回也还是只会有一个分支的语句会被运行。elif语句的数量是无限制的。如果有else语句的话，这个else语句必须放到整个条件链的末尾，不过else语句并不是必须有的。

```Python
if choice == 'a':
	draw_a()
elif choice == 'b':
	draw_b()
elif choice == 'c':
	draw_c()
```

Each condition is checked in order. If the first is false, the next is checked, and so on. If one of them is true, the corresponding branch runs and the statement ends. Even if more than one condition is true, only the first true branch runs.
>每一个条件都会依次被检查。如果第一个是假，下一个就会被检查，依此类推。如果有一个为真了，相应的分支语句就运行了，这些条件判断的语句就都结束了。如果有一个以上的条件为真，只有先出现的为真的条件所对应的分支语句会运行。



##5.7  Nested conditionals 嵌套条件

One conditional can also be nested within another. We could have written the example in the previous section like this:
>一个条件判断也可以嵌套在另一个条件判断内。上一节的例子可以改写成如下：

```Python
if x == y:
	print('x and y are equal')
else:
	if x < y:
		print('x is less than y')
	else:
		print('x is greater than y')
```


The outer conditional contains two branches. The first branch contains a simple statement. The second branch contains another if statement, which has two branches of its own. Those two branches are both simple statements, although they could have been conditional statements as well.
>外部的条件判断包含两个分支。第一个分支只有一个简单的语句。第二个分支包含了另外一重条件判断，这个内部条件判断有两个分支。这两个分支都是简单的语句，他们的位置也可以继续放条件判断语句的。


Although the indentation of the statements makes the structure apparent,nested conditionals become difficult to read very quickly. It is a good idea to avoid them when you can.
>虽然语句的缩进会让代码结构看着比较清晰明显，但嵌套的条件语句读起来还是有点难度。所以建议你如果可以的话，尽量避免使用嵌套的条件判断。

Logical operators often provide a way to simplify nested conditional statements. For example, we can rewrite the following code using a single conditional:
>逻辑运算符有时候对简化嵌套条件判断很有用。比如下面这个代码就能改写成更简单的版本:

```Python
if 0 < x:
	if x < 10:
		print('x is a positive single-digit number.')
```


The print statement runs only if we make it past both conditionals, so we can get the same effect with the and operator:
>上面的例子中，只有两个条件都满足了才会运行print语句，所以就用逻辑运算符来实现同样的效果即可：

```Python
if 0 < x and x < 10:
	print('x is a positive single-digit number.')
```


For this kind of condition, Python provides a more concise option:
>这种条件下，Python提供了更简洁的表达方法：

```Python
if 0 < x < 10:
	print('x is a positive single-digit number.')
```
（译者注：Python的这种友善度远远超过了C和C++，这也是为何我一直建议国内高校用Python取代C++来给本科生和研究生做编程入门课程。）


##5.8  Recursion 递归运算

It is legal for one function to call another; it is also legal for a function to call itself. It may not be obvious why that is a good thing, but it turns out to be one of the most magical things a program can do. For example, look at the following function:
>一个函数可以去调用另一个函数；函数来调用自己也是允许的。这就是递归，是程序最神奇的功能之一，现在可能还不好理解为什么，那么来看看下面这个函数为例：

```Python
def countdown(n):
	if n <= 0:
		print('Blastoff!')
	else:
		print(n)
		countdown(n-1)
```


If n is 0 or negative, it outputs the word, “Blastoff!” Otherwise, it outputs nand then calls a function named countdown—itself—passing n-1 as an argument.
What happens if we call this function like this?
>如果n为0或者负数，程序会输出『Blastoff！』。其他情况下，程序会调用自身来运行，以自身参数n减去1为参数。如果像下面这样调用这个函数会怎么样？


```Bash
>>> countdown(3) 
```


The execution of countdown begins with n=3, and since n is greater than 0, it outputs the value 3, and then calls itself...
The execution of countdown begins with n=2, and since n is greater than 0, it outputs the value 2, and then calls itself...
The execution of countdown begins with n=1, and since n is greater than 0, it outputs the value 1, and then calls itself...
The execution of countdown begins with n=0, and since n is not greater than 0, it outputs the word, “Blastoff!” and then returns.
The countdown that got n=1 returns.
The countdown that got n=2 returns.
The countdown that got n=3 returns.
And then you’re back in __main__. So, the total output looks like this:
>开始时候函数参数n是3，大于0，输出n的值3，然后调用自身，用n-1也就是2作为参数。。。
接下来的函数参数n是2，大于0，输出n的值2，然后调用自身，用n-1也就是1作为参数。。。
再往下去函数参数n是1，大于0，输出n的值1，然后调用自身，用n-1也就是0作为参数。。。
最后这次函数参数n是0，等于0了，输出『Blastoff！』，然后返回。
n=1的时候的countdown也执行完了，返回。
n=2的时候的countdown也执行完了，返回。
n=3的时候的countdown也执行完了，返回。
（译者注：这时候一定要注意不是输出字符串就完毕了，要返回的每一个层次的函数调用者。这里不理解的话说明对函数调用的过程掌握的不透彻，一定要好好想仔细了。）
接下来你就回到主函数__main__里面了。所以总的输出会如下所示：

```Bash
3
2
1
Blastoff!
```

A function that calls itself is recursive; the process of executing it is called recursion.
>调用自身的函数就是递归的；执行这种函数的过程就叫递归运算。

As another example, we can write a function that prints a string n times.
>我们再写一个用print把一个字符串s显示n次的例子：

```Python
def print_n(s, n):
    if n <= 0:
        return
    print(s)
    print_n(s, n-1)


s="Python is good"
n=4
print_n(s, n)

```

If n <= 0 the return statement exits the function. The flow of execution immediately returns to the caller, and the remaining lines of the function don’t run.
>如果n小于等于0了，返回语句return就会终止函数的运行。运行流程立即返回到函数调用者，函数其余各行的代码也都不会执行。


The rest of the function is similar to countdown: it displays s and then calls itself to display s n−1 additional times. So the number of lines of output is 1 + (n - 1), which adds up to n.
>函数其余部分的代码很容易理解：print一下s，然后调用自身，用n-1做参数来继续运行，这样就额外对s进行了n-1次的显示。所以输出的行数是1+（n-1），最终一共有n行输出。

For simple examples like this, it is probably easier to use a for loop. But we will see examples later that are hard to write with a for loop and easy to write with recursion, so it is good to start early.
>上面这种简单的例子，实际上用for循环更简单。不过后面我们就会遇到一些用for循环不太好写的例子了，这些情况往往用递归更简单，所以早点学习下递归是有好处的。



##5.9  Stack diagrams for recursive functions 递归函数的栈图

In Section 3.9, we used a stack diagram to represent the state of a program during a function call. The same kind of diagram can help interpret a recursive function.
>在本书的第三章第九节，我们用栈图来表征函数调用过程中程序的状态。同样是这种栈图，将有助于给大家展示递归函数的运行过程。

Every time a function gets called, Python creates a frame to contain the function’s local variables and parameters. For a recursive function, there might be more than one frame on the stack at the same time.
Figure 5.1 shows a stack diagram for countdown called with n = 3.
>每次有一个函数被调用的时候，Python都会创建一个框架来包含这个函数的局部变量和形式参数。对于递归函数来说，可能会在栈中同时生成多层次的框架。
>图5.1展示了前面样例中coundown函数在n=3的时候的栈图。

________________________________________
![Figure 5.1: Stack diagram.](http://7xnq2o.com1.z0.glb.clouddn.com/ThinkPythonFigure5.1.png)
Figure 5.1: Stack diagram.
________________________________________

As usual, the top of the stack is the frame for __main__. It is empty because we did not create any variables in __main__ or pass any arguments to it.
>栈图的开头依然是主函数__main__。这里主函数是空的，因为我们没有在主函数里面创建变量或者传递参数进去。
The four countdown frames have different values for the parameter n. The bottom of the stack, where n=0, is called the base case. It does not make a recursive call, so there are no more frames.
>四个coundown方框中形式参数n的值都是不同的。在栈图底部是n=0的时候，也叫基准条件。这时候不再进行递归调用，也就没有更多框架了。


As an exercise, draw a stack diagram for print_n called with s = 'Hello' and n=2. Then write a function called do_n that takes a function object and a number, n, as arguments, and that calls the given function n times.
>下面练习一下，画一个print_n函数的栈图，让s为字符串『Hello』，n为2。然后写一个函数，名字为do_n，使用一个操作对象和一个数字n作为实际参数，给出一个n作为次数来调用这个函数。



##5.10  Infinite recursion 无穷递归

If a recursion never reaches a base case, it goes on making recursive calls forever, and the program never terminates. This is known as infinite recursion, and it is generally not a good idea. Here is a minimal program with an infinite recursion:
>如果一个递归一直都不能到达基准条件，那就会持续不断地进行自我调用，程序也就永远不会终止了。这就叫无穷递归，一般这都不是个好事情哈。下面就是一个无穷递归的最简单的例子：

```Python
def recurse():
	recurse()
```
In most programming environments, a program with infinite recursion does not really run forever. Python reports an error message when the maximum recursion depth is reached:
>在大多数的开发环境下，无穷递归的程序并不会真的永远运行下去。Python会在函数达到允许递归的最大层次后返回一个错误信息：

```Bash
File "<stdin>", line 2, in recurse
File "<stdin>", line 2, in recurse
File "<stdin>", line 2, in recurse
File "<stdin>", line 2, in recurse
RuntimeError: Maximum recursion depth exceeded
```


This traceback is a little bigger than the one we saw in the previous chapter. When the error occurs, there are 1000 recurse frames on the stack!
>这个追踪会我们之前看到的长很多。这种错误出现的时候，栈中都已经有1000层递归框架了！

If you write encounter an infinite recursion by accident, review your function to confirm that there is a base case that does not make a recursive call. And if there is a base case, check whether you are guaranteed to reach it.
>如果你意外写出来一个无穷递归的代码，好好检查一下你的函数，一定要确保有一个基准条件来停止递归调用。如果存在了基准条件，检查一下一定要确保能使之成立。




##5.11  Keyboard input 键盘输入

The programs we have written so far accept no input from the user. They just do the same thing every time.
>目前为止咱们写过的程序还都没有接收过用户的输入。这写程序每次都是做一些同样的事情。

Python provides a built-in function called input that stops the program and waits for the user to type something. When the user presses Return or Enter, the program resumes and input returns what the user typed as a string. In Python 2, the same function is called raw_input.
>Python提供了内置的一个函数，名叫input，这个函数会停止程序运行，等待用户来输入一些内容。用户按下ESC或者Enter回车键，程序就恢复运行，input函数就把用户输入的内容作为字符串返回。在Python2里面，同样的函数名字不同，叫做raw_input。

```Bash
>>> text = input()
What are you waiting for?
>>> text
What are you waiting for?
```

Before getting input from the user, it is a good idea to print a prompt telling the user what to type. input can take a prompt as an argument:
>在用户输入内容之前，最好显示一些提示，来告诉用户需要输入什么内容。input函数能够把提示内容作为参数：

```Bash
>>> name = input('What...is your name?\n')
What...is your name?
Arthur, King of the Britons!
>>> name
Arthur, King of the Britons!
```

The sequence \n at the end of the prompt represents a newline, which is a special character that causes a line break. That’s why the user’s input appears below the prompt.
>提示内容末尾的\n表示要新建一行，这是一个特殊的字符，表示换行。因为有了换行字符，所以用户输入就跑到了提示内容下面去了。

If you expect the user to type an integer, you can try to convert the return value to int:
>如果你想要用户来输入一个整形变量，可以把返回的值手动转换一下：

```Bash
>>> prompt = 'What...is the airspeed velocity of an unladen swallow?\n'
>>> speed = input(prompt)
What...is the airspeed velocity of an unladen swallow?
42
>>> int(speed)
42
```


But if the user types something other than a string of digits, you get an error:
>如果用户输入的是其他内容，而不是一串数字，就会得到一个错误了：

```Python
>>> speed = input(prompt)
What...is the airspeed velocity of an unladen swallow?
What do you mean, an African or a European swallow?
>>> int(speed) ValueError: invalid literal for int() with base 10

```

We will see how to handle this kind of error later.
>稍后我们再来看看如何应对这种错误。



##5.12  Debugging 调试

When a syntax or runtime error occurs, the error message contains a lot of information, but it can be overwhelming. The most useful parts are usually:
>当语法错误或者运行错误出现的时候，错误信息会包含很多有用的信息，不过信息量太大，太繁杂。最有用的也就下面这两类：

* 	What kind of error it was, and
> 错误的类型是什么，以及
* 	Where it occurred.
> 错误的位置在哪里。

Syntax errors are usually easy to find, but there are a few gotchas. Whitespace errors can be tricky because spaces and tabs are invisible and we are used to ignoring them.


```Bash
>>> x = 5
>>>  y = 6
	File "<stdin>", line 1
	y = 6
	^
IndentationError: unexpected indent
```



In this example, the problem is that the second line is indented by one space. But the error message points to y, which is misleading. In general, error messages indicate where the problem was discovered, but the actual error might be earlier in the code, sometimes on a previous line.

>这个例子里面，错误的地方是第二行开头用一个空格来缩进了。但这个错误是指向y的，这就有点误导了。一般情况下，错误信息都会表示出发现问题的位置，但具体的错误可能是在此位置之前的代码引起的，有的时候甚至是前一行。

The same is true of runtime errors. Suppose you are trying to compute a signal-to-noise ratio in decibels. The formula is 
$$SNR_{db} = 10 \log_{10} (P_{signal} / P_{noise})$$. 
In Python, you might write something like this:
>同样情况也发生在运行错误的情况下。假设你试着用分贝为单位来计算信噪比。
公式为：$$SNR_{db} = 10 \log_{10} (P_{signal} / P_{noise})$$.。
>在Python，你可能像下面这样写：

```Python
import math
signal_power = 9
noise_power = 10
ratio = signal_power // noise_power
decibels = 10 * math.log10(ratio) print(decibels)
```




When you run this program, you get an exception:
>运行这个程序，你就会得到如下错误信息：


```Bash
Traceback (most recent call last):
	File "snr.py", line 5, in ?
		decibels = 10 * math.log10(ratio)
ValueError: math domain error
```


The error message indicates line 5, but there is nothing wrong with that line. To find the real error, it might be useful to print the value of ratio, which turns out to be 0. The problem is in line 4, which uses floor division instead of floating-point division.
>这个错误信息提示第五行，但那一行实际上并没有错。要找到真正的错误，就要输出一下ratio的值来看一下，结果发现是0了。那问题实际是在第四行，应该用浮点除法，结果多打了一个右斜杠，弄成了地板除法，才导致的错误。

You should take the time to read error messages carefully, but don’t assume that everything they say is correct.
>所以你得花点时间仔细阅读错误信息，但不要轻易就认为出错信息说的内容都是完全正确可靠的。



##5.13  Glossary 术语列表

floor division:
An operator, denoted //, that divides two numbers and rounds down (toward zero) to an integer.
>地板除法：一种运算符，双右斜杠，把两个数相除，舍弃小数位，结果为整形。

modulus operator:
An operator, denoted with a percent sign (%), that works on integers and returns the remainder when one number is divided by another.
>求模取余：一种运算符，百分号%，对整形起作用，返回两个数字相除的余数。

boolean expression:
An expression whose value is either True or False.
>布尔表达式：一种值为真或假的表达式。

relational operator:
One of the operators that compares its operands: ==, !=, >, <, >=, and <=.
>关系运算符：对比运算对象关系的运算符：==相等, !=不等, >大于, <小于, >=大于等于, 以及<=小于等于。

logical operator:
One of the operators that combines boolean expressions: and, or, and not.
>逻辑运算符：把布尔表达式连接起来的运算符：and且，or或，以及not非。

conditional statement:
A statement that controls the flow of execution depending on some condition.
>条件语句：控制运行流程的语句，根据不同条件有不同语句去运行。

condition:
The boolean expression in a conditional statement that determines which branch runs.
>条件：条件语句所适用的布尔表达式，根据真假来决定运行分支。

compound statement:
A statement that consists of a header and a body. The header ends with a colon (:). The body is indented relative to the header.
>复合语句：包含头部与语句体的一套语句组合。头部要有冒号做结尾，语句体相对于头部要有一次缩进。

branch:
One of the alternative sequences of statements in a conditional statement.
>分支：条件语句当中备选的一系列语句。

chained conditional:
A conditional statement with a series of alternative branches.
>链式条件：一系列可选分支构成的条件语句。

nested conditional:
A conditional statement that appears in one of the branches of another conditional statement.
>嵌套条件：条件语句分支中继续包含次级条件语句的情况。

return statement:
A statement that causes a function to end immediately and return to the caller.
>返回语句：一种特殊的语句，功能是终止当前函数，立即跳出到函数调用者。

recursion:
The process of calling the function that is currently executing.
>递归：函数对自身进行调用的过程。

base case:
A conditional branch in a recursive function that does not make a recursive call.
>基准条件：递归函数中一个条件分支，要实现终止递归调用。

infinite recursion:
A recursion that doesn’t have a base case, or never reaches it. Eventually, an infinite recursion causes a runtime error.
>无穷递归：一个没有基准条件的递归，或者永远无法达到基准条件的递归。一般无穷递归总会引起运行错误。






##5.14  Exercises 练习

###Exercise 1  练习1

The time module provides a function, also named time, that returns the current Greenwich Mean Time in “the epoch”, which is an arbitrary time used as a reference point. On UNIX systems, the epoch is 1 January 1970.
>time模块提供了一个名字同样叫做time的函数，会返回当前格林威治时间的时间戳，就是以某一个时间点作为初始参考值。在Unix系统中，时间戳的参考值是1970年1月1号。
>（译者注：时间戳就是系统当前时间相对于1970.1.1 00:00:00以秒计算的偏移量，时间戳是惟一的。）

```Bash
>>> import time
>>> time.time() 1437746094.5735958
```


Write a script that reads the current time and converts it to a time of day in hours, minutes, and seconds, plus the number of days since the epoch.
>写一个脚本，读取当前的时间，把这个时间转换以天为单位，剩余部分转换成小时-分钟-秒的形式，加上参考时间以来的天数。

###Exercise 2  练习2

Fermat’s Last Theorem says that there are no positive integers a, b, and c such that
$$a^n + b^n = c^n$$
for any values of n greater than 2.
>费马大定理内容为，a、b、c、n均为正整数，在n大于2的情况，下面的等式关系不成立：
>$$a^n + b^n = c^n$$

1.	Write a function named check_fermat that takes four parameters—a, b, c and n—and checks to see if Fermat’s theorem holds. If n is greater than 2 and

>写一个函数，名叫check_fermat，这个函数有四个形式参数：a、b、c以及n，检查一下费马大定理是否成立，看看在n大于2的情况下下列等式
>$$a^n + b^n = c^n$$
>是否成立。

2.	The program should print, “Holy smokes, Fermat was wrong!” Otherwise the program should print, “No, that doesn’t work.”
>要求程序输出『Holy smokes, Fermat was wrong!』或者『No, that doesn’t work.』

3.	Write a function that prompts the user to input values for a, b, c and n, converts them to integers, and uses check_fermat to check whether they violate Fermat’s theorem.
>写一个函数来提醒用户要输入a、b、c和n的值，然后把输入值转换为整形变量，接着用check_fermat这个函数来检查他们是否违背了费马大定理。

###Exercise 3  练习3

If you are given three sticks, you may or may not be able to arrange them in a triangle. For example, if one of the sticks is 12 inches long and the other two are one inch long, you will not be able to get the short sticks to meet in the middle. For any three lengths, there is a simple test to see if it is possible to form a triangle:
>给你三根木棍，你能不能把它们拼成三角形呢？比如一个木棍是12英寸长，另外两个是1英寸长，这两根短的就不够长，无法拼成三角形了。
>（译者注：1英寸=2.54厘米）对于任意的三个长度，有一个简单的方法来检测它们能否拼成三角形：

If any of the three lengths is greater than the sum of the other two, then you cannot form a triangle. Otherwise, you can. (If the sum of two lengths equals the third, they form what is called a “degenerate” triangle.)
>只要三个木棍中有任意一个的长度大于其他两个的和，就拼不成三角形了。必须要任意一个长度都小于两边和才能拼成三角形。（如果两边长等于第三边，就只能组成所谓『退化三角形』了。译者注：实际上这不就成了线段了么？）

1.	Write a function named is_triangle that takes three integers as arguments, and that prints either “Yes” or “No”, depending on whether you can or cannot form a triangle from sticks with the given lengths.
>写一个叫做is_triangle的函数，用三个整形变量为实际参数，函数根据你输入的值能否拼成三角形来判断输出『Yes』或者『No』。

2.	Write a function that prompts the user to input three stick lengths, converts them to integers, and uses is_triangle to check whether sticks with the given lengths can form a triangle.
>写一个函数来提示下用户，要输入三遍长度，把它们转换成整形，用is_triangle函数来检测这些给定长度的边能否组成三角形。

Exercise 4   练习4

What is the output of the following program? Draw a stack diagram that shows the state of the program when it prints the result.
>下面的代码输出会是什么？画一个栈图来表示一下如下例子中程序输出结果时候的状态。

```Python
def recurse(n, s):
	if n == 0:
		print(s)
	else:
		recurse(n-1, n+s)
recurse(3, 0)
```


1.	What would happen if you called this function like this: recurse(-1, 0)?
>recurse(-1, 0)这样的调用函数会有什么效果？

2.	Write a docstring that explains everything someone would need to know in order to use this function (and nothing else).
>为这个函数写一个文档字符串，解释一下用法（仅此而已）。

The following exercises use the turtle module, described in Chapter 4:
>接下来的练习用到了第四章我们提到过的turtle小乌龟模块。


###Exercise 5  练习5
Read the following function and see if you can figure out what it does. Then run it (see the examples in Chapter 4).
>阅读下面的函数，看看你能否弄清楚函数的作用。运行一下试试（参考第四章里面的例子来酌情修改代码）。

```Python
def draw(t, length, n):
	if n == 0:
		return
	angle = 50
	t.fd(length*n)
	t.lt(angle)
	draw(t, length, n-1)
	t.rt(2*angle)
	draw(t, length, n-1)
	t.lt(angle)
	t.bk(length*n)
```

________________________________________
![Figure 5.2: A Koch curve.](http://7xnq2o.com1.z0.glb.clouddn.com/ThinkPythonFigure5.2Koch%20curve.png)
Figure 5.2: A Koch curve.
________________________________________



###Exercise 6  练习6


The Koch curve is a fractal that looks something like Figure 5.2. To draw a Koch curve with length x, all you have to do is
>Koch科赫曲线是一种分形曲线，外观如图5.2所示。要画长度为x的这种曲线，你要做的步骤如下：

1.	Draw a Koch curve with length x/3.
>画一个长度为三分之一x的Koch曲线。

2.	Turn left 60 degrees.
>左转60度。

3.	Draw a Koch curve with length x/3.
>画一个长度为三分之一x的Koch曲线。

4.	Turn right 120 degrees.
>右转120度。

5.	Draw a Koch curve with length x/3.
>画一个长度为三分之一x的Koch曲线。

6.	Turn left 60 degrees.
>左转60度。

7.	Draw a Koch curve with length x/3.
>画一个长度为三分之一x的Koch曲线。

The exception is if x is less than 3: in that case, you can just draw a straight line with length x.
>特例是当x小于3的时候：这种情况下，你就可以只画一个长度为x的直线段。

1.	Write a function called koch that takes a turtle and a length as parameters, and that uses the turtle to draw a Koch curve with the given length.
>写一个叫做koch的函数，用一个小乌龟turtle以及一个长度length做形式参数，用这个小乌龟来画给定长度length的Koch曲线。

2.	Write a function called snowflake that draws three Koch curves to make the outline of a snowflake.[Solution](http://thinkpython2.com/code/koch.py).
>写一个叫做snowflake的函数，画三个Koch曲线来制作一个雪花的轮廓。[参考代码](http://thinkpython2.com/code/koch.py)




3.	The Koch curve can be generalized in several ways. See [here](http://en.wikipedia.org/wiki/Koch_snowflake) for examples and implement your favorite.
>生成Koch曲线的方法还有很多。点击 [这里](http://en.wikipedia.org/wiki/Koch_snowflake)来查看更多的例子，探索一下看看你喜欢哪个。



