Title: ThinkPython 双语学编程 Chapter 7
Date: 2015-11-19
Category: ThinkPython
Tag: 双语,Python,ThinkPython

#Chapter 7 Iteration 迭代

This chapter is about iteration, which is the ability to run a block of statements repeatedly. We saw a kind of iteration, using recursion, in Section 5.8. We saw another kind, using a for loop, in Section 4.2. In this chapter we’ll see yet another kind, using a while statement. But first I want to say a little more about variable assignment.
>这一章我们讲迭代，简单说就是指重复去运行一部分代码。在5.8的时候我们接触了一种迭代——递归。在4.2我们还学了另外一种迭代——for循环。在本章，我们会见到新的迭代方式：whie语句。但我要先再稍微讲一下变量赋值。

##7.1  Reassignment 再赋值

As you may have discovered, it is legal to make more than one assignment to the same variable. A new assignment makes an existing variable refer to a new value (and stop referring to the old value).
>你可能已经发现了，对同一个变量可以多次进行赋值。一次新的赋值使得已有的变量获得新的值（也就不再有旧的值了。）
>（译者注：这个其实中文很好理解，英文当中词汇逻辑关系比较紧密，但灵活程度不如中文高啊。）

```Python
>>> x = 5
>>> x
5
>>> x = 7
>>> x
7
```


The first time we display x, its value is 5; the second time, its value is 7.
>第一次显示x的值，是5，第二次，就是7了。


Figure 7.1 shows what reassignment looks like in a state diagram.
>图7.1表示了再赋值的操作在状态图中的样子。



At this point I want to address a common source of confusion. Because Python uses the equal sign (=) for assignment, it is tempting to interpret a statement like a = b as a mathematical proposition of equality; that is, the claim that a and b are equal. But this interpretation is wrong.
>这里我就要强调一下大家常发生的误解。因为Python使用单等号（=）来赋值，所以有的人会以为像a=b这样的语句就如同数学上的表达一样来表达两者相等，这种想法是错误的！


First, equality is a symmetric relationship and assignment is not. For example, in mathematics, if a=7 then 7=a. But in Python, the statement a = 7 is legal and 7 = a is not.
>首先，数学上的等号所表示的相等是一个对称的关系，而Python中等号的赋值操作是不对称的。比如，在数学上，如果a=7，那么7=a。而在Python，a=7这个是合乎语法的，而7=a是错误的。
>（译者注：这里就是说Python中等号是一种单向的运算，就是把等号右边的值赋给等号左边的变量，而Python中其实也有数学上相等判断的表达式，就是双等号（==），这个是有对称性的，就是说a==b，那么b==a，或者a==3，3==a也可以。）


Also, in mathematics, a proposition of equality is either true or false for all time. If a=b now, then a will always equal b. In Python, an assignment statement can make two variables equal, but they don’t have to stay that way:
>另外在数学上，一个相等关系要么是真，要么是假。比如a=b，那么a就会永远等于b。在Python里面，赋值语句可以让两个变量相等，但可以不始终都相等，如下所示：


```Python
>>> a = 5
>>> b = a    # a and b are now equal a和b相等了
>>> a = 3    # a and b are no longer equal 现在a和b就不相等了
>>> b
5
```


The third line changes the value of a but does not change the value of b, so they are no longer equal.
>第三行改变了a的值，但没有改变b的值，所以它们就不再相等了。

Reassigning variables is often useful, but you should use it with caution. If the values of variables change frequently, it can make the code difficult to read and debug.
>对变量进行再赋值总是很有用的，但你用的时候要做好备注和提示。如果变量的值频繁变化，就可能让代码难以阅读和调试。

________________________________________
![Figure 7.1: State diagram.](http://7xnq2o.com1.z0.glb.clouddn.com/ThinkPython7.1jpg.jpg)
Figure 7.1: State diagram.
________________________________________




##7.2  Updating variables 更新变量



A common kind of reassignment is an update, where the new value of the variable depends on the old.
>最常见的一种再赋值就是对变量进行更新，这种情况下新的值是在旧值基础上进行修改得到的。

```Python
>>> x = x + 1
```





This means “get the current value of x, add one, and then update x with the new value.”
If you try to update a variable that doesn’t exist, you get an error, because Python evaluates the right side before it assigns a value to x:
>上面的语句的意思是：获取x当前的值，在此基础上加1，然后把结果作为新值赋给x。如果你对不存在的变量进行更新，你就会得到错误了，因为Python要先进行等号右边的运算，然后才能赋值给x。



```Python
>>> x = x + 1
NameError: name 'x' is not defined
```



Before you can update a variable, you have to initialize it, usually with a simple assignment:
>在你更新一个变量之前，你要先初始化一下，一般就是简单赋值一下就可以了：

```Python
>>> x = 0
>>> x = x + 1
```

Updating a variable by adding 1 is called an increment; subtracting 1 is called a decrement.
>对一个变量每次加1也可以叫做一种递增，每次减去1就可以叫做递减了。



##7.3  The while statement 循环：While语句



Computers are often used to automate repetitive tasks. Repeating identical or similar tasks without making errors is something that computers do well and people do poorly. In a computer program, repetition is also called iteration.
>计算机经常被用来自动执行一些重复的任务。重复同样的或者相似的任务，而不出错，这是计算机特别擅长的事情，咱们人就做不到了。在一个计算机程序里面，重复操作也被叫做迭代。


We have already seen two functions, countdown and print_n, that iterate using recursion. Because iteration is so common, Python provides language features to make it easier. One is the for statement we saw in Section 4.2. We’ll get back to that later. Another is the while statement. Here is a version of countdown that uses a while statement:
>我们已经见过两种使用了递归来进行迭代的函数：倒计时函数countdown，以及n次输出函数print_n。Python还提供了一些功能来简化迭代，因为迭代用的很普遍。其中一个就是我们在4.2中见到的for循环语句。往后我们还要复习一下它。另外一个就是while循环语句。下面就是一个使用了while循环语句来实现的倒计时函数countdown：


```Python
def countdown(n):
	while n > 0:
		print(n)
		n = n - 1
	print('Blastoff!')
```

You can almost read the while statement as if it were English. It means, “While n is greater than 0, display the value of n and then decrement n. When you get to 0, display the word Blastoff!”
>while循环语句读起来很容易，几乎就像是英语一样简单。这个函数的意思是：当n大于0，就输出n的值，然后对n减1，到n等于0的时候，就输出单词『Blastoff』。

More formally, here is the flow of execution for a while statement:
>更正式一点，下面是一个while循环语句的执行流程：

1.	Determine whether the condition is true or false.
>判断循环条件的真假。

2.	If false, exit the while statement and continue execution at the next statement.
>如果是假的，退出while语句，继续运行后面的语句。

3.	If the condition is true, run the body and then go back to step 1.
>如果条件为真，执行循环体，然后再调回到第一步。


This type of flow is called a loop because the third step loops back around to the top.
The body of the loop should change the value of one or more variables so that the condition becomes false eventually and the loop terminates.
>这种类型的运行流程叫做循环，因为第三步会循环到第一步。循环体内要改变一个或者更多变量的值，这样循环条件最终才能变成假，然后循环才能终止。


Otherwise the loop will repeat forever, which is called an infinite loop. An endless source of amusement for computer scientists is the observation that the directions on shampoo, “Lather, rinse, repeat”, are an infinite loop.
>否则的话，条件不能为假，循环不能停止，这就叫做无限循环。计算机科学家有一个笑话，就是看到洗发液的说明：起泡，冲洗，重复；这就是一个无限循环。


In the case of countdown, we can prove that the loop terminates: if n is zero or negative, the loop never runs. Otherwise, n gets smaller each time through the loop, so eventually we have to get to 0.
>在倒计时函数countdown里面，咱们能够保证有办法让循环终止：只要n小于等于0了，循环就不进行了。否则的话，n每次就会通过循环来递减，最终还是能到0的。


For some other loops, it is not so easy to tell. For example:
>其他一些循环就不那么好描述了。比如：

```Python
def sequence(n):
	while n != 1:
		print(n)
		if n % 2 == 0:			# n is even
			n = n / 2
		else:					# n is odd
			n = n*3 + 1
```



The condition for this loop is n != 1, so the loop will continue until n is 1, which makes the condition false.
>这个循环的判断条件是n不等于1，所以循环一直进行，直到n等于1了，条件为假，就不再循环了。

Each time through the loop, the program outputs the value of n and then checks whether it is even or odd. If it is even, n is divided by 2. If it is odd, the value of n is replaced with n*3 + 1. For example, if the argument passed to sequence is 3, the resulting values of n are 3, 10, 5, 16, 8, 4, 2, 1.
>每次循环的时候，程序都输出n的值，然后检查一下是偶数还是奇数。如果是偶数，就把n除以2。如果是奇数，就把n替换为n乘以3再加1的值。比如让这个函数用3做参数，也就是sequence(3)，得到的n的值就依次为：3, 10, 5, 16, 8, 4, 2, 1.


Since n sometimes increases and sometimes decreases, there is no obvious proof that n will ever reach 1, or that the program terminates. For some particular values of n, we can prove termination. For example, if the starting value is a power of two, n will be even every time through the loop until it reaches 1. The previous example ends with such a sequence, starting with 16.
>有时候n在增加，有时候n在降低，所以没有明显证据表明n最终会到1而程序停止。对于一些特定的n值，我们能够确保循环的终止。例如如果起始值是一个2的倍数，n每次循环过后依然是偶数，直到到达1位置。之前的例子都最终得到了一个数列，从16开始的就是了。



The hard question is whether we can prove that this program terminates for all positive values of n. So far, no one has been able to prove it or disprove it! 
See [WikiPedia](http://en.wikipedia.org/wiki/Collatz_conjecture)
>真正的难题是，我们能否证明这个程序对任意正数的n值都能终止循环。目前为止，没有人能够证明或者否定这个命题。
参考[维基百科](http://en.wikipedia.org/wiki/Collatz_conjecture)


As an exercise, rewrite the function print_n from Section 5.8 using iteration instead of recursion.
>做一个练习，把5.8里面的那个n次打印函数print_n用迭代的方法来实现。


##7.4  break 中断

Sometimes you don’t know it’s time to end a loop until you get half way through the body. In that case you can use the break statement to jump out of the loop.
>有时候你不知道啥时候终止循环，可能正好在中间循环体的时候要终止了。这时候你就可以用break语句来跳出循环。

For example, suppose you want to take input from the user until they type done. You could write:
>比如，假设你要让用户输入一些内容，当他们输入done的时候结束。你就可以用如下的方法实现：



```Python
while True:
	line = input('> ')
	if line == 'done':
		break
		print(line)
	print('Done!')
```



The loop condition is True, which is always true, so the loop runs until it hits the break statement.
>循环条件就是true，意味条件总是真的，所以循环就一直进行，一直到触发了break语句才跳出。



Each time through, it prompts the user with an angle bracket. If the user types done, the break statement exits the loop. Otherwise the program echoes whatever the user types and goes back to the top of the loop. Here’s a sample run:
>每次循环的时候，程序都会有一个大于号>来提示用户。如果用输入了done，break语句就会让程序跳出循环。否则的话程序会重复用户输入的内容，然后回到循环的头部。下面就是一个简单的运行例子：

```Python
>not done
>not done
>done
Done!
```


This way of writing while loops is common because you can check the condition anywhere in the loop (not just at the top) and you can express the stop condition affirmatively (“stop when this happens”) rather than negatively (“keep going until that happens”).
>这种while循环的写法很常见，因为这样你可以在循环的任何一个部位对条件进行检测，而不仅仅是循环的头部，你可以确定地表达循环停止的条件（在这种情况下就停止了），而不是消极地暗示『程序会一直运行，直到某种情况』。


##7.5  Square roots 平方根

Loops are often used in programs that compute numerical results by starting with an approximate answer and iteratively improving it.
>循环经常被用于进行数值运算的程序中，这种程序往往是有一个近似值作为初始值，然后逐渐迭代去改进以接近真实值。


For example, one way of computing square roots is Newton’s method. Suppose that you want to know the square root of a. If you start with almost any estimate, x, you can compute a better estimate with the following formula:
>比如，可以用牛顿法来计算平方根。加入你要知道一个数a的平方根。如果你用任意一个估计值x来开始，你可以用下面的公式获得一个更接近的值：


$$y = \frac{x + \frac{a}{x}}{2}$$


For example, if a is 4 and x is 3:
>比如，如果a是3，x设为3：


```Python
>>> a = 4
>>> x = 3
>>> y = (x + a/x) / 2
>>> y
2.16666666667
```




The result is closer to the correct answer (square root of 4 is 2). If we repeat the process with the new estimate, it gets even closer:
>得到的结果比初始值3更接近真实值（4的平方根是2）。如果我们用这个结果做新的估计值来重复这个操作，结果就更加接近了：

```Python
>>> x = y
>>> y = (x + a/x) / 2
>>> y 2.00641025641
```


After a few more updates, the estimate is almost exact:
>这样进行一些次重复之后，估计值就几乎很准确了：


```Python
>>> x = y
>>> y = (x + a/x) / 2
>>> y 2.00001024003
>>> x = y
>>> y = (x + a/x) / 2
>>> y 2.00000000003
```

In general we don’t know ahead of time how many steps it takes to get to the right answer, but we know when we get there because the estimate stops changing:
>一般情况下，我们不能提前知道到达正确结果需要多长时间，但是当估计值不再有明显变化的时候我们就知道了：

```Python
>>> x = y
>>> y = (x + a/x) / 2
>>> y 2.0
>>> x = y
>>> y = (x + a/x) / 2
>>> y 2.0
```


When y == x, we can stop. Here is a loop that starts with an initial estimate, x, and improves it until it stops changing:
>当y和x相等的时候，我们就可以停止了。下面这个循环中，用一个初始值x来开始循环，然后进行改进，一直到x的值不再变化为止：



```Python
while True:
	print(x)
	y = (x + a/x) / 2
	if y == x:
		break
	x = y
```


For most values of a this works fine, but in general it is dangerous to test float equality. Floating-point values are only approximately right: most rational numbers, like 1/3, and irrational numbers, like √2, can’t be represented exactly with a float.
>对大多数值来说，这个循环都挺管用的，但一般来说用浮点数来测试等式是很危险的。浮点数的值只能是近似正确：大多数的有理数，比如1/3，以及无理数，比如根号2，都不能用浮点数来准确表达的。


Rather than checking whether x and y are exactly equal, it is safer to use the built-in function abs to compute the absolute value, or magnitude, of the difference between them:
>相比之下，与其对比x和y是否精确相等，倒不如以下方法更安全：用内置的绝对值函数来计算一下差值的绝对值，也叫做数量级。

```Python
if abs(y-x) < epsilon:
	break
```


Where epsilon has a value like 0.0000001 that determines how close is close enough.
>这里可以让epsilon的值为like 0.0000001，差值比这个小就说明已经足够接近了。


##7.6  Algorithms 算法


Newton’s method is an example of an algorithm: it is a mechanical process for solving a category of problems (in this case, computing square roots).
>牛顿法是算法的一个例子：通过一系列机械的步骤来解决一类问题（在本章中是用来计算平方根）。


To understand what an algorithm is, it might help to start with something that is not an algorithm. When you learned to multiply single-digit numbers, you probably memorized the multiplication table. In effect, you memorized 100 specific solutions. That kind of knowledge is not algorithmic.
>要理解算法是什么，先从一些不是算法的内容来开始也许会有所帮助。当你学个位数字乘法的时候，你可能要背下来整个乘法表。实际上你记住了100个特定的算式。这种知识就不是算法。

But if you were “lazy”, you might have learned a few tricks. For example, to find the product of n and 9, you can write n−1 as the first digit and 10−n as the second digit. This trick is a general solution for multiplying any single-digit number by 9. That’s an algorithm!
>但如果你很『懒』，你就可能会有一些小技巧。比如找到一个n与9的成绩，你可以把n-1写成第一位，10-n携程第二位。这个技巧是应对任何个位数字乘以9的算式。这就是一个算法了！


Similarly, the techniques you learned for addition with carrying, subtraction with borrowing, and long division are all algorithms. One of the characteristics of algorithms is that they do not require any intelligence to carry out. They are mechanical processes where each step follows from the last according to a simple set of rules.
>相似地，你学过的进位的加法，借位的减法，以及长除法，都是算法。这些算法的一个共同特点就是不需要任何智力就能进行。它们都是机械的过程，每一步都跟随上一步，遵循着很简单的一套规则。


Executing algorithms is boring, but designing them is interesting, intellectually challenging, and a central part of computer science.
>执行算法是很无聊的，但设计算法很有趣，是智力上的一种挑战，也是计算机科学的核心部分。

Some of the things that people do naturally, without difficulty or conscious thought, are the hardest to express algorithmically. Understanding natural language is a good example. We all do it, but so far no one has been able to explain how we do it, at least not in the form of an algorithm.
>有的事情人们平时做起来很简单，甚至都不用思考，这些事情往往最难用算法来表达。比如理解自然语言就是个例子。我们都能理解自然语言，但目前为止还没有人能解释我们到底是怎么做到的，至少没有人把这个过程归纳出算法的形式。


##7.7  Debugging 调试

As you start writing bigger programs, you might find yourself spending more time debugging. More code means more chances to make an error and more places for bugs to hide.
>现在你已经开始写一些比较大的程序了，你可能发现自己比原来花更多时间来调试了。代码越多，也就意味着出错的可能也越大了，bug也有了更多的藏身之处了。


One way to cut your debugging time is “debugging by bisection”. For example, if there are 100 lines in your program and you check them one at a time, it would take 100 steps. Instead, try to break the problem in half. Look at the middle of the program, or near it, for an intermediate value you can check. Add a print statement (or something else that has a verifiable effect) and run the program.
>『对折调试』是一种节省调试时间的方法。比如，如果你的程序有100行，你检查一遍就要大概100步了。而对折方法就是把程序分成两半。看程序中间位置，或者靠近中间位置的，检查一些中间值。在这些位置添加一些print语句（或者其他能够能起到验证效果的东西），然后运行程序。


If the mid-point check is incorrect, there must be a problem in the first half of the program. If it is correct, the problem is in the second half.
>如果中间点检查出错了，那必然是程序的前半部分有问题。如果中间点没调试，那问题就是在后半段了。


Every time you perform a check like this, you halve the number of lines you have to search. After six steps (which is fewer than 100), you would be down to one or two lines of code, at least in theory.
>每次你都这样检查，你就让你要检查的代码数量减半了。一般六步之后（远小于100次了），理论上你就差不多已经到代码的末尾一两行了。

In practice it is not always clear what the “middle of the program” is and not always possible to check it. It doesn’t make sense to count lines and find the exact midpoint. Instead, think about places in the program where there might be errors and places where it is easy to put a check. Then choose a spot where you think the chances are about the same that the bug is before or after the check.
>在实际操作当中，程序中间位置并不是总那么明确，也未必就很容易去检查。所以不用数行数来找确定的中间点。相反的，只要考虑一下程序中哪些地方容易调试，然后哪些地方进行检验比较容易就行了。然后你就在你考虑好的位置检验一下看看bug是在那个位置之前还是之后。

##7.8  Glossary 术语列表

reassignment:
Assigning a new value to a variable that already exists.
>再赋值：对一个已经存在的有值变量赋予一个新的值。

update:
An assignment where the new value of the variable depends on the old.
>更新：根据一个变量的旧值，进行一定的修改，再赋值给这个变量。


initialization:
An assignment that gives an initial value to a variable that will be updated.
>初始化：给一个变量初始值，以便于后续进行更新。

increment:
An update that increases the value of a variable (often by one).
>递增：每次给一个变量增加一定的值（一般是加1）

decrement:
An update that decreases the value of a variable.
>递减：每次给一个变量减去一定的值。

iteration:
Repeated execution of a set of statements using either a recursive function call or a loop.
>迭代：重复执行一系列语句，使用递归函数调用的方式，或者循环的方式。

infinite loop:
A loop in which the terminating condition is never satisfied.
>无限循环：终止条件永远无法满足的循环。

algorithm:
A general process for solving a category of problems.
>算法：解决某一类问题的一系列通用的步骤。

##7.9  Exercises 练习
###Exercise 1 练习1

Copy the loop from Section 7.5 and encapsulate it in a function called mysqrt that takes a as a parameter, chooses a reasonable value of x, and returns an estimate of the square root of a.
>从7.5复制一个循环，然后改写成名字叫做mysqrt的函数，该函数用一个a作为参数，选择一个适当的起始值x，然后返回a的平方根的近似值。

To test it, write a function named test_square_root that prints a table like this:
>测试这个函数，写一个叫做test_suqare_root的函数来输出以下这样的表格：

| a |mysqrt(a)|math.sqrt(a)|diff |
|--------|--------|--------|--------|
|1.0 |1.0       |    1.0        |   0.0|
|2.0| 1.41421356237| 1.41421356237| 2.22044604925e-16|
|3.0| 1.73205080757| 1.73205080757| 0.0|
|4.0| 2.0         |  2.0          | 0.0|
|5.0| 2.2360679775 | 2.2360679775 | 0.0|
|6.0| 2.44948974278| 2.44948974278| 0.0|
|7.0| 2.64575131106 |2.64575131106 |0.0|
|8.0| 2.82842712475| 2.82842712475| 4.4408920985e-16|
|9.0| 3.0          | 3.0          | 0.0|
|        |        |        |        |

The first column is a number, a; the second column is the square root of acomputed with mysqrt; the third column is the square root computed by math.sqrt; the fourth column is the absolute value of the difference between the two estimates.
>第一列是数a；第二列是咱们自己写的函数mysqrt计算出来的平方根，第三行是用Python内置的math.sqrt函数计算的平方根，最后一行是这两者的差值的绝对值。


###Exercise 2 练习2

The built-in function eval takes a string and evaluates it using the Python interpreter. For example:
>Python的内置函数eval接收字符串作为参数，然后用Python的解释器来运行。例如：

```Python
>>> eval('1 + 2 * 3')
7
>>> import math
>>> eval('math.sqrt(5)')
2.2360679774997898
>>> eval('type(math.pi)')
<class 'float'>
```

Write a function called eval_loop that iteratively prompts the user, takes the resulting input and evaluates it using eval, and prints the result.
>写一个叫做eval_loop的函数，交互地提醒用户，获取输入，然后用eval对输入进行运算，把结果打印出来。


It should continue until the user enters 'done', and then return the value of the last expression it evaluated.
>这个程序要一直运行，直到用户输入『done』才停止，然后输出最后一次计算的表达式的值。


##Exercise 3 练习3

The mathematician Srinivasa Ramanujan found an infinite series that can be used to generate a numerical approximation of 1 / π:
>传奇的数学家拉马努金发现了一个无穷级数（1914年的论文），能够用来计算圆周率倒数的近似值：

$$\frac{1}{\pi}=\frac{2\sqrt{2}}{99^2}\sum_{k=0}^\infty\frac{(4k)!(26390k+1103)}{(k!)^4396^{4k}}$$

（译者注：这位拉马努金是一位非常杰出的数学家，自学成才，以数论为主要研究内容，可惜33岁的时候就英年早逝。他被哈代誉为超越希尔伯特的天才。）

Write a function called estimate_pi that uses this formula to compute and return an estimate of π. It should use a while loop to compute terms of the summation until the last term is smaller than 1e-15 (which is Python notation for 10−15). You can check the result by comparing it to math.pi.
[Solution](http://thinkpython2.com/code/pi.py)
>写一个名叫estimate_pi的函数，用上面这个方程来计算并返回一个圆周率π的近似值。要使用一个while循环来计算出总和的每一位，最后一位要小于10的-15次方。你可以对比一下计算结果和Python内置的math.pi。
>[样例代码](http://thinkpython2.com/code/pi.py)

