# Language syntax

The syntax of the sharkC64 language is as follows

```
<module>                ::= "module" <LABEL> 
                            [<use-section>] [<const-section>] [<var-section>] 
                            [<fun-section>] [<body>]

<use-section>           ::= "use" <module-list>
<module-list>           ::= <LABEL> ["," <module-list>]                     (1)

<fun-section>           ::= <fun-declaration> [<fun-section>]
<fun-declaration>       ::= "fun" <LABEL> "()" <body>

<const-section>         ::= "const" <const-declarations>
<const-declarations>    ::= <const-declaration> [<const-declarations>]
<const-declaration>     ::= <LABEL> [":" <type>] <intial-value>

<var-section>           ::= "var" <var-declarations>
<var-declarations>      ::= <var-declaration> [<var-declarations>]
<var-declaration>       ::= <var-labels> <var-type>
<var-labels>            ::= <LABEL> ["," <var-labels>]
<var-type>              ::= <type-primitive> | <type-array>

<type-primitive>        ::= ":" <type-a-primitive> [<type-address>] [<intial-value>] |
                            [":" <type-address>] <intial-value>
<type-a-primitive>      ::= <type-boolean> |                                (2) 
                            <type-byte> |                                   (3)
                            <type-word>                                     (4)

<type-array>            ::= <type-1d-array> | <type-2d-array>
<type-1d-array>         ::= ":" <type-1d-byte-array> [<type-address>] |
                            [":" <type-1d-byte-array>] <intial-1d-values>  
<type-2d-array>         ::= ":" <type-2d-byte-array> [<type-address>] |
                            [":" <type-2d-byte-array>] <intial-2d-values>  
<type-1d-byte-array>    ::= <type-byte> "[" <expression> "]" |              (5)
<type-2d-byte-array>    ::= <type-byte> "[" <expression>, <expression> "]"  (5) 

<type-boolean>          ::= "boolean"
<type-byte>             ::= "byte"
<type-word>             ::= "word"

<type-address>          ::= "at" <expression>                                  (6)

<intial-value>          ::= ":=" <expression>                                  (7)
<intial-1d-values>      ::= ":=" "{" <initial-1d-sequence> "}"                 (7)
<intial-2d-values>      ::= ":=" "{" <initial-2d-sequence> "}"                 (7)
<initial-1d-sequence>   ::= <expression> ["," <initial-1d-sequence>]           (7)
<initial-2d-sequence>   ::= <initial-1d-sequence> [";" <initial-2d-sequence>]  (7)

<body>                  ::= "begin" <statements> "end"
<statements>            ::= <statement> [<statements>]
<statement>             ::= <assignment> | 
                            <if-then-else> | <while-do> | <function-call> | ";"
<assignment>            ::= <name> ":=" <expression> |
                            <byte-array-element>":=" <expression> |
                            <byte-array> ":=" [<array-modifiers>] <byte-array>
<if-then-else>          ::= "if" <expression> "then" <statements>               (8)
                            ["else" <statements>] "end"  
<while-do>              ::= "while" <expression> "do" <statements> "end"        (8)
<function-call>         ::= <name> "()"                                         (9)

<expression>            ::= <operand> [<rhs-expression>]
<rhs-expression>        ::= <binary-operator> <unary-expression> [<rhs-expression>]
<unary-expression>      ::= "(" <expression> ")" | 
                            <unary-operator> <expression> | <operand> 
<operand>               ::= <byte-array-element>| <BOOLEAN-VALUE> |             (10)
                            <name> | <BYTE-VALUE> | <WORD-VALUE>                (10)
<byte-array-element>    ::= <1d-byte-array-element> | <2d-byte-array-element>
<1d-byte-array-element> ::= <name> "[" <expression> "]"                         (11, 12)
<2d-byte-array-element> ::= <name> "[" <expression>, <expression> "]"           (11, 13)
<binary-operator>       ::= "-" | "+" | "and" | "or" | "xor" |                  (14)
                            "<=" | "<" | "=" | "<>" | ">=" | ">"                (14) 
<unary-operator>        ::= "-" | "not" |                                       (14)
                            "(byte)" | "(byte.lo)" | "(byte.hi)" |              (14)
                            "(word)" | "(word.lo)" | "(word.hi)" |              (14)
                            "(array.size)"                                      (14)
<array-modifiers>       ::= "(array.up)" | "(array.down)"                         
<name>                  ::= <LABEL> ["." <LABEL>] 

    
<LABEL>         is a letter followed by a sequence of letetrs and digits        (15) 
<BOOLEAN-VALUE> is a binary truth value {false, true}
<BYTE-VALUE>    is an 8-bit unsigned value in the range [0..255]    
<WORD-VAULUE>   is a 16-bit unsigned value in the range [0..65535]
```

1. `<LABEL>` must refer to an existing module with that name 
2. `<type-boolean>` evaluates to a fixed `<BOOLEAN-VALUE>`. 
3. `<type-byte>` evaluates to a fixed `<BYTE-VALUE>`. 
4. `<type-word>` evaluates to a fixed `<WORD-VALUE>`. 
5. `expression` must evaluate to a fixed value in the range `[1..256]`. 
6. `expression` must evaluate to a fixed `<WORD-VALUE>`. 
7. `expression` must match with the contextual type. 
   For instance, if the contextual type is `byte`, the expression must evaluate to a fixed `<BYTE-VALUE>`.
8. `expression` must be of `<type-boolean>` type.
9. `<name>` must denote a function
10. `operand` type must match with the contextual type.
11. `expression` must be of `<type-byte>` type.
12. `<name>` must denote a 1D byte array
13. `<name>` must denote a 2D byte array 
14. `operator` type must match with the contextual type. 
15. Context may limit possible `<LABEL>` values. For instance, in variable declaration,  
   each `<LABEL>` must be unique within the defining scope. Also, a `<LABEL>` denoting a variable
   in an expression must refer to a variable that matches with the contextual type. 

### Notes
- Single-line comment starting with `//` is not part of the language syntax.
  Lexer uses it to remove characters till the end of the line when tokenizing
  the source code.

<br /><br />
:leftwards_arrow_with_hook: [Back to index](../index.md)