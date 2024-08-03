# Variables
Variables are listed in a `var` section. Variables with the same type can
be listed together by separating them with a comma.
A variable can also be given a static address and an initial value.
```
var  a, b, c : byte
     zero := $00
     corner : byte at $400 := zero + $01
```

Each variable must have a unique name. In sharkC64, all the names are case-sensitive.
The type of the variable must also be given, unless the type of the variable 
can be inferred from its initial value. For instance, above, the type of the
variable `zero` is `byte` as that is the type of the initial value `$00`.


### Memory allocation
Variables are normally allocated memory based on the type. Allocation is dynamic.
It is, however, possible to give a static address to a variable,
see the variable `corner` in the example above.
The static address must resolve to a `word` data type, having the value in the range `[$0000 .. $FFFF]`.

Two or more variables may refer to the same memory location. Then, however, the compiler issues a warning.
If there are several variables referring to the same memory location,
special care must be taken in assigning values to those variables.
Assigning a value to one variable with a static address is immediately reflected
in the value of the other variable with the same static address.


### Initial value
A variable can be given an initial value. The initial value must conform to
the data type of the variable. The initial value can be an expression, as long as it
simplifies to a fixed value with a correct data type. The expression may also
refer to previously declared variables that have initial values.

If an initial value is not given, the variable is initialized a "zero" value. 
In the case of a byte, for instance, the zero value is `0`.
There is one exception to initialization, however. If the variable is given 
a static address without an initial value, the variable will not be initialized at all.
Then, the initial value of the variable is whatever value happens to be in that
memory location when the variable is accessed.

<br /><br />
:leftwards_arrow_with_hook: [Back to index](../../index.md)