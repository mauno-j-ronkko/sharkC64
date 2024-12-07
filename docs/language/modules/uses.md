# Uses
A module may depend on other modules. Dependencies are declared in a ```use``` section.
Module files are listed using comma as separator.
```
use moduleA, moduleB, moduleC
```

All module files are assumed to be in the same folder. 
Modules are read in the same order as they are listed. 
Listed modules may have further dependencies,
and it is also possible that several modules refer to the same module. 
Such a module is then read only once. 
In any case, inner dependencies are read before outer dependencies.
Consider, for instance, the following case where moduleC, moduleD, and moduleE have no further
dependencies.
```
moduleA
  use moduleB, moduleC
  ...

moduleB
  use moduleD, moduleC, moduleE
  ...
```
Then, modules are read in the order: moduleA, moduleB, moduleD, moduleC, and moduleE.
In particular, moduleC is read only once.

> :no_entry: Modules may not form circular dependencies.
> A circular dependency results in a compiler error.
> The simplest example of a circular dependency is the case, 
> where moduleA uses moduleB and vice versa.
> ```
> moduleA
>   use moduleB
>   ...
> 
> moduleB
>   use moduleA
>   ...
> ```

Note that, although all the names and labels in Shark are case-sensitive, 
the operating system may consider file names case-insensitive.
Therefore, module names that differ only by letter cases are not recommended.  

Note also that the name of the module must comply with the filename.
A file with some name must contain a module with the same name.
Furthermore, all used modules must have unique names. 
