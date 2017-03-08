Title: ThinkPython 双语学编程 Chapter 16
Date: 2016-1-21
Category: ThinkPython
Tag: 双语,Python,ThinkPython

#Chapter 16 Classes and functions 类和函数

Now that we know how to create new types, the next step is to write functions that take programmer-defined objects as parameters and return them as results. In this chapter I also present “functional programming style” and two new program development plans.
>现在我们已经知道如何创建新类型了，下一步就要写一些函数了，这些函数用自定义类型做参数和返回值。在本章中还提供了一种函数式编程的模式，以及两种新的程序开发规划方式。


Code examples from this chapter are available from [Here](http://thinkpython2.com/code/Time1.py). Solutions to the exercises are at [Here](http://thinkpython2.com/code/Time1_soln.py).
>本章的样例代码可以在[这里](http://thinkpython2.com/code/Time1.py)下载。然后练习题的样例代码可以在[这里](http://thinkpython2.com/code/Time1_soln.py)下载到。




##16.1  Time 时间


As another example of a programmer-defined type, we’ll define a class called Time that records the time of day. The class definition looks like this:
>下面又是一个自定义类型的例子，这次咱们定义一个叫做 Time 的类，记录下当日的时间。
>类的定义是如下这样：

```Python
class Time:
"""Represents the time of day.
attributes: hour, minute, second     """
```

We can create a new Time object and assign attributes for hours, minutes, and seconds:
>我们可以建立一个新的 Time 对象，然后对时分秒分别进行赋值：

```Python
time = Time()
time.hour = 11
time.minute = 59
time.second = 30
```


The state diagram for the Time object looks like Figure 16.1.
>这个 Time 对象的状态图如图16.1所示。


As an exercise, write a function called print_time that takes a Time object and prints it in the form hour:minute:second. Hint: the format sequence '%.2d' prints an integer using at least two digits, including a leading zero if necessary.
>下面做个练习，写一个名为print_time 的函数，接收一个 Time 对象，然后以时：分：秒的格式来输出。提示：格式序列'%.2d'就会用两位来输出一个整数，第一位可以为0。


Write a boolean function called is_after that takes two Time objects, t1 andt2, and returns True if t1 follows t2 chronologically and False otherwise. Challenge: don’t use an if statement.
>写一个布尔函数，名为 is_after，接收两个 Time 对象，分别为 t1和 t2，然后如果 t1在时间上位于 t2的后面，就返回真，否则返回假。难度提高一下：不要用 if 语句，看你能搞定不。


________________________________________
![Figure 16.1: Object diagram.](http://7xnq2o.com1.z0.glb.clouddn.com/ThinkPython16.1.png)
Figure 16.1: Object diagram.
________________________________________





##16.2  Pure functions 纯函数


In the next few sections, we’ll write two functions that add time values. They demonstrate two kinds of functions: pure functions and modifiers. They also demonstrate a development plan I’ll call prototype and patch, which is a way of tackling a complex problem by starting with a simple prototype and incrementally dealing with the complications.
>后面的这些章节中，我们要写两个函数来对 time 进行加法操作。这两个函数展示了两种函数类型：纯函数和修改器。写这两个函数的过程中，也体现了我即将讲到的一种新的开发模式：原型和补丁模式，这种方法就是在处理复杂问题的时候，先从简单的原型开始，然后逐渐解决复杂的内容。


Here is a simple prototype of add_time:
>下面这段代码就是 add_time 函数的一个原型：


```Python
def add_time(t1, t2):
	sum = Time()
	sum.hour = t1.hour + t2.hour
	sum.minute = t1.minute + t2.minute
	sum.second = t1.second + t2.second
	return sum
```



The function creates a new Time object, initializes its attributes, and returns a reference to the new object. This is called a pure function because it does not modify any of the objects passed to it as arguments and it has no effect, like displaying a value or getting user input, other than returning a value.
>这个函数新建了一个新的 Time 对象，初始化了所有的值，然后返回了一个对新对象的引用。这种函数叫纯函数，因为这种函数并不修改传来做参数的对象，也没有什么效果，比如显示值啊或者让用户输入啊等等，而只是返回一个值而已。


To test this function, I’ll create two Time objects: start contains the start time of a movie, like Monty Python and the Holy Grail, and duration contains the run time of the movie, which is one hour 35 minutes. add_time figures out when the movie will be done.
>下面就来测试一下这个函数，我将建立两个 Time 对象，start 包含了一个电影的开始时间，比如《巨蟒与圣杯》（译者注：1975年喜剧电影。Python的创造者Guido van Rossum特别喜欢这个喜剧团体：巨蟒飞行马戏团（Monty Python’s Flying Circus ），所以命名为 Python。），然后 duration（汉译就是持续时间）包含了该电影的时长，《巨蟒与圣杯》这部电影是一小时三十五分钟。add_time 函数就会算出电影结束的时间。



```Python
>>> start = Time()
>>> start.hour = 9
>>> start.minute = 45
>>> start.second =  0
>>> duration = Time()
>>> duration.hour = 1
>>> duration.minute = 35
>>> duration.second = 0
>>> done = add_time(start, duration)
>>> print_time(done)
10:80:00
```




The result, 10:80:00 might not be what you were hoping for. The problem is that this function does not deal with cases where the number of seconds or minutes adds up to more than sixty. When that happens, we have to “carry” the extra seconds into the minute column or the extra minutes into the hour column.
Here’s an improved version:
>很明显，10点80分00秒这样的时间肯定不是你想要的结果。问题就出在了函数不值得如何应对时分秒的六十位进位，所以超过60的时候没进位就这样了。所以我们得把超出六十秒的进位到分，超过六十分的进位到小时。
>下面这个是改进版本：


```Python
def add_time(t1, t2):
	sum = Time()
	sum.hour = t1.hour + t2.hour
	sum.minute = t1.minute + t2.minute
	sum.second = t1.second + t2.second
	if sum.second >= 60:
		sum.second -= 60
		sum.minute += 1
		if sum.minute >= 60:
			sum.minute -= 60
			sum.hour += 1
	return sum
```



Although this function is correct, it is starting to get big. We will see a shorter alternative later.
>这回函数正确工作了，但代码也开始变多了。稍后我们就能看到一个短一些的替代方案。


16.3  Modifiers 修改器



Sometimes it is useful for a function to modify the objects it gets as parameters. In that case, the changes are visible to the caller. Functions that work this way are called modifiers.
>有时候需要对作为参数的对象进行一些修改。这时候这些修改就可以被调用者察觉。这样工作的函数就叫修改器了。

increment, which adds a given number of seconds to a Time object, can be written naturally as a modifier. Here is a rough draft:
>increment 函数，增加给定的秒数到一个 Time 对象，就可以被改写成一个修改器。
>下面是个简单的版本：


```Python
def increment(time, seconds):
	time.second += seconds
	if time.second >= 60:
		time.second -= 60
		time.minute += 1
		if time.minute >= 60:
			time.minute -= 60
			time.hour += 1
```



The first line performs the basic operation; the remainder deals with the special cases we saw before.
Is this function correct? What happens if seconds is much greater than sixty?
>第一行代码进行了最简单的运算；后面的代码是用来应对我们之前讨论过的特例情况。
>那么这个函数正确么？秒数超过六十会怎么样？


In that case, it is not enough to carry once; we have to keep doing it until time.second is less than sixty. One solution is to replace the if statements with while statements. That would make the function correct, but not very efficient.
>很明显，秒数超过六十的时候，就需要运行不只一次了；必须一直运行，之道 time.second 的值小于六十了才行。有一种办法就是把 if 语句换成 while 语句。这样就可以解决这个问题了，但效率不太高。




As an exercise, write a correct version of increment that doesn’t contain any loops.
>做个练习，写一个正确的 increment 函数，并且要不包含任何循环。


Anything that can be done with modifiers can also be done with pure functions. In fact, some programming languages only allow pure functions. There is some evidence that programs that use pure functions are faster to develop and less error-prone than programs that use modifiers. But modifiers are convenient at times, and functional programs tend to be less efficient.
>能用修改器实现的功能也都能用纯函数来实现。实际上有的编程语言只允许纯函数。有证据表明，与修改器相比，使用修改器能够更快地开发，而且不容易出错误。但修改器往往很方便好用，而函数式的程序一般效率要差一些。



In general, I recommend that you write pure functions whenever it is reasonable and resort to modifiers only if there is a compelling advantage. This approach might be called a functional programming style.
>总的来说，我还是建议你写纯函数，除非用修改器有特别显著的好处。这种模式也叫做函数式编程。



As an exercise, write a “pure” version of increment that creates and returns a new Time object rather than modifying the parameter.
>做个练习，写一个用纯函数实现的 increment，创建并返回一个新的 Time 对象，而不是修改参数。


##16.4  Prototyping versus planning 原型与规划




The development plan I am demonstrating is called “prototype and patch”. For each function, I wrote a prototype that performed the basic calculation and then tested it, patching errors along the way.
>这次我演示的开发规划就是『原型与补丁模式』。对每个函数，我都先谢了一个简单的原型，只进行基本的运算，然后测试一下，接下来逐步修补错误。


This approach can be effective, especially if you don’t yet have a deep understanding of the problem. But incremental corrections can generate code that is unnecessarily complicated—since it deals with many special cases—and unreliable—since it is hard to know if you have found all the errors.
>这种模式很有效率，尤其是在你对问题的理解不是很深入的时候。不过渐进式的修改也会产生过分复杂的代码——因为要应对很多特例情况，而且也不太靠靠——因为不好确定你是否找到了所有的错误。




An alternative is designed development, in which high-level insight into the problem can make the programming much easier. In this case, the insight is that a Time object is really a three-digit number in base 60 (see [Here](http://en.wikipedia.org/wiki/Sexagesimal))! The second attribute is the “ones column”, the minute attribute is the “sixties column”, and the hour attribute is the “thirty-six hundreds column”.
>另一种模式就是设计规划开发，这种情况下对问题的深入透彻的理解就让开发容易很多了。本节中的根本性认识就在于 TIme 对象实际上是一个三位的六十进制数字(参考 [这里的解释](http://en.wikipedia.org/wiki/Sexagesimal)。)！秒数也就是个位，分数也就是六十位，小时数就是三千六百位。


When we wrote add_time and increment, we were effectively doing addition in base 60, which is why we had to carry from one column to the next.
>这样当我们写 add_time 和 increment 函数的时候，用60进制来进行计算就很有效率。



This observation suggests another approach to the whole problem—we can convert Time objects to integers and take advantage of the fact that the computer knows how to do integer arithmetic.
>这一观察表明有另外一种方法来解决整个问题——我们可以把 Time 对象转换成整数，然后因为计算机最擅长整数运算，这样就有优势了。


Here is a function that converts Times to integers:
>下面这个函数就把 Times 转换成了整数：


```Python
def time_to_int(time):
	minutes = time.hour * 60 + time.minute
	seconds = minutes * 60 + time.second
	return seconds
```




And here is a function that converts an integer to a Time (recall that divmod divides the first argument by the second and returns the quotient and remainder as a tuple).
>然后下面这个函数是反过来的，把整数转换成 Time（还记得 divmod 么，使用第一个数除以第二个数，返回的是除数和余数组成的元组。）


```Python
def int_to_time(seconds):
	time = Time()
	minutes, time.second = divmod(seconds, 60)
	time.hour, time.minute = divmod(minutes, 60)
	return time
```



You might have to think a bit, and run some tests, to convince yourself that these functions are correct. One way to test them is to check that time_to_int(int_to_time(x)) == x for many values of x. This is an example of a consistency check.
>你最好先考虑好了，然后多进行几次测试运行，然后要确保这些函数都是正确的。比如你就可以试着用很多个 x 的值来运算time_to_int(int_to_time(x)) == x。这也是连贯性检测的一个例子。



Once you are convinced they are correct, you can use them to rewrite add_time:
>一旦你确定这些函数都没问题，就可以用它们来重写一下 add_time 这个函数了：


```Python
def add_time(t1, t2):
	seconds = time_to_int(t1) + time_to_int(t2)
	return int_to_time(seconds)
```



This version is shorter than the original, and easier to verify. As an exercise, rewrite increment using time_to_int and int_to_time.
>这个版本就比最开始那个版本短多了，也更容易去检验了。接下来就做个联系吧，用time_to_int 和 int_to_time 这两个函数来重写一下 increment。



In some ways, converting from base 60 to base 10 and back is harder than just dealing with times. Base conversion is more abstract; our intuition for dealing with time values is better.
>在一定程度上，从六十进制到十进制的来回转换，远远比计算时间要麻烦的多。进制转换要更加抽象很多；我们处理时间计算的直觉要更好些。



But if we have the insight to treat times as base 60 numbers and make the investment of writing the conversion functions (time_to_int and int_to_time), we get a program that is shorter, easier to read and debug, and more reliable.
>然而，如果我们有足够的远见，把时间值当做六十进制的数值来对待，然后写出一些转换函数（比如 time_to_int 和 int_to_time），就能让程序变得更短，可读性更好，调试更容易，也更加可靠。




It is also easier to add features later. For example, imagine subtracting two Times to find the duration between them. The naive approach would be to implement subtraction with borrowing. Using the conversion functions would be easier and more likely to be correct.
>而且后续添加功能也更容易了。比如，假设要对两个时间对象进行相减来求二者之间的持续时间。简单版本的方法就是要用借位的减法。而使用转换函数的版本就更容易了，也更不容易出错。




Ironically, sometimes making a problem harder (or more general) makes it easier (because there are fewer special cases and fewer opportunities for error).
>有意思的事，有时候以困难模式来写一个程序（比如用更加泛化的模式），反而能让开发更简单（因为这样就减少了特例情况，也减少了出错误的概率了。）




##16.5  Debugging 调试



A Time object is well-formed if the values of minute and second are between 0 and 60 (including 0 but not 60) and if hour is positive. hour and minute should be integral values, but we might allow second to have a fraction part.
>对于一个 Time 对象来说，只要分和秒的值在0-60的前闭后开区间（即可以为0但不可以为60），并且小时数为正数，就是格式正确的。小时和分钟都应该是整数，但秒是可以为小数的。




Requirements like these are called invariants because they should always be true. To put it a different way, if they are not true, something has gone wrong.
>像这些要求也叫约束条件，因为通常都得满足这些条件才行。反过来说，如果这些条件没满足，就有可能是程序中某处存在错误了。




Writing code to check invariants can help detect errors and find their causes. For example, you might have a function like valid_time that takes a Time object and returns False if it violates an invariant:
>写一些检测约束条件的代码，能够帮助找出这些错误，并且找到导致错误的原因。例如，你亏写一个名字未 calid_time 的函数，接收一个 Time 对象，然后如果该对象不满足约束条件就返回 False：



```Python
def valid_time(time):
	if time.hour < 0 or time.minute < 0 or time.second < 0:
		return False
	if time.minute >= 60 or time.second >= 60:
		return False
	return True
```



At the beginning of each function you could check the arguments to make sure they are valid:
>然后在每个自定义函数的开头部位，你就可以检测一下参数，来确保这些参数没有错误：


```Python
def add_time(t1, t2):
	if not valid_time(t1) or not valid_time(t2):
		raise ValueError('invalid Time object in add_time')
	seconds = time_to_int(t1) + time_to_int(t2)
	return int_to_time(seconds)
```




Or you could use an assert statement, which checks a given invariant and raises an exception if it fails:
>或者你也可以用一个 assert 语句，这个语句也是检测给定的约束条件的，如果出现错误就会抛出一个异常：


```Python
def add_time(t1, t2):
	assert valid_time(t1) and valid_time(t2)
	seconds = time_to_int(t1) + time_to_int(t2)
	return int_to_time(seconds)
```



assert statements are useful because they distinguish code that deals with normal conditions from code that checks for errors.
>assert 语句是很有用的，可以用来区分条件语句的用途，将 assert 这种用于检查错误的语句与常规的条件语句在代码上进行区分。




##16.6  Glossary 术语列表




prototype and patch:
A development plan that involves writing a rough draft of a program, testing, and correcting errors as they are found.
>原型和补丁模式：一种开发模式，先写一个程序的草稿，然后测试，再改正发现的错误，这样逐步演化的开发模式。





designed development:
A development plan that involves high-level insight into the problem and more planning than incremental development or prototype development.
>设计规划开发：这种开发模式要求对所面对问题的高程度的深刻理解，相比渐进式开发和原型增补模式要更具有计划性。




pure function:
A function that does not modify any of the objects it receives as arguments. Most pure functions are fruitful.
>纯函数：不修改参数对象的函数。这种函数多数是有返回值的函数。



modifier:
A function that changes one or more of the objects it receives as arguments. Most modifiers are void; that is, they return None.
>修改器：修改参数对象的函数。大多数这样的函数都是无返回值的，也就是返回的都是 None。




functional programming style:
A style of program design in which the majority of functions are pure.
>函数式编程模式：一种程序设计模式，主要特征为大多数函数都是纯函数。



invariant:
A condition that should always be true during the execution of a program.
>约束条件：在程序运行过程中，应该一直为真的条件。



assert statement:
A statement that check a condition and raises an exception if it fails.
>assert 语句：一种检查错误的语句，检查一个条件，如果不满足就抛出异常。




##16.7  Exercises 练习



Code examples from this chapter are available from [Here](http://thinkpython2.com/code/Time1.py); solutions to the exercises are available from [Here](http://thinkpython2.com/code/Time1_soln.py).
>本章的例子可以在 [这里](http://thinkpython2.com/code/Time1.py)下载；练习题的答案可以在[这里](http://thinkpython2.com/code/Time1_soln.py)下载。



###Exercise 1  练习1




Write a function called mul_time that takes a Time object and a number and returns a new Time object that contains the product of the original Time and the number.
>写一个函数，名为mul_time，接收一个Time 对象和一个数值，返回一个二者相乘得到的新的Time 对象。


Then use mul_time to write a function that takes a Time object that represents the finishing time in a race, and a number that represents the distance, and returns a Time object that represents the average pace (time per mile).
>然后用 mul_time 这个函数写一个函数，接收一个 Time 对象，代表着一个比赛的结束时间，还有一个数值，代表比赛距离，然后返回一个表示了平均步调（单位距离花费的时间）的新的 Time 对象。



###Exercise 2  练习2


The datetime module provides time objects that are similar to the Time objects in this chapter, but they provide a rich set of methods and operators. Read the documentation at [Here](http://docs.python.org/3/library/datetime.html).
>datetime 模块提供了一些 time 对象，和本章的 Time 对象很相似，但前者提供了更多的方法和运算符。读一读[这里的文档] [Here](http://docs.python.org/3/library/datetime.html)吧。




1.	Use the datetime module to write a program that gets the current date and prints the day of the week.
>用 datetime 模块来写一个函数，获取当前日期，然后输出今天是星期几。




2.	Write a program that takes a birthday as input and prints the user’s age and the number of days, hours, minutes and seconds until their next birthday.
>写一个函数，要求输入生日，然后输出用户的年龄以及距离下一个生日的日、时、分、秒数。




3.	For two people born on different days, there is a day when one is twice as old as the other. That’s their Double Day. Write a program that takes two birthdays and computes their Double Day.
>有的两个人在不同日期出生，会在某一天，一个人的年龄是另外一个人年龄的两杯。这一天就叫做他们的双倍日。写一个函数，接收两个生日，然后计算双倍日。




4.	For a little more challenge, write the more general version that computes the day when one person is n times older than the other.
>再来点有挑战性的，写一个更通用的版本，来计算一下一个人的年龄为另外一个人年龄 n 倍时候的日期。



[Solution](http://thinkpython2.com/code/double.py).
>[样例代码](http://thinkpython2.com/code/double.py)。

