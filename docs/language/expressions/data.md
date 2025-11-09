# Data
Data elements are listed in a `data` section. 
Each data element defines a sequence of bytes starting at a fixed memory location.
```
data numbers at $1000 := {1, 2, 3, 4}
```

Each data element must have a unique name and a starting address.
The byte sequence then defines both the content and the length of the data element.

### Name
The name of the data element is treated as a constant in the program.
Its value is the given memory address.

### Memory address
The memory address of the data element is the starting location of the byte sequence in the memory.
Currently, the starting address is limited to be in the range `[$0811..$A000]`.
In addition, no two data elements may overlap in memory.
This means, in particular, that the starting address must not fall within some other data element.

### Byte sequence
The byte sequence of the data element is also limited.
Each value in the byte sequence must be of `byte` data type, having the value in the range `[$00 .. $FF]`.
Moreover, all bytes of the data element must fall within the range of allowed memory addresses `[$0811..$A000]`.
So, for instance, the following definition is illegal, as the byte sequence spans outside the allowed memory range.
```
data outsideOfMemory at $9FFF := {1, 2, 3, 4}
```

Lastly, no bytes in the byte sequence may overlap in memory with bytes of any other data elements.
So, for instance, the following definitions are illegal, as they overlap in memory.
```
data firstSequence       at $1000 := {1, 2, 3, 4}
     overlappingSequence at $1002 := {5, 6, 7, 8}
```

### Accessing bytes in data sequence
The data element is intentionally limited to define a static byte sequence at a fixed memory location
without any structure for accessing it. 
In this way, you can define for instance bitmap data that is read only by the graphics chip,
and you do not need to worry about changing it accidentally in the program.

However, if you wish to access the byte values in a data element, you can define an array to do so.
Then, you can also define the array structure to access the data element.
Consider the following definitions.
```
data sequence at $1000 := {10, 11, 20, 21}
var  value : byte[2, 2] at sequence  
```

Here, the `value` variable is defined to access the byte values in the data element called `sequence`
as a two-dimensional array. For instance, the value of `value[1, 0]` in the above example is `20`.


<br /><br />
:leftwards_arrow_with_hook: [Back to index](../../index.md)