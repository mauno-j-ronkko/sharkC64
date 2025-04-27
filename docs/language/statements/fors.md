# For statements

A for statement traverse through given values and executes a statement block
for each value. The for statement is of the following form.
```
for a := 0 to 10 do
   b := b + a
end 
```

After the `for` keyword there is an initial value assignment.
The variable in the assignment is used as a loop counter.
Only `byte` and `word` values variables are accepted as loop counters.
The initial value is the first value that is used to execute the statement block.

After the initial assignment there is a `to` keyword.
It indicates the loop direction - increasing values.
There could also be a `downto` keyword that indicates a decreasing loop direction.

After the direction keyword there is the final value.
The for statement is executed for all the values starting from the initial value
and stepping by one increment or decrement till the final value is reached.
The statement block is then executed for the last time with the final value.

The statement block may have multiple statements.
It can consist of any statements, including if statements and nested for statements.
Each nested while statement must end with the `end` keyword.

<br /><br />
:leftwards_arrow_with_hook: [Back to index](../../index.md)