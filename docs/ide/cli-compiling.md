# Compiling a module from the command line

Before compiling with sharkC64, check that you have installed a compatible Java Runtime
environment, see [setup](../prerequisites/setup.md).

Steps to compile a s64 source file:
1. To make sure that harkC64 is properly initialized,
   run it first as instructed in the text for [starting sharkC64](starting.md). 
2. Open a command prompt or a terminal window on your computer.
3. Move to the folder where you have installed sharkC64;
   for instance,
   ```
   cd C:\SHARKC64
   ```
4. Check where the sharkC64 compiler and the source file are in the folder structure:
   ```
   C:\SHARKC64
   |
   +-- sharkC64-x.y.z
   |   |
   |   +-- bin
   |   |   |
   |   |   +-- examples            // examples folder created by sharkC64
   |   |   |   |
   |   |   |   +--example01.s64
   |   |   |   +--example01b.s64
   |   |   |   ...
   |   |   |
   |   |   +--sharkC64             // starter script for MacOS
   |   |   +--sharkC64.bat         // starter script for Windows
   |   |   +--sharkC64.ini         // settings for the sharkC64
   |   |
   |   +-- lib
   |   |   |
   |   |   ...
   ```
5. Compile the example file `example01.s64` by typing the following command
   ```
   sharkC64-x.y.z\bin\sharkC64 home:sharkC64-x.y.z\bin\examples example01.s64
   ```
   It should produce the following output:
   ```
   sharkC64 version x.y.z  (C) 2023
   https://github.com/mauno-j-ronkko/sharkC64

   Compiled with no errors.
   Saved 'example01.prg'.
   ```
6. Check that the file `example01.prg` has been created. 
   In this case, you should find it at folder `sharkC64-x.y.z\bin\prg`


<br /><br />
:leftwards_arrow_with_hook: [Back to index](../index.md)

