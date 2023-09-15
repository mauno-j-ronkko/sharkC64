# Compiling 

Before compiling with sharkC64, check that you have installed a compatible Java Runtime
environment, see [setup](setup.md).

Steps to compile a s64 source file with
1. Open command prompt or a terminal window on your computer.
2. Move to the folder where you have installed sharkC64;
   for instance,
   ```
   cd C:\SHARKC64
   ```
3. Check where the sharkC64 compiler and the source file are in the folder structure:
    ```
   C:\SHARKC64
   |
   +-- sharkC64-x.y.z
   |   |
   |   +-- bin
   |   |   |
   |   |   +--sharkC64       // the sharkC64 compiler
   |   |
   |   +-- lib
   |
   +-- sharkC64
       |
       +-- docs
       +-- examples
           |
           +-- example01.s64  // the source file
   ```
4. Compile the example file `example01.s64` by typing the following command
   ```
   sharkC64-x.y.z\bin\sharkC64 path:sharkC64\examples example01.s64
   ```
   It should produce the following output:
   ```
   sharkC64 version x.y.z  (C) 2023
   https://github.com/mauno-j-ronkko/sharkC64

   Compiling example01.s64 ...
   Compiled with no errors.
   Saved example01.prg
   ```
5. Check that the file `example01.prg` has been created to the same folder,
   where the source file is. In this case, the file is created to the folder
   `C:\SHARKC64\sharkC64\examples`


<br /><br />
:leftwards_arrow_with_hook: [Back to index](../index.md)

