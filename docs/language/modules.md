# Modules

A module is defined in a file, and it has the structure shown below.
In particular, a module consists of sections that start with a section keyword.
```
module UniqueName01
 
    var  a,b : byte
         corner : byte at $400 := $01
```

### Module name
Each module must have a unique name that is given after the `module` keyword.
```
module UniqueName01
```

All names in sharkC64 are case-sensitive, and a name may contain upper or
lower case letters followed by digits. However, as the name of the module must match 
the filename, module names should differ in some other ways than by letter case.
Otherwise, operating systems that are case-insensitive cannot distinguish them.

### Variables
Variables are listed in a `var` section. Variables with the same type can
be listed together by separating them with a comma.
A variable can also be given a static address and an initial value.
```
var  a, b : byte
     corner : byte at $400 := $01
```

<br /><br />
:leftwards_arrow_with_hook: [Back to index](../index.md)