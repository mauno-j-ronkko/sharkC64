# Assignment statements

Assignment statement computes the value of an expression and stores it to
the given variable.
```
corner := (char + attributes) and bitFilter 
```

In an assignment statement, the type of the variable must match with the 
result type of the expression. In other words, if the expression returns
a result value of type `byte`, the variable must also be of type `byte`.


### Increments and decrements
The sharkC64 compiler recognizes and optimizes two special cases: increments and decrements.
If an assignment increments the value of a variable by one, it will be computed by
using the increment instruction of the microprocessor. 
The same applies to an assignment statement that decrements the values of a variable by one.
Fo instance, the following assignment statement for a `byte` variable `x` gets 
compiled into a single increment instruction:
```
  x := x + 1 
```


### Assignment of arrays and array elements
The value of a byte array element can also be changed by using an assignment statement.
For instance, the following assignment statement sets the value of a byte array element
at index `$02` to be the sum of the byte array element at index `$01` plus `$F0` for
a byte array called `data`.
```
  data[$02] := data[$01] + $F0 
```

The sharkC64 language supports also the assignment of one-dimensional byte arrays.
For instance, the following assignment statement copies all the values from
an array called `source` to an array called `target`.
```
  target := source 
```

The assignment of arrays and arrays elements is discussed in more detail 
in the [Byte array](../expressions/arrays.md) section.

<br /><br />
:leftwards_arrow_with_hook: [Back to index](../../index.md)