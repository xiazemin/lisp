# 支持中文

只需要修改 slime 目录（我的是 F:\lispbox-0.9\slime-2012-11-13\ ）下的 slime.el 文件中的键图映射代码，涉及4个命令：

slime-load-file

slime-compile-and-load-file

slime-compile

slime-compile-defun

在这些命令后加个参数 :external-format :utf-8 ，指定使用 UTF-8 就可以了，具体代码如下：

\(defvar slime-prefix-bindings

  '\(\("\C-r"  slime-eval-region\)

    \(":"     slime-interactive-eval\)

    \("\C-e"  slime-interactive-eval\)

    \("E"     slime-edit-value\)

    \("\C-l"  slime-load-file :external-format :utf-8\)

    \("\C-b"  slime-interrupt\)

    \("\M-d"  slime-disassemble-symbol\)

    \("\C-t"  slime-toggle-trace-fdefinition\)

    \("I"     slime-inspect\)

    \("\C-xt" slime-list-threads\)

    \("\C-xn" slime-cycle-connections\)

    \("\C-xc" slime-list-connections\)

    \("&lt;"     slime-list-callers\)

    \("&gt;"     slime-list-callees\)

    ;; Include DOC keys...

    \("\C-d"  slime-doc-map\)

    ;; Include XREF WHO-FOO keys...

    \("\C-w"  slime-who-map\)

    \)\)

\(defvar slime-keys

  '\( ;; Compiler notes

    \("\M-p"       slime-previous-note\)

    \("\M-n"       slime-next-note\)

    \("\C-c\M-c"   slime-remove-notes\)

    \("\C-c\C-k"   slime-compile-and-load-file :external-format :utf-8\)

    \("\C-c\M-k"   slime-compile-file :external-format :utf-8\)

    \("\C-c\C-c"   slime-compile-defun :external-format :utf-8\)\)\)

如果是在EVAL下使用 load 函数，也需要加上额外的参数，如下所示：

\(load "cnfile.lisp" :external-format :utf-8\)

所有涉及文件打开操作的函数都有这个参数，比如 open 和 with-open-file 函数，使用形式如下所示：

\(open "cnfile.lisp" :external-format :utf-8\)

\(with-open-file :external-format :utf-8\)



