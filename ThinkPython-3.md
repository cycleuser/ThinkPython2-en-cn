Title: ThinkPython 双语学编程 Chapter 3 
Date: 2015-10-24
Category: ThinkPython
Tag: 双语,Python,ThinkPython

#Chapter 3  Functions 函数
In the context of programming, a function is a named sequence of statements that performs a computation. When you define a function, you specify the name and the sequence of statements. Later, you can “call” the function by name.

>在编程的语境下，“函数”这个词的意思是对一系列语句的组合，这些语句共同完成一种运算。定义函数的时候，你要给这个函数指定一个名字，另外还好写出这些进行运算的语句。定义完成后，就可以通过函数名来“调用”函数。

##3.1  Function calls 函数调用
We have already seen one example of a function call:

>此前我们已经见识过函数调用的一个例子了：


```Python
>>> type(42) 
<class 'int'> 
```

The name of the function is type. The expression in parentheses is called the argument of the function. The result, for this function, is the type of the argument.

>这个函数的名字就是tpye，括号里面的表达式叫做函数的参数。这个函数的结果是返回参数的类型。

It is common to say that a function “takes” an argument and “returns” a result. The result is also called the return value.
Python provides functions that convert values from one type to another. The int function takes any value and converts it to an integer, if it can, or complains otherwise:

>一般来说，函数都要“传入”一个参数，“返回”一个结果。结果也被叫做返回值。Python提供了一些转换数值类型的函数。比如int这个函数就可以把值转换成整形，但不是什么都能转的，遇到不能转换的就会报错了，如下所示：

```Python 
>>> int('32') 
32 
>>> int('Hello') 
ValueError: invalid literal for int(): Hello
```
 
int can convert floating-point values to integers, but it doesn’t round off; it chops off the fraction part:

>int这个函数能把浮点数转成整形，但不是很完美，小数部分就都给砍掉了。


```Python 
>>> int(3.99999) 
3 
>>> int(-2.3) 
-2 
```

float converts integers and strings to floating-point numbers:
>float能把整形和字符串转变成浮点数：
```Python 
>>> float(32) 
32.0 
>>> float('3.14159') 
3.14159 
```

Finally, str converts its argument to a string:
>最后来看下，str可以把参数转变成字符串：

```Python 
>>> str(32) 
'32' 
>>> str(3.14159) 
'3.14159' 
```
##3.2  Math functions

Python has a math module that provides most of the familiar mathematical functions. A module is a file that contains a collection of related functions.
>Python内置了一个数学模块，这一模块提供了绝大部分常用的数学函数。模块就是一系列相关函数的集合成的文件。

Before we can use the functions in a module, we have to import it with an import statement:
>在使用模块中的函数之前，必须先要导入这个模块，使用导入语句：

```Python 
>>> import math 
```

This statement creates a module object named math. If you display the module object, you get some information about it:
>这个语句建立了一个模块对象，名字叫做math。如果你让这个模块对象显示一下，你就会得到与之相关的信息了：

```Python
>>> math 
<module 'math' (built-in)> 
```

The module object contains the functions and variables defined in the module. To access one of the functions, you have to specify the name of the module and the name of the function, separated by a dot (also known as a period). This format is called dot notation.
>模块对象包含了一些已经定义好的函数和变量。指定模块名和函数名，要用点（也就是英文的句号）来连接模块名和函数名，就可以调用指定的函数了。

```Python
>>> ratio = signal_power / noise_power 
>>> decibels = 10 * math.log10(ratio)  
>>> radians = 0.7 
>>> height = math.sin(radians) 
```

The first example uses math.log10 to compute a signal-to-noise ratio in decibels (assuming that signal_power and noise_power are defined). The math module also provides log, which computes logarithms base e.
第一个例子用了数学的log10的函数，来计算信噪比的分贝值（假设信号强度和噪音强度都已知了）。数学模块同时也提供了log，用自然底数e取对数的函数。

The second example finds the sine of radians. The name of the variable is a hint that sin and the other trigonometric functions (cos, tan, etc.) take arguments in radians. To convert from degrees to radians, divide by 180 and multiply by π:
>第二个例子是对弧度值计算正弦值。通过变量名你应该能推测出正弦以及其他的三角函数（比如余弦、正切等等）都要用弧度值作为参数。所以要把角度的值从度转换成弧度，方法就是除以180然后再乘以圆周率π：


```Python
>>> degrees = 45 
>>> radians = degrees / 180.0 * math.pi 
>>> math.sin(radians) 
0.707106781187 
```

The expression math.pi gets the variable pi from the math module. Its value is a floating-point approximation of π, accurate to about 15 digits.
>math.pi这个表达式从数学模块中得到π的一个大概精确到15位的近似值，存成一个浮点数。

If you know trigonometry, you can check the previous result by comparing it to the square root of two divided by two:
>了解了三角函数之后，你可以用试着把2的平方根除以二，然后对比一下这个结果和上一个结果：

```Python
>>> math.sqrt(2) / 2.0 
0.707106781187 
```

>译者注：画一个三角形就知道了，45度角两直角边是单位1，斜边必然是2的平方根了，对应的正弦余弦也都是这个值了。大家应该能理解吧？

##3.3  Composition 组合

So far, we have looked at the elements of a program—variables, expressions, and statements—in isolation, without talking about how to combine them.
>目前为止，我们已经见识了一个程序所需要的大部分元素了：变量、表达式、语句。不过咱们都是一个个单独看到的，还没有把它们结合起来试试。

One of the most useful features of programming languages is their ability to take small building blocks and compose them. For example, the argument of a function can be any kind of expression, including arithmetic operators:
>一门编程语言最有用的功能莫过于能够用一个个小模块来拼接创作。例如函数的参数可以是任何一种表达式，包括代数运算符：

```Python
x = math.sin(degrees / 360.0 * 2 * math.pi) ß
```

And even function calls:
>再或者函数的调用本身也可以作为参数：

```Python
x = math.exp(math.log(x+1)) 
```

Almost anywhere you can put a value, you can put an arbitrary expression, with one exception: the left side of an assignment statement has to be a variable name. Any other expression on the left side is a syntax error (we will see exceptions to this rule later).
>你可以在任何地方放一个值，放任何一个表达式，只有一个例外：一个声明语句的左边必须是变量名。任何其他的表达式放到等号左边都会导致语法错误（当然也有例外，等会再给介绍）。


```Python
>>> minutes = hours * 60                 # right 
>>> hours * 60 = minutes                 # wrong! 
SyntaxError: can't assign to operator 
```

>译者注：上述例子里面把表达式复制为变量是不行的，所说的例外估计是指尤达大师命名法，这个后面看到再说。

##3.4  Adding new functions 添加新函数

So far, we have only been using the functions that come with Python, but it is also possible to add new functions. A function definition specifies the name of a new function and the sequence of statements that run when the function is called.
Here is an example:
>目前我们学到了一些Python自带的函数，自己添加新的函数也是可以的。函数定义要指定这个心函数的名字，还需要一系列语句放到这个函数里面，当调用这个函数的时候，就会运行这些语句了。

```Python
def print_lyrics():
    print("I'm a lumberjack, and I'm okay.")
    print("I sleep all night and I work all day.")
```


def is a keyword that indicates that this is a function definition. The name of the function is print_lyrics. The rules for function names are the same as for variable names: letters, numbers and underscore are legal, but the first character can’t be a number. You can’t use a keyword as the name of a function, and you should avoid having a variable and a function with the same name.
>这里的def就是一个关键词，意思是这是在定义一个函数。函数的名字就是print_lyrics，函数的命名规则和变量命名规则基本差不多，都是字幕梳子或者下划线，但是不能用数字打头。另外也不能用关键词做函数名，还要注意尽量避免函数名和变量名发生重复。


The empty parentheses after the name indicate that this function doesn’t take any arguments.
>函数名后面的括号是空的，意思是这个函数不需要参数。

The first line of the function definition is called the header; the rest is called the body. The header has to end with a colon and the body has to be indented. By convention, indentation is always four spaces. The body can contain any number of statements.
>函数定义的第一行叫做头部，剩下的叫做函数体。函数头部的末尾必须有一个冒号，函数体必须是相对函数头部有缩进的，距离行首相对于函数头要有四个空格的距离。函数体可以有任意长度的语句。

（译者注：缩进是Python最强制的要求，本书的翻译用的MarkDown在生成的时候可能未必能够完美缩进，所以大家多注意一下自己调整哈，这个超级重要！）


The strings in the print statements are enclosed in double quotes. Single quotes and double quotes do the same thing; most people use single quotes except in cases like this where a single quote (which is also an apostrophe) appears in the string.
>在打印语句中，要打印的字符串需要用双引号括着。单引号和双引号效果一样，除非是字符串中已经出现了单引号，大家一般都是用单引号的。


All quotation marks (single and double) must be “straight quotes”, usually located next to Enter on the keyboard. “Curly quotes”, like the ones in this sentence, are not legal in Python.
>所有的引号都必须是键盘上直接是引号的那个"键，无论是单引号还是双引号。就是回车键左边那个。“Curly quotes”这种引号，在Python里面是非法的。


If you type a function definition in interactive mode, the interpreter prints dots (...) to let you know that the definition isn’t complete:
>如果你在交互模式下面定义函数，解释器会显示三个小点来提醒你定义还没有完成：

```Python
>>> def print_lyrics(): 
...     
print("I'm a lumberjack, and I'm okay.") ...     
print("I sleep all night and I work all day.") ... 
```

To end the function, you have to enter an empty line.
Defining a function creates a function object, which has type function:
>在函数定义完毕的结尾，必须输入一行空白行。定义函数会创建一个函数类的对象，有type函数。

```Python
>>> print(print_lyrics) 
<function print_lyrics at 0xb7e99e9c> 
>>> type(print_lyrics) 
<class 'function'> 
```

The syntax for calling the new function is the same as for built-in functions:
>调用新函数的语法和调用内置函数是一样的：

```Python
>>> print_lyrics() 
I'm a lumberjack, and I'm okay. I sleep all night and I work all day. 
```


Once you have defined a function, you can use it inside another function. For example, to repeat the previous refrain, we could write a function called repeat_lyrics:
>一旦你定义了一个函数，就可以在其它函数里面来调用这个函数。比如咱们重复一下刚刚讨论的，写一个叫做重repeat_lyrics的函数。

```Python
def repeat_lyrics():
	print_lyrics()
	print_lyrics()
    
```

And then call repeat_lyrics:
>然后调用一下这个函数：

```Python
>>> repeat_lyrics() 
I'm a lumberjack, and I'm okay. I sleep all night and I work all day. I'm a lumberjack, and I'm okay. I sleep all night and I work all day. 
```

But that’s not really how the song goes.
>当然了，实际这首歌可不是这样的哈。


##3.5  Definitions and uses 定义并使用
Pulling together the code fragments from the previous section, the whole program looks like this:
>把前面这些小块的代码来整合一下，整体上程序看着大概是这样的：


```Python
def print_lyrics():     
	print("I'm a lumberjack, and I'm okay.")     
	print("I sleep all night and I work all day.")  

def repeat_lyrics():     
	print_lyrics()     
	print_lyrics()  

repeat_lyrics() 

```

This program contains two function definitions: print_lyrics and repeat_lyrics. Function definitions get executed just like other statements, but the effect is to create function objects. The statements inside the function do not run until the function is called, and the function definition generates no output.
>这个程序包含两个函数的定义：print_lyrics以及repeat_lyrics，函数定义的执行就和其他语句一样，但是效果是创建函数对象。函数定义中的语句直到函数被调用的时候才会运行，函数的定义本身不会有任何输出。


As you might expect, you have to create a function before you can run it. In other words, the function definition has to run before the function gets called.
>如你所愿了，你可以建立一个函数，然后运行一下试试了。换种说法就是，在调用之前一定要先把函数定义好。

As an exercise, move the last line of this program to the top, so the function call appears before the definitions. Run the program and see what error message you get.
Now move the function call back to the bottom and move the definition of print_lyrics after the definition of repeat_lyrics. What happens when you run this program?
>作为练习，把这个程序的最后一行放到顶部，这样函数调用就在函数定义之前了。运行一下看看出错的信息是什么。
>然后再把函数调用放到底部，把print_lyrics这个函数的定义放到repeat_lyrics这个函数的后面。再看看这次运行会出现什么样子？


##3.6  Flow of execution 运行流程
To ensure that a function is defined before its first use, you have to know the order statements run in, which is called the flow of execution.
>为了确保一个函数在首次被调用之前已经定义，你必须要之道语句运行的顺序，也就是所谓『运行流程』。


Execution always begins at the first statement of the program. Statements are run one at a time, in order from top to bottom.
>一个Python程序都是从第一个语句开始运行的。从首至尾，每次运行一个语句。


Function definitions do not alter the flow of execution of the program, but remember that statements inside the function don’t run until the function is called.
>函数的定义并不会改变程序的运行流程，但要注意，函数体内部的语句只有在函数被调用的时候才会运行。


A function call is like a detour in the flow of execution. Instead of going to the next statement, the flow jumps to the body of the function, runs the statements there, and then comes back to pick up where it left off.
>函数调用就像是运行流程有了绕道的行为。没有直接去执行下一个语句，运行流跳入到函数体内，运行里面的语句，然后再回来从离开的地方继续执行。


That sounds simple enough, until you remember that one function can call another. While in the middle of one function, the program might have to run the statements in another function. Then, while running that new function, the program might have to run yet another function!
>这么解释很简明易懂了，只要你记住一个函数可以调用另一个就行。在一个函数的中间，程序有可能必须运行一下其他函数中的语句。所以运行新的函数的时候，程序可能也必须运行其他的函数！

译者注：看着很绕嘴，其实蛮简单的，就是跳出跳入互相调用而已。


Fortunately, Python is good at keeping track of where it is, so each time a function completes, the program picks up where it left off in the function that called it. When it gets to the end of the program, it terminates.
>幸运的是，Python很善于追踪应该执行的位置，所以每次一个函数执行完毕了，程序都会回到当时跳出的位置，然后继续运行。等执行到了程序的末尾，就终止了。


In summary, when you read a program, you don’t always want to read from top to bottom. Sometimes it makes more sense if you follow the flow of execution.
>总的来说，你阅读一个程序的时候，并不一定总是要从头到尾来读的。有时候你要按照运行流程来读才更好理解。


##3.7  Parameters and arguments 形式参数和实际参数



译者注：这里提到的形参和实参实际上是传值方式的区别，这个在最基本的编程入门课程中老师应该都比较强调的。实际参数就是调用函数时候传给他的那个参数；而形式参数可以理解为函数内部定义用的参数。老外对这个的思辩也很多。这里我先不说太多，翻译着再看。
大家可以去网上多搜索一下，比如在[StackOverflow](http://stackoverflow.com/questions/1788923/parameter-vs-argument)和[MSDN](https://msdn.microsoft.com/en-us/library/9kewt1b3.aspx)

Some of the functions we have seen require arguments. For example, when you call math.sin you pass a number as an argument. Some functions take more than one argument: math.pow takes two, the base and the exponent.
>我们已经看到了一些函数了，他们都需要实际参数。比如当你调用数学的正弦函数的时候你就需要给它一个数值作为实际参数。有的函数需要一个以上的实际参数，比如幂指数函数需要两个，一个是底数，一个是幂次。


Inside the function, the arguments are assigned to variables called parameters. Here is a definition for a function that takes an argument:
>在函数里面，实际参数会被赋值给形式参数。下面就是一个使用单个实际参数的函数的定义：


```Python
def print_twice(bruce):
	print(bruce)     
	print(bruce) 
    
```


This function assigns the argument to a parameter named bruce. When the function is called, it prints the value of the parameter (whatever it is) twice.
This function works with any value that can be printed.
>这个函数把传来的实际参数的值赋给了一个名字叫做burce的形式参数。当函数被调用的时候，就会打印出形式参数的值两次（无论是什么内容）。任何能打印的值都适用于这个函数。

```Python
>>> print_twice('Spam') 
Spam 
Spam 
>>> print_twice(42) 
42 
42 
>>> print_twice(math.pi) 
3.14159265359 
3.14159265359 
```


The same rules of composition that apply to built-in functions also apply to programmer-defined functions, so we can use any kind of expression as an argument for print_twice:
适用于Python内置函数的组合规则对自定义的函数也是适用的，所以我们可以把表达式作为实际参数：

```Python
>>> print_twice('Spam '*4) 
Spam Spam Spam Spam 
Spam Spam Spam Spam 
>>> print_twice(math.cos(math.pi)) 
-1.0 
-1.0 
```


The argument is evaluated before the function is called, so in the examples the expressions 'Spam '*4 and math.cos(math.pi) are only evaluated once.
You can also use a variable as an argument:
>实际参数在函数被调用之前要先被运算一下，所以上面例子中作为实际参数的两个表达式都是在print_twice函数调用之前仅计算了一次。
>当然了，也可以用变量做实际参数了：

```Python
>>> michael = 'Eric, the half a bee.' 
>>> print_twice(michael) 
Eric, the half a bee. Eric, the half a bee. 
```


The name of the variable we pass as an argument (michael) has nothing to do with the name of the parameter (bruce). It doesn’t matter what the value was called back home (in the caller); here in print_twice, we call everybody bruce.
>咱们传递给函数的这个实际参数是一个变量，这个变量名michael和函数内部的形式参数bruce没有任何关系。在程序主体内部参数传过去就行了，参数名字对于函数内部没有作用；比如在这个print_twice函数里面，任何传来的值，在这个print_twice函数体内，都被叫做bruce。


译者注：这里要跟大家解释一下，传递参数的时候用的是实际参数，是把这个实际参数的值交给调用的函数，函数内部接收这个值，可以命名成任意其他名字的形式参数，差不多就这么个意思了。



##3.8  Variables and parameters are local 函数内部变量和形参都是局部的

When you create a variable inside a function, it is local, which means that it only exists inside the function. For example:
>在函数内部建立一个变量，这个变量是仅在函数体内部才存在。例如：

```Python
def cat_twice(part1, part2):     
	cat = part1 + part2     
	print_twice(cat) 
    
```


This function takes two arguments, concatenates them, and prints the result twice. Here is an example that uses it:
>这个函数得到两个实参，把它们连接起来，然后调用print_twice函数来输出结果两次。


```Python
>>> line1 = 'Bing tiddle ' 
>>> line2 = 'tiddle bang.' 
>>> cat_twice(line1, line2) 
Bing tiddle tiddle bang. 
Bing tiddle tiddle bang.
```


When cat_twice terminates, the variable cat is destroyed. If we try to print it, we get an exception:
>当cat_twice运行完毕了，这个名字叫做cat的变量就销毁了。咱们再尝试着打印它一下，就会得到异常：

```Python
>>> print(cat) 
NameError: name 'cat' is not defined 
```
Parameters are also local. For example, outside print_twice, there is no such thing as bruce.
>形式参数也是局部起作用的。例如在print_twice这个函数之外，是不存在bruce这个变量的。

译者注：当然你可以在函数外定义一个同名变量叫做bruce，但这两个没有关系，大家可以动手自己试试，这也是作者所鼓励的一种探索思维。


##3.9  Stack diagrams 栈图

To keep track of which variables can be used where, it is sometimes useful to draw a stack diagram. Like state diagrams, stack diagrams show the value of each variable, but they also show the function each variable belongs to.
>要追踪一个变量能在哪些位置使用，咱们就可以画个图表来实现，这种图表叫做栈图。栈图和我们之前提到的状态图有些相似，也会表征每个变量的值，不同的是栈图还会标识出每个变量所属的函数。

Each function is represented by a frame. A frame is a box with the name of a function beside it and the parameters and variables of the function inside it. The stack diagram for the previous example is shown in Figure 3.1.
>每个函数都用一个框架来表示。框架的边上要标明函数的名字，框内填写函数内部的形参和变量。上文中样例代码的栈图如下图3.1所示。

![Figure 3.1: Stack diagram.](http://7xnq2o.com1.z0.glb.clouddn.com/ThinkPythonfigure3.1.png)
Figure 3.1: Stack diagram.
>图3.1 栈图

The frames are arranged in a stack that indicates which function called which, and so on. In this example, print_twice was called by cat_twice, and cat_twice was called by __main__, which is a special name for the topmost frame. When you create a variable outside of any function, it belongs to__main__.
>一个栈中的这些框也表示了函数调用的关系等等。在上面这个例子中，print_twice被cat_twice调用了两次，而cat_twice被__main__这个函数调用。__main__这个函数很特殊，属于最外层框架，也被叫做主函数。当你在所有函数之外建立一个变量的时候，这个变量就属于主函数所有。

Each parameter refers to the same value as its corresponding argument. So,part1 has the same value as line1, part2 has the same value as line2, and bruce has the same value as cat.
>每个形式参数都保存了所对应的实际参数的值。因此part1的值和line1一样，part2的值就和line2一样，同理可知bruce的值就和cat一样了。


If an error occurs during a function call, Python prints the name of the function, the name of the function that called it, and the name of the function that called that, all the way back to __main__.
>如果函数调用的时候出错了，Python会打印出这个出错函数的名字，调用这个出错函数的函数名，以及调用这个调用了出错函数的函数的函数名，一直追溯到主函数。（译者注：好绕口哈。。。就是会溯源回去啦。）

For example, if you try to access cat from within print_twice, you get a NameError:
>例如，如果你想在print_twice这个函数中读取cat的值，就会得到一个变量名错误：

```Python
Traceback (innermost last):  
File "test.py", line 13, in __main__  
cat_twice(line1, line2)   
File "test.py", line 5, in cat_twice     
print_twice(cat)   
File "test.py", line 9, in print_twice     
print(cat) 
NameError: name 'cat' is not defined 
```

This list of functions is called a traceback. It tells you what program file the error occurred in, and what line, and what functions were executing at the time. It also shows the line of code that caused the error.
>这个一系列的函数列表，就是一个追溯了。这回告诉你哪个程序文件出了错误，哪一行出了错误，以及当时哪些函数在运行。还会告诉你引起错误的代码所在行号。（译者注：这个简直太棒了，大家一定要留心这个功能以及出错提示，以后要用来解决很多bug呢。）


The order of the functions in the traceback is the same as the order of the frames in the stack diagram. The function that is currently running is at the bottom.
>追溯中对函数顺序的排列是同栈图的方框顺序一样的。当前运行的函数会放在最底部。


##3.10  Fruitful functions and void functions 有返回值的函数 和 无返回值的函数


Some of the functions we have used, such as the math functions, return results; for lack of a better name, I call them fruitful functions. Other functions, like print_twice, perform an action but don’t return a value. They are called void functions.
>咱们用过的一些函数，比如数学的函数，都会返回各种结果；也没别的好名字，就叫他们有返回值函数。其他的函数，比如print_twice，都是进行一些操作，但不返回值。那就叫做无返回值函数好了。

When you call a fruitful function, you almost always want to do something with the result; for example, you might assign it to a variable or use it as part of an expression:
>当你调用一个有返回值的函数的时候，一般总是要利用一下结果的；比如，你可能需要把结果赋值给某个变量，然后在表达式里面来使用一下：

```Python
x = math.cos(radians) 
golden = (math.sqrt(5) + 1) / 2 

```

When you call a function in interactive mode, Python displays the result:
>当你在交互模式调用一个函数的时候，Python会显示结果：

```Python
>>> math.sqrt(5) 2.2360679774997898 
```

But in a script, if you call a fruitful function all by itself, the return value is lost forever!
>如果是脚本模式，你运行一个有返回值的函数，但没有利用这个返回值，这个返回值就会永远丢失了！（译者注：只要有返回值就一定要利用！）

```Python
math.sqrt(5) 
```


This script computes the square root of 5, but since it doesn’t store or display the result, it is not very useful.
>这个脚本计算了5的平方根，但没存储下来，也没有显示出来，所以就根本没用了。


Void functions might display something on the screen or have some other effect, but they don’t have a return value. If you assign the result to a variable, you get a special value called None.
>无返回值的函数要么就是屏幕上显示出一些内容，要么就有其他的功能，但就是没有返回值。如果你把这种函数的结果返回给一个变量，就会的到特殊的值：空。


```Python
>>> result = print_twice('Bing') 
Bing Bing 
>>> print(result) 
None 
```


The value None is not the same as the string 'None'. It is a special value that has its own type:
>这种None是空值的意思，和字符串'None'是不一样的。是一种特殊的值，并且有自己的类型。（译者注，就相当于null了。）


```Python
>>> print(type(None)) 
<class 'NoneType'> 

```

The functions we have written so far are all void. We will start writing fruitful functions in a few chapters.
>我们目前为止写的函数还都是无返回值的。接下来的新的章节里面，咱们就要开始写一些有返回值的函数了。



##3.11  Why functions? 为啥要用函数？

It may not be clear why it is worth the trouble to divide a program into functions. There are several reasons:
>为什么要费这么多力气来把程序划分成一个个函数呢？这么麻烦值得么？原因如下：


*	Creating a new function gives you an opportunity to name a group of statements, which makes your program easier to read and debug.
>*	创建一个新的函数，你就可以把一组语句用一个名字来命名，这样你的程序读起来就清晰多了，后期维护调试也方便。


*	Functions can make a program smaller by eliminating repetitive code. Later, if you make a change, you only have to make it in one place.
>*	函数的出现能够避免代码冗余，程序内的一些重复的内容就会简化了，变得更小巧。而且在后期进行修改的时候，你只要改函数中的一处地方就可以了，很方便。

*	Dividing a long program into functions allows you to debug the parts one at a time and then assemble them into a working whole.
>*	把长的程序切分成一个个函数，你就可以一步步来debug调试，每次只应对一小部分就可以，然后把它们组合起来就可以用了。

*	Well-designed functions are often useful for many programs. Once you write and debug one, you can reuse it.
>*	精细设计的函数会对很多程序都有用处。一旦你写好了并且除了错，这种函数代码可以再利用。



##3.12  Debugging 调试

One of the most important skills you will acquire is debugging. Although it can be frustrating, debugging is one of the most intellectually rich, challenging, and interesting parts of programming.
>给程序调试是你应当掌握的最关键技能之一了。尽管调试的过程会有挫败感，也依然是最满足智力，最有挑战性，也是编程过程中最有趣的一个项目了。


In some ways debugging is like detective work. You are confronted with clues and you have to infer the processes and events that led to the results you see.
>某种程度上，调试像是侦探工作一样。你面对着很多线索，必须推断出导致当前结果的整个过程和事件。

Debugging is also like an experimental science. Once you have an idea about what is going wrong, you modify your program and try again. If your hypothesis was correct, you can predict the result of the modification, and you take a step closer to a working program.
>调试也有点像一门实验科学。一旦你有了一个关于所出现的错误的想法，你就修改一下程序再试试看。如果你的假设是正确的，你就能够预料到修改导致的结果，这样在编程的水平上，你就上了一层台阶了，距离让程序工作起来也更近了。

If your hypothesis was wrong, you have to come up with a new one. As Sherlock Holmes pointed out, “When you have eliminated the impossible, whatever remains, however improbable, must be the truth.” (A. Conan Doyle, The Sign of Four)
>如果你的推测是错误的，你必须提出新的来。就像夏洛克.福尔摩斯之处的那样，『当你剔除了所有那些不可能，剩下的无论多么荒谬，都必然是真相。』（引自柯南道尔的小说《福尔摩斯探案：四签名》）



For some people, programming and debugging are the same thing. That is, programming is the process of gradually debugging a program until it does what you want. The idea is that you should start with a working program and make small modifications, debugging them as you go.
>对于一些人来说，编程和调试是一回事。也就是说，编程就是对一个程序逐渐进行调试，一直到程序按照设想工作为止。这种思想意味着你要从一段能工作的程序来起步，一点点做小修改和调试。


For example, Linux is an operating system that contains millions of lines of code, but it started out as a simple program Linus Torvalds used to explore the Intel 80386 chip. According to Larry Greenfield, “One of Linus’s earlier projects was a program that would switch between printing AAAA and BBBB. This later evolved to Linux.” (The Linux Users’ Guide Beta Version 1).
>例如，Linux是一个有上百万行代码的操作系统，但最早它起源于Linus Torvalsd的一段小代码。这个小程序是作者用来探索Intel的80386芯片的。根据Larry Greenfield回忆，『Linus早起的项目就是很小的一个程序，这个程序能够在输出AAAA和BBBB之间进行转换。这后来就发展除了Linux了。』（引用自Linux用户参考手册beta1版）


##3.13  Glossary 术语列表

function:
A named sequence of statements that performs some useful operation. Functions may or may not take arguments and may or may not produce a result.
>函数：一系列有序语句的组合，有自己的名字，并且用在某些特定用途。可以要求输入参数，也可以没有参数，可以返回值，也可以没有返回值。


function definition:
A statement that creates a new function, specifying its name, parameters, and the statements it contains.
>函数定义：创建新函数的语句，确定函数的名字，形式参数，以及函数内部的语句。


function object:
A value created by a function definition. The name of the function is a variable that refers to a function object.
>函数对象：由函数定义所创建的值，函数名字指代了这一函数对象。


header:
The first line of a function definition.
>函数头：函数定义的第一行。

body:
The sequence of statements inside a function definition.
>函数体：函数定义内部的一系列有序语句。

parameter:
A name used inside a function to refer to the value passed as an argument.
>形式参数：用来在函数内部接收实际参数传来的值，并被函数在函数内部使用。

function call:
A statement that runs a function. It consists of the function name followed by an argument list in parentheses.
>函数调用：运行某个函数的语句。包括了函数的名字以及括号，括号内放函数需要的实际参数。


argument:
A value provided to a function when the function is called. This value is assigned to the corresponding parameter in the function.
>实际参数：当函数被调用的时候，提供给函数的值。这个值会被函数接收，赋给函数内部的形式参数。

local variable:
A variable defined inside a function. A local variable can only be used inside its function.
>局部变量：函数体内定义的变量。局部变量只在函数内部有效。


return value:
The result of a function. If a function call is used as an expression, the return value is the value of the expression.
>返回值：函数返回的结果。如果一个函数调用被用作了表达式，这个返回值就是这个表达式所代表的值。

fruitful function:
A function that returns a value.
>有返回值函数：返回一个值作为返回值的函数。

void function:
A function that always returns None.
>无返回值函数：不返回值，只返回一个空None的函数。

None:
A special value returned by void functions.
>空值：无返回值函数所返回的一种特殊的值。

module:
A file that contains a collection of related functions and other definitions.
>模块：包含一系列相关函数以及其他一些定义的文件。

import statement:
A statement that reads a module file and creates a module object.
>导入语句：读取模块并且创建一个模块对象的语句。

module object:
A value created by an import statement that provides access to the values defined in a module.
>模块对象：导入语句创建的一个值，允许访问模块所定义的值。

dot notation:
The syntax for calling a function in another module by specifying the module name followed by a dot (period) and the function name.
>点符号：调用某一个模块的某一函数的语法形式，就是模块名后加一个点，也就是英文的句号，再加函数名。

composition:
Using an expression as part of a larger expression, or a statement as part of a larger statement.
>组合：把表达式作为更大的表达式的一部分，或者把语句作为更大语句的一部分。

flow of execution:
The order statements run in.
>运行流程：语句运行的先后次序。


stack diagram:
A graphical representation of a stack of functions, their variables, and the values they refer to.
>栈图：对函数关系、变量内容及结构的图形化表示。


frame:
A box in a stack diagram that represents a function call. It contains the local variables and parameters of the function.
>框架：栈图中的方框，表示了一次函数调用。包括函数的局部变量和形式参数。


traceback:
A list of the functions that are executing, printed when an exception occurs.
>追踪：对运行中函数的列表，当有异常的时候就会输出。

##3.14  Exercises 练习


###Exercise 1  练习1

Write a function named right_justify that takes a string named s as a parameter and prints the string with enough leading spaces so that the last letter of the string is in column 70 of the display.
>写一个名叫right_justify的函数，形式参数是名为s的字符串，将字符串打印，前面流出足够的空格，让字符串最后一个字幕在第70列显示。


```Python
>>> right_justify('monty')                                                                  monty 
```


Hint: Use string concatenation and repetition. Also, Python provides a built-in function called len that returns the length of a string, so the value of len('monty') is 5.
>提示：使用字符拼接和重复来实现。另外Python还提供了内置的名字叫做len的函数，可以返回一个字符串的长度，比如len('monty')的值就是5了。


###Exercise 2  练习2

A function object is a value you can assign to a variable or pass as an argument. For example, do_twice is a function that takes a function object as an argument and calls it twice:
>你可以把一个函数对象作为一个值赋给一个变量或者作为一个实际参数来传递给其他函数。比如，do_twice就是一个把其他函数对象当做参数的函数，它的功能是调用对象函数两次：


```Python
def do_twice(f):     
f()     
f() 
```


Here’s an example that uses do_twice to call a function named print_spam twice.
>下面是另一个例子，这里用了do_twice来调用一个名叫print_spam的函数两次。

```Python
def print_spam():     
print('spam')  
do_twice(print_spam) 
```


1.Type this example into a script and test it.
>把上面的例子写成脚本然后试一下。


2.Modify do_twice so that it takes two arguments, a function object and a value, and calls the function twice, passing the value as an argument.
>修改一下do_twice这个函数，让它接收两个实际参数，一个是函数对象，一个是值，调用对象函数两次，并且赋这个值给对象函数作为实际参数。


3.Copy the definition of print_twice from earlier in this chapter to your script.
>把print_twice这个函数的定义复制到你的脚本里面，去本章开头找一下这个例子哈。

4.Use the modified version of do_twice to call print_twice twice, passing'spam' as an argument.
>用修改过的这个do_twice来调用print_twice两次，用字符串『spam』传递过去作为实际参数。


5.Define a new function called do_four that takes a function object and a value and calls the function four times, passing the value as a parameter. There should be only two statements in the body of this function, not four.
>定义一个新的函数，名字叫做do_four，使用一个函数对象和一个值作为实际参数，调用这个对象函数四次，传递这个值作过去为对象函数的一个形式参数。这个函数体内只要有两个语句就够了，而不是四个。


[Solution](http://thinkpython2.com/code/do_four.py)
>[样例代码](http://thinkpython2.com/code/do_four.py)：



###Exercise 3  练习三


Note: This exercise should be done using only the statements and other features we have learned so far.
>注意：这个练习应该只用咱们目前学习过的语句和其他功能来实现。


1.Write a function that draws a grid like the following:
>写一个函数，输出如下：

![](http://7xnq2o.com1.z0.glb.clouddn.com/ThinkPythonExcise3.14.png)



Hint: to print more than one value on a line, you can print a comma-separated sequence of values:
>提示：要一次打印超过一行，可以用逗号分隔一下就能换行了。如下所示：

```Python
print('+', '-') 
```



By default, print advances to the next line, but you can override that behavior and put a space at the end, like this:
>默认情况下，print会打印到下一行，你可以手动覆盖掉这个行为，在末尾输出一个空格就可以了：


```Python
print('+', end=' ') 
print('-') 
```

The output of these statements is '+ -'.
>上面的语句输出结果就是：'+ -'。



A print statement with no argument ends the current line and goes to the next line.
>没有参数的print语句会把当前的行结束，去下一行。


2.Write a function that draws a similar grid with four rows and four columns.
>写一个四行四列的小网格绘制的程序。

[Solution](http://thinkpython2.com/code/grid.py)
[样例](http://thinkpython2.com/code/grid.py)

Credit: This exercise is based on an exercise in Oualline, Practical C Programming, Third Edition, O’Reilly Media, 1997.
>此练习基于Oualline的书《实践C语言编程》第三版，O'Reilly出版社，1997年版