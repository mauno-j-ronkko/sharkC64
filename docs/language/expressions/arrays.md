# Byte arrays

At the moment, the sharkC64 language supports only byte arrays. A byte array is an array 
whose elements are bytes. Furthermore, the length of a byte array is limited 
to 256 elements. Working with such an array is supported by the microprocessor 
of the Commodore 64. 

### Variable declaration
A byte array variable is declared in a `var` section just like any other variable.
A byte array can also be given a static memory address.
```
var  data      : byte[$10]
     hello     := {8, 5, 12, 12, 15}
     screenRow : byte[$28] at $400 
```

A byte array is given a length. A byte array must have at least one element, and
it cannot have more than 256 elements. Therefore, the length of a byte array
must be in the range `[1..256]` .

If a byte array is not given a static memory location, the sharkC64 compiler will
allocate as many bytes from the memory for it as its length states.
Moreover, the allocated memory is initialized with zero values.
This means that, for instance, the value of `data[$05]` in the above example is 
set to `0` initially, and it will remain `0` as long as no other value is assigned to it.

A byte array without a static memory location can be given initial values. 
Then, the sharkC64 compiler infers the length of the byte array. 
If the length is explicitly given for the array, it must agree with the number of the initial values.
When a byte array is given initial values, the allocated memory is initialized
with them instead of the default zero values.
This means that, for instance, the value of `hello[$01]` in the above example is
set to `5` initially, and it will remain `5` as long as no other value is assigned to it.

If a byte array is given a static memory location, the sharkC64 compiler will
not allocate any memory for it, and it will not be initialized to any value either.
Then, its first element is found at the memory address, and the rest of the
elements in the byte array are found in the following memory locations.
This means that, for instance, the value of `screenRow[$15]` in the above example 
has whatever value happens to be at the memory location `$400 + $15` at that moment.


### In expressions

Byte array elements can appear in expressions just like any other variables.
They are checked for type consistency and the resulting byte code is optimized for 
performance. In particular, this means that a byte array element can appear in an
index expression of another byte array element. So, an expression like
`data[screen[$12]]` is perfectly valid.

The first element in a byte array has the index value `0`, and the last element 
has the index `length - 1`, where `length` is the length of the byte array.

It should be noted, however, that there is no index value range check during run-time.
So, for instance, if the value of a variable `i` is `$12`and the length of a byte array 
`data` is only `$10` bytes, the expression `data[i]` gets evaluated in run-time without
any error messages.  Still, the compiler does perform a static range check 
during compile time. Therefore, a similar expression `data[$12]` will not
compile, if the length of a byte array `data` is only `$10` bytes.

The length of an array can be obtained also by using `(.length)` unary operator.
The returned length of an array is either of type `byte` or of type `word`
depending on the returned value. As an example, `(.length)data` returns the
length of a byte array called `data`, which for the declaration example above would 
thus return `$10`.


### Assigning a value to an element

The value of a byte array element can be changed by using an assignment statement.
In the assignment statement, a byte array element behaves just like any other variable.
For instance, the following assignment statement sets the value of a byte array element
at index `$02` to be the sum of the byte array element at index `$01` plus `$F0` for 
a byte array called `data`.
```
  data[$02] := data[$01] + $F0 
```

In an assignment statement, the right-hand side is computed first. 
After that, the left-hand side index expression is computed.
Lastly, the computed right-hand side value is assigned to the byte array
element that has the computed left-hand side index value.


### Array assignment

It is also possible to copy all the values of an array to another array. 
This is called array assignment. The only condition for array assignment is that the
source array does not have more elements than the target array.
For instance, the following assignment statement copies all the values from
an array called `source` to an array called `target`.
```
  target := source 
```

By default, the array assignment copies element values from one array to another 
by starting from the first index and ending at the last index. This order works
correctly in most of the cases. However, if the arrays overlap and the source array
start before the target array in the memory, this order of copying can cause artifacts. 
For this purpose, we can use array modifiers `(.up)` or `(.down)`. 
The `(.up)` modifier corresponds to the default order of copying that
starts from the first index and ends at the last index.
The `(.down)` modifier corresponds the order of copying that
starts from the last index and ends at the first index.
As an example, the following example copies all the values from the `source` array to 
the `target` array starting from the last index and ending at the first index.
```
  target := (.down)source 
```

<br /><br />
:leftwards_arrow_with_hook: [Back to index](../../index.md)