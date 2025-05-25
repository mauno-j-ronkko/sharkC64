# Language syntax

The syntax of the sharkC64 language is as follows

```
<module>                ::= "module" <LABEL> 
                            [<use-section>] [<const-section>] [<var-section>] 
                            [<fun-section>] <body>

<use-section>           ::= "use" <module-list>
<module-list>           ::= <LABEL> ["," <module-list>]                        (1)

<fun-section>           ::= <fun-declaration> [<fun-section>]
<fun-declaration>       ::= "fun" <LABEL> "(" [<fun-parameters>] ")"
                            [<const-section>] [<var-section>] <body>
<fun-parameters>        ::= <fun-parameter> ["," <fun-parameters>]
<fun-parameter>         ::= <LABEL> ":" <type-primitive>                   

<const-section>         ::= "const" <const-declarations>
<const-declarations>    ::= <const-declaration> [<const-declarations>]
<const-declaration>     ::= <LABEL> [":" <type>] <intial-value>

<var-section>           ::= "var" <var-declarations>
<var-declarations>      ::= <var-declaration> [<var-declarations>]
<var-declaration>       ::= <var-labels> <var-type>
<var-labels>            ::= <LABEL> ["," <var-labels>]
<var-type>              ::= <var-primitive> | <var-array>
<var-primitive>         ::= ":" <type-primitive> [<var-address>] [<intial-value>] |
                            [":" <var-address>] <intial-value>
<var-array>             ::= <var-1d-array> | <var-2d-array>
<var-1d-array>          ::= ":" <type-1d-byte-array> [<var-address>] |
                            [":" <type-1d-byte-array>] <intial-1d-values>  
<var-2d-array>          ::= ":" <type-2d-byte-array> [<var-address>] |
                            [":" <type-2d-byte-array>] <intial-2d-values>  
<var-address>           ::= "at" <expression>                                  (2)
                           
<type-1d-byte-array>    ::= <type-byte> "[" <expression> "]" |                 (3)
<type-2d-byte-array>    ::= <type-byte> "[" <expression>, <expression> "]"     (3) 
<type-primitive>        ::= <type-boolean> |                                   (4) 
                            <type-byte> |                                      (5)
                            <type-word>                                        (6)
<type-boolean>          ::= "boolean"
<type-byte>             ::= "byte"
<type-word>             ::= "word"

<intial-value>          ::= ":=" <expression>                                  (7)
<intial-1d-values>      ::= ":=" "{" <initial-1d-sequence> "}"                 (7)
<intial-2d-values>      ::= ":=" "{" <initial-2d-sequence> "}"                 (7)
<initial-1d-sequence>   ::= <expression> ["," <initial-1d-sequence>]           (7)
<initial-2d-sequence>   ::= <initial-1d-sequence> [";" <initial-2d-sequence>]  (7)

<body>                  ::= "begin" <statements> "end" | "end"
<statements>            ::= <statement> [<statements>]
<statement>             ::= <assignment> | 
                            <if-then-else> | <while-do> | <for-do> 
                            <function-call> | ";"

<assignment>            ::= <primitive-assignment> |
                            <byte-array-element> ":=" <expression> |
                            <1d-array-name> ":=" [<array-modifiers>] <1d-array-name>
<primitive-assignment>  ::= <var-name> ":=" <expression> 
<array-modifiers>       ::= "(array.up)" | "(array.down)"

<if-then-else>          ::= "if" <expression> "then" <statements>               (8)
                            ["else" <statements>] "end"  
<while-do>              ::= "while" <expression> "do" <statements> "end"        (8)
<for-do>                ::= <for-to-do> | <for-downto-do> 
<for-to-do>             ::= "for" <primitive-assignment> "to" <expression>      (9) 
                            "do" <statements> "end" 
<for-downto-do>         ::= "for" <primitive-assignment> "downto" <expression>  (9)
                            "do" <statements> "end" 
<function-call>         ::= <function-name> "(" [function-arguments] ")"
<function-arguments>    ::= <expression> ["," <function-arguments> ]            (10)                                

<expression>            ::= <operand> [<rhs-expression>]
<rhs-expression>        ::= <binary-operator> <unary-expression> [<rhs-expression>]
<unary-expression>      ::= "(" <expression> ")" | 
                            <unary-operator> <expression> | <operand> 
<operand>               ::= <BOOLEAN-VALUE> | <BYTE-VALUE> | <WORD-VALUE> |     (11)
                            <const-name> | <var-name> | <byte-array-element>    (11)
<byte-array-element>    ::= <1d-byte-array-element> | <2d-byte-array-element>
<1d-byte-array-element> ::= <1d-array-name> "[" <expression> "]"                (12)
<2d-byte-array-element> ::= <2d-array-name> "[" <expression>, <expression> "]"  (12)
<binary-operator>       ::= "-" | "+" | "and" | "or" | "xor" |                  (13)
                            "<=" | "<" | "=" | "<>" | ">=" | ">"                (13) 
<unary-operator>        ::= "-" | "not" |                                       (13)
                            "(byte)" | "(byte.lo)" | "(byte.hi)" |              (13)
                            "(word)" | "(word.lo)" | "(word.hi)" |              (13)
                            "(array.size)"                                      (13)

<const-name>            ::= <name>                                              (14)
<var-name>              ::= <name>                                              (15)
<1d-array-name>         ::= <name>                                              (16)
<2d-array-name>         ::= <name>                                              (17)
<function-name>         ::= <name>                                              (18)
<name>                  ::= <LABEL> ["." <LABEL>] 

    
<LABEL>         is a letter followed by a sequence of letters and digits        (19) 
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
9. `primitive-assignment` and `expression` must be of the same `<type-byte>` or `<type-word>` type.
10. `expression` must be of the same type as corresponding function parameter.
11. `operand` type must match with the contextual type.
12. `expression` must be of `<type-byte>` type.
13. `operator` type must match with the contextual type. 
14. `<name>` must denote a constant.
15. `<name>` must denote a variable; not an array.
16. `<name>` must denote a one dimensional array.
17. `<name>` must denote a two-dimensional array.
18. `<name>` must denote a function.
19. Context may limit possible `<LABEL>` values. For instance, in variable declaration,  
    each `<LABEL>` must be unique within the defining scope. Also, a `<LABEL>` denoting a variable
    in an expression must refer to a variable that matches with the contextual type. 

### Notes
- Single-line comment starting with `//` is not part of the language syntax.
  Lexer uses it to remove characters till the end of the line when tokenizing
  the source code.

<br /><br />
:leftwards_arrow_with_hook: [Back to index](../index.md)