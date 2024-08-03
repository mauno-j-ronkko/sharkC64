# Expressions

### Boolean values
A Boolean value can be either `false` or `true`.


### Numbers
The sharkC64 language recognizes decimal values, hexadecimal values, and binary values.
Hexadecimal values start with `$`, and binary values start with `%`.
A number value can be in the range [`$0000` .. `$FFFF`]. 
The data type of a value bigger than `$FF` is always a `word`.
The data type of a value in the range [`$00` .. `$FF`] can be either a `byte` or a `word`.
For such values, the program context defines the exact data type.


### Operators
The sharkC64 language supports all standard operators that are also supported by the processor.
Supported operators are listed below. 
An operator belonging to a higher precedence group in the table binds 
stronger than an operator belonging to a lower precedence group in the table.
In the table, (any) means any of the data types `boolean`, `byte` or `word`.
Also, (operand) means that the result data type is the same as the operand data type. 
  

| Operator | Description              | Precedence | Arity   | Commutative | Operand type    | Result type |
|:---------|--------------------------|:-----------|:--------|-------------|:----------------|:------------|
| `not`    | Logical/bitwise negation | 4          | unary   | no          | (any)           | (operand)   |
| `-`      | Negation                 | 4          | unary   | no          | `byte`, `word`  | (operand)   |
| `+`      | Sum                      | 3          | binary  | yes         | `byte`, `word`  | (operand)   |
| `-`      | Subtraction              | 3          | binary  | no          | `byte`, `word`  | (operand)   |
| `<`      | Less than                | 2          | binary  | no          | (any)           | `boolean`   |
| `<=`     | Less or equal to         | 2          | binary  | no          | (any)           | `boolean`   |
| `=`      | Equal to                 | 2          | binary  | no          | (any)           | `boolean`   |
| `<>`     | Not equal to             | 2          | binary  | no          | (any)           | `boolean`   |
| `>=`     | Greater or equal to      | 2          | binary  | no          | (any)           | `boolean`   |
| `>`      | Greater than             | 2          | binary  | no          | (any)           | `boolean`   |
| `and`    | Logical/bitwise and      | 1          | binary  | yes         | (any)           | (operand)   |
| `or`     | Logical/bitwise or       | 0          | binary  | yes         | (any)           | (operand)   |
| `xor`    | Logical/bitwise xor      | 0          | binary  | yes         | (any)           | (operand)   |

> :warning: &nbsp; At the moment, multiplication and division are not supported.
> 


### Type inference and type casting
The sharkC64 compiler has a bottom-up type inference.
You can read more about the type inference in [Types](types.md) section.
The sharkC64 compiler does not perform any type casting automatically. It must be given 
explicitly by the programmer. For this purpose, there are the following unary operators.


| Operator    | Description                               | Precedence | Operand type | Result type |
|:------------|-------------------------------------------|:-----------|:-------------|:------------|
| `(byte)`    | Cast low byte of `word` value to `byte`   | 4          | `word`       | `byte`      |
| `(byte.lo)` | Cast low byte of `word` value to `byte`   | 4          | `word`       | `byte`      |
| `(byte.hi)` | Cast high byte of `word` value to `byte`  | 4          | `word`       | `byte`      |
| `(word)`    | Cast `byte` value to low value of `word`  | 4          | `byte`       | `word`      |
| `(word.lo)` | Cast `byte` value to low value of `word`  | 4          | `byte`       | `word`      |
| `(word.hi)` | Cast `byte` value to high value of `word` | 4          | `byte`       | `word`      |


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

The goal of the sharkC64 compiler is to produce compact and efficient bytecode.
To do this, it first tries to simplify the expression by using fixed values and constants.
With fixed values and constants, the sharkC64 compiler can precompute the expression at 
compile time. Then, the resulting fixed value us used directly in the bytecode.
After that, the compiler compiles bytecode instructions for the right-hand side expression 
before the left-hand side expression. This produces fewer instructions in general, 
as intermediate results can be used more effectively.


<br /><br />
:leftwards_arrow_with_hook: [Back to index](../../index.md)