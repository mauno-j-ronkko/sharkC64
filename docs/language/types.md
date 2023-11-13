# Types

Currently, there is only one data type: `byte`.
It defines a variable with an 8-bit value. Thus, its value must be in the range
`[$00 .. $FF]`.

### Type inference

sharkC64 has a bottom-up type inference.
The type of the operator or its result is equal to the type of its operands.
When operands have different types, the lowest common type is used for
both of the operands, and for the result.
Type mismatch occurs if there is no lowest common type for the operands.

> :warning: &nbsp; Type inference is very limited at the moment,
> because `byte` is the only data type.
>

Type inference is used with expressions. It is also used in variable declaration, 
where the type of the variable can be omitted if there is an initial value. 
The variable is then assigned the type inferred from the initial value.


<br /><br />
:leftwards_arrow_with_hook: [Back to index](../index.md)