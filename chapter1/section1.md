# lisp eval程序

; SLIME 2011-02-04

CL-USER&gt; \(defun eval \(e a\)

	   \(cond 

	     \(\(atom e\) \(assoc e a\)\)

	     \(\(atom \(car e\)\)

	      \(cond

		\(\(eq \(car e\) 'quote\) \(cadr e\)\)

		\(\(eq \(car e\) 'atom\) \(atom \(eval \(cadr e\) a\)\)\)

		\(\(eq \(car e\) 'eq\) \(eq \(eval \(cadr e\) a\)

				      \(eval \(caddr e\) a\)\)\)

		\(\(eq \(car e\) 'car\) \(car \(eval \(cadr e\) a\)\)\)

		\(\(eq \(car e\) 'cons\) \(cons \(eval \(cadr e\) a\)

					  \(eval \(caddr e\) a\)\)\)

		\(\(eq \(car e\) 'cond\) \(evcon \(cdr e\) a\)\)

		\('t \(eval \(cons \(assoc \(car e\) a\)

				\(cdr e\)\)

			  a\)\)\)\)

	     \(\(eq \(caar e\) 'label\)

	      \(eval \(cons \(caddar e\) \(car e\)\) a\)\)\)

	   \(\(eq \(caar e\) 'lambda\)

	    \(append \(pair \(cadar e\) \(evlis \(cdr e\) a\)\)

		    a\)\)\)\)\)

\(defun evcon \(c a\)

 \(cond \(\(eval \(caar c\) a\)

	\(eval \(cadar c\) a\)\)

\('t \(evcon \(cdr c\) a\)\)\)\)

;Compiler warnings :

;   In EVCON: In the call to EVAL with arguments \(\(CAR \(CAR C\)\) A\),

;     2 arguments were provided, but at most 1 is accepted

;     by the current global definition of EVAL

;   In EVCON: In the call to EVAL with arguments \(\(CAR \(CDR \(CAR C\)\)\) A\),

;     2 arguments were provided, but at most 1 is accepted

;     by the current global definition of EVAL

EVCON

CL-USER&gt; \(defun evlis \(m a\)

	   \(cond \(\(null m\) '\(\)\)

		 \('t \(cons \(eval \(car m\) a\)

			   \(evlis \(cdr m\) a\)\)\)\)\)

;Compiler warnings :

;   In EVLIS: In the call to EVAL with arguments \(\(CAR M\) A\),

;     2 arguments were provided, but at most 1 is accepted

;     by the current global definition of EVAL

EVLIS

CL-USER&gt; 

; No value

CL-USER&gt; 

