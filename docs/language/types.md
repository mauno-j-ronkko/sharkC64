# Types

Currently, there are two data types: `boolean` and `byte`.

| Type       | Description    | Range             | Default initial value |
|------------|----------------|-------------------|-----------------------|
| `boolean`  | A truth value  | {`false`, `true`} | `false`               |
| `byte`     | An 8-bit value | [`$00` .. `$FF`]  | `0`                   |



### Type inference
Type inference is used with expressions. 
It is also used when declaring a constant or a variable with an initial value.
Then, the type of the identifier can be inferred from the initial value.

The sharkC64 compiler has a bottom-up type inference. When analyzing the syntax tree of an expression,
there are always operands at the bottom of the expression tree. 
Operands always have either a predetermined type, or their type can be inferred from the value.
Therefore, the type of the operator is determined by the type of its operands.
If the operands have different types, the lowest common type is used for the operator.
Type mismatch occurs if there is no lowest common type for the operands.
Moreover, the expression is considered illegal 
if the operator does not apply to the type of the operators.

Some operators may have a result type that is different form the type of the operands.
For instance, comparisons result always in a boolean type.
As an example, when byte values are compared, the result is a boolean value indicating
if the comparison holds between the byte values.

<br /><br />
:leftwards_arrow_with_hook: [Back to index](../index.md)