# Language syntax

The syntax of the sharkC64 language is as follows

```
<module>             ::= "module" <LABEL> 
                         [<use-section>] [<const-section>] [<var-section>] [<body>]

<use-section>        ::= "use" <module-list>
<module-list>        ::= <LABEL> ["," <module-list>]             (1)

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
<type-address>       ::= "at" <expression>                      (2)
<type-byte-array>    ::= <type-byte> "[" <expression> "]"       (3) 
<type-primitive>     ::= <type-boolean> |                       (4) 
                         <type-byte> |                          (5)
                         <type-word>                            (6)
<type-boolean>       ::= "boolean"
<type-byte>          ::= "byte"
<type-word>          ::= "word"

<intial-values>      ::= ":=" "{" <initial-sequence> "}"        (7)
<intial-value>       ::= ":=" <expression>                      (7)
<initial-sequence>   ::= <expression> ["," <initial-sequence>]  (7)

<body>               ::= "begin" <statements> "end"
<statements>         ::= <statement> [<statements>]
<statement>          ::= <assignment> | <if-then-else> | <while-do> | ";"
<assignment>         ::= <LABEL> ":=" <expression> |
                         <byte-array-element> ":=" <expression>
                         <byte-array> ":=" [<array-modifiers>] <byte-array>
<if-then-else>       ::= "if" <expression> "then" <statements> ["else" <statements>] "end"  (8)
<while-do>           ::= "while" <expression> "do" <statements> "end"                       (8)

<expression>         ::= <operand> [<rhs-expression>]
<rhs-expression>     ::= <binary-operator> <unary-expression> [<rhs-expression>]
<unary-expression>   ::= "(" <expression> ")" | <unary-operator> <expression> | <operand> 
<operand>            ::= <byte-array-element> | <BOOLEAN-VALUE> |  (9)
                         <LABEL> | <BYTE-VALUE> | <WORD-VALUE>     (9)
<byte-array-element> ::= <byte-array> "[" <expression> "]"         (10)
<byte-array>         ::= <LABEL>                                   (11) 
<binary-operator>    ::= "-" | "+" | "and" | "or" | "xor" |        (12)
                         "<=" | "<" | "=" | "<>" | ">=" | ">"      (12) 
<unary-operator>     ::= "-" | "not" |                             (12)
                         "(byte)" | "(byte.lo)" | "(byte.hi)" |    (12)
                         "(word)" | "(word.lo)" | "(word.hi)" |    (12)
                         "(.length)"                               (12)
<array-modifiers>    ::= "(.up)" | "(.down)"                         
    
    
<LABEL>         is a letter followed by a sequence of letetrs and digits  (13) 
<BOOLEAN-VALUE> is a binary truth value {false, true}
<BYTE-VALUE>    is an 8-bit unsigned value in the range [0..255]    
<WORD-VAULUE>   is a 16-bit unsigned value in the range [0..65535]
```

1. `<LABEL>` must refer to an existing module with that name 
2. `expression` must evaluate to a fixed `<WORD-VALUE>`.
3. `expression` must evaluate to a fixed value in the range `[1..256]`.
4. `<type-boolean>` evaluates to a fixed `<BOOLEAN-VALUE>`.
5. `<type-byte>` evaluates to a fixed `<BYTE-VALUE>`.
6. `<type-word>` evaluates to a fixed `<WORD-VALUE>`.
7. `expression` must match with the contextual type. 
   For instance, if the contextual type is `byte`, the expression must evaluate to a fixed `<BYTE-VALUE>`.
8. `expression` must be of `<type-boolean>` type.
9. `operand` must match with the contextual type.
10. `expression` must be of `<type-byte>` type.
11. `<LABEL>` must denote a variable that is a byte array
12. `operator` must match with the contextual type.
13. Context may limit possible `<LABEL>` values. For instance, in variable declaration, 
   each `<LABEL>` must be unique within the defining scope. Also, a `<LABEL>` denoting a variable
   in an expression must refer to a variable that matches with the contextual type. 

### Notes
- Single-line comment starting with `//` is not part of the language syntax.
  Lexer uses it to remove characters till the end of the line when tokenizing
  the source code.

<br /><br />
:leftwards_arrow_with_hook: [Back to index](../index.md)