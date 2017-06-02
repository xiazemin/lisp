# common lisp 开发环境

[https://common-lisp.net/project/lispbox/](https://common-lisp.net/project/lispbox/)

下载lispbox

什么是Lispbox？

lispbox 是Common Lisp的集成开发环境。实际是Lispbox只是组合配置了Emacs编辑器，SLIME\(Emacs的高级Lisp 交互模式\)和Quicklisp 库管理工具和CCL Lisp编译器。

这些工具组合在一起给你了你所期望的一个ide能给你的所用的功能集合，甚至更多。Lispbox使你可以迅速和简单的投入使用。

Lispbox可以让新的Lisp程序员在一流的开发环境上近似于无痛的起步。所以强烈建议新手下载安装Lispbox作为学习Common Lisp的开始。

SLIME \(Superior Lisp Interaction Mode forEmacs\)

　　SLIME对Emacs进行了扩充，提供了Common Lisp的一种交互式编程环境。SLIME由两部分组成:一部分针对Emacs，使用EmacsLisp开发，用来定义Emacs的编辑模式、提供CommonLisp调试器SLDB的用户界面以及创建一个REPL\(Read-Eval-Print Loop\) 缓冲区等;另一部分称为Swank，使用使用CommonLisp开发，是一个服务器程序，运行在某种特定的CommonLisp实现中。Emacs通过IP协议连接Swank，因此Emacs可以连接到本地或者远程机器上的Swank。本文中主要介绍Emacs连接本地Swank实例的情况。



　　SLIME定义了一种新的次模式\(minormode\)slime-mode用以扩充标准的lisp-mode。lisp-mode使得Emacs能够编辑Lisp源程序，而slime-mode使得Emacs能够与一个运行中的CommonLisp进程进行通信以完成编译、调试CommonLisp程序等任务。



Lispbox的安装和使用



想使用Lispbox很简单，只要下载和解压对应你操作系统的版本即可。不需要安装！可以通过运行lispbox.bat \(Windows\) / lispbox.sh \(Linux\) / Emacs \(OS X\)开始Lispbox使用。

下载地址:http://common-lisp.net/project/lispbox/







Lispbox的中文问题

默认的Emacs没有开启UTF-8字符集支持，所以并不支持中文，甚至中文注释也不行。如果输入中文将会出现如下错误：

CL-USER&gt; '你好



slime-net-send: Coding system iso-latin-1-unix not suitable for "00004c\(:emacs-rex \(swank:listener-eval \"'你好

\"\) \"COMMON-LISP-USER\" :repl-thread 4\)"



要对中文支持需修改文件解压后的文件夹下的文件 emacs-23.2\site-lisp\lispbox.el

在\(require 'slime\) 这一行的后面增加一行:

\(setq slime-net-coding-system 'utf-8-unix\)

也可以设置成其它编码，重启Lispbox即可。

