# Types

These are the currently available data types:

| Type      | Description           | Range                | Default initial value |
|-----------|-----------------------|----------------------|-----------------------|
| `boolean` | Truth value           | {`false`, `true`}    | `false`               |
| `byte`    | 8-bit unsigned value  | [`$00` .. `$FF`]     | `0`                   |
| `word`    | 16-bit unsigned value | [`$0000` .. `$FFFF`] | '0'                   |



### Type inference
Type inference is used with expressions. 
It is also used when declaring a constant or a variable with an initial value.
Then, the type of the identifier can be inferred from the initial value.

The sharkC64 compiler has a bottom-up type inference. When analyzing the syntax tree 
of an expression, there are always operands at the bottom of the expression tree. 
The operands have either a predetermined type, or their type can be inferred from 
the value. Therefore, the type of the operator is determined by the type of its operands.
If the operands have different types, the lowest common type is used for the operator.
Type mismatch occurs if there is no lowest common type for the operands.
Moreover, the expression is considered illegal if the operator does not apply 
to the type of the operators.

Some operators may have a result type that is different from the type of the operands.
For instance, comparisons result always in a boolean type.
As an example, when byte values are compared, the result is a boolean value indicating
if the comparison holds between the byte values.

Note that there is not automatic type casting between data types. 
The programmer must give any type casting explicitly, see [Expressions](expressions.md). 

### Performance consideration
The microprocessor of the Commodore 64, MOS Technology 6510, is an 8-bit microprocessor.
It can natively operate only on 8-bit values. Because of this, the microprocessor
provides native instructions for handling the `boolean` and the `byte` data type.
This means that the 16-bit `word` data type requires use of multiple instructions that
swap intermediate computational values in and out of the 8-bit accumulator of the
6510 microprocessor. Therefore, the expressions with the `word` data type are
significantly slower than, for instance, similar expressions with the `byte` data type. 

> :warning: &nbsp; Assigning a word value from one variable to another,
> partially overlapping variable could fail. The failure occurs when the low byte
> of the target variable is at the same address as the high byte of the source variable.
> Then, the low byte value is first copied over the high byte value overwriting the
> correct high byte value. As a result, both the source and the target variables get 
> corrupted having the low byte value also as their high byte value.
> Because of this, **partially overlapping variables (with word data type) 
> should be avoided.**
>


<br /><br />
:leftwards_arrow_with_hook: [Back to index](../../index.md)