#Style philosophy

What follows is a set of short essays that collectively encourage a philosophy of clarity in programming rather than giving hard rules.

Under no circumstances should you program the way I say to because I say to; program the way you think expresses best what you're trying to accomplish in the program.

Typographic conventions consistently held are important to clear presentation.

Say what you want to say in the program, neatly and consistently.  Then move on. 

This is largely a matter of taste, but taste is relevant to clarity. 

##procedure names
 Procedure names should reflect what they do; function names should reflect what they return.  Functions are used in expressions, often in things like if's, so they need to read appropriately. 
 
        if(checksize(x))

is unhelpful because we can't deduce whether checksize returns true on error or non­error; instead

        if(validsize(x))

makes the point clear and makes a future mistake in using the routine less likely. 

------
#Programming with data
Rule 5.  Data dominates.  If you've chosen the right data structures and organized things well, the algorithms will almost always be self­evident.  Data structures, not algorithms, are central to programming.  (See Brooks p. 102.) 

------
#Function pointers
Another result of the tyranny of Pascal is that beginners don't use function pointers.  (You can't have function­valued variables in Pascal.) Using function pointers to encode complexity has some interesting properties.

Some of the complexity is passed to the routine pointed to.  The routine must obey some standard protocol - it's one of a set of routines invoked identically - but beyond that, what it does is its business alone.  The complexity is distributed.

There is this idea of a protocol, in that all functions used similarly must behave similarly.  This makes for easy documentation, testing, growth and even making the program run distributed over a network - the protocol can be encoded as remote procedure calls.

I argue that clear use of function pointers is the heart of object­oriented programming.  Given a set of operations you want to perform on data, and a set of data types you want to respond to those operations, the easiest way to put the program together is with a group of function pointers for each type.  This, in a nutshell, defines class and method.  The O­O languages give you more of course - prettier syntax, derived types and so on - but conceptually they provide little extra.

Combining data­driven programs with function pointers leads to an astonishingly expressive way of working, a way that, in my experience, has often led to pleasant surprises. Even without a special O­O language, you can get 90% of the benefit for no extra work and be more in control of the result.  I cannot recommend an implementation style more highly.  All the programs I have organized this way have survived comfortably after much development - far better than with less disciplined approaches.  Maybe that's it: the discipline it forces pays off handsomely in the long run. 

------
#Include files
Simple rule: include files should never include include files. 

 There's a little dance involving #ifdef's that can prevent a file being read twice, but it's usually done wrong in practice - the #ifdef's are in the file itself, not the file that includes it.  The result is often thousands of needless lines of code passing through the lexical analyzer, which is (in good compilers) the most expensive phase. 

------

#Comments
##style
Students are taught that it's important to comment everything, Professional programmers are often required to comment all their code. But the purpose of commenting can be lost in blindly following rules. Comments are meant to help the reader of a program. They do not help by saying things the code already plainly says, or by contradicting the code, or by distracting the reader with elaborate typographical displays. Comments should not only agree with code, They should support it. The best comments aid the understanding of a  program by briefly pointing out salient details or by providing a larger-scale view of the proceedings.

*    **Eliminate comments.** As much as possible, write code that is easy to understand; the better you do this, the fewer comments you need. Good code needs fewer comments than bad code. For several reasons:

   * If the code is clear, and uses good type names and variable names, it should explain itself.
	 
   * Comments aren't checked by the compiler, so there is no guarantee they're right, especially after the code is modified.  A misleading comment can be very confusing.
   * The issue of typography: comments clutter code.

*   **Don't belabor the obvious.**  Comments should add somethings that is not immediately evident from the code, or collect into one place information that is spread through the source.

*   **Comment functions and global data.** Global variables have tendency to crop up intermittently throughout a program, a comment serve as a reminder to be referred to as needed. Sometimes code is genuinely difficult, perhaps because the algorithm is complicated or the data structures are intricate. In this case, a comment that points to a source of understanding can aid the reader. It may also be valuable to suggest **why** particular decisions were made.

*   **When change code, make sure the comments are still accurate.** 

There are two ways to write a comment in Standard C. 

*    Traditionally, a comment begins with an occurrence of two characters **/\*** and ends with the first subsequent occurrence of the two character **\*/**. Comments may contain any number of characters and are always treated as whitespace.

*    Beginning with C99, a comment also begins with the characters **//** and extends up to (but does not include) the next line break.

Comments are not recognized inside string or character constants or within other comments, for example:

	    printf("%d //won't comment// is \n", i);

the **//** inside**""**, not a comment. Standard C specifies that all comments are to be replaced by single space character for the purposes of translation of the C program, but the older implementations do not insert any whitespace.

##Nestable comments issue
A few non-Standard C implementations implement "nestable comments", but it is not standard, and programmers should not depend on it. Comments are sometimes used in other language to "comment out" code, thus removing the code from the program without physically deleting it from the source file. This practice is a bad idea in C, because it won't work if the code you're trying to get rid of has any comments in it. To cause the compiler to ignore large parts of a C program, it is best to enclose the parts to be removed with the preprocessor commands

	    #if 0
			statements
	    #endif

the program statements between the **#if** and the **#endif** are effectively removed from the program. This avoids having to worry about **/*-style** comments in the statements. 
	

