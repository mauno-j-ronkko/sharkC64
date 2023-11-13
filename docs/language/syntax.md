# Language syntax

The syntax of sharkC64 is as follows

```
<module>      ::= "module" <LABEL> <module-body>
<module-body> ::= [<var-section>] [<initialization>]

<var-section>      ::= "var" <var-declarations>
<var-declarations> ::= <var-declaration> [<var-declarations>]
<var-declaration>  ::= <labels> ":" [<type>] [<var-address>] [<var-assignment>]
<var-address>      ::= "at" <WORD-VALUE>
<var-assignment>   ::= ":=" <expression>  (1)

<initialization> ::= "begin" <statements> "end"
<statements>     ::= <statement> [<statements>]
<statement>      ::= <assignment>
<assignment>     ::= <LABEL> ":=" <expression>

<type> ::= "byte"

<expression>      ::= <operand> [<rhs-expression>]
<rhs-expression>  ::= <binary-operator> <operand> [<rhs-expression>]
<operand>         ::= "(" <expression> ")" | <LABEL> | <CONSTANT> | <unary-operator> <expression>
<binary-operator> ::= "-" | "+" | "and" | "or" | "xor"  (2) 
<unary-operator>  ::= "-" | "not"                       (2)
    
<labels> ::= <LABEL> ["," <labels>] 

<LABEL>        is a letter followed by a sequence of letetrs and digits  (3) 
<CONSTANT>     is some constant value                                    (4)
<WORD-VAULUE>  is a 16-bit value
```

1. Expression in variable assignment must match with the contextual type. 
   For instance, if the contextual type is `byte`, the expression must have an 8-bit value.
   Furthermore, in variable declaration, the expression must resolve into a constant value.
2. Operator must match with the contextual type.
3. Context may limit possible label values. For instance, in variable declaration, 
   each label must be unique within the defining scope. Also, a label denoting a variable
   in an expression must refer to a variable that matches with the contextual type. 
4. Constant must match with the contextual type.

### Notes
1. Single-line comment starting with `//` is not part of the language syntax.
   Lexer uses it to remove characters till the end of the line when tokenizing
   the source code.

<br /><br />
:leftwards_arrow_with_hook: [Back to index](../index.md)