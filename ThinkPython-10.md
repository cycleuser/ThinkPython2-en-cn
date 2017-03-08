Title: ThinkPython 双语学编程 Chapter 10
Date: 2015-11-30
Category: ThinkPython
Tag: 双语,Python,ThinkPython

#Chapter 10  Lists 列表
This chapter presents one of Python’s most useful built-in types, lists. You will also learn more about objects and what can happen when you have more than one name for the same object.
>本章讲述的是 Python 里面最有用的一种内置类型：列表。你还能在本章中学到更多关于类的内容，你还会看到如果同一个对象有多个名字会有什么情况发生。


##10.1  A list is a sequence 列表即序列
Like a string, a list is a sequence of values. In a string, the values are characters; in a list, they can be any type. The values in a list are called elements or sometimes .
>和字符串差不多，列表是一系列的数值的序列。在字符串里面，这些值是字符；在列表里面，这些值可以是任意类型的。一个列表中的值一般叫做列表的元素，有时候也叫列表项。

There are several ways to create a new list; the simplest is to enclose the elements in square brackets ([ and ]):
>创建一个新的列表有好几种方法；最简单的方法就是把列表的元素用方括号包含起来：


```Python
[10, 20, 30, 40]
['crunchy frog', 'ram bladder', 'lark vomit']
```


The first example is a list of four integers. The second is a list of three strings. The elements of a list don’t have to be the same type. The following list contains a string, a float, an integer, and (lo!) another list:
>第一个例子建立了一个由四个整形变量组成的列表。第二个是一个由三个字符串组成的列表。

```Python
['spam', 2.0, 5, [10, 20]]
```

A list within another list is nested.
A list that contains no elements is called an empty list; you can create one with empty brackets, [].
As you might expect, you can assign list values to variables:
>列表内部可以包含一个列表作为元素，这种包含列表的列表也叫做网状列表。
>不含有任何元素的列表叫做空列表；可以就用空的方括号来建立一个。
>你估计也会预料到，列表的值可以赋给变量：


```Python
>>> cheeses = ['Cheddar', 'Edam', 'Gouda']
>>> numbers = [42, 123]
>>> empty = []
>>> print(cheeses, numbers, empty)
['Cheddar', 'Edam', 'Gouda']
[42, 123]
[]
```




##10.2  Lists are mutable 列表元素可修改

The syntax for accessing the elements of a list is the same as for accessing the characters of a string—the bracket operator. The expression inside the brackets specifies the index. Remember that the indices start at 0:
>读取列表元素的语法就如同读取字符串中的字符一样-用方括号运算符就可以了。方括号内的数字用来确定索引位置。一定要记住，Python 是从零开始计数的：

```Python
>>> cheeses[0]
'Cheddar'
```


Unlike strings, lists are mutable. When the bracket operator appears on the left side of an assignment, it identifies the element of the list that will be assigned.
>和字符串不同的是，列表是可以修改的。方括号运算符放到一个赋值语句的等号左侧的时候，就会把对应位置的列表元素重新赋值。


```Python
>>> numbers = [42, 123]
>>> numbers[1] = 5
>>> numbers
[42, 5]
```



The one-eth element of numbers, which used to be 123, is now 5.
Figure 10.1 shows the state diagram for cheeses, numbers and empty:
>列表 numbers 的第『1』个元素之前是123，现在被改为5了。
>图10.1展示了 cheeses、numbers 和空列表的状态图：



________________________________________
![Figure 10.1: State diagram](http://7xnq2o.com1.z0.glb.clouddn.com/ThinkPythonFigure10.1-%20State%20diagram.png)
Figure 10.1: State diagram.
________________________________________

Lists are represented by boxes with the word “list” outside and the elements of the list inside. cheeses refers to a list with three elements indexed 0, 1 and 2.numbers contains two elements; the diagram shows that the value of the second element has been reassigned from 123 to 5. empty refers to a list with no elements.
>这三个列表都用标记了『list』的三个小盒子表示，盒子外面的是列表的名字，盒子内的就是列表元素了。cheese 是一个有0，1，2三个元素的列表。numbers 包含两个元素；图示表明第二个元素的值从123被重新赋值为5。empty 是一个不包含元素的空列表。




List indices work the same way as string indices:
>列表的索引和字符串的索引的格式是一样的：

•	Any integer expression can be used as an index.
>任意的一个整型表达式，都可以用来作为索引编号。



•	If you try to read or write an element that does not exist, you get an IndexError.
>如果你试图读取或者写入一个不存在的列表元素，你就会得到一个索引错误 IndexError。


•	If an index has a negative value, it counts backward from the end of the list.
>如果一个索引是负值，意味着是从列表末尾向前倒序计数查找相对应的位置。

The in operator also works on lists.
>在列表中也可以使用 in 运算符。

```Python
>>> cheeses = ['Cheddar', 'Edam', 'Gouda']
>>> 'Edam' in cheeses
True
>>> 'Brie' in cheeses
False
```





##10.3  Traversing a list 遍历一个列表


The most common way to traverse the elements of a list is with a for loop. The syntax is the same as for strings:
>遍历一个列表中所有元素的最常用的办法就是 for 循环了。这种 for 循环和我们在遍历一个字符串的时候用的是一样的的语法：



```Python
for cheese in cheeses:
	print(cheese)
```



This works well if you only need to read the elements of the list. But if you want to write or update the elements, you need the indices. A common way to do that is to combine the built-in functions range and len:
>如果你只是要显示一下列表元素，上面这个代码就够用了。但如果你还想写入或者更新这些元素，你还是需要用索引。一般来说，这需要把两个内置函数 range 和 len 结合起来使用：


```Python
for i in range(len(numbers)):
	numbers[i] = numbers[i] * 2
```



This loop traverses the list and updates each element. len returns the number of elements in the list. range returns a list of indices from 0 to n−1, where n is the length of the list. Each time through the loop i gets the index of the next element. The assignment statement in the body uses i to read the old value of the element and to assign the new value.
>这个循环遍历了列表，然后对每个元素都进行了更新。len 这个函数返回的是列表中元素的数量。range 返回的是列表的一系列索引，从0到 n-1，n 就是整个列表的长度了。每次循环的时候，i 都会得到下一个元素的索引值。在循环体内部的赋值语句每次都通过 i 作为索引来读该元素的旧值，进行修改然后赋新值给该元素。


A for loop over an empty list never runs the body:
>空列表的 for 循环中，循环体是永远不会运行的：


```Python
for x in []:
	print('This never happens.')
```



Although a list can contain another list, the nested list still counts as a single element. The length of this list is four:
>尽管列表中可以办好另外一个列表，但这种网状的分支列表依然只会被算作一个元素。所以下面这个列表的长度是4：

```Python
['spam', 1, ['Brie', 'Roquefort', 'Pol le Veq'], [1, 2, 3]]
```





##10.4  List operations 列表运算符



The + operator concatenates lists:
>加号+运算符可以把列表拼接在一起：

```Python
>>> a = [1, 2, 3]
>>> b = [4, 5, 6]
>>> c = a + b
>>> c
[1, 2, 3, 4, 5, 6]
```



The * operator repeats a list a given number of times:
>星号*运算符可以将列表重复指定的次数：

```Python
>>> [0] * 4
[0, 0, 0, 0]
>>> [1, 2, 3] * 3
[1, 2, 3, 1, 2, 3, 1, 2, 3]
```


The first example repeats [0] four times. The second example repeats the list[1, 2, 3] three times.
>第一个例子中，[0]这个列表被重复四次。第二个例子把列表[1,2,3]重复了三次。




##10.5  List slices 列表切片


The slice operator also works on lists:
>切片操作符也可以用到列表上：

```Python
>>> t = ['a', 'b', 'c', 'd', 'e', 'f']
>>> t[1:3]
['b', 'c']
>>> t[:4]
['a', 'b', 'c', 'd']
>>> t[3:]
['d', 'e', 'f']
```


If you omit the first index, the slice starts at the beginning. If you omit the second, the slice goes to the end. So if you omit both, the slice is a copy of the whole list.
>在切片运算中，如果你省略了第一个索引，切片就会从头开始。如果省略了第二个，切片就会一直走到末尾。所以如果你把两个都省略了，这个切片就是整个列表的一个复制了。


```Python
>>> t[:]
['a', 'b', 'c', 'd', 'e', 'f']
```



Since lists are mutable, it is often useful to make a copy before performing operations that modify lists.
A slice operator on the left side of an assignment can update multiple elements:
>因为列表是可以修改的，所以在进行运算修改列表之前，做个复制来备份经常是很有必要的。
>切片运算符放到赋值语句中等号左边的时候可以对多个元素进行更新：


```Python
>>> t = ['a', 'b', 'c', 'd', 'e', 'f']
>>> t[1:3] = ['x', 'y']
>>> t
['a', 'x', 'y', 'd', 'e', 'f']
```



##10.6  List methods 列表的方法



Python provides methods that operate on lists. For example, append adds a new element to the end of a list:
>Python 为操作列表提供了很多方法。比如，append 就可以在列表末尾添加一个新的元素：


```Python
>>> t = ['a', 'b', 'c']
>>> t.append('d')
>>> t
['a', 'b', 'c', 'd']
```


extend takes a list as an argument and appends all of the elements:
>extend 使用另一个列表做参数，然后把所有的元素添加到一个列表上。


```Python
>>> t1 = ['a', 'b', 'c']
>>> t2 = ['d', 'e']
>>> t1.extend(t2)
>>> t1
['a', 'b', 'c', 'd', 'e']
```


This example leaves t2 unmodified.
>上面这个例子中，t2是没有修改过的。

sort arranges the elements of the list from low to high:
>sort 把列表中的元素从低到高（译者注：下面的例子中是按照 ASCII 码的大小从小到大）排列：


```Python
>>> t = ['d', 'c', 'e', 'b', 'a']
>>> t.sort()
>>> t
['a', 'b', 'c', 'd', 'e']
```

Most list methods are void; they modify the list and return None. If you accidentally write t = t.sort(), you will be disappointed with the result.
>大多数列表的方法都是无返回值的；这些方法都对列表进行修改，返回的是空。如果你不小心写出了一个 t=t.sort()，得到的结果恐怕让你很失望。


##10.7  Map, filter and reduce 列表中最重要的三种运算


To add up all the numbers in a list, you can use a loop like this:
>要得到列表中所有值的综合，你可以用下面这样的一个循环来实现：

```Python
def add_all(t):
	total = 0
	for x in t:
		total += x
	return total
```



total is initialized to 0. Each time through the loop, x gets one element from the list. The += operator provides a short way to update a variable. This augmented assignment statement, total += x is equivalent to total = total + x .
>total 的初始值为0。每次循环的时候，x 都得到列表中一个元素的值。+=这个运算符是更新变量的一种简写。这个运算符是扩展了赋值语句，total += x 就等同于 total = total +x 。


As the loop runs, total accumulates the sum of the elements; a variable used this way is sometimes called an accumulator.
>随着循环的运行，total 积累了所有元素的综合；这种变量也叫做累（三声）加器。


Adding up the elements of a list is such a common operation that Python provides it as a built-in function, sum:
>把列表中所有元素加起来是一种很常用的运算，所以 Python 提供了内置的函数 sum：



```Python
>>> t = [1, 2, 3]
>>> sum(t)
6
```




An operation like this that combines a sequence of elements into a single value is sometimes called reduce.
>把一系列列表元素组合成一个单值的运算，也叫做 reduce（这个单词是缩减的意思）。


Sometimes you want to traverse one list while building another. For example, the following function takes a list of strings and returns a new list that contains capitalized strings:
>有时候建立一个列表需要遍历另一个列表。比如下面的这个函数就接收一个字符串列表，将所有字符串变为大写字母组成的，然后返回一个这些大写字符串组成的新列表：




```Python
def capitalize_all(t):
	res = []
	for s in t:
		res.append(s.capitalize())
	return res
```



res is initialized with an empty list; each time through the loop, we append the next element. So res is another kind of accumulator.
>res 的初始值为一个空列表；每次循环的时候，我们都把下一个元素用 append 方法拼接上去。所以 res 也算是另外一种累加器了。


An operation like capitalize_all is sometimes called a map because it “maps” a function (in this case the method capitalize) onto each of the elements in a sequence.
>像上面这个capitalize_all 的运算也叫做一个 map（单词意思为地图），因为这种预算将某一函数（该例子中是 capitalize 这个方法）应用到一个序列中的每个元素上。


Another common operation is to select some of the elements from a list and return a sublist. For example, the following function takes a list of strings and returns a list that contains only the uppercase strings:
>另外一种常见运算是从列表中选取一些元素，然后返回一个次级列表。比如，下面的函数接收一个字符串列表，然后返回一个其中只包含大写字母的字符串所组成的列表：



```Python
def only_upper(t):
	res = []
	for s in t:
		if s.isupper():
			res.append(s)
	return res
```



isupper is a string method that returns True if the string contains only upper case letters.
>isupper 是一个字符串方法，如果字符串中只包含大写字母就会返回真。



An operation like only_upper is called a filter because it selects some of the elements and filters out the others.
>only_upper 这样的运算也叫 filter（过滤器的意思），因为这种运算筛选出特定的元素，过滤掉其他的。



Most common list operations can be expressed as a combination of map, filter and reduce.
>常用的列表运算都可以表示成 map、filter 以及 reduce 的组合。




##10.8  Deleting elements 删除元素



There are several ways to delete elements from a list. If you know the index of the element you want, you can use pop:
>从一个列表中删除元素有几种方法。如果你知道你要删除元素的索引，你就可以用 pop这个方法来实现：


```Python
>>> t = ['a', 'b', 'c']
>>> x = t.pop(1)
>>> t
['a', 'c']
>>> x
'b'
```


pop modifies the list and returns the element that was removed. If you don’t provide an index, it deletes and returns the last element.
>pop 修改列表，然后返回删除的元素。如果你不指定一个索引位置，pop 就会删除和返回最后一个元素。

If you don’t need the removed value, you can use the del operator:
>如果你不需要删掉的值了，你可以用 del 运算符来实现：


```Python
>>> t = ['a', 'b', 'c']
>>> del t[1]
>>> t
['a', 'c']
```




If you know the element you want to remove (but not the index), you can use remove:
>如果你知道你要删除的元素值，但不知道索引位置，你可以使用 remove 这个方法：


```Python
>>> t = ['a', 'b', 'c']
>>> t.remove('b')
>>> t
['a', 'c']
```



The return value from remove is None.
>remove 的返回值是空。



To remove more than one element, you can use del with a slice index:
>要删除更多元素，可以使用 del 和切片索引：



```Python
>>> t = ['a', 'b', 'c', 'd', 'e', 'f']
>>> del t[1:5]
>>> t
['a', 'f']
```





As usual, the slice selects all the elements up to but not including the second index.
>和之前我们看到的一样，切片是含头不含尾，上面这个例子中从第『1』到第『5』个都被切片所选中，但包含开头的第『1』而不包含末尾的第『5』个元素。


##10.9  Lists and strings 列表和字符串



A string is a sequence of characters and a list is a sequence of values, but a list of characters is not the same as a string. To convert from a string to a list of characters, you can use list:
>字符串是一系列字符的序列，而李白是一系列值的序列，但一个由字符组成的列表是不同于字符串的。要把一个字符串转换成字符列表，你可以用 list 这个函数：


```Python
>>> s = 'spam'
>>> t = list(s)
>>> t
['s', 'p', 'a', 'm']
```



Because list is the name of a built-in function, you should avoid using it as a variable name. I also avoid l because it looks too much like 1. So that’s why I use t.
>list 是一个内置函数的名字了，所以你应该避免用它来作为变量名。我还建议应该尽量少用 l，因为有的字体下，l 和1看着很难区分。所以我都用了 t。


The list function breaks a string into individual letters. If you want to break a string into words, you can use the split method:
>list 这个函数将一个字符串分开成一个个字母。如果你想把字符串切分成一个个单词，你可以用 split 这个方法：


```Python
>>> s = 'pining for the fjords'
>>> t = s.split()
>>> t
['pining', 'for', 'the', 'fjords']
```




An optional argument called a delimiter specifies which characters to use as word boundaries. The following example uses a hyphen as a delimiter:
>可选的参数是定界符，是用来确定单词边界的。下面这个例子中就是把连接号『-』作为定界符：


```Python
>>> s = 'spam-spam-spam'
>>> delimiter = '-'
>>> t = s.split(delimiter)
>>> t
['spam', 'spam', 'spam']
```


join is the inverse of split. It takes a list of strings and concatenates the elements. join is a string method, so you have to invoke it on the delimiter and pass the list as a parameter:
>join 是与 split 功能相反的一个方法。它接收一个字符串列表，然后把所有元素拼接到一起。join 是一个字符串方法，所以必须把 join 放到定界符后面来调用，并且传递一个列表作为参数：


```Python
>>> t = ['pining', 'for', 'the', 'fjords']
>>> delimiter = ' '
>>> s = delimiter.join(t)
>>> s
'pining for the fjords'
```




In this case the delimiter is a space character, so join puts a space between words. To concatenate strings without spaces, you can use the empty string,'', as a delimiter.
>上面这个例子中，定界符是一个空格字符，所以 join 就在单词只见放一个空格。要想把字符聚集到一切而不要空格，你就可以用空字符串""作为一个定界符了。



##10.10  Objects and values 对象和值



If we run these assignment statements:
>如果我们运行下面这种赋值语句：

```Python
a = 'banana'
b = 'banana'
```



We know that a and b both refer to a string, but we don’t know whether they refer to the same string. There are two possible states, shown in Figure 10.2.
>我们知道了 a 和 b 都是字符串，但我们不之道他们到底是不是同一个字符串。这就有可能有两种状态，如图10.2所示。


________________________________________
![Figure 10.2: State diagram](http://7xnq2o.com1.z0.glb.clouddn.com/ThinkPythonFigure10.2-%20State%20diagram.png)
Figure 10.2: State diagram.
________________________________________



In one case, a and b refer to two different objects that have the same value. In the second case, they refer to the same object.
To check whether two variables refer to the same object, you can use the is operator.
>在第一种情况中，a 和 b 指向两个不同的对象，这两个对象有相同的值。在第二个情况下，a 和 b 都指向同一个对象。
>要检查两个变量是否指向的是同一个对象，可以用 is 运算符。


```Python
>>> a = 'banana'
>>> b = 'banana'
>>> a is b
True
```



In this example, Python only created one string object, and both a and b refer to it. But when you create two lists, you get two objects:
>在这个例子中，Python 只建立了一个字符串对象，然后 a 和 b 都指向它。但当你建立两个列表的时候，你得到的就是两个对象了：



```Python
>>> a = [1, 2, 3]
>>> b = [1, 2, 3]
>>> a is b
False
```



So the state diagram looks like Figure 10.3.
>所以这时候的状态图就应该如图10.3所示的样子了。

________________________________________
![](http://7xnq2o.com1.z0.glb.clouddn.com/ThinkPythonFigure10.3-%20State%20diagram.png)
Figure 10.3: State diagram.
________________________________________



In this case we would say that the two lists are equivalent, because they have the same elements, but not identical, because they are not the same object. If two objects are identical, they are also equivalent, but if they are equivalent, they are not necessarily identical.
>在这个情况下，我们可以说两个列表是相等的，因为它们有相同的元素，但它们不是同一个列表，因为他们并不是同一个对象。如果两个对象是同一个对象，那它们必然是相等的，但如果它们相等，却未必是同一个对象。
>（译者注：同一 是 相等 的充分条件，相等 是 同一 的必要条件，仅此而已。）



Until now, we have been using “object” and “value” interchangeably, but it is more precise to say that an object has a value. If you evaluate [1, 2, 3], you get a list object whose value is a sequence of integers. If another list has the same elements, we say it has the same value, but it is not the same object.
>目前位置，我们一直把『对象』和『值』来随意交换使用，但实际上更确切的说法是一个对象拥有一个值。如果你计算[1,2,3]，你得到一个列表对象，整个列表对象的整个值是一个整数序列。如果另外一个列表有相同的元素，我们称之含有相同的值，但并不是相同的对象。



##10.11  Aliasing 别名


If a refers to an object and you assign b = a, then both variables refer to the same object:
>如果 a 是一个对象了，然后你赋值 b=a，那么这两个变量都指向同一个对象：

```Python
>>> a = [1, 2, 3]
>>> b = a
>>> b is a
True
```



The state diagram looks like Figure 10.4.
>此时的状态图如图10.4所示。



________________________________________
![Figure 10.4: State diagram](http://7xnq2o.com1.z0.glb.clouddn.com/ThinkPythonFigure10.4-%20State%20diagram.png)
Figure 10.4: State diagram.
________________________________________



The association of a variable with an object is called a reference. In this example, there are two references to the same object.
>一个变量和一个对象的关系叫做引用。在上面这个例子中，a 和 b 是对同一对象的两个引用。



An object with more than one reference has more than one name, so we say that the object is aliased.
>这样一个对象有不止一个引用，就也有了不止一个名字，所以就说这个对象有别名了。


If the aliased object is mutable, changes made with one alias affect the other:
>如果一个别名对象是可修改的，那么对一个别名做出的修改就会影响到其他引用：


```Python
>>> b[0] = 42
>>> a
[42, 2, 3]
```

Although this behavior can be useful, it is error-prone. In general, it is safer to avoid aliasing when you are working with mutable objects.
>这一性质是很有用处的，但很容易让初学者犯错。所以一般来说，处理可变对象的时候，还是尽量避免别名使用，这样更安全些。

For immutable objects like strings, aliasing is not as much of a problem. In this example:
>对于不可变对象比如字符串来说，别名使用就不是太大问题了。如下所示：


```Python
a = 'banana'
b = 'banana'
```



It almost never makes a difference whether a and b refer to the same string or not.
>a 和 b 是否指向同一个字符就基本无所谓了，几乎不会有任何影响。



##10.12  List arguments 列表参数



When you pass a list to a function, the function gets a reference to the list. If the function modifies the list, the caller sees the change. For example,delete_head removes the first element from a list:
>当你传递一个列表给一个函数的时候，函数得到的是对该列表的一个引用。如果函数修改了列表，调用者会看到变化的。比如下面这个 delete_head 函数就从列表中删除第一个元素：


```Python
def delete_head(t):
	del t[0]
```



Here’s how it is used:
>其用法如下：

```Python
>>> letters = ['a', 'b', 'c']
>>> delete_head(letters)
>>> letters ['b', 'c']
```



The parameter t and the variable letters are aliases for the same object. The stack diagram looks like Figure 10.5.
>形式参数 t 和变量 letters 都是同一对象的别名。栈图如图10.5所示。


________________________________________
![Figure 10.5: Stack diagram](http://7xnq2o.com1.z0.glb.clouddn.com/ThinkPythonFigure10.5-%20Stack%20diagram.png)
Figure 10.5: Stack diagram.
________________________________________




Since the list is shared by two frames, I drew it between them.
It is important to distinguish between operations that modify lists and operations that create new lists. For example, the append method modifies a list, but the + operator creates a new list:
>因为这个列表被两个框架所公用，我就把它画在了它们之间。
>一定要区分修改列表的运算和产生新列表的运算，这特别重要。比如 append 方法修改一个列表，但加号+运算符是产生一个新的列表：


```Python
>>> t1 = [1, 2]
>>> t2 = t1.append(3)
>>> t1
[1, 2, 3]
>>> t2
None
```




append modifies the list and returns None.
>append 修改了列表，返回的是空。

```Python
>>> t3 = t1 + [4]
>>> t1
[1, 2, 3]
>>> t3
[1, 2, 3, 4]
>>> t1
[1, 2, 3]
```


The + operator creates a new list and leaves the original list unchanged.
>加号+运算符创建了新的列表，并不修改源列表。


This difference is important when you write functions that are supposed to modify lists. For example, this function does not delete the head of a list:
>这以区别相当重要，尤其是当你写一些要修改列表的函数的时候。比如下面这个函数并没有能够删除列表的第一个元素：


```Python
def bad_delete_head(t):
	t = t[1:]              # WRONG!
```




The slice operator creates a new list and the assignment makes t refer to it, but that doesn’t affect the caller.
>切片运算符创建了新的列表，然后赋值语句让 t 指向了这个新列表，但这不会影响调用者。


```Python
>>> t4 = [1, 2, 3]
>>> bad_delete_head(t4)
>>> t4
[1, 2, 3]
```




At the beginning of bad_delete_head, t and t4 refer to the same list. At the end,t refers to a new list, but t4 still refers to the original, unmodified list.
>在bad_delete_head这个函数开始运行的时候，t 和 t4指向同一个列表。在结尾的时候，t 指向了新的列表，但 t4依然还是原来那个列表，而且没修改过。


An alternative is to write a function that creates and returns a new list. For example, tail returns all but the first element of a list:
>一种替代方法是写一个能创建并返回新列表的函数。比如 tail 这个函数就返回列表除了首个元素之外的其他所有元素：


```Python
def tail(t):
	return t[1:]
```



This function leaves the original list unmodified. Here’s how it is used:
>这个函数会将源列表保持原样不做修改。下面是用法：


```Python
>>> letters = ['a', 'b', 'c']
>>> rest = tail(letters)
>>> rest
['b', 'c']
```






##10.13  Debugging 调试


Careless use of lists (and other mutable objects) can lead to long hours of debugging. Here are some common pitfalls and ways to avoid them:
>对列表或者其他可变对象，用的不小心的货，就会带来很多麻烦，需要好长时间来调试。下面是一些常见的陷阱，以及避免的方法：



###1.	Most list methods modify the argument and return None. This is the opposite of the string methods, which return a new string and leave the original alone.
>大多数列表方法都修改参数，返回空值。这正好与字符串方法相反，字符串的方法都是返回一个新字符串，保持源字符串不变。


If you are used to writing string code like this:
>如果你习惯些下面这种字符串代码了：


```Python
word = word.strip()
```


It is tempting to write list code like this:
>你估计就会写出下面这种列表代码：


```Python
t = t.sort()           # WRONG!
```




Because sort returns None, the next operation you perform with t is likely to fail.
Before using list methods and operators, you should read the documentation carefully and then test them in interactive mode.
>因为 sort 返回的是空值，所以对 t 的后续运算都将会失败。
>在使用列表的方法和运算符之前，你应该好好读一下文档，然后在交互模式里面对它们进行一下测试。



###2.	Pick an idiom and stick with it. 选一种方法并坚持使用。


Part of the problem with lists is that there are too many ways to do things. For example, to remove an element from a list, you can use pop, remove,del, or even a slice assignment.
>列表使用的问题中很大一部分都是因为有太多方法来实现目的导致的。例如要从一个列表中删除一个元素，可以用 pop，remove，del 甚至简单的切片操作。


To add an element, you can use the append method or the + operator. Assuming that t is a list and x is a list element, these are correct:
>要加一个元素，可以用 append 方法或者加号+运算符。假设 t 是一个列表，而 x 是一个列表元素，下面的代码都是正确的：


```Python
t.append(x)
t = t + [x]
t += [x]
```




And these are wrong:
>下面这就都是错的了：

```Python
t.append([x])          # WRONG!
t = t.append(x)        # WRONG!
t + [x]                # WRONG!
t = t + x              # WRONG!
```


Try out each of these examples in interactive mode to make sure you understand what they do. Notice that only the last one causes a runtime error; the other three are legal, but they do the wrong thing.
>在交互模式下试试上面这些例子，确保你要理解它们的作用。要注意只有最后一个会引起运行错误，其他的三个都是合法的，但产生错误的效果。

###3.	Make copies to avoid aliasing. 尽量做备份，避免用别名。



If you want to use a method like sort that modifies the argument, but you need to keep the original list as well, you can make a copy.
>如果你要用 sort 这样的方法来修改参数，又要同时保留源列表，你可以先做个备份。



```Python
>>> t = [3, 1, 2]
>>> t2 = t[:]
>>> t2.sort()
>>> t
[3, 1, 2]
>>> t2
[1, 2, 3]
```



In this example you could also use the built-in function sorted, which returns a new, sorted list and leaves the original alone.
>在这个例子中，你也可以用内置函数sorted，这个函数会返回一个新的整理过的列表，而不会影响源列表。


```Python
>>> t2 = sorted(t)
>>> t
[3, 1, 2]
>>> t2
[1, 2, 3]
```





##10.14  Glossary 术语列表


list:
A sequence of values.
>列表：一系列值的序列。



element:
One of the values in a list (or other sequence), also called items.
>元素：一个列表或者其他序列中的值，也叫项。



nested list:
A list that is an element of another list.
>网状列表：一个作为其他列表元素的列表。



accumulator:
A variable used in a loop to add up or accumulate a result.
>累加器：一种用来在循环中累加或者拼接结果的变量。



augmented assignment:
A statement that updates the value of a variable using an operator like+=.
>增强赋值语句：使用+=这种自增运算符来更新变量值的语句。



reduce:
A processing pattern that traverses a sequence and accumulates the elements into a single result.
>reduce：一种处理模式，遍历一个序列，把元素积累起来结合成一个单独的结果。




map:
A processing pattern that traverses a sequence and performs an operation on each element.
>map：一种处理模式，遍历一个序列，对每一个元素都进行某种运算。




filter:
A processing pattern that traverses a list and selects the elements that satisfy some criterion.
>filter：一种处理模式，遍历一个列表，选取其中满足特定规则的一些元素。




object:
Something a variable can refer to. An object has a type and a value.
>对象：变量所指向的就是对象。一个对象有特定的某个类型，以及一个值。




equivalent:
Having the same value.
>相等：有相等的值。





identical:
Being the same object (which implies equivalence).
>相同：是同一个对象（意味着必然就是相等了）。




reference:
The association between a variable and its value.
>引用：变量 a 与其值的关系。




aliasing:
A circumstance where two or more variables refer to the same object.
>别名：同一个对象有两个或者更多变量所指向的情况。




delimiter:
A character or string used to indicate where a string should be split.
>定界符：一个字符或者字符串，用来确定字符分割时候的分界。



##10.15  Exercises 练习


You can download solutions to these exercises from [Here](http://thinkpython2.com/code/list_exercises.py).
>你可以从 [这里](http://thinkpython2.com/code/list_exercises.py) 下载下面这些练习的样例代码。

###Exercise 1 练习1

Write a function called nested_sum that takes a list of lists of integers and adds up the elements from all of the nested lists. For example:
>写一个函数，名为 nested_sum，接收一系列的整数列表，然后把所有分支列表中的元素加起来。如下所示：


```Python
>>> t = [[1, 2], [3], [4, 5, 6]]
>>> nested_sum(t)
21
```




###Exercise 2 练习2


Write a function called cumsum that takes a list of numbers and returns the cumulative sum; that is, a new list where the ith element is the sum of the first i+1 elements from the original list. For example:
>写一个函数，明切 cumsum，接收一个数字列表，然后返回累加的总和；也就是新列表的第 i 个元素就是源列表中前 i+1个元素的累加。如下所示：

```Python
>>> t = [1, 2, 3]
>>> cumsum(t)
[1, 3, 6]
```



###Exercise 3 练习3



Write a function called middle that takes a list and returns a new list that contains all but the first and last elements. For example:
> 写一个函数，名为 middle，接收一个列表，返回一个新列表，新列表要求对源列表掐头去尾只要中间部分。如下所示：


```Python
>>> t = [1, 2, 3, 4]
>>> middle(t)
[2, 3]
```



##Exercise 4 练习4


Write a function called chop that takes a list, modifies it by removing the first and last elements, and returns None. For example:
>写一个函数，名为 chop，接收一个列表，修改这个列表，掐头去尾，返回空值。如下所示：


```Python
>>> t = [1, 2, 3, 4]
>>> chop(t)
>>> t
[2, 3]
```





###Exercise 5 练习5


Write a function called is_sorted that takes a list as a parameter and returns True if the list is sorted in ascending order and False otherwise. For example:
>写一个函数，名为 is_sorted，接收一个列表作为参数，如果列表按照字母顺序升序排列，就返回真，否则返回假。如下所示：


```Python
>>> is_sorted([1, 2, 2])
True
>>> is_sorted(['b', 'a'])
False
```




###Exercise 6 练习6


Two words are anagrams if you can rearrange the letters from one to spell the other. Write a function called is_anagram that takes two strings and returns True if they are anagrams.
>两个单词如果可以通过顺序修改来互相转换就互为变位词。写一个函数，名为 is_anagram，接收两个字符串，如果互为变位词就返回真。



###Exercise 7 练习7

Write a function called has_duplicates that takes a list and returns True if there is any element that appears more than once. It should not modify the original list.
>写一个函数，名为 has_duplicates，接收一个列表，如果里面有重复出现的元素，就返回真。这个函数不能修改源列表。


###Exercise 8 练习8


This exercise pertains to the so-called Birthday Paradox, which you can read about at [Here](http://en.wikipedia.org/wiki/Birthday_paradox).
If there are 23 students in your class, what are the chances that two of you have the same birthday? You can estimate this probability by generating random samples of 23 birthdays and checking for matches. Hint: you can generate random birthdays with the randint function in the random module.
You can download my solution from  [Here](http://thinkpython2.com/code/birthday.py).
>这个练习也可以叫做生日悖论，你可以点击[这里](http://en.wikipedia.org/wiki/Birthday_paradox)来读一下更多背景知识。
>加入你班上有23个学生，这当中两个人同一天出生的概率是多大？你可以评估一下23个随机生日中有相同生日的概率。提示一下：你可以用 randint 函数来生成随机的生日，这个函数包含在 random 模块中。
>你可以从 [这里](http://thinkpython2.com/code/birthday.py)下载我的样例代码。



###Exercise 9 练习9


Write a function that reads the file words.txt and builds a list with one element per word. Write two versions of this function, one using the append method and the other using the idiom t = t + [x]. Which one takes longer to run? Why?
[Solution](http://thinkpython2.com/code/wordlist.py) .
>写一个函数，读取文件 words.txt，然后建立一个列表，这个列表中每个元素就是这个文件中的每个单词。写两个版本的这样的函数，一个使用 append 方法，另外一个用自增运算的模式：t= t + [x]。看看哪个运行时间更长？为什么会这样？
>[样例代码](http://thinkpython2.com/code/wordlist.py)



###Exercise 10 练习10


To check whether a word is in the word list, you could use the in operator, but it would be slow because it searches through the words in order.
>要检查一个单词是不是在上面这个词汇列表里，你可以使用 in 运算符，但可能会很慢，因为这个 in 运算符要从头到尾来搜索整个词汇表。


Because the words are in alphabetical order, we can speed things up with a bisection search (also known as binary search), which is similar to what you do when you look a word up in the dictionary. You start in the middle and check to see whether the word you are looking for comes before the word in the middle of the list. If so, you search the first half of the list the same way. Otherwise you search the second half.
>我们知道这些单词是按照字母表顺序组织的，所以我们可以加速一下，用一种对折搜索（也叫做二元搜索），这个过程就和你在现实中用字典来查单词差不多。你在中间部分开始，看看这个要搜索的词汇是不是在中间位置的前面。如果在前面，就又对前半部分取中间，继续这样来找。当然了，不在前半部分，就去后半部分找了，思路是这样的。


Either way, you cut the remaining search space in half. If the word list has 113,809 words, it will take about 17 steps to find the word or conclude that it’s not there.
>不论怎样，每次都会把搜索范围缩减到一半。如果词表包含了113809个单词，最多就是17步就能找到单词，或者能确定单词不在词汇表中。


Write a function called in_bisect that takes a sorted list and a target value and returns the index of the value in the list if it’s there, or None if it’s not.
Or you could read the documentation of the bisect module and use that!
[Solution](http://thinkpython2.com/code/inlist.py)
>那么问题来了，写一个函数，名为 in_bisect，接收一个整理过的按照字母顺序排列的列表，以及一个目标值，在列表中查找这个值，找到了就返回索引位置，找不到就返回空。
>[样例代码](http://thinkpython2.com/code/inlist.py).





###Exercise 11 练习11



Two words are a “reverse pair” if each is the reverse of the other. Write a program that finds all the reverse pairs in the word list. [Solution](http://thinkpython2.com/code/reverse_pair.py).
>两个词如果互为逆序，就称它们是『翻转配对』。写一个函数来找一下在这个词汇表中所有这样的词对。[样例代码](http://thinkpython2.com/code/reverse_pair.py)




###Exercise 12 练习12

Two words “interlock” if taking alternating letters from each forms a new word. For example, “shoe” and “**cold**” interlock to form “s**c**h**o**o**l**e**d**”. [Solution](http://thinkpython2.com/code/interlock.py). Credit: This exercise is inspired by an example at [Here](http://puzzlers.org).
>两个单词，依次拼接各自的字母，如果能组成一个新单词，就称之为『互锁』。比如，shoe 和 **cold**就可以镶嵌在一起组成组成 s**c**h**o**o**l**e**d**。（译者注：shoe+**cold**= s**c**h**o**o**l**e**d** ） [样例代码](http://thinkpython2.com/code/interlock.py). 说明：这个练习受到了[这里一处例子](http://puzzlers.org)的启发。


1.	Write a program that finds all pairs of words that interlock. Hint: don’t enumerate all pairs!
>写一个程序，找到所有这样的互锁单词对。提示：不要枚举所有的单词对！


2.	Can you find any words that are three-way interlocked; that is, every third letter forms a word, starting from the first, second or third?
>你能找到那种三路互锁的单词么；就是那种三三排列三个单词的字母能组成一个单词的三个词？







