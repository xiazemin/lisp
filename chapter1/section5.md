# 缓冲区

这里我开始使用缓冲区（buffer）这个名词，缓冲区是 Emacs 编辑器的一个概念，文本编辑窗口是一个缓冲区，REPL 是一个缓冲区，消息事件也是一个缓冲区，不同的缓冲区可以来回切换，缓冲区的屏幕布局也可以通过快捷键来设置：

C-x 1 当前缓冲区占据整个 Emacs 窗口，其他缓冲区全部放到后台；

C-x 0 关闭当前缓冲区

C-x 2 在当前缓冲区上方新打开一个缓冲区

C-x 3 在当前缓冲区右方新打开一个缓冲区

对于自定义函数的宏 defun ，我们想查看它的源代码，想了解它的具体实现细节，可以把光标放在 defun 上，然后按 M-.

M-.     同时按 Alt 键 和 点键 .

所有的文件操作函数（比如 load open等）默认的字符编码格式类型都是 :latin-1 ，这种编解码类型对应英文字符，遇到中文内容自然就乱码了。

没错，你没看错，我也没写错，这个类型名称就是以冒号打头的个符号，这种类型的符号在 Lisp 中被称为关键字 keyword ，对这种类型的符号求值会得到冒号后面的符号名称，从现在开始初学者要逐步适应 Lisp 对符号的使用习惯。而我们的中文使用的编码恰恰不是这个，而是 :utf-8 ，那么就需要手工指定了，如下：

CL-USER&gt; \(load "~/ecode/markdown-doc/hi.lisp" :external-

format :utf-8\)

\#P"/Users/admin/ECode/Markdown-doc/hi.lisp"

CL-USER&gt; \(hi\)

你好，世界！

NIL

很麻烦，每次加载文件都得输入一长串额外的参数，这里介绍一个稍微简单点的办法，可以通过修改系统的全局变量 \*default-external-format\* 来把默认的文件格式改成我们需要的 :utf-8 ，先查看一下当前的值，如下：

CL-USER&gt; \*default-external-format\*

:UNIX

CL-USER&gt;

用 setq 函数修改，第一个参数是要修改的全局变量，第二个参数是希望修改成的值，修改然后查看：

CL-USER&gt; \(setq \*default-external-format\* :utf-8\)

:UTF-8

CL-USER&gt; \*default-external-format\*

:UTF-8

说明：全局变量 \*default-external-format\* 在 CCL 和 CLisp 中可以用，但是在 SBCL 中不支持

C-c C-z 从代码编辑区切换到 REPL 区；

C-c C-y 把正在编写的函数名称发送到 REPL 区进行调试；

C-x o 从 REPL 区 切换到代码编辑区；

M-p 在 REPL 区查找历史命令，向前翻页

M-n 在 REPL 区查找历史命令，向后翻页

M-. 同时按 Alt 键 和 点键 . ，查看当前光标所在位置的函数的

