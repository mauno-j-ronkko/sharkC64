# Language syntax

The syntax of the sharkC64 language is as follows

```
<module>             ::= "module" <LABEL> [<const-section>] [<var-section>] [<body>]

<const-section>      ::= "const" <const-declarations>
<const-declarations> ::= <const-declaration> [<const-declarations>]
<const-declaration>  ::= <LABEL> [":" <type>] <intial-value>

<var-section>        ::= "var" <var-declarations>
<var-declarations>   ::= <var-declaration> [<var-declarations>]
<var-declaration>    ::= <var-labels> <var-type>
<var-labels>         ::= <LABEL> ["," <var-labels>]
<var-type>           ::= <type-primitive> | <type-array>

<type-primitive>     ::= ":" <type-primitive> [<type-address>] [<intial-value>] |
                         [":" <type-address>] <intial-value>
<type-array>         ::= ":" <type-byte-array> [<type-address>] |
                         [":" <type-byte-array>] <intial-values>  
<type-address>       ::= "at" <expression>                      (1)
<type-byte-array>    ::= <type-byte> "[" <expression> "]"       (2) 
<type-primitive>     ::= <type-boolean> |                       (3) 
                         <type-byte> |                          (4)
                         <type-word>                            (5)
<type-boolean>       ::= "boolean"
<type-byte>          ::= "byte"
<type-word>          ::= "word"

<intial-values>      ::= ":=" "{" <initial-sequence> "}"        (6)
<intial-value>       ::= ":=" <expression>                      (6)
<initial-sequence>   ::= <expression> ["," <initial-sequence>]  (6)

<body>               ::= "begin" <statements> "end"
<statements>         ::= <statement> [<statements>]
<statement>          ::= <assignment> | <if-then-else> | <while-do> | ";"
<assignment>         ::= <LABEL> ":=" <expression> |
                         <byte-array-element> ":=" <expression>
                         <byte-array> ":=" [<array-modifiers>] <byte-array>
<if-then-else>       ::= "if" <expression> "then" <statements> ["else" <statements>] "end"  (7)
<while-do>           ::= "while" <expression> "do" <statements> "end"                       (7)

<expression>         ::= <operand> [<rhs-expression>]
<rhs-expression>     ::= <binary-operator> <unary-expression> [<rhs-expression>]
<unary-expression>   ::= "(" <expression> ")" | <unary-operator> <expression> | <operand> 
<operand>            ::= <byte-array-element> | <BOOLEAN-VALUE> |  (8)
                         <LABEL> | <BYTE-VALUE> | <WORD-VALUE>     (8)
<byte-array-element> ::= <byte-array> "[" <expression> "]"         (9)
<byte-array>         ::= <LABEL>                                   (10) 
<binary-operator>    ::= "-" | "+" | "and" | "or" | "xor" |        (11)
                         "<=" | "<" | "=" | "<>" | ">=" | ">"      (11) 
<unary-operator>     ::= "-" | "not" |                             (11)
                         "(byte)" | "(byte.lo)" | "(byte.hi)" |    (11)
                         "(word)" | "(word.lo)" | "(word.hi)" |    (11)
                         "(.length)"                               (11)
<array-modifiers>    ::= "(.up)" | "(.down)"                         
    
    
<LABEL>         is a letter followed by a sequence of letetrs and digits  (12) 
<BOOLEAN-VALUE> is a binary truth value {false, true}
<BYTE-VALUE>    is an 8-bit unsigned value in the range [0..255]    
<WORD-VAULUE>   is a 16-bit unsigned value in the range [0..65535]
```

1. `expression` must evaluate to a fixed `<WORD-VALUE>`.
2. `expression` must evaluate to a fixed value in the range `[1..256]`.
3. `<type-boolean>` evaluates to a fixed `<BOOLEAN-VALUE>`.
4. `<type-byte>` evaluates to a fixed `<BYTE-VALUE>`.
5. `<type-word>` evaluates to a fixed `<WORD-VALUE>`.
6. `expression` must match with the contextual type. 
   For instance, if the contextual type is `byte`, the expression must evaluate to a fixed `<BYTE-VALUE>`.
7. `expression` must be of `<type-boolean>` type.
8. `operand` must match with the contextual type.
9. `expression` must be of `<type-byte>` type.
10. `label` must denote a variable that is a byte array
11. `operator` must match with the contextual type.
12. Context may limit possible `label` values. For instance, in variable declaration, 
   each `label` must be unique within the defining scope. Also, a `label` denoting a variable
   in an expression must refer to a variable that matches with the contextual type. 

### Notes
- Single-line comment starting with `//` is not part of the language syntax.
  Lexer uses it to remove characters till the end of the line when tokenizing
  the source code.

<br /><br />
:leftwards_arrow_with_hook: [Back to index](../index.md)