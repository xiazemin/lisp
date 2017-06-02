# 语法介绍

; SLIME 2011-02-04

CL-USER&gt; '世界



; No value

CL-USER&gt; \(getf \(list :a 1 :b 2 :c 3\) :b\)

2

CL-USER&gt; \(defun make-cd \(title artist rating ripped\)

	   \(list :title title :artist artist :rating rating :ripped ripped\)\)

MAKE-CD

CL-USER&gt; \(make-cd "Roses" "Kattea" 7 t\)

\(:TITLE "Roses" :ARTIST "Kattea" :RATING 7 :RIPPED T\)

CL-USER&gt; \(defvar \*db\* nil\)

\*DB\*

CL-USER&gt; \(defun add-record \(cd\) \(push cd \*db\*\)\)

ADD-RECORD

CL-USER&gt; \(add-record \(make-cd "Roses" "kathy" 7 t\)\)

\(\(:TITLE "Roses" :ARTIST "kathy" :RATING 7 :RIPPED T\)\)

CL-USER&gt; \*db\*

\(\(:TITLE "Roses" :ARTIST "kathy" :RATING 7 :RIPPED T\)\)

CL-USER&gt; \(format t "~a" "Dixie Chicks"\)

Dixie Chicks

NIL

CL-USER&gt; \(format t "~a" :title\)

TITLE

NIL

CL-USER&gt; \(defun dump-db \(\)

	   \(format t "~{~{~a: ~10t~a~%~}~%~}" \*db\*\)\)

DUMP-DB

CL-USER&gt; 



