Title: ThinkPython 双语学编程 Chapter 0.5 Preface 前言
Date: 2015-10-21
Category: ThinkPython
Tag: 双语,Python,ThinkPython

#Chapter 0  Preface 前言
##The strange history of this book
>本书的奇幻历史

In January 1999 I was preparing to teach an introductory programming class in Java. I had taught it three times and I was getting frustrated. The failure rate in the class was too high and, even for students who succeeded, the overall level of achievement was too low.
>在1999年1月的时候呢，我正准备教一门Java的入门编程课。
我当时已经教过三次了，受挫感很强。班上挂科率特别高，而且即使那些没挂科的学生编程的整体水平也特别低。

One of the problems I saw was the books. They were too big, with too much unnecessary detail about Java, and not enough high-level guidance about how to program. And they all suffered from the trap door effect: they would start out easy, proceed gradually, and then somewhere around Chapter 5 the bottom would fall out. The students would get too much new material, too fast, and I would spend the rest of the semester picking up the pieces.
>当时有很多问题，我首先发现的就是教材。那些教材都特别大部头，有很多关于Java的细节，特别琐碎又并不重要，而且也没有足够的关于如何编程的高层次指导（译者注：就是缺乏战略性指导，没有告诉学生编程的心法）。这些教材总有一些『陷阱门效应』：开头他们都却是挺简单，然后逐步提升，接着突然在某个地方，比如第五章，出现很坑很复杂的陷阱。学生们要突然一下子应对太多新东西，甚至措手不及，而我作为教师就得花费整个后半个学期来一点点给学生们补上。

Two weeks before the first day of classes, I decided to write my own book. My goals were:

*	Keep it short. It is better for students to read 10 pages than not read 50 pages.
*	Be careful with vocabulary. I tried to minimize jargon and define each term at first use.
*	Build gradually. To avoid trap doors, I took the most difficult topics and split them into a series of small steps.
*	Focus on programming, not the programming language. I included the minimum useful subset of Java and left out the rest.

I needed a title, so on a whim I chose How to Think Like a Computer Scientist.

开课的两周之前，我最终决定要写个自己的教科书。目标如下：

*	简短。让学生读10页就够比让他们读50页效果好得多。
*	降低词汇难度。我尽量把术语用量降到最低，并且在首次使用的时候对每一个都进行定义。
*	循序渐进。为了避免『陷阱门效应』，我专门把这些最为复杂的部分抽离成一个个专题，并且都切分成小规模的部分，一步步来进行。
*	专注于编程，而不是编程语言。我只保留了关于Java的最小规模内容，没有涉及更多的细节。
我还需要个标题，就突发奇想，选了个标题叫做『如何像计算机科学家一样思考』。

My first version was rough, but it worked. Students did the reading, and they understood enough that I could spend class time on the hard topics, the interesting topics and (most important) letting the students practice.
>我的第一版教材很粗糙，但挺管用。学生真能看进去，并且理解了我在课上所讲的那些难点和有趣的专题，最重要的是，他们能够据此来实践。

I released the book under the GNU Free Documentation License, which allows users to copy, modify, and distribute the book.
>之后我就以GNU自由文档协议来发布了这本书，这一协议允许所有人去复制、修改以及分发这本书。

What happened next is the cool part. Jeff Elkner, a high school teacher in Virginia, adopted my book and translated it into Python. He sent me a copy of his translation, and I had the unusual experience of learning Python by reading my own book. As Green Tea Press, I published the first Python version in 2001.
>接下来的事情很有趣了。Jeff Elkner，维吉尼亚的一位高中教师，他很欣赏我这本书，把这本书从Java翻译成了Python的版本。他发给我一份『译稿』，然后我开启了阅读『自己的书』来学习Python的奇妙经历。于是在2001年，我通过Green Tea Press出版了本书的第一个Python版本。

In 2003 I started teaching at Olin College and I got to teach Python for the first time. The contrast with Java was striking. Students struggled less, learned more, worked on more interesting projects, and generally had a lot more fun.
>在2003年，我开始在奥林商学院教学，并且第一次开始教Python了。这和Java的对比很鲜明。学生们省力多了，学得也更多了，在有趣的项目上也更努力，整体上都觉得这一学习过程很有乐趣。

Since then I’ve continued to develop the book, correcting errors, improving some of the examples and adding material, especially exercises.
>从那以后，我就继续维护这本书，修正错误，改进样例、附加资料以及练习题。

The result is this book, now with the less grandiose title Think Python. Some of the changes are:

*	I added a section about debugging at the end of each chapter. These sections present general techniques for finding and avoiding bugs, and warnings about Python pitfalls.
*	I added more exercises, ranging from short tests of understanding to a few substantial projects. Most exercises include a link to my solution.
*	I added a series of case studies—longer examples with exercises, solutions, and discussion.
*	I expanded the discussion of program development plans and basic design patterns.
*	I added appendices about debugging and analysis of algorithms.

>结果就产生了现在这本书，现在标题简化了很多——Think Python。主要的改变如下：

>*	在每一章的末尾，我加了关于debug的部分。这些内容提供了关于debug的一些整体策略，比如如何找到和避免bug，还有就是关于Python一些陷阱进行了提醒。
>*		我加了更多的练习，从简单的理解方面的测试，到一些比较充足的项目。大多数练习都有解决方案的样本链接。
>*		我还添加了一些案例研究，包含练习、解决方案和讨论的更大规模的样例。
>*		此外我还扩展了关于程序开发规划和基本设计模式的讨论。
>*		关于debug和算法分析，还额外加了一些附录。
	
The second edition of Think Python has these new features:

*	The book and all supporting code have been updated to Python 3.
*	I added a few sections, and more details on the web, to help beginners get started running Python in a browser, so you don’t have to deal with installing Python until you want to.
*	For Chapter 4.1 I switched from my own turtle graphics package, called Swampy, to a more standard Python module, turtle, which is easier to install and more powerful.
*	I added a new chapter called “The Goodies”, which introduces some additional Python features that are not strictly necessary, but sometimes handy.

>这本Think Python 的第二版有如下的新内容：

>*	本书内的所有参考代码都升级到Python3了。
>*	我增加了一部分内容，以及一些关于web方面的细节，这是为了帮助初学者能够在浏览器中开始尝试Python，这样即便你不想安装Python也没问题了。
>*	在第四章的第一节，我把我自己的一个原来叫做Swampy的小乌龟图形包转换撑了一个更标准的Python模块，名字叫做turtle，更好安装，功能也比之前强大了。
>*	我还添加了新的一章，叫做『彩蛋』，介绍了一些Python的额外功能，严格来说，这些功能并不算必备的，但有时候蛮好用的。

I hope you enjoy working with this book, and that it helps you learn to program and think like a computer scientist, at least a little bit.
>我希望大家能享受学习这本书的过程，也希望这本书能帮助大家学习编程，并且让大家学会像计算机科学家一样思考，哪怕有一点点也好。

Allen B. Downey
>艾伦 唐尼

Olin College
>奥林商学院

##Acknowledgments 
>##致谢

Many thanks to Jeff Elkner, who translated my Java book into Python, which got this project started and introduced me to what has turned out to be my favorite language.
>非常感谢Jeff Elkner，是他把我的Java教材翻译成了Python，才引起了这一项目的开始，并且也把Python语言介绍给我，它已经是我最喜欢的编程语言了。

Thanks also to Chris Meyers, who contributed several sections to How to Think Like a Computer Scientist.
>也要感谢Chris Meyers，他对『如何像计算机科学家一样思考』的一些章节有贡献。

Thanks to the Free Software Foundation for developing the GNU Free Documentation License, which helped make my collaboration with Jeff and Chris possible, and Creative Commons for the license I am using now.
>感谢自由软件基金会，是他们提出了GNU自由文档协议，在这一协议的帮助下，我和Jeff以及Chris的合作成为了可能，当然也要感谢我现在使用的知识共享协议。

Thanks to the editors at Lulu who worked on How to Think Like a Computer Scientist.
>感谢Lulu的编辑们，他们出版了『如何像计算机科学家一样思考』。

Thanks to the editors at O’Reilly Media who worked on Think Python.
>感谢O’Reilly公司的编辑们，他们出版了这本『Think Python』。

Thanks to all the students who worked with earlier versions of this book and all the contributors (listed below) who sent in corrections and suggestions.
>最后还要感谢所有曾对本书早期版本做出过贡献的同学们，以及其他参与改错和提出建议的朋友们（列表如下）。
###Contributor List 
>###贡献列表

More than 100 sharp-eyed and thoughtful readers have sent in suggestions and corrections over the past few years. Their contributions, and enthusiasm for this project, have been a huge help.
>百名以上目光敏锐又思维迅捷的读者都在过去的这些年里发来了各种建议或是发现了各种错误。他们贡献和热情都是对本项目的巨大帮助。

If you have a suggestion or correction, please send email tofeedback@thinkpython2.com. If I make a change based on your feedback, I will add you to the contributor list (unless you ask to be omitted).
>如果大家有任何意见建议，请发邮件到feedback@thinkpython2.com联系我们。如果基于反馈做出了修改，我会将你添加到贡献列表（当然你不想被添加也可以的）。

If you include at least part of the sentence the error appears in, that makes it easy for me to search. Page and section numbers are fine, too, but not quite as easy to work with. Thanks!
>希望你能至少把出错句子的一部分提供出来，这都让我更容易去搜索。页码和章节编号也可以，但不太容易找。多谢了！
（译者注：以下贡献列表不翻译了）

*	Lloyd Hugh Allen sent in a correction to Section 8.4.
*	Yvon Boulianne sent in a correction of a semantic error in Chapter 5.
*	Fred Bremmer submitted a correction in Section 2.1.
*	Jonah Cohen wrote the Perl scripts to convert the LaTeX source for this book into beautiful HTML.
*	Michael Conlon sent in a grammar correction in Chapter 2 and an improvement in style in Chapter 1, and he initiated discussion on the technical aspects of interpreters.
*	Benoit Girard sent in a correction to a humorous mistake in Section 5.6.
*	Courtney Gleason and Katherine Smith wrote horsebet.py, which was used as a case study in an earlier version of the book. Their program can now be found on the website.
*	Lee Harr submitted more corrections than we have room to list here, and indeed he should be listed as one of the principal editors of the text.
*	James Kaylin is a student using the text. He has submitted numerous corrections.
*	David Kershaw fixed the broken catTwice function in Section 3.10.
*	Eddie Lam has sent in numerous corrections to Chapters 1, 2, and 3. He also fixed the Makefile so that it creates an index the first time it is run and helped us set up a versioning scheme.
*	Man-Yong Lee sent in a correction to the example code in Section 2.4.
*	David Mayo pointed out that the word “unconsciously" in Chapter 1 needed to be changed to “subconsciously".
*	Chris McAloon sent in several corrections to Sections 3.9 and 3.10.
*	Matthew J. Moelter has been a long-time contributor who sent in numerous corrections and suggestions to the book.
*	Simon Dicon Montford reported a missing function definition and several typos in Chapter 3. He also found errors in the increment function in Chapter 13.
*	John Ouzts corrected the definition of “return value" in Chapter 3.
*	Kevin Parks sent in valuable comments and suggestions as to how to improve the distribution of the book.
*	David Pool sent in a typo in the glossary of Chapter 1, as well as kind words of encouragement.
*	Michael Schmitt sent in a correction to the chapter on files and exceptions.
*	Robin Shaw pointed out an error in Section 13.1, where the printTime function was used in an example without being defined.
*	Paul Sleigh found an error in Chapter 7 and a bug in Jonah Cohen’s Perl script that generates HTML from LaTeX.
*	Craig T. Snydal is testing the text in a course at Drew University. He has contributed several valuable suggestions and corrections.
*	Ian Thomas and his students are using the text in a programming course. They are the first ones to test the chapters in the latter half of the book, and they have made numerous corrections and suggestions.
*	Keith Verheyden sent in a correction in Chapter 3.
*	Peter Winstanley let us know about a longstanding error in our Latin in Chapter 3.
*	Chris Wrobel made corrections to the code in the chapter on file I/O and exceptions.
*	Moshe Zadka has made invaluable contributions to this project. In addition to writing the first draft of the chapter on Dictionaries, he provided continual guidance in the early stages of the book.
*	Christoph Zwerschke sent several corrections and pedagogic suggestions, and explained the difference between gleich and selbe.
*	James Mayer sent us a whole slew of spelling and typographical errors, including two in the contributor list.
*	Hayden McAfee caught a potentially confusing inconsistency between two examples.
*	Angel Arnal is part of an international team of translators working on the Spanish version of the text. He has also found several errors in the English version.
*	Tauhidul Hoque and Lex Berezhny created the illustrations in Chapter 1 and improved many of the other illustrations.
*	Dr. Michele Alzetta caught an error in Chapter 8 and sent some interesting pedagogic comments and suggestions about Fibonacci and Old Maid.
*	Andy Mitchell caught a typo in Chapter 1 and a broken example in Chapter 2.
*	Kalin Harvey suggested a clarification in Chapter 7 and caught some typos.
*	Christopher P. Smith caught several typos and helped us update the book for Python 2.2.
*	David Hutchins caught a typo in the Foreword.
*	Gregor Lingl is teaching Python at a high school in Vienna, Austria. He is working on a German translation of the book, and he caught a couple of bad errors in Chapter 5.
*	Julie Peters caught a typo in the Preface.
*	Florin Oprina sent in an improvement in makeTime, a correction inprintTime, and a nice typo.
*	D. J. Webre suggested a clarification in Chapter 3.
*	Ken found a fistful of errors in Chapters 8, 9 and 11.
*	Ivo Wever caught a typo in Chapter 5 and suggested a clarification in Chapter 3.
*	Curtis Yanko suggested a clarification in Chapter 2.
*	Ben Logan sent in a number of typos and problems with translating the book into HTML.
*	Jason Armstrong saw the missing word in Chapter 2.
*	Louis Cordier noticed a spot in Chapter 16 where the code didn’t match the text.
*	Brian Cain suggested several clarifications in Chapters 2 and 3.
*	Rob Black sent in a passel of corrections, including some changes for Python 2.2.
*	Jean-Philippe Rey at Ecole Centrale Paris sent a number of patches, including some updates for Python 2.2 and other thoughtful improvements.
*	Jason Mader at George Washington University made a number of useful suggestions and corrections.
*	Jan Gundtofte-Bruun reminded us that “a error” is an error.
*	Abel David and Alexis Dinno reminded us that the plural of “matrix” is “matrices”, not “matrixes”. This error was in the book for years, but two readers with the same initials reported it on the same day. Weird.
*	Charles Thayer encouraged us to get rid of the semi-colons we had put at the ends of some statements and to clean up our use of “argument” and “parameter”.
*	Roger Sperberg pointed out a twisted piece of logic in Chapter 3.
*	Sam Bull pointed out a confusing paragraph in Chapter 2.
*	Andrew Cheung pointed out two instances of “use before def”.
*	C. Corey Capel spotted the missing word in the Third Theorem of Debugging and a typo in Chapter 4.
*	Alessandra helped clear up some Turtle confusion.
*	Wim Champagne found a brain-o in a dictionary example.
*	Douglas Wright pointed out a problem with floor division in arc.
*	Jared Spindor found some jetsam at the end of a sentence.
*	Lin Peiheng sent a number of very helpful suggestions.
*	Ray Hagtvedt sent in two errors and a not-quite-error.
*	Torsten Hübsch pointed out an inconsistency in Swampy.
*	Inga Petuhhov corrected an example in Chapter 14.
*	Arne Babenhauserheide sent several helpful corrections.
*	Mark E. Casida is is good at spotting repeated words.
*	Scott Tyler filled in a that was missing. And then sent in a heap of corrections.
*	Gordon Shephard sent in several corrections, all in separate emails.
*	Andrew Turner spotted an error in Chapter 8.
*	Adam Hobart fixed a problem with floor division in arc.
*	Daryl Hammond and Sarah Zimmerman pointed out that I served upmath.pi too early. And Zim spotted a typo.
*	George Sass found a bug in a Debugging section.
*	Brian Bingham suggested Exercise 5.
*	Leah Engelbert-Fenton pointed out that I used tuple as a variable name, contrary to my own advice. And then found a bunch of typos and a “use before def”.
*	Joe Funke spotted a typo.
*	Chao-chao Chen found an inconsistency in the Fibonacci example.
*	Jeff Paine knows the difference between space and spam.
*	Lubos Pintes sent in a typo.
*	Gregg Lind and Abigail Heithoff suggested Exercise 3.
*	Max Hailperin has sent in a number of corrections and suggestions. Max is one of the authors of the extraordinary Concrete Abstractions, which you might want to read when you are done with this book.
*	Chotipat Pornavalai found an error in an error message.
*	Stanislaw Antol sent a list of very helpful suggestions.
*	Eric Pashman sent a number of corrections for Chapters 4–11.
*	Miguel Azevedo found some typos.
*	Jianhua Liu sent in a long list of corrections.
*	Nick King found a missing word.
*	Martin Zuther sent a long list of suggestions.
*	Adam Zimmerman found an inconsistency in my instance of an “instance” and several other errors.
*	Ratnakar Tiwari suggested a footnote explaining degenerate triangles.
*	Anurag Goel suggested another solution for is_abecedarian and sent some additional corrections. And he knows how to spell Jane Austen.
*	Kelli Kratzer spotted one of the typos.
*	Mark Griffiths pointed out a confusing example in Chapter 3.
*	Roydan Ongie found an error in my Newton’s method.
*	Patryk Wolowiec helped me with a problem in the HTML version.
*	Mark Chonofsky told me about a new keyword in Python 3.
*	Russell Coleman helped me with my geometry.
*	Wei Huang spotted several typographical errors.
*	Karen Barber spotted the the oldest typo in the book.
*	Nam Nguyen found a typo and pointed out that I used the Decorator pattern but didn’t mention it by name.
*	Stéphane Morin sent in several corrections and suggestions.
*	Paul Stoop corrected a typo in uses_only.
*	Eric Bronner pointed out a confusion in the discussion of the order of operations.
*	Alexandros Gezerlis set a new standard for the number and quality of suggestions he submitted. We are deeply grateful!
*	Gray Thomas knows his right from his left.
*	Giovanni Escobar Sosa sent a long list of corrections and suggestions.
*	Alix Etienne fixed one of the URLs.
*	Kuang He found a typo.
*	Daniel Neilson corrected an error about the order of operations.
*	Will McGinnis pointed out that polyline was defined differently in two places.
*	Swarup Sahoo spotted a missing semi-colon.
*	Frank Hecker pointed out an exercise that was under-specified, and some broken links.
*	Animesh B helped me clean up a confusing example.
*	Martin Caspersen found two round-off errors.
*	Gregor Ulm sent several corrections and suggestions.
*	Dimitrios Tsirigkas suggested I clarify an exercise.
*	Carlos Tafur sent a page of corrections and suggestions.
*	Martin Nordsletten found a bug in an exercise solution.
*	Lars O.D. Christensen found a broken reference.
*	Victor Simeone found a typo.
*	Sven Hoexter pointed out that a variable named input shadows a build-in function.
*	Viet Le found a typo.
*	Stephen Gregory pointed out the problem with cmp in Python 3.
*	Matthew Shultz let me know about a broken link.
*	Lokesh Kumar Makani let me know about some broken links and some changes in error messages.
*	Ishwar Bhat corrected my statement of Fermat’s last theorem.
*	Brian McGhie suggested a clarification.
*	Andrea Zanella translated the book into Italian, and sent a number of corrections along the way.
*	Many, many thanks to Melissa Lewis and Luciano Ramalho for excellent comments and suggestions on the second edition.
*	Thanks to Harry Percival from PythonAnywhere for his help getting people started running Python in a browser.
 



