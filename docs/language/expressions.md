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
An operator belonging to a precedence higher group in the table binds 
stronger than an operator belonging to a lower precedence group in the table.
  

| Operator | Precedence | Type    | Boolean                     | Number                 |
|:---------|:-----------|:--------|-----------------------------|:-----------------------|
| not      | 1          | unary   | Logical negation            | Bitwise negation       |
| -        | 1          | unary   | N/A                         | Arithmetic negation    |
| +        | 2          | binary  | N/A                         | Arithmetic sum         |
| -        | 2          | binary  | N/A                         | Arithmetic subtraction |
| and      | 3          | binary  | Logical conjunct            | Bitwise "and"          |
| or       | 4          | binary  | Logical disjunct            | Bitwise "or"           |
| xor      | 4          | binary  | Logical exclusive disjunct  | Bitwise "exclusive or" |

<br />

> :warning: &nbsp; At the moment, multiplication and division are not supported.
> 


### Evaluation order
Expressions are evaluated from left to right. There are two exceptions to this:
1. Operators that bind stronger are evaluated first
2. Expression in parentheses is evaluated before the binding operator

For instance, 
`a + b or -c + d`
is equal to an expression 
`(a + b) or ((-c) + d)`. 
If, however, disjunction needs to be evaluated before the sums, 
it can be achieved by using parentheses:
`a + (b or -c) + d`

### Type inference
The sharkC64 compiler has a bottom-up type inference.
You can read more about the type inference in [Types](types.md) section. 

<br /><br />
:leftwards_arrow_with_hook: [Back to index](../index.md)