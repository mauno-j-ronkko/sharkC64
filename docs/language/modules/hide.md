# Hiding identifiers and functions
A module may hide its constant values, data, variables, and functions 
from other modules to improve encapsulation. Hidden elements are declared in an `own` section.
Names of the elements that are to be hidden are listed using comma as separator.
```
own corner, myHello
```

Hidden elements are accessible within the module itself, but not from the other modules.
For instance, in the example below, the variable `corner` and the function `myHello` are hidden.
They can be used within `moduleA`, but not from `moduleB`.
```
moduleA
  own corner, myHello
  
  var corner : byte
      line   : byte
        
  fun myHello() is
      ...
    
  fun greet() is
      myHello()    // OK: myHello is accessible within moduleA
  
  ...
end

moduleB
  use moduleA
  ...
  
init
  moduleA.greet()    // OK: greet is accessible from moduleB
  moduleA.myHello()  // Error: myHello is hidden in moduleA
  
  moduleA.line   := $02  // OK: line is accessible from moduleB
  moduleA.corner := $01  // Error: corner is hidden in moduleA
  ...
end
```
