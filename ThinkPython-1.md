Title: ThinkPython 双语学编程 Chapter 1  
Date: 2015-10-22  
Category: ThinkPython  
Tag: 双语,Python,ThinkPython

# Chapter 1  The way of the program 编程之路

The goal of this book is to teach you to think like a computer scientist. This way of thinking combines some of the best features of mathematics, engineering, and natural science. Like mathematicians, computer scientists use formal languages to denote ideas \(specifically computations\). Like engineers, they design things, assembling components into systems and evaluating tradeoffs among alternatives. Like scientists, they observe the behavior of complex systems, form hypotheses, and test predictions.

> 本书的目的是叫你学会像计算机科学家一样来思考。这种思考方式汇聚了数学、工程和自然科学的精华。计算机科学家像数学家一样，使用规范的语言来阐述思想（尤其是一些计算）；像工程师一样设计、组装系统，并且在多重选择中寻找最优解；像自然科学家一样观察复杂系统的行为模式，建立猜想，测试预估的结果。

The single most important skill for a computer scientist is problem solving. Problem solving means the ability to formulate problems, think creatively about solutions, and express a solution clearly and accurately. As it turns out, the process of learning to program is an excellent opportunity to practice problem-solving skills. That’s why this chapter is called, “The way of the program”.

> 计算机科学家唯一最重要的技能就是『解决问题』。解决问题意味着要有能力把问题进行方程化，创造性地考虑解决思路，并且清晰又精确地表达出解决方案。而学习编程的过程，正是一个培养这种解决问题能力的绝佳机会。本章的标题是『编程之路』，原因就在此。

On one level, you will be learning to program, a useful skill by itself. On another level, you will use programming as a means to an end. As we go along, that end will become clearer.

> 在一定层面上，大家将通过编程本身来学习编程这一重要的技巧。在另外一些层面上，大家也将把编程作为实现一种目的的途径。这一目的会随着我们逐渐学习而越发清楚。
>
> ## 1.1  What is a program? 程序是什么？
>
> A program is a sequence of instructions that specifies how to perform a computation. The computation might be something mathematical, such as solving a system of equations or finding the roots of a polynomial, but it can also be a symbolic computation, such as searching and replacing text in a document or something graphical, like processing an image or playing a video.  
> 程序是一个指令的序列，来告诉机器如何进行一组运算。这种运算也许是数学上的，比如求解一组等式或者求多项式的根；当然也可以是符号运算，比如在文档中搜索和替换文字，或者一些图形化过程，比如处理图像或者播放一段视频。

The details look different in different languages, but a few basic instructions appear in just about every language:

> 不同编程语言的具体细节看着很不一样，但几乎所有编程语言都会有一些基础指令：

* input: Get data from the keyboard, a file, the network, or some other device.

  > * 输入系统：从键盘、文件、网络或者其他设备上获得数据。

* output: Display data on the screen, save it in a file, send it over the network, etc.

  > * 输出系统：将数据在屏幕中显示，或者存到文件中、通过网络发送等等。

* math: Perform basic mathematical operations like addition and multiplication.

  > * 数学运算：进行基本的数学操作，比如加法或者乘法。

* conditional execution: Check for certain conditions and run the appropriate code.

  > * 条件判断：检查特定条件是否满足来运行相应的代码。

* repetition: Perform some action repeatedly, usually with some variation.

  > * 重复判断：重复进行一些操作，通常会有些变化。

Believe it or not, that’s pretty much all there is to it. Every program you’ve ever used, no matter how complicated, is made up of instructions that look pretty much like these. So you can think of programming as the process of breaking a large, complex task into smaller and smaller subtasks until the subtasks are simple enough to be performed with one of these basic instructions.

> 大家可能不太相信，核心内容就这么多。你用过的所有程序，无论多么复杂，都是由一些这样的指令组合而成的。因此大家可以把编程的过程理解成一个把庞大复杂任务进行拆分来解决的过程，分解到适合使用上述的基本指令来解决为止。

## 1.2  Running Python 运行Python

One of the challenges of getting started with Python is that you might have to install Python and related software on your computer. If you are familiar with your operating system, and especially if you are comfortable with the command-line interface, you will have no trouble installing Python. But for beginners, it can be painful to learn about system administration and programming at the same time.

> 新手在刚接触Python的时候遇到的困难之一就是必须在电脑上安装Python和相关的一些软件。如果你熟悉操作系统，并且还很习惯用命令行界面，那安装Python对你来说就没啥问题了。但对初学者来说，要求他们既要了解系统管理又要学习编程，就可能有些困难了。

To avoid that problem, I recommend that you start out running Python in a browser. Later, when you are comfortable with Python, I’ll make suggestions for installing Python on your computer.

> 为了避免这种问题，我推荐大家可以在开始的时候用浏览器来体验Python。熟悉了之后，再安装Python到计算机上。

There are a number of web pages you can use to run Python. If you already have a favorite, go ahead and use it. Otherwise I recommend PythonAnywhere. I provide detailed instructions for getting started at [http://tinyurl.com/thinkpython2e](http://tinyurl.com/thinkpython2e).

> 有很多站点提供在线运行Python的功能。如果你已经用过并且有一定经验了，可以选择你喜欢的。我推荐大家可以试试PythonAnywhere，对此的使用介绍可以在下面的链接中找到 [http://tinyurl.com/thinkpython2e](http://tinyurl.com/thinkpython2e)。

There are two versions of Python, called Python 2 and Python 3. They are very similar, so if you learn one, it is easy to switch to the other. In fact, there are only a few differences you will encounter as a beginner. This book is written for Python 3, but I include some notes about Python 2.

> Python现在有两个主要的分之，即Python2和Python3。如果你学过其中的一个，你会发现他们还挺相似的，而且转换起来也不算难。实际上对于初学者来说，他们只有很细微的差别而已。这本书是用Python3写的，但也会对Python2进行注解。

The Python interpreter is a program that reads and executes Python code. Depending on your environment, you might start the interpreter by clicking on an icon, or by typing python on a command line. When it starts, you should see output like this:

> Python的解释器是一个读取并执行Python代码的程序。根据你的系统环境，你可以点击图标或者在命令行中输入python来运行解释器。它运行起来，你会看到类似这样的输出：

```python
Python 3.4.0 (default, Jun 19 2015, 14:20:21)  
[GCC 4.8.2] on linux 
Type "help", "copyright", "credits" or "license" for more information. 
>>>  
```

The first three lines contain information about the interpreter and the operating system it’s running on, so it might be different for you. But you should check that the version number, which is 3.4.0 in this example, begins with 3, which indicates that you are running Python 3. If it begins with 2, you are running \(you guessed it\) Python 2.

> 开头的三行包含了关于解释器和所在操作系统的信息，所以大家各自的情况可能有所不同。不过当你检查版本的时候，比如例子中的是3.4.0，使用3开头的，那就告诉你了，他运行的是Python3。你肯定也能猜到，如果开头的是2那就是Python2咯。

The last line is a prompt that indicates that the interpreter is ready for you to enter code. If you type a line of code and hit Enter, the interpreter displays the result:

> 最后一行那个是提示符，告诉你解释器已经就绪了，你可以输入代码了。如果你输入一行代码然后回车键，解释器就会显示结果了，如下所示：

```python
>>> 1 + 1 
2
```

Now you’re ready to get started. From here on, I assume that you know how to start the Python interpreter and run code.

> 现在你已经做好开始学习Python的准备了。现在我估计你应该已经知道怎么来启动Python解释器和运行Python代码了。

## 1.3  The first program 第一个程序

Traditionally, the first program you write in a new language is called “Hello, World!” because all it does is display the words “Hello, World!”. In Python, it looks like this:

> 传统意义上，大家学一门新编程语言要写的第一个程序都被叫做『Hello，World！』，因为这第一个程序就用来显示这个词组『Hello，World！』。在Python中，是这样实现的：

```python
>>> print('Hello, World!') 
```

This is an example of a print statement, although it doesn’t’t actually print anything on paper. It displays a result on the screen. In this case, the result is the words `Hello, World!`

> 这是一个打印语句的例子，虽然并没有往纸张上面进行实际的『打印』。这个程序把结果显示在屏幕上。结果就是输出了这个词组`Hello, World!`

The quotation marks in the program mark the beginning and end of the text to be displayed; they don’t appear in the result.

> 输出的文字前后在源代码中有引号；这些引号在输出的时候不显示。

The parentheses indicate that print is a function. We’ll get to functions in Chapter 3.

> 括号表明了print是一个函数。关于函数我们到第三章再讨论。

In Python 2, the print statement is slightly different; it is not a function, so it doesn’t use parentheses.

> 在Python2中，打印的语句有一点点不一样：print不是一个函数，所以就不用有括号了。

```python
>>> print 'Hello, World!' 
```

This distinction will make more sense soon, but that’s enough to get started.

> 这个区别以后会理解更深入，现在说这点就够了。

## 1.4  Arithmetic operators 运算符

After “Hello, World”, the next step is arithmetic. Python provides operators, which are special symbols that represent computations like addition and multiplication.

> 在『Hello，World！』之后，下一步就是运算了。Python提供了运算符，就是一些用来表示例如加法、乘法等运算的符号了。

The operators +, -, and \* perform addition, subtraction, and multiplication, as in the following examples:

> 运算符+，-和\*表示加法、减法和乘法，如下所示：

```python
>>> 40 + 2 
42 
>>> 43 - 1 
42 
>>> 6 * 7 
42 
```

The operator / performs division:

> 运算符右斜杠/意味着除法：

```python
>>> 84 / 2 
42.0 
```

You might wonder why the result is 42.0 instead of 42. I’ll explain in the next section.

> 你估计在纳闷为啥结果是42.0而不是42，这个下一章节我再解释。

Finally, the operator \*\* performs exponentiation; that is, it raises a number to a power:

> 最后，再说个运算符\*\*，它表示乘方，就是前一个数为底数，后一个数为指数的次幂运算：

```python
>>> 6**2 + 6 
42 
```

In some other languages, `^` is used for exponentiation, but in Python it is a bitwise operator called XOR. If you are not familiar with bitwise operators, the result will surprise you:

> 在其他的一些编程语言中， `^`这个符号是乘方的意思，但在Python中这是一个位运算操作符叫做『异或』。要是你不熟悉位运算操作符，结果一定让你很惊讶：

```python
>>> 6 ^ 2 
4 
```

I won’t cover bitwise operators in this book, but you can read about them at [Wiki](http://wiki.python.org/moin/BitwiseOperators).  
我在本书中不会涉及到位运算，但你可以在下面这个链接里面读一下来了解：[Wiki](http://wiki.python.org/moin/BitwiseOperators)。

## 1.5  Values and types 值和类型

A value is one of the basic things a program works with, like a letter or a number. Some values we have seen so far are 2, 42.0, and 'Hello, World!'.

> 值就是一个程序操作的基本对象之一，比如一个字母啊，或者数字。刚刚我们看到了一些值的例子了，比如2，42.0，还有那个字符串『Hello，World！』

These values belong to different types: 2 is an integer, 42.0 is a floating-point number, and 'Hello, World!' is a string, so-called because the letters it contains are strung together.

> 这些值属于不同的类型：2是一个整形值，42.0是浮点数，『Hello，World！』是字符串咯。之所以叫字符串就是因为有一串字符。（译者注：这本书的作者真心掰开揉碎地讲解每一个点啊，高中生甚至初中生都应该理解起来没有什么问题，所以大家用这本书来学编程绝对是最佳选择了。）

If you are not sure what type a value has, the interpreter can tell you:

> 如果你不确定一个值是什么类型呢，你可以让解释器来告诉你：

```python
>>> type(2) 
<class 'int'> 
>>> type(42.0) 
<class 'float'> 
>>> type('Hello, World!') 
<class 'str'> 
```

In these results, the word “class” is used in the sense of a category; a type is a category of values.

> 在这些例子中，『class』这个字样表明这是一类，一种类型就是对值的一种划分。

Not surprisingly, integers belong to the type int, strings belong to str and floating-point numbers belong to float.

> 很自然了，整形的就是int了，字符串就是str了，浮点数就是float了。

What about values like '2' and '42.0'? They look like numbers, but they are in quotation marks like strings.

> 那'2' 和 '42.0'这种是啥呢？他们看着像是数字，但带了单引号了。

```python
>>> type('2') 
<class 'str'> 
>>> type('42.0') 
<class 'str'> 
```

They’re strings.

> 真相就是——他们也是字符串了。

When you type a large integer, you might be tempted to use commas between groups of digits, as in 1,000,000. This is not a legal integer in Python, but it is legal:

> 咱们现在输入一个大的整数，在中间用逗号分隔试试看，比如1，000，000，并不是Python中合乎语法的整形，但也被接受了：

```python
>>> 1,000,000 
(1, 0, 0) 
```

That’s not what we expected at all! Python interprets 1,000,000 as a comma-separated sequence of integers. We’ll learn more about this kind of sequence later.

> 出乎意料吧，Python把逗号当做了分隔三个整形数字的分隔符了。我们以后再对这种序列进行讨论。

## 1.6  Formal and natural languages 公式语言和自然语言

Natural languages are the languages people speak, such as English, Spanish, and French. They were not designed by people \(although people try to impose some order on them\); they evolved naturally.

> 自然语言就是人说的语言，比如英语、西班牙语、法语，当然包括中文了。他们往往都不是人主动去设计出来的（当然，人会试图去分析语言的规律），自然而然地发生演进。

Formal languages are languages that are designed by people for specific applications. For example, the notation that mathematicians use is a formal language that is particularly good at denoting relationships among numbers and symbols. Chemists use a formal language to represent the chemical structure of molecules. And most importantly:  
Programming languages are formal languages that have been designed to express computations.

> 公式语言是人们为了特定用途设计出来的。比如数学的符号就是一种公式语言，特别适合表达数字和符号只见的关系。化学家也用元素符号和化学方程式来表示分子的化学结构。要注意的是：  
> 编程语言是一种用来表达运算的公式语言。

Formal languages tend to have strict syntax rules that govern the structure of statements. For example, in mathematics the statement 3 + 3 = 6 has correct syntax, but 3 + = 3 $ 6 does not. In chemistry H2O is a syntactically correct formula, but 2Zz is not.

> 公式语言有严格的语法规则和对语句结构的要求。比如数学式3+3=6是正确的，而3+=3￥6就不是了。化学上H2O 是正确的化学式，而2Zz 就不是。

Syntax rules come in two flavors, pertaining to tokens and structure. Tokens are the basic elements of the language, such as words, numbers, and chemical elements. One of the problems with 3 += 3 $ 6 is that $ is not a legal token in mathematics \(at least as far as I know\). Similarly, 2Zz is not legal because there is no element with the abbreviation Zz.

> 语法规则体现在两个方面，代号和结构。 代号是语言的基础元素，比如单词、数字以及化学元素。3 += 3 $ 6这个式子数学上无意义的一个原因就是因为 $ 并不是数学上的符号 \(至少我所学的数学是没有这个符号的\)。类似地， 2Zz 也不对，因为没有一种化学元素的缩写是 Zz.

The second type of syntax rule pertains to the way tokens are combined. The equation 3 += 3 is illegal because even though + and = are legal tokens, you can’t have one right after the other. Similarly, in a chemical formula the subscript comes after the element name, not before.

> 第二个语法规则是代号必须有严格的组合结构。3 += 3这个式子数学上错误就因为虽然这些符号都是数学符号，但不能把加号等号放一起。类似地，化学方程式中要先写元素名字后写个数，而不是反着。

This is @ well-structured Engli$h sentence with invalid t\*kens in it. This sentence all valid tokens has, but invalid structure with.

> 这句英语的单词和结构都有错误，大家还是能看懂的哈。（译者注，作者故意这样写，来表明人类的自然语言容错率高。）

When you read a sentence in English or a statement in a formal language, you have to figure out the structure \(although in a natural language you do this subconsciously\). This process is called parsing.

> 你读一句英语或者公式语言中的语句时候，你必须搞清楚结构（虽然在自然语言中大家潜意识就能搞定了）。这就叫做解译。

Although formal and natural languages have many features in common—tokens, structure, and syntax—there are some differences:

> 虽然公式语言和自然语言有很多共同特征，比如代号、结构、语法这些元素，但差别还是显著的，比如：

* ambiguity 二义性:
  Natural languages are full of ambiguity, which people deal with by using contextual clues and other information. Formal languages are designed to be nearly or completely unambiguous, which means that any statement has exactly one meaning, regardless of context.
  > 自然语言充满二义性，也就是歧义了，人们有时候用上下文线索或者其他信息来帮助处理这种情况。公式语言被设计为尽量不具有二义性，这就意味着一个语句往往只有唯一的一种含义，与上下文无关。

* redundancy 冗余性:
  In order to make up for ambiguity and reduce misunderstandings, natural languages employ lots of redundancy. As a result, they are often verbose. Formal languages are less redundant and more concise.
  > 为了弥补歧义，减少误解，自然语言有很多冗余，结果就是经常有废话。公式语言要精简的多。

* literalness 文字修辞:
  Natural languages are full of idiom and metaphor. If I say, “The penny dropped”, there is probably no penny and nothing dropping \(this idiom means that someone understood something after a period of confusion\). Formal languages mean exactly what they say.
  > 自然语言充满习语和隐喻等。比如我说 “The penny dropped”, 可能并不是字面意思说硬币掉了\(这个俚语意思是过了一会终于弄明白了\)。公式语言的意思严格精准。

Because we all grow up speaking natural languages, it is sometimes hard to adjust to formal languages. The difference between formal and natural language is like the difference between poetry and prose, but more so:

> 咱们大家都是说着自然语言长大的，要调节到公式语言有时候挺难的。这两者之间的差别有点像诗词和散文，但差别更大：

* Poetry 诗词:  
  Words are used for their sounds as well as for their meaning, and the whole poem together creates an effect or emotional response. Ambiguity is not only common but often deliberate.

  > 单词的运用要兼顾词义和押韵，诗的整体要有一定的意境或者情感上的共鸣。双关很常见，并且多是故意的。

* Prose 散文:  
  The literal meaning of words is more important, and the structure contributes more meaning. Prose is more amenable to analysis than poetry but still often ambiguous.

  > 文字意思更重要，结构也有重要作用。相比诗词更好理解，但也有一定的双关语歧义。

* Programs 程序:
  The meaning of a computer program is unambiguous and literal, and can be understood entirely by analysis of the tokens and structure.
  > 计算机程序的意义必须是无歧义和文采修饰的，能完全用代号和结构的方式进行解析。

Formal languages are more dense than natural languages, so it takes longer to read them. Also, the structure is important, so it is not always best to read from top to bottom, left to right. Instead, learn to parse the program in your head, identifying the tokens and interpreting the structure. Finally, the details matter. Small errors in spelling and punctuation, which you can get away with in natural languages, can make a big difference in a formal language.

> 公式语言比自然语言要更加密集，读起来也需要更长时间。公式语言的结构也非常重要，所以从头到尾或者从左到右未必就是最佳方式。大家应该学着动脑来解译程序，分辨代号，解析结构。最后要注意的就是在公式语言中，细节特别特别重要。拼写和符号的小错误对于自然语言来说没什么，但对公式语言来说就能带来大问题。

## 1.7  Debugging 调试

Programmers make mistakes. For whimsical reasons, programming errors are called bugs and the process of tracking them down is called debugging.

> 程序员也会犯错的。由于很奇妙的原因，程序的错误被叫做bug，调试的过程就叫debug了。（译者注：一个传言是最早的计算机中经常有虫子进去导致短路之类的，清理虫子就成了常规调试的操作，流传至今。。。）

Programming, and especially debugging, sometimes brings out strong emotions. If you are struggling with a difficult bug, you might feel angry, despondent, or embarrassed.

> 编程，尤其是调试的过程，有时候会给人带来强烈的挫败感。面对特别复杂的状况，你可能就感到愤怒、压抑，或者特别难受。

There is evidence that people naturally respond to computers as if they were people. When they work well, we think of them as teammates, and when they are obstinate or rude, we respond to them the same way we respond to rude, obstinate people \(Reeves and Nass, The Media Equation: How People Treat Computers, Television, and New Media Like Real People and Places\).

> 别担心，这些都是正常人对计算机的正常反应。计算机工作正常了，我们会觉得他们像是队友一样；一旦工作出错了，对我们很粗暴，我们对他们的反应就像是对待粗暴可恨的人一样（参考Reeves和Nass，The Media Equation: How People Treat Computers, Television, and New Media Like Real People and Places）。

Preparing for these reactions might help you deal with them. One approach is to think of the computer, as an employee with certain strengths, like speed and precision, and particular weaknesses, like lack of empathy and inability to grasp the big picture.

> 为这些反应做好心理准备，这样你在遇到类似情况就更好应对了。我们也可以把计算机当做一个有一定优点但也有特定缺陷的员工，比如速度快精度高，但缺乏共鸣和应对大场面的能力。

Your job is to be a good manager: find ways to take advantage of the strengths and mitigate the weaknesses. And find ways to use your emotions to engage with the problem, without letting your reactions interfere with your ability to work effectively.

> 你的工作就是做个好的经理人：尽量充分利用员工优势并降低他们缺陷的作用。然后想办法把你的情绪用在解决问题上，而不要让过激的反应干扰工作效率。

Learning to debug can be frustrating, but it is a valuable skill that is useful for many activities beyond programming. At the end of each chapter there is a section, like this one, with my suggestions for debugging. I hope they help!

> 调试的过程挺烦人的，但这个本领很有价值，而且在编程之外的其他领域都有用武之地。在每一章的末尾，都会有这样的一段，我会给出一些关于调试方面的建议。希望能帮到大家！

1.8  Glossary 术语列表  
problem solving:  
The process of formulating a problem, finding a solution, and expressing it.

> 问题解决：将问题方程化，找到解决方案，并表达出来的过程。

high-level language:  
A programming language like Python that is designed to be easy for humans to read and write.

> 高级语言：例如Python这样的编程语言，设计初衷为易于被人阅读和书写。

low-level language:  
A programming language that is designed to be easy for a computer to run; also called “machine language” or “assembly language”.

> 低级语言：设计初衷为易于被计算机运行的语言，比如机器语言和汇编语言。

portability:  
A property of a program that can run on more than one kind of computer.

> 可移植性：程序能运行于多种平台的特性。  
> interpreter:

A program that reads another program and executes it

> 解释器：一边读取一边执行代码的程序。

prompt:  
Characters displayed by the interpreter to indicate that it is ready to take input from the user.

> 提示符：解释器显示的，提醒用户准备就绪，随时可以输入。

program:  
A set of instructions that specifies a computation.

> 程序：进行一种特定运算的一系列指令。

print statement:  
An instruction that causes the Python interpreter to display a value on the screen.

> 打印语句：让Python解释器输出值到屏幕的指令。

operator:  
A special symbol that represents a simple computation like addition, multiplication, or string concatenation.

> 运算符（操作符）：一系列特殊的符号，表示一些简单的运算，比如加减乘除或者字符串操作。

value:  
One of the basic units of data, like a number or string, that a program manipulates.

> 值：数据的基本组成单元，比如数字或者字符串，是程序处理的对象。

type:  
A category of values. The types we have seen so far are integers \(typeint\), floating-point numbers \(type float\), and strings \(type str\).

> 类型：对值的分类，大家刚刚接触到的有整形int，浮点数float，以及字符串str。  
> integer:  
> A type that represents whole numbers.  
> 整形：就是整数咯。

floating-point:  
A type that represents numbers with fractional parts.

> 浮点数：简单说，就是有小数点的数了。

string:  
A type that represents sequences of characters.

> 字符串：一串有序的字符了。

natural language:  
Any one of the languages that people speak that evolved naturally.

> 自然语言：人们说的语言，自然地演化。

formal language:  
Any one of the languages that people have designed for specific purposes, such as representing mathematical ideas or computer programs; all programming languages are formal languages.

> 公式语言：人为设计的用于特定用途的语言，比如数学用途或者计算机编程用的；所有编程语言都是公式语言。

token:  
One of the basic elements of the syntactic structure of a program, analogous to a word in a natural language.

> 代号：程序结构中的一种基本元素，相当于自然语言中的单词。

syntax:  
The rules that govern the structure of a program.

> 语法：程序语言结构的规则。

parse:  
To examine a program and analyze the syntactic structure.

> 解译：理解程序并分析语法结构的过程。

bug:  
An error in a program.

> Bug：程序的错误。

debugging:  
The process of finding and correcting bugs.

> 调试（debug）：搜索和改正程序错误的过程。

## 1.9  Exercises 练习

### Exercise 1  练习1

It is a good idea to read this book in front of a computer so you can try out the examples as you go.

> 你读这本书的同时最好手边有台电脑，这样你就能把样例在电脑上随时运行来看看效果了。

Whenever you are experimenting with a new feature, you should try to make mistakes. For example, in the “Hello, world!” program, what happens if you leave out one of the quotation marks? What if you leave out both? What if you spell print wrong?

> 无论你学任何一种新功能的时候，都可以试着犯点错误。比如就在这个『Hello，World！』程序，你可以试试去掉一个引号会怎么样，都去掉会怎么样，print这个单词拼错了会怎么样等等。

This kind of experiment helps you remember what you read; it also helps when you are programming, because you get to know what the error messages mean. It is better to make mistakes now and on purpose than later and accidentally.

> 这种尝试能让你对读到的内容有更深刻的记忆；也有助于你编程，因为你在编程的时候也得知道调试信息的意思。所以最好现在就故意犯些错误来看看，比以后毫无准备地遇到要好多了。

1. In a print statement, what happens if you leave out one of the parentheses, or both?

   > 在print语句后面的括号去掉一个或者两个，看看会怎么样？

2. If you are trying to print a string, what happens if you leave out one of the quotation marks, or both?

   > Print字符串的时候如果你丢掉一个引号或者两个引号试试看会如何？

3. You can use a minus sign to make a negative number like -2. What happens if you put a plus sign before a number? What about 2++2?

   > 输入一个负数试试，比如-2。然后再试试在数字前面添加加号会怎么样？比如2++2。

4. In math notation, leading zeros are ok, as in 02. What happens if you try this in Python?

   > 数学上计数用零开头是可以得，比如02，在Python下面试试会怎样？

5. What happens if you have two values with no operator between them?

   > 两个值中间没有运算符会怎么样？



