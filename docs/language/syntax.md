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
<var-declaration>  ::= <labels> ":" <type> [<var-address>] [<var-assignment>] |
                       <labels> [":" <var-address>] [<var-assignment>] 
<var-address>      ::= "at" <WORD-VALUE>
<var-assignment>   ::= ":=" <expression>  (1)

<body>         ::= "begin" <statements> "end"
<statements>   ::= <statement> [<statements>]
<statement>    ::= <assignment> | <if-then-else>
<assignment>   ::= <LABEL> ":=" <expression>
<if-then-else> ::= "if" <expression> "then" <statements> ["else" <statements>] "end"  (2)

<type> ::= "byte" | "boolean"

<expression>      ::= <operand> [<rhs-expression>]
<rhs-expression>  ::= <binary-operator> <operand> [<rhs-expression>]
<operand>         ::= "(" <expression> ")" | <unary-operator> <expression> | 
                      <LABEL> | <boolean> | <BYTE-VALUE>    (3)
<binary-operator> ::= "-" | "+" | "and" | "or" | "xor" |    (4)
                      "<=" | "<" | "=" | "<>" | ">=" | ">"  (4) 
<unary-operator>  ::= "-" | "not"                           (4)
    
<labels>  ::= <LABEL> ["," <labels>]
<boolean> ::= "true" | "false" 

<LABEL>        is a letter followed by a sequence of letetrs and digits  (5) 
<BYTE-VALUE>   is an 8-bit value   
<WORD-VAULUE>  is a 16-bit value
```

1. `expression` must match with the contextual type. 
   For instance, if the contextual type is `byte`, the expression must have an 8-bit value.
   Furthermore, the expression must resolve into a constant value.
2. `expression` must be a boolean expression.
3. `operand` must match with the contextual type.
4. `operator` must match with the contextual type.
5. Context may limit possible `label` values. For instance, in variable declaration, 
   each `label` must be unique within the defining scope. Also, a `label` denoting a variable
   in an expression must refer to a variable that matches with the contextual type. 

### Notes
- Single-line comment starting with `//` is not part of the language syntax.
  Lexer uses it to remove characters till the end of the line when tokenizing
  the source code.

<br /><br />
:leftwards_arrow_with_hook: [Back to index](../index.md)