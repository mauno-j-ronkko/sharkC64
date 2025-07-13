# Functions

Functions are defined after variable section and before the module initialization.
Each function starts with the keyword `fun` followed by the name of the function.
A function may have type parameters that are listed in parentheses after the function name.
A function can also return a value. 
Then, its type is a primitive type, and it is declared right after the parameter list. 
Functions may define constants and variables that are local to them.
The statements for the body of the function are then given within a `begin` ... `end` block.
```
fun hello(first: byte, second: word) : byte
    var c := 12 
begin
    c := c + a
    difference := first - (byte)second
    hello := difference + c
end
```

### Function parameters
Function parameters are defined in parentheses after the function name.
Parameters are separated with a comma and each parameter is given a type.
The type of a parameter must be a primitive type, i.e. `boolean`, `byte`, or `word`.  


### Return value
For a function, the type of the return value is declared after the 
function parameter declaration, separated with a colon.
For instance, in the example above, the type of the return value is `byte`.
A function defines automatically a variable for the return value.
The variable carries the name of the function.
So, to return some value from the function, the value is assigned to that variable.
For instance, in the example above, the value is `difference + c`
is returned from the function `hello` with the assignment `hello := difference + c`.
It should be noted that the variable for the return value is a real variable.
It can be assigned many values in the function; however, only the latest value
remains and is returned from the function.
Therefore, an assignment, `hello := hello + 1` is perfectly valid, 
causing an increment by one to the returned value.

Functions with return values can appear in expressions as operands.
For instance, `a + hello(12,1234) + 5` is valid expression.


### Forcing return from a function
The `return` statement can be used to return from a function at any time.
For instance, the following function exits as soon as it finds the
index for the given value in an array. If the index is not found, 
the function returns `-1`.
```
fun indexOf(value: byte) : byte
begin
    for indexOf := 0 to maxIndex do
      if array[indexOf] = value then return end
    end
    indexOf := -1
end
```


### Function variables
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
the difference of the two parameters each time the function is called.


### Function calls and call chaining
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


### Function calls and call chaining
The sharkC64 language supports also implicit setter functions that can be embedded in 
call chaining. In the sharkC64 language, all primitive variables have automatically 
generated setter functions. The setter functions have the same name as the variables.
When a setter function is called with a value, it simply assigns that value to the variable.
In fact, the setter function is mere syntactic sugar, and it is always translated
into a corresponding assignment statement with no actual function call at all.

Consider for instance the following statements:
```
ball.erase()
ball.row := 10
ball.column := 25
ball.draw(color.white)
```
Here, the `ball` module has two variables `row` and `column`. 
They are set in between the calls to the `ball` module functions.
With implicit setter functions, these statements can be expressed equivalently as:
```
ball.erase().row(10).column(25).draw(color.white)
```


<br /><br />
:leftwards_arrow_with_hook: [Back to index](../../index.md)