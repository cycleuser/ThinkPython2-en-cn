Title: ThinkPython 双语学编程 Chapter 19
Date: 2016-2-10
Category: ThinkPython
Tag: 双语,Python,ThinkPython

#Chapter 19 The Goodies 额外补充




One of my goals for this book has been to teach you as little Python as possible. When there were two ways to do something, I picked one and avoided mentioning the other. Or sometimes I put the second one into an exercise.
>我在本书中的一个目标就是尽量少教你 Python（译者注：而要多教编程）。有的时候完成一个目的有两种方法，我都会只选择一种而不提其他的。或者有的时候我就把第二个方法放到练习里面。



Now I want to go back for some of the good bits that got left behind. Python provides a number of features that are not really necessary—you can write good code without them—but with them you can sometimes write code that’s more concise, readable or efficient, and sometimes all three.
>现在我就要往回倒车一下，捡起一些当时略过的重要内容来给大家讲一下。Python 提供了很多并非必须的功能—你完全可以不用这些功能也能写出很好的代码—但用这些功能有时候能让你的代码更加简洁，可读性更强，或者更有效率，甚至有时候能兼顾这三个方面。




##19.1  Conditional expressions 条件表达式



We saw conditional statements in Section 5.4. Conditional statements are often used to choose one of two values; for example:
>在5.4中，我们见到了条件语句。条件语句往往用于二选一的情况下；比如：


```Python
if x > 0:
	y = math.log(x)
else:
	y = float('nan')
```



This statement checks whether x is positive. If so, it computes math.log. If not,math.log would raise a ValueError. To avoid stopping the program, we generate a “NaN”, which is a special floating-point value that represents “Not a Number”.
>这个语句检查了 x 是否为正数。如果为正数，程序就计算对数值 math.log。如果非正，对数函数会返回一个值错误 ValueError。要避免因此而导致程序异常退出，咱们就生成了一个『NaN』，这个符号是一个特别的浮点数的值，表示的意思是『不是一个数』。



We can write this statement more concisely using a conditional expression:
>用一个条件表达式能让这个语句更简洁：


```Python
y = math.log(x) 	if x > 0 	else 	float('nan')
```



You can almost read this line like English: “y gets log-x if x is greater than 0; otherwise it gets NaN”.
Recursive functions can sometimes be rewritten using conditional expressions. For example, here is a recursive version of factorial:
>上面这行代码读起来就跟英语一样了：『如果 x 大于0就让 y 等于 x 的对数；否则的话就返回 Nan』。
>递归函数有时候也可以用这种条件表达式来改写。例如下面就是分形函数 factorial 的一个递归版本：



```Python
def factorial(n):
	if n == 0:
		return 1
	else:
		return n * factorial(n-1)
```




We can rewrite it like this:
>我们可以这样改写：



```Python
def factorial(n):
	return 1 if n == 0  else  return n * factorial(n-1)
```


Another use of conditional expressions is handling optional arguments. For example, here is the init method from GoodKangaroo (see Exercise 2):
>条件表达式还可以用于处理可选参数。例如下面就是练习2中 GoodKangaroo 类的 init 方法：


```Python
def __init__(self, name, contents=None):
	self.name = name
	if contents == None:
		contents = []
	self.pouch_contents = contents
```




We can rewrite this one like this:
>我们可以这样来改写：


```Python
def __init__(self, name, contents=None):
	self.name = name
	self.pouch_contents = []
	if contents == None else contents
```





In general, you can replace a conditional statement with a conditional expression if both branches contain simple expressions that are either returned or assigned to the same variable.
>一般来讲，你可以用条件表达式来替换掉条件语句，无论这些语句的分支是返回语句或者是赋值语句。




##19.2  List comprehensions 列表推导




In Section 10.7 we saw the map and filter patterns. For example, this function takes a list of strings, maps the string method capitalize to the elements, and returns a new list of strings:
>在10.7当中，我们看到了映射和过滤模式。例如，下面这个函数接收一个字符串列表，然后将每一个元素都用字符串方法 capitalize 处理成大写的，然后返回一个新的字符串列表：


```Python
def capitalize_all(t):
	res = []
	for s in t:
		res.append(s.capitalize())
	return res
```




We can write this more concisely using a list comprehension:
>用列表推导就可以将上面的代码写得更简洁：


```Python
def capitalize_all(t):
	return [s.capitalize() for s in t]
```



The bracket operators indicate that we are constructing a new list. The expression inside the brackets specifies the elements of the list, and the for clause indicates what sequence we are traversing.
>方括号的意思是我们正在建立一个新的列表。方括号内的表达式确定了此新列表中的元素，然后 for 语句表明我们要遍历的序列。



The syntax of a list comprehension is a little awkward because the loop variable, s in this example, appears in the expression before we get to the definition.
>列表推导的语法有点复杂，就因为这个循环变量，在上面例子中是 s，这个 s 在我们定义之前就出现在语句中了。



List comprehensions can also be used for filtering. For example, this function selects only the elements of t that are upper case, and returns a new list:
>列表推导也可以用到滤波中。例如，下面的函数从 t 中选择了大写的元素，然后返回成一个新的列表：


```Python
def only_upper(t):
	res = []
	for s in t:
		if s.isupper():
			res.append(s)
	return res
```





We can rewrite it using a list comprehension:
>咱们可以用列表推导来重写这个函数：


```Python
def only_upper(t):
	return [s for s in t if s.isupper()]
```





List comprehensions are concise and easy to read, at least for simple expressions. And they are usually faster than the equivalent for loops, sometimes much faster. So if you are mad at me for not mentioning them earlier, I understand.
>列表推导很简洁，也很容易阅读，至少在简单的表达式上是这样。这些语句的执行也往往比同样情况下的 for 循环更快一些，有时候甚至快很多。所以如果你因为我没有早些给你讲而发怒，我也能理解。




But, in my defense, list comprehensions are harder to debug because you can’t put a print statement inside the loop. I suggest that you use them only if the computation is simple enough that you are likely to get it right the first time. And for beginners that means never.
>但是，我也要辩护一下，列表推导会导致调试非常困难，因为你不能在循环内部放 print 语句了。我建议你只去在一些简单的地方使用，要确保你第一次写出来就能保证代码正常工作。也就是说初学者就还是别用为好。





##19.3  Generator expressions 生成器表达式



Generator expressions are similar to list comprehensions, but with parentheses instead of square brackets:
>生成器表达式与列表推导相似，用的不是方括号，而是圆括号：

```Python
>>> g = (x**2 for x in range(5))
>>> g
<generator object <genexpr> at 0x7f4c45a786c0>
```



The result is a generator object that knows how to iterate through a sequence of values. But unlike a list comprehension, it does not compute the values all at once; it waits to be asked. The built-in function next gets the next value from the generator:
>上面这样运行得到的结果就是一个生成器对象，用来遍历一个值的序列。但与列表推导不同的是，生成器表达式并不会立即计算出所有的值；它要等着被调用。内置函数 next 会从生成器中得到下一个值：


```Python
>>> next(g)
0
>>> next(g)
1
```

When you get to the end of the sequence, next raises a StopIteration exception. You can also use a for loop to iterate through the values:
>当程序运行到序列末尾的时候，next 函数就会抛出一个停止遍历的异常。你也可以用一个 for 循环来遍历所有的值：


```Python
>>> for val in g: ...
print(val)
4
9
16
```






The generator object keeps track of where it is in the sequence, so the for loop picks up where next left off. Once the generator is exhausted, it continues to raise StopException:
>生成器对象能够追踪在序列中的位置，所以 for 语句就会在 next 函数退出的地方开始。一旦生成器使用完毕了，接下来就要抛出一个停止异常了：



```Python
>>> next(g)
StopIteration
```




Generator expressions are often used with functions like sum, max, and min:
>生成器表达式多用于求和、求最大或者最小这样的函数中：



```Python
>>> sum(x**2 for x in range(5))
30
```



##19.4  any and all 任意和所有



Python provides a built-in function, any, that takes a sequence of boolean values and returns True if any of the values are True. It works on lists:
>Python 提供了一个名为 any 的内置函数，该函数接收一个布尔值序列，只要里面有任意一个是真，就返回真。该函数适用于列表：



```Python
>>> any([False, False, True])
True
```





But it is often used with generator expressions:
>但这个函数多用于生成器表达式中：




```Python
>>> any(letter == 't' for letter in 'monty')
True
```





That example isn’t very useful because it does the same thing as the in operator. But we could use any to rewrite some of the search functions we wrote in Section 9.3. For example, we could write avoids like this:
>这个例子没多大用，因为效果和 in 运算符是一样的。但我们能用 any 函数来改写我们在9.3中写的一些搜索函数。例如，我们可以用如下的方式来改写 avoids：




```Python
def avoids(word, forbidden):
	return not any(letter in forbidden for letter in word)
```



The function almost reads like English, “word avoids forbidden if there are not any forbidden letters in word.”
>这样这个函数读起来基本就跟英语一样了。

Using any with a generator expression is efficient because it stops immediately if it finds a True value, so it doesn’t have to evaluate the whole sequence.
>用 any 函数和生成器表达式来配合会很有效率，因为只要发现真值程序就会停止了，所以并不需要对整个序列进行运算。



Python provides another built-in function, all, that returns True if every element of the sequence is True. As an exercise, use all to re-write uses_all from Section 9.3.
>Python 还提供了另外一个内置函数 all，该函数在整个序列都是真的情况下才返回真。
>做个练习，用 all 来改写一下9.3中的uses_all 函数。




##19.5  Sets 集合




In Section 13.6 I use dictionaries to find the words that appear in a document but not in a word list. The function I wrote takes d1, which contains the words from the document as keys, and d2, which contains the list of words. It returns a dictionary that contains the keys from d1 that are not in d2.
>在13.6中，我用了字典来查找存在于文档中而不存在于词汇列表中的词汇。我写的这个函数接收两个参数，一个是 d1是包含了文档中的词作为键，另外一个是 d2包含了词汇列表。程序会返回一个字典，这个字典包含的键存在于 d1而不在 d2中。



```Python
def subtract(d1, d2):
	res = dict()
	for key in d1:
		if key not in d2:
			res[key] = None
	return res
```






In all of these dictionaries, the values are None because we never use them. As a result, we waste some storage space.
>在这些字典中，键值都是 None，因为根本没有使用。结果就是，浪费了一些存储空间。


Python provides another built-in type, called a set, that behaves like a collection of dictionary keys with no values. Adding elements to a set is fast; so is checking membership. And sets provide methods and operators to compute common set operations.
>Python 还提供了另一个内置类型，名为 set（也就是集合的意思），其性质就是有字典的键而无键值。
>对集合中添加元素是很快的；对集合成员进行检查也很快。此外集合还提供了一些方法和运算符来进行常见的集合运算。



For example, set subtraction is available as a method called difference or as an operator, -. So we can rewrite subtract like this:
>例如，集合的减法就可以用一个名为 difference 的方法，或者就用减号-。所以我们可以把 subtract 改写成如下形式：




```Python
def subtract(d1, d2):
	return set(d1) - set(d2)
```






The result is a set instead of a dictionary, but for operations like iteration, the behavior is the same.
>上面这个函数的结果就是一个集合而不是一个字典，但对于遍历等等运算来说，用起来都一样的。




Some of the exercises in this book can be done concisely and efficiently with sets. For example, here is a solution to has_duplicates, from Exercise 7, that uses a dictionary:
>本书中的一些练习都可以通过使用集合而改写成更精简更高效的形式。例如，下面的代码就是 has_duplicates 的一个实现方案，来自练习7，用的是字典：






```Python
def has_duplicates(t):
	d = {}
	for x in t:
		if x in d:
			return True
	d[x] = True
	return False
```










When an element appears for the first time, it is added to the dictionary. If the same element appears again, the function returns True.
>当一个元素第一次出现的时候，就被添加到字典中。如果同一个元素又出现了，该函数就返回真。



Using sets, we can write the same function like this:
>用集合的话，我们就能把该函数写成如下形式：




```Python
def has_duplicates(t):
	return len(set(t)) < len(t)
```







An element can only appear in a set once, so if an element in t appears more than once, the set will be smaller than t. If there are no duplicates, the set will be the same size as t.
>一个元素在一个集合中只能出现一次，所以如果一个元素在 t 中出现次数超过一次，集合会比 t 规模小一些。如果没有重复，集合的规模就应该和 t 一样大。



We can also use sets to do some of the exercises in Chapter 9. For example, here’s a version of uses_only with a loop:
>我们还能用集合来做一些第九章的练习。例如，下面就是用一个循环实现的一个版本的 uses_only：



```Python
def uses_only(word, available):
	for letter in word:
	if letter not in available:
		return False
	return True
```





uses_only checks whether all letters in word are in available. We can rewrite it like this:
>uses_only 会检查 word 中的所有字母是否出现在 available 中。我们可以用如下方法重写：



```Python
def uses_only(word, available):
	return set(word) <= set(available)
```




The <= operator checks whether one set is a subset or another, including the possibility that they are equal, which is true if all the letters in word appear in available.
As an exercise, rewrite avoids using sets.
>这里的<=运算符会检查一个集合是否切另外一个集合的子集或者相等，如果 word 中所有的字符都出现在 available 中就返回真。




##19.6  Counters 计数器




A Counter is like a set, except that if an element appears more than once, the Counter keeps track of how many times it appears. If you are familiar with the mathematical idea of a multiset, a Counter is a natural way to represent a multiset.
>计数器跟集合相似，除了一点，就是如果计数器中元素出现的次数超过一次，计数器会记录下出现的次数。如果你对数学上多重集的概念有所了解，就会知道计数器是一种对多重集的表示方式。



Counter is defined in a standard module called collections, so you have to import it. You can initialize a Counter with a string, list, or anything else that supports iteration:
>计数器定义在一个名为 collections 的标准模块中，所以你必须先导入一下。你可以用字符串，列表或者任何支持遍历的类型来初始化一个计数器：


```Python
>>> from collections import Counter
>>> count = Counter('parrot')
>>> count
Counter({'r': 2, 't': 1, 'o': 1, 'p': 1, 'a': 1})
```





Counters behave like dictionaries in many ways; they map from each key to the number of times it appears. As in dictionaries, the keys have to be hashable.
>计数器的用法与字典在很多方面都相似；二者都映射了每个键到出现的次数上。在字典中，键必须是散列的。


Unlike dictionaries, Counters don’t raise an exception if you access an element that doesn’t appear. Instead, they return 0:
>与字典不同的是，当你读取一个不存在的元素的时候，计数器并不会抛出异常。相反的，这时候程序会返回0：



```Python
>>> count['d']
0
```




We can use Counters to rewrite is_anagram from Exercise 6:
>我们可以用计数器来重写一下练习6中的这个 is_anagram 函数：


```Python
def is_anagram(word1, word2):
	return Counter(word1) == Counter(word2)
```



If two words are anagrams, they contain the same letters with the same counts, so their Counters are equivalent.
Counters provide methods and operators to perform set-like operations, including addition, subtraction, union and intersection. And they provide an often-useful method, most_common, which returns a list of value-frequency pairs, sorted from most common to least:
>如果两个单词是换位词，他们包含同样个数的同样字母，所以他们的计数器是相等的。
>计数器提供了一些方法和运算器来运行类似集合的运算，包括加法，剪发，合并和交集等等。此外还提供了一个最常用的方法，most_common，该方法会返回一个由值-出现概率组成的数据对的列表，按照概率从高到低排列：



```Python
>>> count = Counter('parrot')
>>> for val, freq in count.most_common(3): ...
print(val, freq)
r 2
p 1
a 1
```




##19.7  defaultdict 默认字典



The collections module also provides defaultdict, which is like a dictionary except that if you access a key that doesn’t exist, it can generate a new value on the fly.
>collection 模块还提供了一个默认字典，与普通字典的区别在于当你读取一个不存在的键的时候，程序会添加上一个新值给这个键。



When you create a defaultdict, you provide a function that’s used to create new values. A function used to create objects is sometimes called a factory. The built-in functions that create lists, sets, and other types can be used as factories:
>当你创建一个默认字典的时候，就提供了一个能创建新值的函数。用来创建新对象的函数也被叫做工厂。内置的创建列表、集合以及其他类型的函数都可以被用作工厂：


```Python
>>> from collections import defaultdict
>>> d = defaultdict(list)
```




Notice that the argument is list, which is a class object, not list(), which is a new list. The function you provide doesn’t get called unless you access a key that doesn’t exist.
>要注意到这里的参数是一个列表，是一个类的对象，而不是 list()，带括号的就是一个新列表了。这个创建新值的函数只有当你试图读取一个不存在的键的时候才会被调用。


```Python
>>> t = d['new key']
>>> t []
```

The new list, which we’re calling t, is also added to the dictionary. So if we modify t, the change appears in d:
>新的这个我们称之为 t 的列表，也会被添加到字典中。所以如果我们修改 t，这种修改也会在 d 中出现。




```Python
>>> t.append('new value')
>>> d
defaultdict(<class 'list'>, {'new key': ['new value']})
```




If you are making a dictionary of lists, you can often write simpler code using defaultdict. In my solution to Exercise 2, which you can get from [Here](http://thinkpython2.com/code/anagram_sets.py), I make a dictionary that maps from a sorted string of letters to the list of words that can be spelled with those letters. For example, ’opst’ maps to the list [’opts’, ’post’, ’pots’, ’spot’, ’stop’, ’tops’].
>所以如果你要用列表组成字典的话，你就可以多用默认字典来写出更简洁的代码。你可以在[这里](http://thinkpython2.com/code/anagram_sets.py)下载我给练习2提供的样例代码，其中我建立了一个字典，字典中建立了从一个字母字符串到一个可以由这些字母拼成的单词的映射。例如，『opst』就映射到了列表[’opts’, ’post’, ’pots’, ’spot’, ’stop’, ’tops’]。



Here’s the original code:
>下面就是原版的代码：

```Python
def all_anagrams(filename):
	d = {}
	for line in open(filename):
		word = line.strip().lower()
		t = signature(word)
		if t not in d:
			d[t] = [word]
		else:
			d[t].append(word)
	return d
```






This can be simplified using setdefault, which you might have used in Exercise 2:
>用默认集合就可以简化一下，就如你在练习2中用过的那样：


```Python
def all_anagrams(filename):
	d = {}
	for line in open(filename):
		word = line.strip().lower()
		t = signature(word)
		d.setdefault(t, []).append(word)
	return d
```





This solution has the drawback that it makes a new list every time, regardless of whether it is needed. For lists, that’s no big deal, but if the factory function is complicated, it might be.
>这个代码有一个不足，就是每次都要建立一个新列表，而不论是否需要创建。对于列表来说，这倒不要紧，不过如果工厂函数比较复杂的话，这就麻烦了。



We can avoid this problem and simplify the code using a defaultdict:
>这时候咱们就可以用默认字典来避免这个问题并且简化代码：


```Python
def all_anagrams(filename):
	d = defaultdict(list)
	for line in open(filename):
		word = line.strip().lower()
		t = signature(word)
		d[t].append(word)
	return d
```




My solution to Exercise 3, which you can download from [Here](http://thinkpython2.com/code/PokerHandSoln.py), uses setdefault in the function has_straightflush. This solution has the drawback of creating a Hand object every time through the loop, whether it is needed or not. As an exercise, rewrite it using a defaultdict.
>你可以从[这里](http://thinkpython2.com/code/PokerHandSoln.py)下载我给练习3写的样例代码，该代码中在 has_straightflush函数用的是默认集合。这份代码的不足就在于每次循环都要创建一个 Hand 对象，而不论是否必要。做个练习，用默认字典来该写一下这个程序。



##19.8  Named tuples 命名元组



Many simple objects are basically collections of related values. For example, the Point object defined in Chapter 15 contains two numbers, x and y. When you define a class like this, you usually start with an init method and a str method:
>很多简单的类就是一些相关值的集合。例如在15章中定义的 Point 类中就包含两个数值，x 和 y。当你这样定义一个类的时候，你通常要写一个 init 方法和一个 str 方法：


```Python
class Point:
	def __init__(self, x=0, y=0):
		self.x = x
		self.y = y

	def __str__(self):
		return '(%g, %g)' % (self.x, self.y)
```





This is a lot of code to convey a small amount of information. Python provides a more concise way to say the same thing:
>要传达这么小规模的信息却要用这么多代码。Python 提供了一个更简单的方式来做类似的事情：



```Python
from collections import namedtuple
	Point = namedtuple('Point', ['x', 'y'])
```





The first argument is the name of the class you want to create. The second is a list of the attributes Point objects should have, as strings. The return value from named tuple is a class object:
>第一个参数是你要写的类的名字。第二个是 Point 对象需要有的属性列表，为字符串。命名元组返回的值是一个类的对象。



```Python
>>> Point
<class '__main__.Point'>
```




Point automatically provides methods like __init__ and __str__ so you don’t have to write them.
To create a Point object, you use the Point class as a function:
>Point 会自动提供诸如 init 和 str 之类的方法，所以就不用再去写了。
>要建立一个 Point 对象，你就可以用 Point 类作为一个函数用：



```Python
>>> p = Point(1, 2)
>>> p
Point(x=1, y=2)
```






The init method assigns the arguments to attributes using the names you provided. The str method prints a representation of the Point object and its attributes.
You can access the elements of the named tuple by name:
>init 方法把参数赋值给按照你设定来命名的属性。 str 方法输出整个 Point 类及其属性的一个字符串表达。
>你可以用名字来读取命名元组中的元素：



```Python
>>> p.x, p.y
(1, 2)
```




But you can also treat a named tuple as a tuple:
>但你也可以把命名元组当做元组来用：


```Python
>>> p[0], p[1]
(1, 2)
>>> x, y = p
>>> x, y
(1, 2)
```






Named tuples provide a quick way to define simple classes. The drawback is that simple classes don’t always stay simple. You might decide later that you want to add methods to a named tuple. In that case, you could define a new class that inherits from the named tuple:
>命名元组提供了定义简单类的快捷方式。缺点就是这些简单的类不能总保持简单的状态。有时候你可能想给一个命名元组添加方法。这时候你就得定义一个新类来继承命名元组：


```Python
class Pointier(Point):
	# add more methods here
```



Or you could switch to a conventional class definition.
>或者你可以把命名元组转换成一个常规的类的定义。



##19.9  Gathering keyword args 收集关键词参数



In Section 12.4, we saw how to write a function that gathers its arguments into a tuple:
>在12.4中，我们已经学过了如何写将参数收集到一个元组中的函数：

```Python
def printall(*args):
	print(args)
```




You can call this function with any number of positional arguments (that is, arguments that don’t have keywords):
>这种函数可以用任意数量的位置参数（就是无关键词的参数）来调用。


```Python
>>> printall(1, 2.0, '3')
(1, 2.0, '3')
```





But the * operator doesn’t gather keyword arguments:
>但*运算符并不能收集关键词参数：


```Python
>>> printall(1, 2.0, third='3')
TypeError: printall() got an unexpected keyword argument 'third'
```






To gather keyword arguments, you can use the ** operator:
>要收集关键词参数，你就可以用**运算符：


```Python
def printall(*args, **kwargs):
	print(args, kwargs)
```





You can call the keyword gathering parameter anything you want, but kwargs is a common choice. The result is a dictionary that maps keywords to values:
>你可以用任意名字来命名这里的关键词收集参数，不过通常大家都用kwargs。得到的结果是一个字典，映射了关键词键名与键值：


```Python
>>> printall(1, 2.0, third='3')
(1, 2.0) {'third': '3'}
```






If you have a dictionary of keywords and values, you can use the scatter operator, ** to call a function:
>如果你有一个关键词和值组成的字典，你就可以用散射运算符，**来调用一个函数：


```Python
>>> d = dict(x=1, y=2)
>>> Point(**d)
Point(x=1, y=2)
```




Without the scatter operator, the function would treat d as a single positional argument, so it would assign d to x and complain because there’s nothing to assign to y:
>不用散射运算符的话，函数会把 d 当做一个单独的位置参数，所以就会把 d 赋值股额 x，然后出错，因为没有给 y 赋值：


```Python
>>> d = dict(x=1, y=2)
>>> Point(d)
Traceback (most recent call last):   File "<stdin>", line 1, in <module> TypeError: __new__() missing 1 required positional argument: 'y'
```




When you are working with functions that have a large number of parameters, it is often useful to create and pass around dictionaries that specify frequently-used options.
>当你写一些有大量参数的函数的时候，就可以创建和使用一些字典，这样能把各种常用选项弄清。



##19.10  Glossary 术语列表




conditional expression:
An expression that has one of two values, depending on a condition.
>条件表达式：一种根据一个条件来从两个值中选一个的表达式。



list comprehension:
An expression with a for loop in square brackets that yields a new list.
>列表推导：一种用表达式， 方括号内有一个for 循环，生成一个新的列表。





generator expression:
An expression with a for loop in parentheses that yields a generator object.
>生成器表达式：一种表达式，圆括号内放一个 for 循环，产生一个生成器对象。




multiset:
A mathematical entity that represents a mapping between the elements of a set and the number of times they appear.
>多重集：一个数学上的概念，表示了一种从集合中元素到出现次数只见的映射关系。




factory:
A function, usually passed as a parameter, used to create objects.
>工厂：一个函数，通常作为参数传递，用来产生对象。



##19.11  Exercises 练习


###Exercise 1 练习1



The following is a function computes the binomial coefficient recursively.
>线面的函数是递归地计算二项式系数的。


```Python
def binomial_coeff(n, k):
	"""Compute the binomial coefficient "n choose k".
	n: number of trials
	k: number of successes
	returns: int     """
	if k == 0:
		return 1
	if n == 0:
		return 0
	res = binomial_coeff(n-1, k) + binomial_coeff(n-1, k-1)
	return res
```







Rewrite the body of the function using nested conditional expressions.
>用网状条件语句来重写一下函数体。




One note: this function is not very efficient because it ends up computing the same values over and over. You could make it more efficient by memoizing (see Section 11.6). But you will find that it’s harder to memoize if you write it using conditional expressions.
>一点提示：这个函数并不是很有效率，因为总是要一遍一遍地计算同样的值。你可以通过存储已有结果（参考11.6）来提高效率。但你会发现如果你用条件表达式实现，就会导致这种记忆更困难。
