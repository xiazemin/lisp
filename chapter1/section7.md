# SLIME

\*SLIME 是一个革命性的开发工具\*。它的重要性将在未来几年内逐渐被主流开发界所认识（主流总是很迟钝）。任何其他编程语言，如果不能实现SLIME的功能，则不能称之为“高级语言”。

SLIME是： The Superior Lisp Interaction Mode for Emacs 的缩写。

SLIME 的官方网站： [http://common-lisp.net/project/slime/](http://common-lisp.net/project/slime/)

各种文档，介绍在上述网站中都有。这个网站看上去很out。但，不要被外表欺骗。它里面的开发技术与理念非常的领先前卫。

SLIME是 Emacs 与 Common LISP之间的桥梁，是开发环境与运行环境之间的桥梁。

我个人认为SLIME最重要的一点意义在于：它强调了快速迭代式的开发方式。首先要了解这一点，然后SLIME的各种特性都是为这一点服务的。这其实一直是LISP的开发方式。

SLIME支持远程开发与热升级，之前在我的blog上写过一篇文章介绍： [http://www.feime.net/lisp利器/远程开发调试与hot-update/](http://www.feime.net/lisp利器/远程开发调试与hot-update/)

SLIME的特性包括：

1. Emacs 的slime-mode 包括了lisp代码的编辑支持，代码执行，编译，宏展开，等等

2. 在线文档

3. REPL

4. 交叉引用

5. 调试

6. Inspector

等等。。

===================

SLIME 与 Emacs， LISP 之间的关系，可以通过下图表示：

![](/assets/imports.png)

SLIME架构图

swank 是LISP下的server，emacs中的slime模块通过tcp连接上swank服务器。使用者在emacs中编写代码，发送命令，通过网络传递给lisp进程执行，然后返回结果。

比如，最典型的：我们在emacs中编写了一段函数，然后调用 slime-compile-defun 命令（一般用快捷键 C-c C-c\) ， 这段函数的代码就会发送给lisp进程，lisp进程最终调用compile命令将代码编译到进程内部，并返回执行结果，emacs获得结果显示。

注意，我们可以重复定义一个函数，可以定义新的函数，而LISP进程是一直在那里的。你可以随时去执行任意的命令或函数。你可以将一大坨测试数据（甚至真实数据）load到LISP的进程中，然后随便折腾他们。

甚至，你可以连接上一个远程运行的服务程序，修改里面的函数定义，或增加新的功能，而不用重启这个进程。这就是远程调试和热升级。

======================

下面演示一些 SLIME 的特性：注意，这些特性很多在LISP环境下都可以直接做到，例如宏展开，反汇编，调试等等，使用SLIME只是更方便而已。这里不严格区分是SLIME的功能还是LISP的功能，众所周知，SLIME自古以来就是LISP不可分割的一部分了，是LISP的固有领土。

1. 想一边写代码，一边测试运行？ 

没错，SLIME就是这么用的。

![](/assets/importl.png)

1. 想获得更详细的在线文档？ 

当我写下一个函数时，在emacs下面的minibuffer里会有一个简单的文档：

![](/assets/importm.png)

但是，我不满足，想看看更详细的文档怎么办？用 slime-hyperspec-look 命令，我绑定到快捷键上了，一键即可在浏览器上打开详细的文档。

1. 我想看一段代码编译后的汇编代码？ 

用 slime-dissassemble-definition

![](/assets/import23.png)

1. 想知道一个函数被谁引用过？ 

slime-list-callers

xref

xref

1. 想知道一行宏调用展开后是啥德行么？ 

slime-macroexpand-1 \(all\)

macroexpand

macroexpand

1. 查看对象内部的值？ 

slime-inspect

Inspect Object

Inspect Object

想知道一个package的信息？

inspect package 即可

注意，里面列出的内容是可以点击的，回车可以看到更详细的信息，比如我们想知道那1个 external symbols 是什么：

Inspect Package, show details

Inspect Package, show details

这里 flags 中的 f 表示这个符号是个函数。

==========

SLDB 调试方面，请听下回分解。

