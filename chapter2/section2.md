# 函数

lisp最基本的三个部分是函数、变量、宏

![](/assets/import33.png)

&optimal可选形参，&rest剩余形参&key关键字形参

默认最后一个表达式的值被作为函数返回值，return－from可以从函数或者代码块任意位置返回

function可以返回函数对象，＃‘也一样

（foo 1 2）＝（functioncall ＃‘foo 1 2）＝（apply foo （1 2））

defun 定义函数 lambda定义匿名函数





