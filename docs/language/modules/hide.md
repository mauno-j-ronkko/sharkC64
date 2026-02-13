# Hiding identifiers and functions
A module may hide its elements, constant, variables, and functions, from other modules
to improve encapsulation. Hidden elements are declared in a ```hide``` section.
Elements that are to be hidden are listed using comma as separator.
```
hide corner, myHello
```

Hidden elements are accessible within the module itself, 
but not from other modules that use the module.
For instance, in the example below, the variable `corner` and the function `myHello` are hidden.
They can be used within `moduleA`, but not from `moduleB`.
```
moduleA
  hide corner, myHello
  
  var corner : byte
      line   : byte
        
  fun myHello() begin
      ...
  end
    
  fun greet() begin
      myHello()    // OK: myHello is accessible within moduleA
  end
  ...
end

moduleB
  use moduleA
  ...
  
begin
  moduleA.greet()    // OK: greet is accessible from moduleB
  moduleA.myHello()  // Error: myHello is hidden in moduleA
  
  moduleA.line   := $02  // OK: line is accessible from moduleB
  moduleA.corner := $01  // Error: corner is hidden in moduleA
  ...
end
```
