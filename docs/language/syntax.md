# Language syntax

The syntax of sharkC64 is as follows

```
<module>      ::= "module" <LABEL> [<const-section>] [<var-section>] [<body>]

<const-section>      ::= "const" <const-declarations>
<const-declarations> ::= <const-declaration> [<const-declarations>]
<const-declaration>  ::= <LABEL> [":" <type>] <const-assignment>
<const-assignment>   ::= ":=" <expression>  (1)

<var-section>      ::= "var" <var-declarations>
<var-declarations> ::= <var-declaration> [<var-declarations>]
<var-declaration>  ::= <labels> ":" <byte-array> [<var-address>] |
                       <labels> ":" <type> [<var-address>] [<var-assignment>] |
                       <labels> [":" <var-address>] [<var-assignment>]
<byte-array>       ::= "byte" "[" <expression> "]"  (2) 
<var-address>      ::= "at" <expression>            (3)
<var-assignment>   ::= ":=" <expression>            (1)

<body>         ::= "begin" <statements> "end"
<statements>   ::= <statement> [<statements>]
<statement>    ::= <assignment> | <if-then-else> | <while-do>
<assignment>   ::= <byte-array-element> ":=" <expression> | 
                   <LABEL> ":=" <expression>
<if-then-else> ::= "if" <expression> "then" <statements> ["else" <statements>] "end"  (4)
<while-do>     ::= "while" <expression> "do" <statements> "end"                       (4)

<expression>         ::= <operand> [<rhs-expression>]
<rhs-expression>     ::= <binary-operator> <unary-expression> [<rhs-expression>]
<unary-expression>   ::= "(" <expression> ")" | <unary-operator> <expression> | <operand> 
<operand>            ::= <byte-array-element> | <boolean> |       (5)
                         <LABEL> | <BYTE-VALUE> | <WORD-VALUE>    (5)
<byte-array-element> ::= <LABEL> "[" <expression> "]"             (6) 
<binary-operator>    ::= "-" | "+" | "and" | "or" | "xor" |       (7)
                         "<=" | "<" | "=" | "<>" | ">=" | ">"     (7) 
<unary-operator>     ::= "-" | "not" |                            (7)
                         "(byte)" | "(byte.lo)" | "(byte.hi)"     (7)
                         "(word)" | "(word.lo)" | "(word.hi)"     (7)
    
<labels>  ::= <LABEL> ["," <labels>]
<boolean> ::= "true" | "false" 
<type>    ::= "byte" | "boolean" | "word"

<LABEL>        is a letter followed by a sequence of letetrs and digits  (8) 
<BYTE-VALUE>   is an 8-bit unsigned value   
<WORD-VAULUE>  is a 16-bit unsigned value
```

1. `expression` must match with the contextual type. 
   For instance, if the contextual type is `byte`, the expression must have an 8-bit value.
   Furthermore, the expression must resolve into a constant value.
2. `expression` must be a numerical expression and its value must be in range `[1..255]`
3. `expression` must be a `word` expression.
4. `expression` must be a `boolean` expression.
5. `operand` must match with the contextual type.
6. `expression` must be a `byte` expression.
7. `operator` must match with the contextual type.
8. Context may limit possible `label` values. For instance, in variable declaration, 
   each `label` must be unique within the defining scope. Also, a `label` denoting a variable
   in an expression must refer to a variable that matches with the contextual type. 

### Notes
- Single-line comment starting with `//` is not part of the language syntax.
  Lexer uses it to remove characters till the end of the line when tokenizing
  the source code.

<br /><br />
:leftwards_arrow_with_hook: [Back to index](../index.md)