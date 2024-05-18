# Expressions

### Boolean values
A Boolean value can be either `false` or `true`.

### Numbers
The sharkC64 language recognizes decimal values, hexadecimal values, and binary values.
Hexadecimal values start with `$`, and binary values start with `%`.
At the moment, a number can only be a byte value in the range [`$00` .. `$FF`]

### Operators
Shark supports all standard operators that are also supported by the processor.
Supported operators are listed below. 
An operator belonging to a higher precedence group in the table binds 
stronger than an operator belonging to a lower precedence group in the table.
  

| Operator  | Description              | Precedence | Arity   | Commutative | Operand type  | Result type  |
|:----------|--------------------------|:-----------|:--------|-------------|:--------------|:-------------|
| not       | Logical/bitwise negation | 4          | unary   | no          | boolean, byte | boolean/byte |
| -         | Negation                 | 4          | unary   | no          | byte          | byte         |
| +         | Sum                      | 3          | binary  | yes         | byte          | byte         |
| -         | Subtraction              | 3          | binary  | no          | byte          | byte         |
| <         | Less than                | 2          | binary  | no          | boolean, byte | boolean      |
| <=        | Less or equal to         | 2          | binary  | no          | boolean, byte | boolean      |
| =         | Equal to                 | 2          | binary  | no          | boolean, byte | boolean      |
| <>        | Not equal to             | 2          | binary  | no          | boolean, byte | boolean      |
| >=        | Greater or equal to      | 2          | binary  | no          | boolean, byte | boolean      |
| >         | Greater than             | 2          | binary  | no          | boolean, byte | boolean      |
| and       | Logical/bitwise and      | 1          | binary  | yes         | boolean, byte | boolean/byte |
| or        | Logical/bitwise or       | 0          | binary  | yes         | boolean, byte | boolean/byte |
| xor       | Logical/bitwise xor      | 0          | binary  | yes         | boolean, byte | boolean/byte |

<br />

> :warning: &nbsp; At the moment, multiplication and division are not supported.
> 


### Evaluation order
Generally, the evaluation order for the operators in an expression is from left to right.
However, there are exceptions to this:
1. Operators that bind stronger are evaluated first.
2. Expression in parentheses is evaluated before the binding operator.

For instance,
`a + b or -c + d`
is equal to an expression
`(a + b) or ((-c) + d)`.
If, however, disjunction needs to be evaluated before the sums,
it can be achieved by using parentheses:
`a + (b or -c) + d`

Although sharkC64 follows the left-to-right evaluation order for expressions while parsing them,
the optimization and simplification rules most likely change the computation order at run-time.
As long as expression operands have no side effects, the computation result is equivalent to
that computed using a strict left-to-right evaluation order.

The goal of the sharkC64 compiler is to produce compact and efficient byte code.
To do this, it first tries to simplify the expression by using static values and constants.
After that, the compiler compiles byte code instructions for the right-hand side expression 
before the left-hand side expression. This produces fewer instructions in general, 
as intermediate results can be used more effectively.


### Type inference
The sharkC64 compiler has a bottom-up type inference.
You can read more about the type inference in [Types](types.md) section. 

<br /><br />
:leftwards_arrow_with_hook: [Back to index](../../index.md)