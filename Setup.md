# Setup

To set up your working environment to run _sharkC64_, you'll need Java Runtime
environment (or development kit) and VICE emulator.
Java environment is needed to run _sharkC64_ compiler.
VICE emulator is needed to run the compiled program.
For compatibility, it is recommended that you install the latest version
of the Java environment. Java Temurin JDK is used for the development of
_sharkC64_. Detailed installation instructions follow below,
as written by Bing chat [^1].


1. To install the latest version of Java Temurin JDK, you can use
   the package manager of your operating system, or download the installer
   or archive file from the official website [^2].
   For example, on Debian or Ubuntu Linux, you can run the following command in a terminal:

   `sudo apt-get install temurin-17-jdk`

   On Windows, you can download and run the MSI installer file for your architecture (x86 or x64).
   On macOS, you can use Homebrew to install the JDK with this command:

   `brew install temurin`

   For more details and options, please refer to the installation instructions [^3].


2. To install the VICE emulator, you can also use the package manager of
   your operating system, or download the binary distribution from
   the official website [^4]. For example, on Debian or Ubuntu Linux,
   you can run the following command in a terminal:

   `sudo apt-get install vice`

   On Windows, you can download and run the GTK3 or SDL2 installer file for your architecture (x86 or x64).
   On macOS, you can use Homebrew to install the emulator with this command:

   `brew install vice`

   For more details and options, please refer to the VICE manual [^5].



[^1]: Source: Discussion with Bing chat, September 10, 2023.

[^2]: Latest Releases | Adoptium.  https://adoptium.net/temurin/releases/ .

[^3]: Install Eclipse Temurin™ | Adoptium.  https://adoptium.net/installation/ .

[^4]: VICE - the Versatile Commodore Emulator.  https://vice-emu.sourceforge.io/ .

[^5]: VICE Manual - Table of Contents.  https://vice-emu.sourceforge.io/vice_toc.html .
