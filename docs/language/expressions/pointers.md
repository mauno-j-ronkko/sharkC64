# Byte pointers 

At the moment, the SharkC64 language supports only byte pointers.
A byte pointer is a variable that holds the memory address to an array of bytes.
It can be used for accessing bytes in memory locations directly.
It supports indexing as a byte array up to 256 bytes.
The design of a byte pointer is strongly influenced by the microprocessor architecture of the Commodore 64.


### Variable declaration
A byte pointer variable is declared in a `var` section just like any other variable.
A byte pointer can also be given a memory address at initialization.
```
var myPtr  : pointer
    screen := pointer($400)
    fixPtr : pointer at $1234
      
```

A byte pointer is defined by using the `pointer` keyword. 
The byte pointer is a 16-bit variable containing only a memory address.
The memory address can be given as an initial value, like above in `screen := pointer($400)`.
The value can be changed later with an assignment statement.
A byte pointer can also be set to a fixed memory address, as above in `fixPtr : pointer at $1234`.
Then, `fixPtr` is at the address `$1234` and it contains the pointed memory address.


### Setting the pointer address value
As a variable, a byte pointer is simply a 16-bit memory address.
The data type of byte pointer is `pointer`, and it can be assigned only a value of that type.
For the moment, there are no arithmetic operators for a pointer data type.
To assign a memory address to a pointer variable, typecast from a word value is required.
For instance, the following assignment sets the `screen` pointer to point to the screen data area at a
memory location `$400`.
```
screen := pointer($400)
```

Typecast from pointer to word can be used to compute a new address for a pointer variable based its current value.
For instance, the following assignment moves the `screen` pointer forward to a new location by 400 bytes.
```
screen := pointer(word(screen) + 400)
```

SharkC64 requires explicit use of typecast functions to avoid ambiguity.
Implicit typecasting would cause confusion and potential errors when mixing word values with pointer values.

There is a `@` operator that can be used to get the address of a variable as a pointer value.
So, the following example sets the address of a variable `myVar` to a pointer `myPtr`:
```
myPtr := @myVar
```


### Accessing byte values 
The `byte` value is accessed with a pointer by using indexes just like with byte arrays.
The index value is of `byte` data type, so its value must be in the range `[0..255]`.
For instance, `screen[0]` accesses the first byte pointed to by `screen`.
Likewise, `screen[255]` accesses the last byte pointed to by `screen`.
The index for a pointer has to be a valid `byte` valued expression.

Just like with byte arrays, assignment statement is used to change a `byte` value with a pointer.
For instance, the following assignment statement assigns the computed value `data[$01] + $F0` 
to the byte pointed to by `screen` at index `$02`.
```
  screen[$02] := data[$01] + $F0 
```

In an assignment statement, the right-hand side is computed first.
After that, the left-hand side index expression is computed.
Lastly, the computed right-hand side value is assigned to the byte pointer
element that has the computed left-hand side index value.


### Passing pointer values with functions
Pointers can be passed as parameters to functions just like any other primitive values.
A function can also return a pointer value just like a primitive value.

For instance, in the example below, there is a function that takes a pointer value
`passedPtr` and returns a new pointer value based on it. 
The returned value is obtained by advancing the current pointer value with 128 bytes.
Note that the function does not change the original pointer value of `passedPtr`.

```
fun advance(passedPtr: pointer) : pointer
    is  advance := pointer(word(passedPtr) + 128)
```


<br /><br />
:leftwards_arrow_with_hook: [Back to index](../../index.md)