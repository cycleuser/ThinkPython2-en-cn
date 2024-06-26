Title: ThinkPython 双语学编程 Chapter 12
Date: 2015-12-12
Category: ThinkPython
Tag: 双语,Python,ThinkPython

#Chapter 12 Tuples 元组



This chapter presents one more built-in type, the tuple, and then shows how lists, dictionaries, and tuples work together. I also present a useful feature for variable-length argument lists, the gather and scatter operators.
>本章我们要说的是另外一种内置类型，元组，以及列表、字典和元组如何协同工作。此外还有一个非常有用的功能：可变长度的列表，聚集和分散运算符。



One note: there is no consensus on how to pronounce “tuple”. Some people say “tuh-ple”, which rhymes with “supple”. But in the context of programming, most people say “too-ple”, which rhymes with “quadruple”.
>一点提示：元组的英文单词 tuple 怎么读还有争议。有人认为是发[tʌpəl] 的音，就跟『supple』里面的一样读音。但编程语境下，大家普遍读[tu:pəl]，跟『quadruple』里一样。


##12.1  Tuples are immutable 元组不可修改


A tuple is a sequence of values. The values can be any type, and they are indexed by integers, so in that respect tuples are a lot like lists. The important difference is that tuples are immutable.
Syntactically, a tuple is a comma-separated list of values:
>元组是一系列的值。这些值可以是任意类型的，并且用整数序号作为索引，所以可以发现元组和列表非常相似。二者间重要的区别就是元组是不可修改的。
>元组的语法是一系列用逗号分隔的值：


```Python
>>> t = 'a', 'b', 'c', 'd', 'e'
```



Although it is not necessary, it is common to enclose tuples in parentheses:
>通常都用一对圆括号把元组的元素包括起来，当然不这样也没事。


```Python
>>> t = ('a', 'b', 'c', 'd', 'e')
```



To create a tuple with a single element, you have to include a final comma:
>要建立一个单个元素构成的元组，必须要在结尾加上逗号：


```Python
>>> t1 = 'a',
>>> type(t1)
<class 'tuple'>
```




A value in parentheses is not a tuple:
>只用括号放一个值则并不是元组：


```Python
>>> t2 = ('a')
>>> type(t2)
<class 'str'>
```


Another way to create a tuple is the built-in function tuple. With no argument, it creates an empty tuple:
>另一中建立元组的方法是使用内置函数 tuple。不提供参数的情况下，默认就建立一个空的元组。

```Python
>>> t = tuple()
>>> t
()
```



If the argument is a sequence (string, list or tuple), the result is a tuple with the elements of the sequence:
>如果参数为一个序列（比如字符串、列表或者元组），结果就会得到一个以该序列元素组成的元组。

```Python
>>> t = tuple('lupins')
>>> t
('l', 'u', 'p', 'i', 'n', 's')
```


Because tuple is the name of a built-in function, you should avoid using it as a variable name.
Most list operators also work on tuples. The bracket operator indexes an element:
>tuple 是内置函数命了，所以你就不能用来作为变量名了。
>列表的各种运算符也基本适用于元组。方括号可以用来索引元素：


```Python
>>> t = ('a', 'b', 'c', 'd', 'e')
>>> t[0]
'a'
```



And the slice operator selects a range of elements.
>切片运算符也可以用于选取某一区间的元素。


```Python
>>> t[1:3]
('b', 'c')
```



But if you try to modify one of the elements of the tuple, you get an error:
>但如果你想修改元组中的某个元素，就会得到错误了：

```Python
>>> t[0] = 'A'
TypeError: object doesn't support item assignment
```



Because tuples are immutable, you can’t modify the elements. But you can replace one tuple with another:
>因为元组是不能修改的，你不能修改其中的元素。但是可以用另一个元组来替换已有的元组。

```Python
>>> t = ('A',) + t[1:]
>>> t
('A', 'b', 'c', 'd', 'e')
```



This statement makes a new tuple and then makes t refer to it.
The relational operators work with tuples and other sequences; Python starts by comparing the first element from each sequence. If they are equal, it goes on to the next elements, and so on, until it finds elements that differ. Subsequent elements are not considered (even if they are really big).
>上面这个语句建立了一个新的元组，然后让 t 指向了这个新的元组。
>关系运算符也适用于元组和其他序列；Python 从每个元素的首个元素开始对比。如果相等，就对比下一个元素，依此类推，之道找到不同元素为止。
>有了不同元素之后，后面的其他元素就被忽略掉了（即便很大也没用）。


```Python
>>> (0, 1, 2) < (0, 3, 4)
True
>>> (0, 1, 2000000) < (0, 3, 4)
True
```



##12.2  Tuple assignment 元组赋值

It is often useful to swap the values of two variables. With conventional assignments, you have to use a temporary variable. For example, to swap a and b:
>对两个变量的值进行交换是一种常用操作。用常见语句来实现的话，就必须有一个临时变量。比如下面这个例子中是交换 a 和 b：



```Python
>>> temp = a
>>> a = b
>>> b = temp
```


This solution is cumbersome; tuple assignment is more elegant:
>这样解决还是挺麻烦的；用元组赋值就更简洁了：

```Python
>>> a, b = b, a
```


The left side is a tuple of variables; the right side is a tuple of expressions. Each value is assigned to its respective variable. All the expressions on the right side are evaluated before any of the assignments.
The number of variables on the left and the number of values on the right have to be the same:
>等号左边的是变量组成的一个元组；右边的是表达式的元组。每个值都被赋给了对应的变量。等号右边的表达式的值保留了赋值之前的初始值。
>等号左右两侧的变量和值的数目都必须是一样的。


```Python
>>> a, b = 1, 2, 3
ValueError: too many values to unpack
```



More generally, the right side can be any kind of sequence (string, list or tuple). For example, to split an email address into a user name and a domain, you could write:
>更普适的情况下，等号右边以是任意一种序列（字符串、列表或者元组）。比如，要把一个电子邮件地址转换成一个用户名和一个域名，可以用如下代码实现：


```Python
>>> addr = 'monty@python.org'
>>> uname, domain = addr.split('@')
```




The return value from split is a list with two elements; the first element is assigned to uname, the second to domain.
>split 的返回值是一个有两个元素的列表；第一个元素赋值给了 uname 这个变量，第二个赋值给了 domain 这个变量。



```Python
>>> uname
'monty'
>>> domain
'python.org'
```



##12.3  Tuples as return values 用元组做返回值



Strictly speaking, a function can only return one value, but if the value is a tuple, the effect is the same as returning multiple values. For example, if you want to divide two integers and compute the quotient and remainder, it is inefficient to compute x/y and then x%y. It is better to compute them both at the same time.
>严格来说，一个函数只能返回一个值，但如果这个值是一个元组，效果就和返回多个值一样了。例如，如果你想要将两个整数相除，计算商和余数，如果要分开计算 x/y 以及 x%y 就很麻烦了。更好的办法是同时计算这两个值。



The built-in function divmod takes two arguments and returns a tuple of two values, the quotient and remainder. You can store the result as a tuple:
>内置函数 divmod 就会接收两个参数，然后返回一个有两个值的元组，这两个值分别为商和余数。
>可以把结果存储为一个元组：


```Python
>>> t = divmod(7, 3)
>>> t
(2, 1)
```




Or use tuple assignment to store the elements separately:
>或者可以用元组赋值来分别存储这两个值：


```Python
>>> quot, rem = divmod(7, 3)
>>> quot
2
>>> rem
1
```



Here is an example of a function that returns a tuple:
>下面的例子中，函数返回一个元组作为返回值：


```Python
def min_max(t):
	return min(t), max(t)
```


max and min are built-in functions that find the largest and smallest elements of a sequence. min_max computes both and returns a tuple of two values.
>max 和 min 都是内置函数，会找到序列中的最大值或者最小值，min_max 这个函数会同时求得最大值和最小值，然后把这两个值作为元组来返回。


##12.4  Variable-length argument tuples 参数长度可变的元组



Functions can take a variable number of arguments. A parameter name that begins with * gathers arguments into a tuple. For example, printall takes any number of arguments and prints them:
>函数的参数可以有任意多个。用星号*开头来作为形式参数名，可以将所有实际参数收录到一个元组中。例如 printall 就可以获取任意多个数的参数，然后把它们都打印输出：


```Python
def printall(*args):
	print(args)
```


The gather parameter can have any name you like, but args is conventional. Here’s how the function works:
>你可以随意命名收集来的这些参数，但 args 这个是约定俗成的惯例。下面展示一下这个函数如何使用：


```Python
>>> printall(1, 2.0, '3')
(1, 2.0, '3')
```


The complement of gather is scatter. If you have a sequence of values and you want to pass it to a function as multiple arguments, you can use the *operator. For example, divmod takes exactly two arguments; it doesn’t work with a tuple:
>与聚集相对的就是分散了。如果有一系列的值，然后想把它们作为多个参数传递给一个函数，就可以用星号*运算符。比如 divmod 要求必须是两个参数；如果给它一个元组，是不能进行运算的：


```Python
>>> t = (7, 3)
>>> divmod(t)
TypeError: divmod expected 2 arguments, got 1
```



But if you scatter the tuple, it works:
>但如果拆分这个元组，就可以了：


```Python
>>> divmod(*t)
(2, 1)
```



Many of the built-in functions use variable-length argument tuples. For example, max and min can take any number of arguments:
>很多内置函数都用到了参数长度可变的元组。比如 max 和 min 就可以接收任意数量的参数：



```Python
>>> max(1, 2, 3)
3
```


But sum does not.
>但求和函数 sum 就不行了。


```Python
>>> sum(1, 2, 3)
TypeError: sum expected at most 2 arguments, got 3
```


As an exercise, write a function called sumall that takes any number of arguments and returns their sum.
>做个练习，写一个名为 sumall 的函数，让它可以接收任意数量的参数，返回总和。


##12.5  Lists and tuples 列表和元组




zip is a built-in function that takes two or more sequences and returns a list of tuples where each tuple contains one element from each sequence. The name of the function refers to a zipper, which joins and interleaves two rows of teeth.
This example zips a string and a list:
>zip 是一个内置函数，接收两个或更多的序列作为参数，然后返回返回一个元组列表，该列表中每个元组都包含了从各个序列中的一个元素。这个函数名的意思就是拉锁，就是把不相关的两排拉锁齿连接到一起。
>下面这个例子中，一个字符串和一个列表通过 zip 这个函数连接到了一起：

```Python
>>> s = 'abc'
>>> t = [0, 1, 2]
>>> zip(s, t)
<zip object at 0x7f7d0a9e7c48>
```




The result is a zip object that knows how to iterate through the pairs. The most common use of zip is in a for loop:
>该函数的返回值是一个 zip 对象，该对象可以用来迭代所有的数值对。zip 函数经常被用到 for 循环中：


```Python
>>> for pair in zip(s, t): ...
print(pair) ...
('a', 0) ('b', 1) ('c', 2)
```


A zip object is a kind of iterator, which is any object that iterates through a sequence. Iterators are similar to lists in some ways, but unlike lists, you can’t use an index to select an element from an iterator.
If you want to use list operators and methods, you can use a zip object to make a list:
>zip 对象是一种迭代器，也就是某种可以迭代整个序列的对象。迭代器和列表有些相似，但不同于列表的是，你无法通过索引来选择迭代器中的指定元素。
>如果想用列表的运算符和方法，可以用 zip 对象来构成一个列表：


```Python
>>> list(zip(s, t))
[('a', 0), ('b', 1), ('c', 2)]
```



The result is a list of tuples; in this example, each tuple contains a character from the string and the corresponding element from the list.
If the sequences are not the same length, the result has the length of the shorter one.
>返回值是一个由元组构成的列表；在这个例子中，每个元组都包含了字符串中的一个字母，以及列表中对应位置的元素。
>在长度不同的序列中，返回的结果长度取决于最短的一个。


```Python
>>> list(zip('Anne', 'Elk'))
[('A', 'E'), ('n', 'l'), ('n', 'k')]
```



You can use tuple assignment in a for loop to traverse a list of tuples:
>用 for 循环来遍历一个元组列表的时候，可以用元组赋值语句：



```Python
t = [('a', 0), ('b', 1), ('c', 2)]
for letter, number in t:
	print(number, letter)
```


Each time through the loop, Python selects the next tuple in the list and assigns the elements to letter and number. The output of this loop is:
>每次经历循环的时候，Python 都选中列表中的下一个元组，然后把元素赋值给字母和数字。该循环的输出如下：


```Python
0 a 1 b 2 c
```



If you combine zip, for and tuple assignment, you get a useful idiom for traversing two (or more) sequences at the same time. For example, has_match takes two sequences, t1 and t2, and returns True if there is an index i such that t1[i] == t2[i]:
>如果结合使用 zip、for 循环以及元组赋值，就能得到一种能同时遍历两个以上序列的代码组合。比如下面例子中的 has_match 这个函数，接收两个序列t1和 t2作为参数，然后如果存在一个索引位置 i 使得 t1[i] == t2[i]就返回真：


```Python
def has_match(t1, t2):
	for x, y in zip(t1, t2):
		if x == y:
			return True
	return False
```



If you need to traverse the elements of a sequence and their indices, you can use the built-in function enumerate:
>如果你要遍历一个序列中的所有元素以及它们的索引，可以用内置的函数 enumerate：



```Python
for index, element in enumerate('abc'):
	print(index, element)
```



The result from enumerate is an enumerate object, which iterates a sequence of pairs; each pair contains an index (starting from 0) and an element from the given sequence. In this example, the output is
```Python
0 a 1 b 2 c
```
Again.
>enumerate 函数的返回值是一个枚举对象，它会遍历整个成对序列；每一对都包括一个索引（从0开始）以及给定序列的一个元素。在本节的例子中，输出依然如下：
>



```Python
0 a 1 b 2 c
```



##12.6  Dictionaries and tuples 词典与元组


Dictionaries have a method called items that returns a sequence of tuples, where each tuple is a key-value pair.
>字典有一个名为 items 的方法，会返回一个由元组组成的序列，每一个元组都是字典中的一个键值对。

```Python
>>> d = {'a':0, 'b':1, 'c':2}
>>> t = d.items()
>>> t
dict_items([('c', 2), ('a', 0), ('b', 1)])
```




The result is a dict_items object, which is an iterator that iterates the key-value pairs. You can use it in a for loop like this:
>结果是一个 dict_items 对象，这是一个迭代器，迭代所有的键值对。可以在 for 循环里面用这个对象，如下所示：

```Python
>>> for key, value in d.items():
...     print(key, value)
... c 2 a 0 b 1
```




As you should expect from a dictionary, the items are in no particular order.
Going in the other direction, you can use a list of tuples to initialize a new dictionary:
>你也应该预料到了，字典里面的项是没有固定顺序的。
>反过来使用的话，你就也可以用一个元组的列表来初始化一个新的字典：


```Python
>>> t = [('a', 0), ('c', 2), ('b', 1)]
>>> d = dict(t)
>>> d
{'a': 0, 'c': 2, 'b': 1}
```



Combining dict with zip yields a concise way to create a dictionary:
>结合使用 dict 和 zip ，会得到一种建立字典的简便方法：


```Python
>>> d = dict(zip('abc', range(3)))
>>> d
{'a': 0, 'c': 2, 'b': 1}
```



The dictionary method update also takes a list of tuples and adds them, as key-value pairs, to an existing dictionary.
>字典的 update 方法也接收一个元组列表，然后把它们作为键值对添加到一个已存在的字典中。



It is common to use tuples as keys in dictionaries (primarily because you can’t use lists). For example, a telephone directory might map from last-name, first-name pairs to telephone numbers. Assuming that we have defined last, first and number, we could write:
>把元组用作字典中的键是很常见的做法（主要也是因为这种情况不能用列表）。比如，一个电话字典可能就映射了姓氏、名字的数据对到不同的电话号码。假如我们定义了 last，first 和 number 这三个变量，可以用如下方法来实现：


```Python
directory[last, first] = number
```




The expression in brackets is a tuple. We could use tuple assignment to traverse this dictionary.
>方括号内的表达式是一个元组。我们可以用元组赋值语句来遍历这个字典。


```Python
for last, first in directory:
	print(first, last, directory[last,first])
```




This loop traverses the keys in directory, which are tuples. It assigns the elements of each tuple to last and first, then prints the name and corresponding telephone number.
>上面这个循环会遍历字典中的键，这些键都是元组。程序会把每个元组的元素分别赋值给 last 和 first，然后输出名字以及对应的电话号。


There are two ways to represent tuples in a state diagram. The more detailed version shows the indices and elements just as they appear in a list. For example, the tuple ('Cleese', 'John') would appear as in Figure 12.1.
>在状态图中表示元组的方法有两种。更详尽的版本会展示索引和元素，就如同在列表中一样。例如图12.1中展示了元组('Cleese', 'John') 。


________________________________________

![Figure 12.1: State diagram](./images/figure12.1.jpg)

Figure 12.1: State diagram.
________________________________________



But in a larger diagram you might want to leave out the details. For example, a diagram of the telephone directory might appear as in Figure 12.2.
>但随着图解规模变大，你也许需要省略掉一些细节。比如电话字典的图解可能会像图12.2所示。





________________________________________

![Figure 12.2: State diagram](./images/figure12.2.jpg)

Figure 12.2: State diagram.
________________________________________



Here the tuples are shown using Python syntax as a graphical shorthand. The telephone number in the diagram is the complaints line for the BBC, so please don’t call it.
>图中的元组用 Python 的语法来简单表示。其中的电话号码是 BBC 的投诉热线，所以不要给人家打电话哈。





##12.7  Sequences of sequences 序列的序列



I have focused on lists of tuples, but almost all of the examples in this chapter also work with lists of lists, tuples of tuples, and tuples of lists. To avoid enumerating the possible combinations, it is sometimes easier to talk about sequences of sequences.
>之前我一直在讲由元组组成的列表，但本章几乎所有的例子也适用于由列表组成的列表、元组组成的元组以及列表组成的元组。为了避免枚举所有的组合，咱们直接讨论序列组成的序列就更方便一些。





In many contexts, the different kinds of sequences (strings, lists and tuples) can be used interchangeably. So how should you choose one over the others?
>很多情况下，不同种类的序列（字符串、列表和元组）是可以交换使用的。那么该如何选择用哪种序列呢？


To start with the obvious, strings are more limited than other sequences because the elements have to be characters. They are also immutable. If you need the ability to change the characters in a string (as opposed to creating a new string), you might want to use a list of characters instead.
>先从最简单的开始，字符串比起其他序列，功能更加有限，因为字符串中的元素必须是字符。而且还不能修改。如果你要修改字符串里面的字符（而不是要建立一个新字符串），你最好还是用字符列表吧。



Lists are more common than tuples, mostly because they are mutable. But there are a few cases where you might prefer tuples:
>列表用的要比元组更广泛，主要因为列表可以修改。但以下这些情况下，你还是用元组更好：


1.	In some contexts, like a return statement, it is syntactically simpler to create a tuple than a list.
>在某些情况下，比如返回语句中，用元组来实现语法上要比列表简单很多。




2.	If you want to use a sequence as a dictionary key, you have to use an immutable type like a tuple or string.
>如果你要用一个序列作为字典的键，必须用元组或者字符串这样不可修改的类型才行。



3.	If you are passing a sequence as an argument to a function, using tuples reduces the potential for unexpected behavior due to aliasing.
>如果你要把一个序列作为参数传给一个函数，用元组能够降低由于别名使用导致未知情况而带来的风险。



Because tuples are immutable, they don’t provide methods like sort and reverse, which modify existing lists. But Python provides the built-in function sorted, which takes any sequence and returns a new list with the same elements in sorted order, and reversed, which takes a sequence and returns an iterator that traverses the list in reverse order.
>由于元组是不可修改的，所以不提供 sort 和 reverse 这样的方法，这些方法都只能修改已经存在的列表。但 Python 提供了内置函数 sorted，该函数接收任意序列，然后返回一个把该序列中元素重新排序过的列表，另外还有个内置函数 reversed，接收一个序列然后返回一个以逆序迭代整个列表的迭代器。



##12.8  Debugging 调试



Lists, dictionaries and tuples are examples of data structures; in this chapter we are starting to see compound data structures, like lists of tuples, or dictionaries that contain tuples as keys and lists as values. Compound data structures are useful, but they are prone to what I call shape errors; that is, errors caused when a data structure has the wrong type, size, or structure. For example, if you are expecting a list with one integer and I give you a plain old integer (not in a list), it won’t work.

>列表、字典以及元组，都是数据结构的一些样例；在本章我们开始见识这些复合的数据结构，比如由元组组成的列表，或者包含元组作为键而列表作为键值的字典等等。符合数据结构非常有用，但容易导致一些错误，我把这种错误叫做结构错误；这种错误往往是由于一个数据结构中出现了错误的类型、大小或者结构而引起的。比如，如果你想要一个由一个整形构成的列表，而我给你一个单纯的整形变量（不是放进列表的），就会出错了。






To help debug these kinds of errors, I have written a module called structshape that provides a function, also called structshape, that takes any kind of data structure as an argument and returns a string that summarizes its shape. You can download it from [Here](http://thinkpython2.com/code/structshape.py).
>要想有助于解决这类错误，我写了一个叫做structshape 的模块，该模块提供了一个同名函数，接收任何一种数据结构作为参数，然后返回一个字符串来总结该数据结构的形态。可以从 [这里](http://thinkpython2.com/code/structshape.py)下载。


Here’s the result for a simple list:
>下面是一个简单列表的示范：

```Python
>>> from structshape import structshape
>>> t = [1, 2, 3]
>>> structshape(t)
'list of 3 int'
```



A fancier program might write “list of 3 ints”, but it was easier not to deal with plurals. Here’s a list of lists:
>更带劲点的程序可能还应该写“list of 3 ints”，但不理会单复数变化有利于简化问题。下面是一个列表的列表：


```Python
>>> t2 = [[1,2], [3,4], [5,6]]
>>> structshape(t2)
'list of 3 list of 2 int'
```



If the elements of the list are not the same type, structshape groups them, in order, by type:
>如果列表元素是不同类型，structshape 会按照顺序，把每种类型都列出：


```Python
>>> t3 = [1, 2, 3, 4.0, '5', '6', [7], [8], 9]
>>> structshape(t3)
'list of (3 int, float, 2 str, 2 list of int, int)'
```




Here’s a list of tuples:
>下面是一个元组的列表：


```Python
>>> s = 'abc'
>>> lt = list(zip(t, s))
>>> structshape(lt)
'list of 3 tuple of (int, str)'
```



And here’s a dictionary with 3 items that map integers to strings.
>下面是一个有三个项的字典，该字典映射了从整形数到字符串。


```Python
>>> d = dict(lt)
>>> structshape(d)
'dict of 3 int->str'
```




If you are having trouble keeping track of your data structures, structshape can help.
>如果你追踪自己的数据结构有困难，structshape这个模块能有所帮助。




##12.9  Glossary 术语列表



tuple:
An immutable sequence of elements.
>元组：一列元素组成的不可修改的序列。



tuple assignment:
An assignment with a sequence on the right side and a tuple of variables on the left. The right side is evaluated and then its elements are assigned to the variables on the left.
>元组赋值：一种赋值语句，等号右侧用一个序列，左侧为一个变量构成的元组。右侧的内容先进行运算，然后这些元素会赋值给左侧的变量。



gather:
The operation of assembling a variable-length argument tuple.
>收集：变量长度可变元组添加元素的运算。




scatter:
The operation of treating a sequence as a list of arguments.
>分散：将一个序列拆分成一系列参数组成的列表的运算。



zip object:
The result of calling a built-in function zip; an object that iterates through a sequence of tuples.
>拉链对象：调用内置函数 zip 得到的返回结果；一个遍历元组序列的对象。



iterator:
An object that can iterate through a sequence, but which does not provide list operators and methods.
>迭代器：迭代一个序列的对象，这种序列不能提供列表的运算和方法。



data structure:
A collection of related values, often organized in lists, dictionaries, tuples, etc.
>数据结构：一些有关系数据的集合体，通常是列表、字典或者元组等形式。



shape error:
An error caused because a value has the wrong shape; that is, the wrong type or size.
>结构错误：由于一个值有错误的结构而导致的错误；比如错误的类型或者大小。



##12.10  Exercises 练习



###Exercise 1 练习1
Write a function called most_frequent that takes a string and prints the letters in decreasing order of frequency. Find text samples from several different languages and see how letter frequency varies between languages. Compare your results with the tables at [Here](http://en.wikipedia.org/wiki/Letter_frequencies). [Solution](http://thinkpython2.com/code/most_frequent.py).
>写一个名为most_frequent的函数，接收一个字符串，然后用出现频率降序来打印输出字母。找一些不同语言的文本素材，然后看看不同语言情况下字母的频率变化多大。然后用你的结果与[这里](http://en.wikipedia.org/wiki/Letter_frequencies)的数据进行对比。[样例代码](http://thinkpython2.com/code/most_frequent.py)。










###Exercise 2 练习2



More anagrams!
>更多变位词了！

1.	Write a program that reads a word list from a file (see Section 9.1) and prints all the sets of words that are anagrams.
>写一个函数，读取一个文件中的一个单词列表（参考9.1），然后输出所有的变位词。

Here is an example of what the output might look like:
>下面是可能的输出样式的示范：

['deltas', 'desalt', 'lasted', 'salted', 'slated', 'staled']
['retainers', 'ternaries']
['generating', 'greatening']
['resmelts', 'smelters', 'termless']

Hint: you might want to build a dictionary that maps from a collection of letters to a list of words that can be spelled with those letters. The question is, how can you represent the collection of letters in a way that can be used as a key?
>提示：你也许可以建立一个字典，映射一个特定的字母组合到一个单词列表，单词列表中的单词可以用这些字母来拼写出来。那么问题来了，如何去表示这个字母的集合，才能让这个集合能用作字典的一个键？

2.	Modify the previous program so that it prints the longest list of anagrams first, followed by the second longest, and so on.
>修改一下之前的程序，让它先输出变位词列表中最长的，然后是其次长的，依此类推。



3.	In Scrabble a “bingo” is when you play all seven tiles in your rack, along with a letter on the board, to form an eight-letter word. What collection of 8 letters forms the most possible bingos? Hint: there are seven.
[Solution](http://thinkpython2.com/code/anagram_sets.py).
>在拼字游戏中，当你已经有七个字母的时候，再添加一个字母就能组成一个八个字母的单词，这就 TMD『bingo』 了（什么鬼东西？老外者拼字游戏就跟狗一样，翻着恶心死了）。然后哪八个字母组合起来最可能得到 bingo？提示：有七个。（简直就是狗一样的题目，麻烦死了，这里数据结构大家学会了就好了。）




###Exercise 3 练习3


Two words form a “metathesis pair” if you can transform one into the other by swapping two letters; for example, “converse” and “conserve”. Write a program that finds all of the metathesis pairs in the dictionary. Hint: don’t test all pairs of words, and don’t test all possible swaps. [Solution](http://thinkpython2.com/code/metathesis.py). Credit: This exercise is inspired by an example at [Here](http://puzzlers.org).
>两个单词，如果其中一个通过调换两个字母位置就能成为另外一个，就成了一个『交换对』。协议额函数来找到词典中所有的这样的交换对。提示：不用测试所有的词对，不用测试所有可能的替换方案。[样例代码](http://thinkpython2.com/code/metathesis.py)。 鸣谢：本练习受启发于[这里](http://puzzlers.org)的一个例子。





###Exercise 4 练习4

Here’s another [Car Talk Puzzler](http://www.cartalk.com/content/puzzlers):
>接下来又是一个[汽车广播字谜](http://www.cartalk.com/content/puzzlers):

What is the longest English word, that remains a valid English word, as you remove its letters one at a time?
Now, letters can be removed from either end, or the middle, but you can’t rearrange any of the letters. Every time you drop a letter, you wind up with another English word. If you do that, you’re eventually going to wind up with one letter and that too is going to be an English word—one that’s found in the dictionary. I want to know what’s the longest word and how many letters does it have?
>一个英文单词，每次去掉一个字母，又还是一个正确的英文单词，这是什么词？
>然后接下来字母可以从头去掉，也可以从末尾去掉，或者从中间，但不能重新排列其他字母。每次去掉一个字母，都会的到一个新的英文单词。然后最终会得到一个字母，也还是一个英文单词，这个单词也能在词典中找到。符合这样要求的单词有多少？最长的是哪个？


I’m going to give you a little modest example: Sprite. Ok? You start off with sprite, you take a letter off, one from the interior of the word, take the r away, and we’re left with the word spite, then we take the e off the end, we’re left with spit, we take the s off, we’re left with pit, it, and I.
>给你一个合适的小例子：Sprite。这个词就满足上面的条件。把 r 去掉了是 spite，去掉结尾的 e 是 spit，去掉 s 得到的是 pit，it，然后是 I。


Write a program to find all words that can be reduced in this way, and then find the longest one.
This exercise is a little more challenging than most, so here are some suggestions:
>写一个函数找到所有的这样的词，然后找到其中最长的一个。
>这个练习比一般的练习难以些，所以下面是一些提示：


1.	You might want to write a function that takes a word and computes a list of all the words that can be formed by removing one letter. These are the “children” of the word.
>你也许需要写一个函数，接收一个单词然后计算一下这个单词去掉一个字母能得到单词组成的列表。列表中这些单词就如同原始单词的孩子一样。


2.	Recursively, a word is reducible if any of its children are reducible. As a base case, you can consider the empty string reducible.
>只要一个 单词的孩子还可以缩减，那这个单词本身就亏缩减。你可以认为空字符串是可以缩减的，这样来作为一个基准条件。


3.	The wordlist I provided, words.txt, doesn’t contain single letter words. So you might want to add “I”, “a”, and the empty string.
>我上面提供的 words.txt 这个词表，不包含单个字母的单词。所以你需要自行添加 I、a 以及空字符串上去。


4.	To improve the performance of your program, you might want to memoize the words that are known to be reducible.
>要提高程序性能的话，你最好存储住已经算出来能被继续缩减的单词。


[Solution](http://thinkpython2.com/code/reducible.py).
>[样例代码](http://thinkpython2.com/code/reducible.py)。

