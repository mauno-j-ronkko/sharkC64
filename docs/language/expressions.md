# Expressions

### Numbers
Shark recognizes decimal values, hexadecimal values, and binary values.
Hexadecimal values start with `$`, and binary values start with `%`.

### Operators
Shark supports all standard operators that are also supported by the processor.
Supported operators are listed below. 
An operator belonging to a precedence higher group in the table binds 
stronger than an operator belonging to a lower precedence group in the table.
  

| Operator | Precedence group | Type    | Description                   |
|:---------|:-----------------|:--------|:------------------------------|
| not      | 1                | unary   | Bitwise negation              |
| -        | 1                | unary   | Arithmetic negation           |
| +        | 2                | binary  | Arithmetic sum                |
| -        | 2                | binary  | Arithmetic subtraction        |
| and      | 3                | binary  | Bitwise conjunction           |
| or       | 4                | binary  | Bitwise disjunction           |
| xor      | 4                | binary  | Bitwise exclusive disjunction |

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
Shark has bottom-up type inference. 
The type of operator or its result is equal to the type of its operands. 
When operands have a different type, the lowest common type is used for
both of the operands, and for the result.
Type mismatch occurs if there is no lowest common type for the operands.

> :warning: &nbsp; Type inference is very limited at the moment,
> because `byte` is the only data type.
>

<br /><br />
:leftwards_arrow_with_hook: [Back to index](../index.md)