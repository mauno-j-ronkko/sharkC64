# Comments

A single-line comment is indicated by `//`.
Any text after `//` till the end of the line is ignored.

Consider, for instance, the code
```
// Variables with comments
var  a, b, c : byte
     // zero : byte := $00
     corner  : byte at $400 // := zero + $01
```
It is equivalent to the code without comments:
```
var  a, b, c : byte
     corner  : byte at $400
```


<br /><br />
:leftwards_arrow_with_hook: [Back to index](../index.md)