# SharkC64

The SharkC64 programming language is designed to be used for the development of computer programs 
for the Commodore C64. 

The SharkC64 language is a modular programming language. 
It supports primitive data types: booleans, bytes, and words.
It also supports use of one-dimensional and two-dimensional byt arrays.
A module in the SharkC64 language consists of constants, variables, functions, and a module body.
A module may refer to other modules, use their variables, and call their functions.

The SharkC64 IDE comes bundled with a compiler and a bunch of example programs.
The SharkC64 IDE is published under MIT license.


## Index
[Acknowledgements](acknowledgements.md)

1. Prerequisites
   1. [Setup](prerequisites/setup.md)
   2. [Installing SharkC64 IDE](prerequisites/installing.md)
2. Language structures
   1. Expressions
      1. [Types](language/expressions/types.md)
      2. [Constants](language/expressions/constants.md)
      3. [Variables](language/expressions/variables.md)
      4. [Expressions](language/expressions/expressions.md)
      5. [Byte arrays](language/expressions/arrays.md)
      6. [Data](language/expressions/data.md)
   2. Statements
      1. [Empty statements](language/statements/empty.md)
      2. [Assignment statements](language/statements/assignments.md)
      3. [If statements](language/statements/ifs.md)
      4. [While statements](language/statements/whiles.md)
      5. [For statements](language/statements/fors.md)
      6. [Functions](language/statements/functions.md)
   3. Modules
      1. [Modules](language/modules/modules.md)
      2. [Using or including other modules](language/modules/use.md)
      3. [Hiding identifiers and functions](language/modules/hide.md)
      4. [Module initialization](language/modules/initialization.md)
   4. [Comments](language/comments.md)
   5. [Language syntax](language/syntax.md)
3. Using the SharkC64 IDE
   1. Starting up and Settings
      1. [Starting SharkC64 IDE](ide/starting-up/starting.md)
      2. [Setting the home directory](ide/starting-up/set-home.md)
      3. [Setting the emulator for running a program](ide/starting-up/set-emulator.md)
   2. Working with Examples
      1. [Downloading an example](ide/examples/download-example.md)
      2. [Running a downloaded example](ide/examples/run-example.md)
      3. [List of examples](ide/examples/examples.md)
   3. Working with Projects
      1. [Creating a new project](ide/projects/new-project.md)
      2. [Persisting a transient project](ide/projects/persist-project.md)
      3. [Opening an existing project](ide/projects/open-project.md)
      4. [Adding a new module to the project](ide/projects/add-module.md)
      5. [Importing an existing module to the project](ide/projects/import-module.md)
      6. [Editing a module](ide/projects/edit-module.md)
      7. [Deleting a module from the project](ide/projects/delete-module.md)
      8. [Saving changes in a module](ide/projects/save-module.md)
      9. [Reverting a module to opened state](ide/projects/revert-module.md)
      10. [Closing an open project](ide/projects/close-project.md)
   4. Compiler Actions
      1. [Compiling a module](ide/compiler/compile.md)
      2. [Building the project](ide/compiler/build.md)
      3. [Running the project](ide/compiler/run.md)
   5. Designer Actions
      1. [Viewing a module dependency diagram](ide/designer/diagram.md)
4. Roadmap
   1. [Release history](roadmap/history.md)
   2. [Future plans](roadmap/future.md)




