#Variable
There are two concepts hiding behind the word *"variable"*:
*   The identifier.
*   The store variable. This is what the system uses to calulate with. It is part of system's memory, which we call its store.

Imperative programming languages are, to varying degrees, abstractions of the underlying von Neumann computer architecture. The architecture's two primary components are its memory, which stores both instructions and data, and its processor, which provides operations for modifying the contents of the memory. The abstractions in a language for the memory cells of the machine are variables. The attributes of *variable*, including *type*, *address*, and *value*.

The *name* is a string of characters used to identify some entity in a program.

The *address* of a variable is the machine memory address with which it is associated.

The *type* of a variable determins the range of values the variable can store and the set of operations that are defined for values of the type.

The *value* of a variable is the contents of the memory cell or cells associated with the variable.

A *binding* is an association between an attribute and an entity. The time at which a blinding takes place is called *blinding time*.

An *object* is a region of memory with a *type* that specifies what kind of information can be placed in it. A named object is called *variable*. You can think of an object as a "box" into which you can put a value of the object's type. The "places" in which we store data are called *object*, To access an object we need a *name*. A named object is called a *variable* and has a specific *type* that determins what can be put into the object and which operations can be applied. The data items we put into variables are called *values". 

A statement that introduced a new name into program and sets aside memory for a variable is called a *definition*.

##Types and objects
The notion of types is central to C++ and most other programming languages. 

*   A *type* defines a set of possible values and a set of operations(for an object).
*   An *object* is some memory that holds a value of a given type.
*   A *value* is a set of bits in memory interpreted according to a type.
*   A *variable* is a named object.
*   A *declaration* is a statement that gives a name to an object.
*   A *definition* is a declaration that sets aside memory for an object.

The meaning of bits in memory is completely dependent in the type used to access it. Computer memory doesn't know about our types, it just memory. The bits of memory get meaning only when we decide how that memory is to be interpreted.

##Parameter passing mechanisms

Consider how the *actual parameters* (the parameters used in the call of a procedure) are associated with the *formal parameters* (those used in the procedure definition). Which mechanism is used determines how the calling-sequence code treats parameters.

###Call-by-Value
In call-by-value, the actual parameter is evaluated(if it is an expression) or copied (if it is a variable). The value is placed in the location belonging to the corresponding formal parameter of the called procedure. Call-by-value has effect that all computation involving the formal parameters done by the called procedure is local to that procedure, and the actual parameters themselves cannot be changed.

###Call-by-Reference
In call-by-reference, the address of the actual parameter is passed to the callee as the value of the corresponding formal parameter. Uses of the formal parameter in the code of the callee are implemented by following this pointer to location indicated by the caller. Changes to the formal parameter thus appear as changes to actual parameter.

If the actual parameter is an expression, however, then the expression is evaluated before the call, and its value stored in a location if its own. Changes to formal parameter change this location, but can have no effect on the data of the caller.

C provides only call-by-value parameter passing. Note, however, that in C we can pass a pointer to a variable to allow that variable to be changed by the callee.

In C, array arguments behave as though they are passed by *reference*, and scalar variables and constants are passed by *value*. Thus, any changs made by function cannot change the value of calling program's argument in this manner. When a function changes the value of an element of an array argument, however, the array in the calling program is actually modified.

##Style

A variable or function name labels an object and conveys information about its purpose. Much information comes from context and scope; the broader the scope of a variable, the more information should be conveyed by its name.

*   Use descriptive names for globals, short names for locals.

*   Be consistent. Give related things related names that show their relationship and highlight their difference.


*   Be accurate. A name not only labels, it conveys information to the reader. A misleading name can result in mystifying bugs.
