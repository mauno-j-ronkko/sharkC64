# Constants

Constants are listed in a `const` section. Each constant must be given a fixed value.
```
const zero : byte := $00
      one  : zero + $01
```

Each constant must also have a unique name. In the sharkC64 language, all the names are case-sensitive.
The type of the constant must also be given, unless the type
can be inferred from the fixed value. For instance, above, the type of the
constant `one` is `byte` as that is the type of the value `zero + $01`.
Constants are treated as literal values during the compile time. No fixed memory is allocated for them.


### Fixed value
The fixed value must conform to the data type of the constant. 
The fixed value can be an expression, as long as it simplifies to a fixed value with a correct data type. 
The expression may also refer to previously declared constants.

<br /><br />
:leftwards_arrow_with_hook: [Back to index](../../index.md)