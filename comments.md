#Comments

##Style
Students are taught that it's important to comment everything, Professional programmers are often required to comment all their code. But the purpose of commenting can be lost in blindly following rules. Comments are meant to help the reader of a program. They do not help by saying things the code already plainly says, or by contradicting the code, or by distracting the reader with elaborate typographical displays. Comments should not only agree with code, They should support it. The best comments aid the understanding of a  program by briefly pointing out salient details or by providing a larger-scale view of the proceedings.

*    **Reduce comments.** As much as possible, write code that is easy to understand; the better you do this, the fewer comments you need. Good code needs fewer comments than bad code. For several reasons:

   * If the code is clear, and uses good type names and variable names, it should explain itself.
	 
   * Comments aren't checked by the compiler, so there is no guarantee they're right, especially after the code is modified.  A misleading comment can be very confusing.
   * The issue of typography: comments clutter code.

*   **Don't belabor the obvious.**  Comments should add somethings that is not immediately evident from the code, or collect into one place information that is spread through the source.

*   **Say what it is for, not just what it does.** Comments can be useful for functions, global variables,constant definitions,and anythingelse where a brief summary can aid understanding. Global variables have tendency to crop up intermittently throughout a program, a comment serve as a reminder to be referred to as needed. Sometimes code is genuinely difficult, perhaps because the algorithm is complicated or the data structures are intricate. In this case, a comment that points to a source of understanding can aid the reader. It also be valuable to suggest **why** particular decisions were made, explain **why** it needs to be here.

*   **When change code, make sure the comments are still accurate.** 

----

##/* and // 
There are two ways to write a comment in Standard C. 

*    Traditionally, a comment begins with an occurrence of two characters **/\*** and ends with the first subsequent occurrence of the two character **\*/**. Comments may contain any number of characters and are always treated as whitespace.

*    Beginning with C99, a comment also begins with the characters **//** and extends up to (but does not include) the next line break.

Comments are not recognized inside string or character constants or within other comments, for example:

	    printf("%d //won't comment// is \n", i);

because of the **//** inside **" "**, they are regarded as characters. 

Standard C specifies that all comments are to be replaced by single space character for the purposes of translation of the C program, but the older implementations do not insert any whitespace.

###Nestable comments issue
A few non-Standard C implementations implement "nestable comments", but it is not standard, and programmers should not depend on it. Comments are sometimes used in other language to "comment out" code, thus removing the code from the program without physically deleting it from the source file. This practice is a bad idea in C, because it won't work if the code you're trying to get rid of has any comments in it. To cause the compiler to ignore large parts of a C program, it is best to enclose the parts to be removed with the preprocessor commands

        #if 0
		
   *statements*
		   
		#endif

the program statements between the **#if** and the **#endif** are effectively removed from the program. This avoids having to worry about **/*-style** comments in the statements. 
	

