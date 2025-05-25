# Functions

Functions are defined after variable section and before the module initialization.
Each function starts with the keyword `fun`.
Functions may define constants and variables that are local to them.
At the moment, the sharkC64 language does not support use of a return type.
The statements for the body of the function are then given within a `begin` ... `end` block.
```
fun hello(first: byte, second: word)
    var c := 12 
begin
    c := c + a
    difference := first - (byte)second
end
```

Function parameters are defined in parentheses after the function name.
Parameters are separated with a comma and each parameter is given a type.
The type of a parameter must be a primitive type, i.e. `boolean`, `byte`, or `word`.  

Unlike in many other programming languages, the functions in sharkC64 are _stateful_.
This means that the variables that defined locally in functions retain their
value from one function call to the next. 
In particular, this means that initial values defined in the variable declaration
are established only for the first call of the function. 
For instance, in the example above, the variable `c` has initially the value `12`.
After the first function call the value of `c` is `12 + a`.
In effect, the function above adds the value of `a` to the value of `c` each time
the function is called.

Functions may also change the values of module variables.
For instance, in the example above, the module variable `difference` is assigned
teh difference of the two parameters each time the function is called.


## Function calls

A function call is simply of the form `hello(1, 4096)`, 
where `hello` is the name of the function and the arguments are listed in parentheses.
The argument types must match with the parameter types in the function declaration.

Note that a function cannot be recursive, so it cannot call itself.
Functions can, however, call other functions even in other modules.
Module initialization are also permitted to call any functions.

Function calls can be chained by using a period `.` between the function calls. 
For instance, the following chained function calls refer all to the same `ball` module.
```
ball.erase().moveToLeft().draw(color.white)
```


<br /><br />
:leftwards_arrow_with_hook: [Back to index](../../index.md)