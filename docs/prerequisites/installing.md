# Installing

Before installing sharkC64, check that you have installed compatible Java Runtime
environment (or development kit) and VICE emulator, see [setup](setup.md).

### Installing the compiler
Steps to install the latest version of sharkC64:
1. Open the release page [here](https://github.com/mauno-j-ronkko/sharkC64/releases).
2. Click the "Assets" option on the latest release. It will open a list of assets,
   including a zip file named "sharkC64-x.y.z.zip", where "x.y.z" is the latest version.
3. Click the zip file "sharkC64-x.y.z.zip", and it will start the downloading immediately. 
   Your browser will indicate where the zip file has been downloaded.
4. Unzip the zip file to any folder, where you would like to run sharkC64,
   for instance, I have unzipped it on my Windows computer to folder `C:\SHARKC64`
5. Verify that the zip file has been successfully unzipped. 
   The folder structure should be as follows:
   ```
   C:\SHARKC64
   |
   +-- sharkC64-x.y.z
       |
       +-- bin
       +-- lib
   ```

### Installing examples
As for the examples, you can download them individually if you so wish.
The examples are located in the examples folder of this repository.
GitHub also supports downloading the entire repository as a zip package.

However, it is recommended that you use Git to clone this repository to your computer.
Then, it is easy to keep everything up to date simply by pulling the latest updates
to your computer. Also, by cloning the repository, you will get the manual to your computer.
To clone this repository, you need to install Git on your computer first, see [setup](setup.md). GitHub

Steps to clone the repository to your computer:
1. Open command prompt or a terminal window on your computer.
2. Move to the folder where you have installed sharkC64;
   for instance, 
   ```
   cd C:\SHARKC64
   ```
3. Use Git clone command to clone the repository to your computer
   ```
   git clone https://github.com/mauno-j-ronkko/sharkC64.git
   ```
   The folder structure should new be as follows:
    ```
   C:\SHARKC64
   |
   +-- sharkC64-x.y.z
   |   |
   |   +-- bin
   |   +-- lib
   |
   +-- sharkC64
       |
       +-- docs
       +-- examples
   ```

Steps to update the cloned repository later
1. Open command prompt or a terminal window on your computer.
2. Move to the folder where you have cloned the sharkC64 repository;
   for instance,
   ```
   cd C:\SHARKC64\sharkC64
   ```
3. Use Git pull command to pull the latest changes to your computer
   ```
   git pull
   ```

<br /><br />
:leftwards_arrow_with_hook: [Back to index](../index.md)

