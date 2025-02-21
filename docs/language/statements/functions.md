# Functions

Functions are defined after variable section and before the module initialization.
Each function starts with the keyword `fun`.
The statements for the body of the function are then given within a `begin` ... `end` block.
```
fun hello() begin
    b := a
end
```

At the moment sharkC64 language supports only function bodies.
So, the functions are very limited, as they cannot define any parameters,
inner variables, or return type.

A function call is simply of the form `hello()` where `hello` is the name of the function.
Note that a function cannot be recursive, so it cannot call itself.
Functions can, however, call other functions even in other modules.
Module initialization are also permitted to call any functions.


<br /><br />
:leftwards_arrow_with_hook: [Back to index](../../index.md)