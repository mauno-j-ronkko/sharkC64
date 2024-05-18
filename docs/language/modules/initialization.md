# Module initialization

Module initialization is an optional block of code that runs after 
the module variables are initialized. It acts as the main function of the module, 
and it can perform any actions that are needed before the module can be used 
by other parts of the program.

The module initialization block is enclosed by the keywords begin and end, 
and it is placed at the end of the module.
```
begin
    a := $10
    result := corner + a
end
```

The module initialization block is executed only once. 
When it is executed, it can access and modify the module variables.
It cannot, however, return any value or take any parameters. 
It can only perform side effects.


<br /><br />
:leftwards_arrow_with_hook: [Back to index](../../index.md)





