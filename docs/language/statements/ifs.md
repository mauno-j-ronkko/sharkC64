# If statements

An if statement selects one of two branches for execution: an if-branch or an else-branch.
The selection is based on a boolean expression.
If the boolean expression evaluates to `true` the if-branch is executed.
If the boolean expression evaluates to `false` the else-branch is executed.
The if statement is of the following form.
```
if a<b then
   a := a + 1
   b := 0
else
   b := b + 1
end 
```

In the if statement, the expression after the `if` keyword must evaluate to a boolean value.
The else-branch is optional in an if statement. Then, the if-branch is executed only if the
expression evaluates to `true`.
In any case, an if statement ends always with the `end` keyword.

The if-branch and the else-branch may have multiple statements, thus, forming blocks of statements.
Also, if statements can be nested. One if statement can be part of an if-branch or an else-branch 
of another if statement. Then, each if statement must end with the `end` keyword. 

<br /><br />
:leftwards_arrow_with_hook: [Back to index](../../index.md)