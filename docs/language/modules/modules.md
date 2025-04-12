# Modules

A module is defined in a file, and it has the structure shown below.
In particular, a module consists of sections that start with a section keyword.
```
module UniqueName01
    use   moduleA, moduleB
    
    const one    : byte := $01
    var   a,b    : byte
          corner : byte at $400 := one
          result : byte
         
    fun hello()
        var c : byte 
    begin
        c := a
    end
    
begin
    a := $10
    hello()
    result := corner + a
end
```

### Module name
Each module must have a unique name that is given after the `module` keyword.
```
module UniqueName01
```

All names in the sharkC64 language are case-sensitive, and a name may contain upper or
lower case letters followed by digits. However, as the name of the module must match 
the filename, module names should differ in some other ways than by letter case.
Otherwise, operating systems that are case-insensitive cannot distinguish them.

### Uses
A module may depend on other modules. Dependencies are declared in a ```use``` section.
Modules are listed using comma as separator.
```
use moduleA, moduleB
```

### Constants
Constants are listed in a `const` section. Each constant must be given a 
fixed value.
```
const one : byte := $01
```

### Variables
Variables are listed in a `var` section. Variables with the same type can
be listed together by separating them with a comma.
A variable can also be given a static address and an initial value.
```
var a,b    : byte
    corner : byte at $400 := $01
```

### Functions
Functions are defined after variable section and before the module initialization.
Each function starts with the keyword `fun`. 
Functions may define constants and variables that are local to them.
The statements for the body of the function are then given within a `begin` ... `end` block.
```
fun hello()
    var c : byte 
begin
    c := a
end
```
A function call is simply of the form `hello()` where `hello` is the name of the function.

### Module initialization
Module initialization is defined within a `begin` ... `end` block.
It acts as the main function of the module. The statements are executed 
right after the module variables are initialized.
```
begin
    a := $10
    result := corner + a
end
```

<br /><br />
:leftwards_arrow_with_hook: [Back to index](../../index.md)