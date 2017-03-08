Title: ThinkPython 双语学编程 Chapter 4 
Date: 2015-10-28
Category: ThinkPython
Tag: 双语,Python,ThinkPython

#Chapter 4  Case study: interface design 案例学习：交互设计

This chapter presents a case study that demonstrates a process for designing functions that work together.
>本章会提供一个案例，用于展示如何却设计一些共同工作的函数。


It introduces the turtle module, which allows you to create images using turtle graphics. The turtle module is included in most Python installations, but if you are running Python using PythonAnywhere, you won’t be able to run the turtle examples (at least you couldn’t when I wrote this).
>本章介绍了小乌龟这个模块，这允许你用小龟的图形功能来制作一些图形。乌龟模块在大部分的Python中都有安装，不过如果你在线使用PythnAnywhere，你就无法运行这些乌龟样例了（至少我写这本教材的时候还不行）。
>（译者注：都学到第四章了，你还不本地安装个Python也太说不过去了吧。）


If you have already installed Python on your computer, you should be able to run the examples. Otherwise, now is a good time to install. I have posted instructions at http://tinyurl.com/thinkpython2e.
Code examples from this chapter are available from http://thinkpython2.com/code/polygon.py.
>如果你已经安装了Python在你的电脑上，你就能运行这些例子了。没安装的话呢，这就是安装的好时机了呗。我已经把相关介绍放到网页上面了，[点击访问](http://tinyurl.com/thinkpython2e)。
>本章代码样例可以点击[此链接](http://thinkpython2.com/code/polygon.py)来下载了。



##4.1  The turtle module 乌龟模块

To check whether you have the turtle module, open the Python interpreter and type:
>要检查你是不是已经安装了这个乌龟模块，你要打开Python解释器来输入如下内容：


```Python
>>> import turtle 
>>> bob = turtle.Turtle() 
```


When you run this code, it should create a new window with small arrow that represents the turtle. Close the window.
>运行上述例子的时候，应该就能新建一个小窗口，还有个小箭头象征小乌龟。如果有的话就对了，把窗口关掉吧先。

Create a file named mypolygon.py and type in the following code:
>建立一个叫做mypolygon.py的文件，在里面输入如下内容：

```Python
import turtle 
bob = turtle.Turtle() 
print(bob) 
turtle.mainloop() 
```


The turtle module (with a lowercase ’t’) provides a function called Turtle(with an uppercase ’T’) that creates a Turtle object, which we assign to a variable named bob. Printing bob displays something like:
>这个小乌龟模块（记着是小写的t）提供了一个叫做Turtle（注意这里是大写的，大小写要去分！）的函数，这个函数会创建一个Turtle对象，我们把它赋值给bob这个变量。打印一下bob就能显示如下内容：


```Bash
<turtle.Turtle object at 0xb7bfbf4c> 
```


This means that bob refers to an object with type Turtle as defined in module turtle.
>这就意味着bob已经指向了模块turtle中所定义的Turtle类的一个对象。

mainloop tells the window to wait for the user to do something, although in this case there’s not much for the user to do except close the window.
>mainloop这个函数是告诉窗口等用户来做些事情，当然本次尝试的情况下用户也就是关闭窗口而已了。

Once you create a Turtle, you can call a method to move it around the window. A method is similar to a function, but it uses slightly different syntax. For example, to move the turtle forward:
>一旦你创建了一个Trutle，你就可以调用一些方法让他在窗口中移动。方法跟函数有点相似，但语法的使用稍微不太一样。比如你可以让小乌龟往前走：

```Python
bob.fd(100) 
```


The method, fd, is associated with the turtle object we’re calling bob. Calling a method is like making a request: you are asking bob to move forward.
>fd这个方法，是turtle类这个叫做bob的对象所包含的。调用这个方法就像是做出一个请求一样：你再让bob向前移动。

The argument of fd is a distance in pixels, so the actual size depends on your display.
>fd这个方法的参数是像素数距离，所以实际的大小依赖于你显示器的情况了。


Other methods you can call on a Turtle are bk to move backward, lt for left turn, and rt right turn. The argument for lt and rt is an angle in degrees.
>Turtle对象中还有一些其他方法，比如bk是后退，lt是左转，rt是右转。lt和rt用偏转角度做参数。


Also, each Turtle is holding a pen, which is either down or up; if the pen is down, the Turtle leaves a trail when it moves. The methods pu and pd stand for “pen up” and “pen down”.
>另外，每个Turtle都相当于带着笔，可以落下或者抬起；如果笔落下了，Turtle移动的时候就会留下轨迹了。抬笔落笔的方法缩写粉笔嗯是pu和pd。

To draw a right angle, add these lines to the program (after creating bob and before calling mainloop):
>画一个直角，就要把下面这些线加到程序里面（当然要先创建一个bob并且在此之前运行mainloop）：

```Python
bob.fd(100) 
bob.lt(90) 
bob.fd(100) 
```

When you run this program, you should see bob move east and then north, leaving two line segments behind.
>运行这个程序，你就能看到bob先向东再往北，后面就留下了两根互相垂直的线段了。


Now modify the program to draw a square. Don’t go on until you’ve got it working!
>现在修改一下程序，去画一个正方形。这个程序运行不好的话就不要继续后面的章节！



##4.2  Simple repetition 简单的重复

Chances are you wrote something like this:
>你估计会写出如下的内容：

```Python
bob.fd(100) 
bob.lt(90)  
bob.fd(100) 
bob.lt(90)  
bob.fd(100) 
bob.lt(90)  
bob.fd(100) 
```


We can do the same thing more concisely with a for statement. Add this example to mypolygon.py and run it again:
>上面这个太麻烦了，咱们可以用一个for语句来让这个过程更简洁。把下面的代码添加到mypolygon.py中然后运行一下：

```Python
for i in range(4):     
	print('Hello!') 
```


You should see something like this:
>你将会看到这样的输出：

```Bash
Hello! 
Hello! 
Hello! 
Hello! 
```


This is the simplest use of the for statement; we will see more later. But that should be enough to let you rewrite your square-drawing program. Don’t go on until you do.
>这就是for语句的最简单的一种应用；以后我们会看到更多。不过当前这种简单的足够你来重构一下你的正方形绘制程序了。不达目的不罢休，不要跳过困难哈，一定要编写出来这个再进行后面的内容。


Here is a for statement that draws a square:
>这就是一个用for语句来画正方形的语句：

```Python
for i in range(4):     
	bob.fd(100)     
	bob.lt(90) 
```


The syntax of a for statement is similar to a function definition. It has a header that ends with a colon and an indented body. The body can contain any number of statements.
>for语句的语法跟函数定义有点相似。有一个头部，头部的结尾要用冒号，然后还有一个缩进的循环体。循环体可以包含任意多的语句。


A for statement is also called a loop because the flow of execution runs through the body and then loops back to the top. In this case, it runs the body four times.
>for语句也被叫做循环，因为运行流程会重复执行循环体。在本节的例子中，循环进行了四次。

This version is actually a little different from the previous square-drawing code because it makes another turn after drawing the last side of the square. The extra turn takes more time, but it simplifies the code if we do the same thing every time through the loop. This version also has the effect of leaving the turtle back in the starting position, facing in the starting direction.
>这次的正方形绘制代码实际上和之前的少有不同了，因为在画完了最后一个边之后，多了一次转向。多出来的这部分需要消耗额外的时间，但简化了下次我们来循环进行绘制的过程。这个版本的代码也有一个额外的效果：让小乌龟回到起点，朝着初始方向。


##4.3  Exercises 练习


The following is a series of exercises using TurtleWorld. They are meant to be fun, but they have a point, too. While you are working on them, think about what the point is.
>下面是一系列使用TurtleWorld的练习。主要就是比较有意思，不过也有一些训练的作用。你做这些练习的时候，一定要注意考虑这些训练的作用。


The following sections have solutions to the exercises, so don’t look until you have finished (or at least tried).
>练习后面是有一些样例的解决方案的，所以你要做完了再往后看，至少你得试试，不会做了看看答案也行哈。

1.Write a function called square that takes a parameter named t, which is a turtle. It should use the turtle to draw a square.
>写一个函数叫做square（译者注：就是正方形的意思），有一个名叫t的参数，这个t是一个turtle。用这个turtle来画一个正方形。

Write a function call that passes bob as an argument to square, and then run the program again.
>写一个函数调用，把bob作为参数传递给square，然后再运行这个程序。


2.Add another parameter, named length, to square. Modify the body so length of the sides is length, and then modify the function call to provide a second argument. Run the program again. Test your program with a range of values for length.
>给这个square函数再加一个参数，叫做length（译者注：长度）。把函数体修改一下，让长度length赋值给各个边的长度，然后修改一下调用函数的代码，再提供一个这个对应长度的参数。再次运行一下，用一系列不同的长度值来测试一下你的程序。


3.Make a copy of square and change the name to polygon. Add another parameter named n and modify the body so it draws an n-sided regular polygon. Hint: The exterior angles of an n-sided regular polygon are 360/n degrees.
>复制一下square这个函数，把名字改成polygon（译者注：意思为多边形）。另外添加一个参数叫做n，然后修改函数体，让函数实现画一个正n边的多边形。提示：正n多边形的外角为360/n度。


4.Write a function called circle that takes a turtle, t, and radius, r, as parameters and that draws an approximate circle by calling polygon with an appropriate length and number of sides. Test your function with a range of values of r.
>在写一个叫做circle（译者注：圆）的函数，也用一个turtle类的对象t，以及一个半径r，作为参数，画一个近似的圆，通过调用polygon函数来近似实现，用适当的边长和边数。用不同的半径值来测试一下你的函数。

Hint: figure out the circumference of the circle and make sure that length * n = circumference.
>提示：算出圆的周长，确保边长乘以边数的值（近似）等于圆周长。


5.Make a more general version of circle called arc that takes an additional parameter angle, which determines what fraction of a circle to draw. angle is in units of degrees, so when angle=360, arc should draw a complete circle.
>在circle基础上做一个叫做arc的函数，在circle的基础上添加一个angle（译者注：角度）变量，用这个角度值来确定画多大的一个圆弧。用度做单位，当angle等于360度的时候，arc函数就应当画出一个整团了。


##4.4  Encapsulation 封装


The first exercise asks you to put your square-drawing code into a function definition and then call the function, passing the turtle as a parameter. Here is a solution:
>第一个练习让你把正方形绘制的代码定义到一个函数里面，然后调用这个函数，传入一个turtle对象作为参数。下面就是个例子了：


```Python
def square(t):     
	for i in range(4):         
		t.fd(100)         
		t.lt(90)  

square(bob) 
```



The innermost statements, fd and lt are indented twice to show that they are inside the for loop, which is inside the function definition. The next line,square(bob), is flush with the left margin, which indicates the end of both the for loop and the function definition.
>在最内部的语句里面，fd和lt缩进了两次，这个意思是他们是for循环的循环体内部成员，而for循环本身缩进了一次，说明for语句被包含在函数的定义当中。接下来的那行square(bob)，紧靠左侧，没有缩进，这说明for循环和函数定义都结束了。


Inside the function, t refers to the same turtle bob, so t.lt(90) has the same effect as bob.lt(90). In that case, why not call the parameter bob? The idea is that t can be any turtle, not just bob, so you could create a second turtle and pass it as an argument to square:
>在函数体内部，t所指代的就是小乌龟bob，因此让t来左转九十度的效果完全等同于让bob来左转九十度。本文中没有把形式参数的名字设置成bob，这是为啥呢？是因为用t可以指代任意一个小乌龟，不仅仅是bob，所以你就能再创建另一个小乌龟，把它传递给square这个函数作为实际参数：


```Python
alice = Turtle() 
square(alice) 
```



Wrapping a piece of code up in a function is called encapsulation. One of the benefits of encapsulation is that it attaches a name to the code, which serves as a kind of documentation. Another advantage is that if you reuse the code, it is more concise to call a function twice than to copy and paste the body!
>用函数的形式把一段代码包装起来，叫做封装。这样有一个好处，就是给代码起了个名字，有类似文档说明的功能，更好理解了。另外一个好处是下次重复使用这段代码的时候，再次调用函数就可以了，这比复制粘贴函数体可方便多了。


##4.5  Generalization 泛化


The next step is to add a length parameter to square. Here is a solution:
>下一步就是给square函数添加一个长度参数了。下面是样例：

```Python
def square(t, length):     
	for i in range(4):         
		t.fd(length)         
		t.lt(90)  
square(bob, 100) 
```


Adding a parameter to a function is called generalization because it makes the function more general: in the previous version, the square is always the same size; in this version it can be any size.
>给函数添加参数，就叫做泛化，因为者可以让函数的功能更广泛：在之前的版本中，square这个函数画出来的正方形总是一个尺寸的；在这个新版本里面，可以自定义边长了。


The next step is also a generalization. Instead of drawing squares, polygondraws regular polygons with any number of sides. Here is a solution:
>下一步也还是泛化。这次就是不光要画正方形了，要画一个多边形，可以指定边数的。下面是样例：

```Python
def polygon(t, n, length):    
	angle = 360 / n     
	for i in range(n):         
		t.fd(length)         
		t.lt(angle)  
polygon(bob, 7, 70) 
```


This example draws a 7-sided polygon with side length 70.
>这个例子画了一个每个边长度都为70像素的七边形。

If you are using Python 2, the value of angle might be off because of integer division. A simple solution is to compute angle = 360.0 / n. Because the numerator is a floating-point number, the result is floating point.
>如果你用Python2的话，角度可能因为整除而导致的偏差。简单的解决方法就是用360.0来除以n而不是用360，这就是用浮点数替代了原来的整形，结果就是一个浮点数了。


When a function has more than a few numeric arguments, it is easy to forget what they are, or what order they should be in. In that case it is often a good idea to include the names of the parameters in the argument list:
>当一个函数有超过一个数据参数的时候，很容易忘掉这些参数都是什么，或者忘掉他们的顺序。为了避免这个情况，可以把形式参数的名字包含在一个实际参数列表中：

```Python
polygon(bob, n=7, length=70)
```



These are called keyword arguments because they include the parameter names as “keywords” (not to be confused with Python keywords like whileand def).
>这些列表叫做关键参数列表，因为他们把形式参数的名字作为关键词包含了进来。（注意区别这里的关键词可不是Python语言的关键词哈！这里就是字面意思，很关键的词。）


This syntax makes the program more readable. It is also a reminder about how arguments and parameters work: when you call a function, the arguments are assigned to the parameters.
>这种语法结构让程序更容易被人读懂。也能提醒实际参数和形式参数的使用过程：调用一个函数的时候，把实际参数的值赋给了形式参数。


##4.6  Interface design 界面设计


The next step is to write circle, which takes a radius, r, as a parameter. Here is a simple solution that uses polygon to draw a 50-sided polygon:
>下一步就是写circle这个函数了，需要半径r作为一个参数。下面是一个简单的样例，使用polygon函数来画一个50边形，来接近一个圆：


```Python
import math  
def circle(t, r):     
	circumference = 2 * math.pi * r    
	n = 50     
	length = circumference / n     
	polygon(t, n, length) 
```

The first line computes the circumference of a circle with radius r using the formula 2 π r. Since we use math.pi, we have to import math. By convention,import statements are usually at the beginning of the script.
>第一行计算了圆的周长，使用2乘以圆周率再乘以半径r。这个计算用到了圆周率，所以要导入math模块。通常都要把导入语句放到整个脚本的开头。

n is the number of line segments in our approximation of a circle, so length is the length of each segment. Thus, polygon draws a 50-sides polygon that approximates a circle with radius r.
>n是我们用来逼近一个圆所用的线段数量，所以length就是每一个线段的长度了。polygon画一个50边的多边形，来近似做一个半径为r的圆。


One limitation of this solution is that n is a constant, which means that for very big circles, the line segments are too long, and for small circles, we waste time drawing very small segments. One solution would be to generalize the function by taking n as a parameter. This would give the user (whoever calls circle) more control, but the interface would be less clean.
>这种方案的一个局限性就是n是常数，就意味着对于一些大尺寸的圆，线段数目就太多了，而对小的圆，又浪费了很多小线段。解决的方法就是进一步扩展函数，让函数把n也作为一个参数。这就亏让用户（调用circle函数的任何人）有更多决定权，可以控制所用的线段数量，当然，界面就不那么简洁了。

The interface of a function is a summary of how it is used: what are the parameters? What does the function do? And what is the return value? An interface is “clean” if it allows the caller to do what they want without dealing with unnecessary details.
>函数的界面就是关于它如何工作的一个概述：都有什么变量？函数实现什么功能？以及返回值是什么？允许调用者随意操作而不用处理一些无关紧要的细节，这种函数界面就是简洁的。

In this example, r belongs in the interface because it specifies the circle to be drawn. n is less appropriate because it pertains to the details of how the circle should be rendered.
>在本节的例子中，r包含于界面内，因为要用它来确定所画圆的大小。n就不那么合适了，因为它是用来处理如何具体绘制一个圆的。

Rather than clutter up the interface, it is better to choose an appropriate value of n depending on circumference:
>与其让界面复杂冗余，更好的思路是让n根据周长来自适应一个合适的值：


```Python
def circle(t, r):     
	circumference = 2 * math.pi * r     
	n = int(circumference / 3) + 1     
	length = circumference / n     
	polygon(t, n, length) 
```

Now the number of segments is an integer near circumference/3, so the length of each segment is approximately 3, which is small enough that the circles look good, but big enough to be efficient, and acceptable for any size circle.
>现在线段个数就是周长的三分之一了，因此每段线段的长度近似为3，这个大小可以让圆看着不错，也对任意大小的圆都适用了。


##4.7  Refactoring 重构


When I wrote circle, I was able to reuse polygon because a many-sided polygon is a good approximation of a circle. But arc is not as cooperative; we can’t use polygon or circle to draw an arc.
>当我写circle这个函数的时候，我能利用多边形函数polygon是因为一个足够多边的多边形和圆很接近。但圆弧就不太适合这个思路了；我们不能用多边形或者圆来画一个圆弧。


One alternative is to start with a copy of polygon and transform it into arc. The result might look like this:
>一个替代的方法就是把polygon修改一下，转换成圆弧。结果大概如下所示：

```Python
def arc(t, r, angle):     
	arc_length = 2 * math.pi * r * angle / 360     
	n = int(arc_length / 3) + 1     
	step_length = arc_length / n     
	step_angle = angle / n          
	for i in range(n):        
		t.fd(step_length)         
		t.lt(step_angle) 
```


The second half of this function looks like polygon, but we can’t reuse polygon without changing the interface. We could generalize polygon to take an angle as a third argument, but then polygon would no longer be an appropriate name! Instead, let’s call the more general function polyline:
>这个函数的后半段看着和多边形那个还挺像的，但必须修改一下界面才能重利用多边形的代码。我们在多边形函数上增加angle（角度）作为第三个参数，但继续叫多边形就不太合适了，因为不闭合啊！所以就改名叫它多段线polyline：


```Python
def polyline(t, n, length, angle):     
	for i in range(n):         
	t.fd(length)         
	t.lt(angle)
```


Now we can rewrite polygon and arc to use polyline:
>现在就可以用多段线polyline来重写多边形polygon和圆弧arc：


```Python
def polygon(t, n, length):     
	angle = 360.0 / n     
	polyline(t, n, length, angle)  

def arc(t, r, angle):     
	arc_length = 2 * math.pi * r * angle / 360     
	n = int(arc_length / 3) + 1     
	step_length = arc_length / n     
	step_angle = float(angle) / n     
	polyline(t, n, step_length, step_angle) 


```

Finally, we can rewrite circle to use arc:
>最终，咱们就可以用圆弧arc来重写circle的实现了：


```Python
def circle(t, r):     
	arc(t, r, 360) 
```


This process—rearranging a program to improve interfaces and facilitate code re-use—is called refactoring. In this case, we noticed that there was similar code in arc and polygon, so we “factored it out” into polyline.
>这个过程中，改进了界面设计，增强了代码再利用，这就叫做重构。在本节的这个例子中，我们先是注意到圆弧arc和多边形polygon有相似的代码，所以我们把他们都用多段线polyline来实现。


If we had planned ahead, we might have written polyline first and avoided refactoring, but often you don’t know enough at the beginning of a project to design all the interfaces. Once you start coding, you understand the problem better. Sometimes refactoring is a sign that you have learned something.
>如果我们事先进行了计划，估计就会先写出多段线函数polyline，然后就不用重构了，但大家在开始一个项目之前往往不一定了解的那么清楚。一旦开始编码了，你就逐渐更理解其中的问题了。有时候重构就意味着你已经学到了新的内容了。

##4.8  A development plan 开发计划

A development plan is a process for writing programs. The process we used in this case study is “encapsulation and generalization”. The steps of this process are:
>开发计划是写程序的一系列过程。我们本章所用的就是『封装-泛化』的模式。这一过程的步骤如下：

1.	Start by writing a small program with no function definitions.
>开始写一个特别小的程序，没有函数定义。


2.	Once you get the program working, identify a coherent piece of it, encapsulate the piece in a function and give it a name.
>一旦有你的程序能用了，确定一下实现功能的这部分有练习的语句，封装成函数，并命名一下。


3.	Generalize the function by adding appropriate parameters.
>通过逐步给这个函数增加参数的方式来泛化。


4.	Repeat steps 1–3 until you have a set of working functions. Copy and paste working code to avoid retyping (and re-debugging).
>重复1-3步骤，一直到你有了一系列能工作的函数为止。把函数复制粘贴出来，避免重复输入或者修改了。


5.	Look for opportunities to improve the program by refactoring. For example, if you have similar code in several places, consider factoring it into an appropriately general function.
>看看是不是有通过重构来改进函数的可能。比如，假设你在一些地方看到了相似的代码，就可以把这部分代码做成一个函数。

This process has some drawbacks—we will see alternatives later—but it can be useful if you don’t know ahead of time how to divide the program into functions. This approach lets you design as you go along.
>这个模式有一些缺点，我们后续会看到一些替代的方式，但这个模式是很有用的，尤其对耐饿实现不值得怎么去把程序分成多个函数的情况。


##4.9  docstring 文档字符串


A docstring is a string at the beginning of a function that explains the interface (“doc” is short for “documentation”). Here is an example:
>文档字符串是指：在函数开头部位，解释函数的交互界面的字符串，doc是文档documentation的缩写。下面是一个例子：

```Python
def polyline(t, n, length, angle):     
"""
Draws n line segments with the given length and     angle (in degrees) between them. 
t is a turtle.     """         

	for i in range(n):         
		t.fd(length)         
		t.lt(angle) 
```

By convention, all docstrings are triple-quoted strings, also known as multiline strings because the triple quotes allow the string to span more than one line.
>一般情况下，所有文档字符串都是三重引用字符串，也被叫做多行字符串，因为三重的单引号表示允许这个字符串是多行的。


It is terse, but it contains the essential information someone would need to use this function. It explains concisely what the function does (without getting into the details of how it does it). It explains what effect each parameter has on the behavior of the function and what type each parameter should be (if it is not obvious).
>这些文字很简洁，但都包含了一些关键的信息，这些信息对于函数使用者来说至关重要。这些信息简要解释了函数的用途（不会说细节，也不会说如何实现）。文档解释了每个参数对函数行为的影响，以及各自的类型（一般在不是显而易见的情况下就给解释了）。

Writing this kind of documentation is an important part of interface design. A well-designed interface should be simple to explain; if you have a hard time explaining one of your functions, maybe the interface could be improved.
>写这种文档，对交互界面的设计来说，是至关重要的。设计良好的交互界面应该很容易解释明白；如果你的函数有一个特别不好解释了，估计这个函数的交互设计还存在需要改进的地方。


##4.10  Debugging 调试


An interface is like a contract between a function and a caller. The caller agrees to provide certain parameters and the function agrees to do certain work.
>一个交互界面，就像是函数和调用者的一个中间人。调用者提供特定的参数，函数完成特定的任务。


For example, polyline requires four arguments: t has to be a Turtle; n has to be an integer; length should be a positive number; and angle has to be a number, which is understood to be in degrees.
>例如，polyline这个多段线函数，需要四个实际参数：t必须是一个Turtle小乌龟；n（边数）必须是一个整形；length（长度）应该是一个正数；angle（角度）必须是一个以度为单位的角度值。


These requirements are called preconditions because they are supposed to be true before the function starts executing. Conversely, conditions at the end of the function are postconditions. Postconditions include the intended effect of the function (like drawing line segments) and any side effects (like moving the Turtle or making other changes).
>这些要求叫做『前置条件』，因为要在函数开始运行之前就要实现才行。相应的在函数的结尾那里的条件叫『后置条件』。后置条件包含函数的预期效果（如画线段）和其他作用（如移动海龟或进行其他改动）。

Preconditions are the responsibility of the caller. If the caller violates a (properly documented!) precondition and the function doesn’t work correctly, the bug is in the caller, not the function.
>前置条件是准备给函数调用者的。如果调用者违背了（妥当标注的）前置条件，然后函数不能正常工作，这个bug就会反馈在函数调用者上，而不是函数本身。


If the preconditions are satisfied and the postconditions are not, the bug is in the function. If your pre- and postconditions are clear, they can help with debugging.
>如果前置条件得到了满足，而后置条件未能满足，这个bug就是函数的了。所以如果你的前后置条件都弄清晰，对调试很有帮助。



##4.11  Glossary 术语列表


method:
A function that is associated with an object and called using dot notation.
>方法：某个类中一个对象所具有的函数，用点连接来进行调用。

loop:
A part of a program that can run repeatedly.
>循环：程序中重复运行的一部分。

encapsulation:
The process of transforming a sequence of statements into a function definition.
>封装：把一系列相关的语句整理定义成一个函数的过程。

generalization:
The process of replacing something unnecessarily specific (like a number) with something appropriately general (like a variable or parameter).
>泛化：把一些不必要的内容用更广泛通用的内容来替换掉的过程，比如把一个数字替换成了一个变量或者参数。

keyword argument:
An argument that includes the name of the parameter as a “keyword”.
>关键词参数：一种特殊的实际参数，把形式参数的名字作为关键词包含在内。

interface:
A description of how to use a function, including the name and descriptions of the arguments and return value.
>交互界面：对如何使用一个函数的描述，包括了函数名，以及对实际参数和返回值的描述。

refactoring:
The process of modifying a working program to improve function interfaces and other qualities of the code.
>重构：对一份能工作的程序进行修改，改进函数交互界面以及提高代码其他方面质量的过程。

development plan:
A process for writing programs.
>开发计划：写程序的过程。

docstring:
A string that appears at the top of a function definition to document the function’s interface.
>文档字符串：一个在函数定义的顶部的字符串，讲解函数的交互界面。

precondition:
A requirement that should be satisfied by the caller before a function starts.
>前置条件：函数开始之前，调用者应当满足的要求。

postcondition:
A requirement that should be satisfied by the function before it ends.
>后置条件：函数结束之前应该满足的一些要求。


##4.12  Exercises 练习

###Exercise 1 练习1

Download the code in this chapter from [here](http://thinkpython2.com/code/polygon.py).
>点击下面这个链接[下载代码](http://thinkpython2.com/code/polygon.py)。

1.	Draw a stack diagram that shows the state of the program while executing circle(bob, radius). You can do the arithmetic by hand or add print statements to the code.
>画一个栈图，表明运行函数circle(bob,radius)时候程序的状态。你可以手算一下，或者把输出语句加到代码上。


2.	The version of arc in Section 4.7 is not very accurate because the linear approximation of the circle is always outside the true circle. As a result, the Turtle ends up a few pixels away from the correct destination. My solution shows a way to reduce the effect of this error. Read the code and see if it makes sense to you. If you draw a diagram, you might see how it works.
>4.7小节中的那个版本的arc函数并不太精确，因为对圆进行线性逼近总会超过真实情况。结果就是小乌龟总会距离正确位置偏离一些像素。我的样例给出了一种降低这种误差程度的方法。阅读一下代码，看你能不能理解。如果你画一个图标，也许就能明白代码是怎么工作的了。


________________________________________
 ![Turtle flowers](http://7xnq2o.com1.z0.glb.clouddn.com/ThinkPythonExercise4.2.png)
Figure 4.1: Turtle flowers.
________________________________________
###Exercise 2 练习2


Write an appropriately general set of functions that can draw flowers as in Figure 4.1.
>写一系列的合适的函数组合，画出图4.1所示的花图案。


Solution 样例： http://thinkpython2.com/code/flower.py, 
also requires 同时需要： http://thinkpython2.com/code/polygon.py.
________________________________________
 
![Turtle pies](http://7xnq2o.com1.z0.glb.clouddn.com/ThinkPythonExercise4.3.png)
Figure 4.2: Turtle pies.
________________________________________


###Exercise 3 练习3
Write an appropriately general set of functions that can draw shapes as in Figure 4.2.
>写一系列的合适的函数组合，画出图4.2所示的形状。

Solution 样例： http://thinkpython2.com/code/pie.py.

###Exercise 4 练习4
The letters of the alphabet can be constructed from a moderate number of basic elements, like vertical and horizontal lines and a few curves. Design an alphabet that can be drawn with a minimal number of basic elements and then write functions that draw the letters.
>字母表当中的字母都可以用一定数量的基本元素来构建，比如竖直或者水平的线条，以及一些曲线。设计一个能用最小数量的基本元素画出来的字母表，然后写个函数来画字母出来。


You should write one function for each letter, with names draw_a, draw_b, etc., and put your functions in a file named letters.py. You can download a “turtle typewriter” from [this link](http://thinkpython2.com/code/typewriter.py) to help you test your code.
>你应当为没一个字母写一个函数，名字就比如draw_a,draw_b等等，然后把你的函数放到一个叫做letters.py的文件中。你可以从这个[链接](http://thinkpython2.com/code/typewriter.py) 下载一个乌龟打字机来帮你检测一下代码。

You can get a solution from [here](http://thinkpython2.com/code/letters.py); it also requires [this](http://thinkpython2.com/code/polygon.py).
>你可以参考这里的[样例](http://thinkpython2.com/code/letters.py);同时还需要[这些](http://thinkpython2.com/code/polygon.py)。


##Exercise 5 练习5
Read about spirals at [Wiki](http://en.wikipedia.org/wiki/Spiral); then write a program that draws an Archimedian spiral (or one of the other kinds). [Solution](http://thinkpython2.com/code/spiral.py)
>去[Wiki百科](http://en.wikipedia.org/wiki/Spiral)看一下螺旋线的相关内容;然后写个程序来画阿基米德曲线（曲线中的一种）。[样例](http://thinkpython2.com/code/spiral.py)


