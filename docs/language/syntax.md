# Language syntax

The syntax of the SharkC64 language is as follows 

```
<module>                ::= "module" <LABEL> 
                            [<use-section>] [<own-section>] [<val-section>] 
                            [<data-section>] [<var-section>] [<fun-section>] <init>

<use-section>           ::= "use" <module-list>
<module-list>           ::= <LABEL> ["," <module-list>]                         (1)

<own-section>           ::= "own" <identifier-list>
<identifier-list>       ::= <LABEL> ["," <identifier-list>]

<fun-section>           ::= <fun-declaration> [<fun-section>]
<fun-declaration>       ::= "fun" <LABEL> "(" [<fun-parameters>] ")" 
                            [":" <type-primitive>] 
                            [<val-section>] [<var-section>] 
                            "is" <statements>
<fun-parameters>        ::= <fun-parameter> ["," <fun-parameters>]
<fun-parameter>         ::= <LABEL> ":" <type-primitive>                   

<val-section>           ::= "val" <val-declarations>
<val-declarations>      ::= <val-declaration> [<val-declarations>]
<val-declaration>       ::= <LABEL> [":" <type>] <intial-value>

<data-section>          ::= "dat" <data-declarations>
<data-declarations>     ::= <data-declaration> [<data-declarations>]
<data-declaration>      ::= <LABEL> <at-address> <initial-1d-values>
 
<var-section>           ::= "var" <var-declarations>
<var-declarations>      ::= <var-declaration> [<var-declarations>]
<var-declaration>       ::= <var-labels> <var-type>
<var-labels>            ::= <LABEL> ["," <var-labels>]
<var-type>              ::= <var-primitive> | <var-array>
<var-primitive>         ::= ":" <type-primitive> [<at-address>] [<intial-value>] |
                            [":" <at-address>] <intial-value>
<var-array>             ::= <var-1d-array> | <var-2d-array>
<var-1d-array>          ::= ":" <type-1d-byte-array> [<at-address>] |
                            [":" <type-1d-byte-array>] <intial-1d-values>  
<var-2d-array>          ::= ":" <type-2d-byte-array> [<at-address>] |
                            [":" <type-2d-byte-array>] <intial-2d-values>  

<at-address>            ::= "at" <expression>                                   (2)
                           
<type-1d-byte-array>    ::= <type-byte> "[" <expression> "]" |                  (3)
<type-2d-byte-array>    ::= <type-byte> "[" <expression>, <expression> "]"      (3) 
<type-primitive>        ::= <type-boolean> |                                    (4) 
                            <type-byte> |                                       (5)
                            <type-word> |                                       (6)
                            <type-int>  |                                       (7)
                            <type-pointer>                                      (8)
<type-boolean>          ::= "boolean"
<type-byte>             ::= "byte"
<type-word>             ::= "word"
<type-int>              ::= "int"
<type-pointer>          ::= "pointer"

<intial-value>          ::= ":=" <expression>                                   (9)
<intial-1d-values>      ::= ":=" "{" <initial-1d-sequence> "}"                  (9)
<intial-2d-values>      ::= ":=" "{" <initial-2d-sequence> "}"                  (9)
<initial-1d-sequence>   ::= <expression> ["," <initial-1d-sequence>]            (9)
<initial-2d-sequence>   ::= <initial-1d-sequence> [";" <initial-2d-sequence>]   (9)

<init>                  ::= "init" <statements> "end" | "end"
<statements>            ::= <statement> [<statements>]
<statement>             ::= <assignment> | 
                            <if-then-else> | <while-do> | <for-do> | 
                            <function-call> | <setter-call>
                            "return" | ";"

<assignment>            ::= <primitive-assignment> |
                            <byte-array-element> ":=" <expression> |
                            <1d-array-name> ":=" [<array-modifiers>] <1d-array-name>
<primitive-assignment>  ::= <var-name> ":=" <expression> 
<array-modifiers>       ::= "(array.up)" | "(array.down)"

<if-then-else>          ::= "if" <expression> "then" <statements>               (10)
                            ["else" <statements>] "end"  
<while-do>              ::= "while" <expression> "do" <statements> "end"        (10)
<for-do>                ::= <for-to-do> | <for-downto-do> 
<for-to-do>             ::= "for" <primitive-assignment> "to" <expression>      (11) 
                            "do" <statements> "end" 
<for-downto-do>         ::= "for" <primitive-assignment> "downto" <expression>  (11)
                            "do" <statements> "end" 
<function-call>         ::= <function-name> "(" [function-arguments] ")"
<function-arguments>    ::= <expression> ["," <function-arguments> ]            (12)                                
<setter-call>           ::= <setter-name> "(" <expression> ")"                  (13)

<expression>            ::= <operand> [<rhs-expression>]
<rhs-expression>        ::= <binary-operator> <unary-expression> [<rhs-expression>]
<unary-expression>      ::= "(" <expression> ")" | 
                            <unary-operator> <expression> | <operand> 
<operand>               ::= <BOOLEAN-VALUE> | <BYTE-VALUE> |                    (14)
                            <WORD-VALUE> | <INT-VALUE>                          (14)
                            <val-name> | <var-name> | <byte-array-element> |    (14)
                            <typecast> | <function-call>                        (15)
<byte-array-element>    ::= <1d-byte-array-element> | <2d-byte-array-element>
<1d-byte-array-element> ::= <1d-array-name> "[" <expression> "]"                (16)
<2d-byte-array-element> ::= <2d-array-name> "[" <expression>, <expression> "]"  (16)
<typecast>              ::= "boolean(" <BYTE-VALUE> ")" |
                            "byte(" <BOOLEAN-VALUE> ")" |
                            "loByte(" <WORD-VALUE> ")" |
                            "hiByte(" <WORD-VALUE> ")" |
                            "loWord(" <BYTE-VALUE> ")" |
                            "hiWord(" <BYTE-VALUE> ")" |
                            "word(" <INT-VALUE> ")" | 
                            "int(" <WORD-VALUE> ")" | 
                            "word(" <POINTER-VALUE> ")" |      
                            "pointer(" <WORD-VALUE> ")"  
<binary-operator>       ::= "-"  | "+" | "and" | "or" | "xor" |                 (17)
                            "<=" | "<" | "="   | "<>" | ">="  | ">"             (17) 
<unary-operator>        ::= "-" | "not" | "@"                                   (17)

<val-name>              ::= <name>                                              (18)
<var-name>              ::= <name>                                              (19)
<1d-array-name>         ::= <name>                                              (20)
<2d-array-name>         ::= <name>                                              (21)
<function-name>         ::= <name> | "." <LABEL>                                (22)
<setter-name>           ::= <name> | "." <LABEL>                                (23)
<name>                  ::= <LABEL> ["." <LABEL>] 

    
<LABEL>         is a letter followed by a sequence of letters and digits        (24) 
<BOOLEAN-VALUE> is a binary truth value {false, true}
<BYTE-VALUE>    is an 8-bit unsigned value in the range [0..255]    
<WORD-VAULUE>   is a 16-bit unsigned value in the range [0..65535]
<INT-VALUE>     is a 16-bit signed value in the range [-32768..32767]
<POINTER-VALUE> is a pointer typed 16-bit unsigned value in the range [0..65535]
```

1. `<LABEL>` must refer to an existing module with that name
2. `expression` must evaluate to a fixed `<WORD-VALUE>`.
3. `expression` must evaluate to a fixed value in the range `[1..256]`.
4. `<type-boolean>` evaluates to a fixed `<BOOLEAN-VALUE>`.
5. `<type-byte>` evaluates to a fixed `<BYTE-VALUE>`. 
6. `<type-word>` evaluates to a fixed `<WORD-VALUE>`. 
7. `<type-int>` evaluates to a fixed `<INT-VALUE>`.
8. `<type-pointer>` evaluates to a fixed `<POINTER-VALUE>`.
9. `expression` must match with the contextual type. 
   For instance, if the contextual type is `byte`, the expression must evaluate to a fixed `<BYTE-VALUE>`.
10. `expression` must be of `<type-boolean>` type.
11. `primitive-assignment` and `expression` must be of the same numeric type.
12. `expression` must be of the same type as corresponding function parameter.
13. `expression` must be of the same type as corresponding primitive variable for the setter.
14. `operand` type must match with the contextual type.
15. `<typecast>` or `<function-call>` return type must match with the contextual type.
16. `expression` must be of `<type-byte>` type.
17. `operator` type must match with the contextual type. 
18. `<name>` must denote a constant.
19. `<name>` must denote a variable; not an array.
20. `<name>` must denote a one dimensional array.
21. `<name>` must denote a two-dimensional array.
22. `<name>` or a chained `<LABEL>` must denote a function 
23. `<name>` or a chained `<LABEL>` must denote a primitive variable
24. Context may limit possible `<LABEL>` values. For instance, in variable declaration,  
    each `<LABEL>` must be unique within the defining scope. Also, a `<LABEL>` denoting a variable
    in an expression must refer to a variable that matches with the contextual type. 

### Notes
- Single-line comment starting with `//` is not part of the language syntax.
  Lexer uses it to remove characters till the end of the line when tokenizing
  the source code.

<br /><br />
:leftwards_arrow_with_hook: [Back to index](../index.md)