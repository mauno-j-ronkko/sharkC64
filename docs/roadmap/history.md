# Release history

### Version 0.10 published March, 2025
- added support for 2D byte arrays
- added support for zero-page instructions
- improved use of near jumps with word arguments
- refactored bytecode generation
- fixed bytecode generation bug for type casting

### Version 0.9 published February 16, 2025
- added function bodies to the language
- renamed array modifiers as (array.up), (array.down), and (array.size)
- fixed nested array indexing
- fixed sorted file list in file dialog
- fixed saving of emulator file name
- fixed bug in revert all changes
- improved history buffering in editing
- minor UI fixes

### Version 0.8.1 published January 14, 2025
- Home screen
  - Updated home screen to address projects instead of modules
  - Added creation of a new project
  - Added dialog for opening an existing project
  - Added dialog for asking home folder and emulator file
- Editor
  - Added actions for creating or opening a module
  - Added action for building the project without running it
  - Added action for reverting all unsaved changes
  - Added checks for not losing changes
  - Added automatic compilation of a module when opened
  - Updated header to show the project name
  - Improved error messaging
- Language
  - Improved validation of constant declarations
- Miscellaneous
  - Improved submenu stability
  - Improved mouse click responsiveness

### Version 0.8 published December 7, 2024
- Added use statement
- Added referencing of variables and constants in another module
- Refactored settings and home screen
- Fixed handling of invalid files
- Adjusted dialogs on screen
- Simplified compiler error handling

### Version 0.7.2 published November 9, 2024
- refactored IDE implementation
- added some minor usability adjustments
- added dragging of the vertical scroll bar with mouse
- improved find/replace/error messages
- added closing of the editor menu by clicking outside it

### Version 0.7.1 published September 29, 2024
- added array assignment for byte arrays
- added initial value assignment for byte arrays
- added byte array modifiers, (.up), (.down)
- added byte array length operator, (.length)
- added empty statement ";"
- improved simplification of index values for array elements
- improved static type inference in binding
- improved code branching in code generation
- refined the help for finding and replacing text in IDE
- switched to using Temurin 21

### Version 0.7 published August 30, 2024
- Added byte arrays

### Version 0.6 published August 3, 2024
- Added the word data type with type casting operators
- Refined intermediate representation language and its translation
- Refined bytecode generation

### Version 0.5 published June 22, 2024
- Added While statements
- Improved optimization of If statements
- Fixed issue with pressing delete and backspace keys after pressing a shift key
- Removed support for the old "path" attribute when compiling from command line

### Version 0.4 published May 18, 2024
- Added If statements
- Fixed an issue in the editor when deleting selection with backspace

### Version 0.3.4 published April 14, 2024
- Refactored expression parsing and binding
- Improved boolean constant definitions; comparison expressions are now supported
- Added scroll-wheel support to editor view

### Version 0.3.3 published March 17, 2024
- Added comparison operators
- Fixed precedence issue in parser
- Added an indicator for building and running
- Added a scroll bar to edit view
- Simplified translation for commutative operators

### Version 0.3.2 published February 18, 2024
- Boolean types with true and false values
- Logical expression (not, and, or, xor) for booleans
- Build and run module in edit view (Compiler > Build and run / F10)
- Rephrased confirmation dialog when closing the editor without saving changes

### Version 0.3.1 published January 28, 2024
- Constant values
- A newly created module opens with a named module body 

### Version 0.3 published December 29, 2023
- The very first version of an IDE
- The `path` parameter in the command line mode has been deprecated;
  use `home` parameter instead

### Version 0.2 published November 13, 2023
- Assignment statements
- Module initialization

### Version 0.1.1 published October 26, 2023
- Single-line comments
- Inferred variable types
- Language syntax added to the manual

### Version 0.1 published September 15, 2023
- Byte data type 
- Variable declaration 
- Variables with static addresses
- Variables with initial values

<br /><br />
:leftwards_arrow_with_hook: [Back to index](../index.md)
