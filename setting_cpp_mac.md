- [Setting up the development environment](#setting-up-the-development-environment)
  - [Install Xcode](#install-xcode)
  - [Install the  Xcode command line tools](#install-the--xcode-command-line-tools)
  - [Install GCC](#install-gcc)
  - [Install CMake](#install-cmake)
  - [Git](#git)
    - [Install Git](#install-git)
      - [Git for Mac Installer](#git-for-mac-installer)
      - [Install Git with Homebrew](#install-git-with-homebrew)
  - [Text Editors](#text-editors)
    - [Visual Studio Code](#visual-studio-code)
      - [Install Visual Studio Code](#install-visual-studio-code)
      - [Launching from the command line](#launching-from-the-command-line)
      - [Install helper extensions](#install-helper-extensions)
      - [Create a CMake project](#create-a-cmake-project)
        - [Create a CMake hello world project](#create-a-cmake-hello-world-project)
        - [Select a kit](#select-a-kit)
      - [Configure Hello World](#configure-hello-world)
        - [Select a variant](#select-a-variant)
        - [CMake: Configure](#cmake-configure)
      - [Build Hello World](#build-hello-world)
  - [Using libraries](#using-libraries)
    - [vcpkg](#vcpkg)
      - [Install vcpkg](#install-vcpkg)
      - [Install libraries for your project](#install-libraries-for-your-project)
      - [Using vcpkg with CMake](#using-vcpkg-with-cmake)
  - [Unit testing](#unit-testing)
    - [Google Test (GTest)](#google-test-gtest)
      - [Build and install GTest](#build-and-install-gtest)
      - [Using GTest](#using-gtest)
  - [Addtional Tooling](#addtional-tooling)
    - [ClangFormat](#clangformat)
      - [Installing Clang-format](#installing-clang-format)
      - [Configuring Clang-format](#configuring-clang-format)
      - [Using Clang-format with VSCode](#using-clang-format-with-vscode)
    - [C/C++ include guard (proud contributor)](#cc-include-guard-proud-contributor)
    - [include-info (proud maker)](#include-info-proud-maker)

<a name="setting-up-the-development-environment"></a>

## Setting up the development environment

Setting up a C++ development environment on macOS can be done in many ways:

1. Install Xcode
2. Install the Xcode Command Line Tools and use any preferred IDE or Code Editor for writing C or C++ code
3. Install GCC instead of Clang (shipped with Xcode)

<a name="install-xcode"></a>

### Install Xcode

The Xcode development environment includes the Clang C/C++ compiler and various development tools. You can install it from the Mac App Store:

1. Open the Mac App Store.
2. Search for "Xcode."
3. Click the "Install" button next to Xcode.

You will need to agree to the license terms and download the necessary components.
![](screenshots/macOS/xcode_welcome.jpeg)

The next step is to click on “Create a new Xcode project”.
If you have an existing project you will click on “Open a project or file” or “Clone an existing project” if the project is on source control.
Next, click on the macOS tab and then click on the Command-Line app as it is the only thing where we can develop apps in C and C++

![](screenshots/macOS/xcode_create_project.jpeg)

It will now show an interface to give the app a name and the package name. After giving that name there would be a drop-down to select a language. So, instead of swift, you can select C or C++ and click Next

![](screenshots/macOS/xcode_select_language.jpeg)

Then it will ask for the location of the project on your machine
Then, you can open or create a C or C++ file and start editing it

![](screenshots/macOS/xcode_editing_project.jpeg)

<a name="install-the--xcode-command-line-tools"></a>

### Install the  Xcode command line tools

 For command-line development, we can install the command line tools separately by running this command on the terminal

 ```bash
 xcode-select --install
 ```

 ![](screenshots/macOS/xcode_cli_tools.png)

<a name="install-gcc"></a>

### Install GCC

macOS comes with the Clang C/C++ compiler included with Xcode. You can check its version and ensure it's installed by running

```bash
clang++ --version
```

If you prefer using GCC, you can install it using Homebrew

<a name="install-homebrew"></a>

1. Install Homebrew (if not already installed)

   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

2. Install GCC

   ```bash
   brew install gcc
   ```

<a name="install-cmake"></a>

### Install CMake

CMake is an open-source, cross-platform tool that uses compiler and platform independent configuration files to generate native build tool files specific to your compiler and platform.
CMake can be installed on Mac using brew

```bash
brew install cmake
```

or by downloading the binaries unpacking them manually to any location:

```
wget https://cmake.org/files/v3.4/cmake-3.4.1-Darwin-x86_64.tar.gz
tar xf cmake-3.4.1-Darwin-x86_64.tar.gz
export PATH="`pwd`/cmake-3.4.1-Darwin-x86_64/CMake.app/Contents/bin:$PATH"
```

or by downloading the DMG installer from <a href="https://cmake.org/download/" target="_blank"> Download page </a>

![](screenshots/macOS/cmake_dmg_installer.png)
![](screenshots/macOS/cmake_app.png)

<a name="git"></a>

### Git

<a nme="install-git"></a>

#### Install Git

There are several ways to install Git on a Mac. In fact, if you've installed XCode (or it's Command Line Tools), Git may already be installed. To find out, open a terminal and enter `git --version.`

```bash
git --version
git version 2.7.0 (Apple Git-66)
```

Apple actually maintain and ship their own fork of Git, but it tends to lag behind mainstream Git by several major versions. You may want to install a newer version of Git using one of the methods below

<a name="git-for-mac-installer"></a>

##### Git for Mac Installer

The easiest way to install Git on a Mac is via the stand-alone installer:

1. Download the latest <a href="https://sourceforge.net/projects/git-osx-installer/files/" target="_blank">Git for Mac installer.</a>

2. Follow the prompts to install Git.

3. Open a terminal and verify the installation was successful by typing `git --version`
4. Configure your Git username and email using the following commands, replacing Soulimane's name with your own. These details will be associated with any commits that you create

   ```bash
   git config --global user.name "Soulimane MAMMAR"
   git config --global user.email "soulimane.mammar@gmail.com"
   ```

<a name="install-git-with-homebrew"></a>

##### Install Git with Homebrew

If you have [installed Homebrew](#install-homebrew) to manage packages on OS X, you can install Git by issuing the following command:

```bash
brew install git
```

<a name="text-editors"></a>

### Text Editors

There is a wealth of choices in text editors for C++ development that support advanced features such as code completion and name refactoring. To name just a few, we have:

- Atom
- Visual Studio Code
- Sublime Text
- Vim

<a name="visual-studio-code"></a>

#### Visual Studio Code

Visual Studio Code is probably one of the best choices for beginners today. It has a nice UI, offers some basic IDE features like completion and jumping to definitions

<a name="install-visual-studio-code"></a>

##### Install Visual Studio Code

You can install VSCode with Homebrew

```bash
brew install --cask visual-studio-code
```

or

1. <a href="https://go.microsoft.com/fwlink/?LinkID=534106" target="_blank">Download Visual Studio Code</a> for macOS.
2. Open the browser's download list and locate the downloaded app or archive.
3. If archive, extract the archive contents.
4. Drag `Visual Studio Code.app` to the **Applications** folder, making it available in the macOS Launchpad.
5. Open VS Code from the **Applications** folder, by double clicking the icon.
6. Add VS Code to your Dock by right-clicking on the icon, located in the Dock, to bring up the context menu and choosing **Options**, **Keep in Dock**.

<a name="launching-from-the-command-line"></a>

##### Launching from the command line

You can also run VS Code from the terminal by typing 'code' after adding it to the path:

- Launch VS Code.
- Open the **Command Palette** (`Cmd+Shift+P`) and type 'shell command' to find the **Shell Command: Install 'code' command in PATH** command.

![](screenshots/macOS/vscode_shell_command.png)

- Restart the terminal for the new `$PATH` value to take effect. You'll be able to type 'code .' in any folder to start editing files in that folder.

>**Note:** If you still have the old `code` alias in your `.bash_profile` (or equivalent) from an early VS Code version, remove it and replace it by executing the **Shell Command: Install 'code' command in PATH** command.

<a name="install-helper-extensions"></a>

##### Install helper extensions

Install `Microsoft C/C++` extension, It is a Language Server by Microsoft.
     ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Editor/VSCode/Extension_Cpp.png?raw=true)

Install two extensions for cmake. The first one (from twxs) in the list is for syntax highlighting when writing cmake scirpts. The second one (from Microsoft) in the list is for actually running Cmake.
     ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Editor/VSCode/Extension_Cmake.png?raw=true)

<a name="create-a-cmake-project"></a>

##### Create a CMake project

Create a folder for a new project. From the Terminal window, create an empty folder called cmakeQuickStart, navigate into it, and open VS Code in that folder by entering the following commands:

   ```bash
   mkdir cmakeQuickStart
   cd cmakeQuickStart
   code .
   ```

   The `code .` command opens VS Code in the current working folder, which becomes your "workspace".

<a name="create-a-cmake-hello-world-project"></a>

###### Create a CMake hello world project

The CMake Tools extension can create the files for a basic CMake project for you. Open the Command Palette (`Cmd+Shift+P`) and run the CMake: Quick Start command:
![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Linux/cmake-quickstart-command-palette.png?raw=true)

Enter a project name. This will be written to `CMakeLists.txt` and a few initial source files.

Next, select **Executable** as the project type to create a basic source file (`main.cpp`) that includes a basic `main()` function.

![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Linux/cmake-choose-type.png?raw=true)

>**_NOTE_** If you had wanted to create a basic source and header file, you would have selected **Library** instead. But for this tutorial, **Executable** will do. If you are prompted to configure IntelliSense for the folder, select **Allow**.

This creates a hello world CMake project containing `main.cpp`, `CMakeLists.txt` (which tells the CMake tools how to build your project), and a folder named `build` for your build files:

![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Linux/cmake-project-contents.png?raw=true)

<a name="select-a-kit"></a>

###### Select a kit

Before you can use the CMake Tools extension to build a project, you need to configure it to know about the compilers on your system. Do that by scanning for 'kits'. A kit represents a toolchain, which is the compiler, linker, and other tools used to build your project. To scan for kits:

1. Open the Command Palette (`Cmd+Shift+P`) and run CMake: Select a Kit. The extension will automatically scan for kits on your computer and create a list of compilers found on your system.
2. Select the compiler you want to use. For example, depending on the compilers you have installed, you might see something like:

![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Linux/cmake-selectkit.png?raw=true)

<a name="configure-hello-world"></a>

##### Configure Hello World

There are two things you must do to configure your CMake project: select a kit (which you just did) and select a variant.

The kit you selected previously is shown in the Status bar. For example:
![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Linux/cmake-kit-statusbar.png?raw=true)

To change the kit, you can click on the kit in the Status bar, or run the **CMake: Select a kit** command again from the Command Palette. If you don't see the compiler you're looking for, you can edit the `cmake-tools-kits.json` file in your project. To edit the file, open the Command Palette (`Ctrl+Shift+P`) and run the **CMake: Edit User-Local CMake Kits** command.

<a name="select-a-variant"></a>

###### Select a variant

A variant contains instructions for how to build your project. By default, the CMake Tools extension provides four variants, each corresponding to a default build type: `Debug`, `Release`, `MinRelSize`, and `RelWithDebInfo`. These options do the following:

`Debug`: disables optimizations and includes debug info.
`Release` : Includes optimizations but no debug info.
`MinRelSize` : Optimizes for size. No debug info.
`RelWithDebInfo` : Optimizes for speed and includes debug info.

To select a variant, open the Command Palette (`Ctrl+Shift+P`) run the CMake: Select Variant command.
![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Linux/cmake-select-variant.png?raw=true)

Select **Debug** to include debug information with your build.
![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Linux/cmake-variant-type.png?raw=true)
The selected variant will appear in the Status bar next to the active kit.

<a name="cmake-configure"></a>

###### CMake: Configure

Now that you've selected a kit and a variant, open the Command Palette (`Ctrl+Shift+P`) and run the **CMake: Configure** command to configure your project. This generates build files in the project's build folder using the kit and variant you selected.

<a name="build-hello-world"></A>

##### Build Hello World

To run and debug your project, open `main.cpp` and put a breakpoint on the `std::cout` line. Then open the Command Palette (`Cmd+Shift+P`) and run **CMake: Debug**. The debugger will stop on the `std::cout` line:
![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Linux/cmake-debug.png?raw=true)
Go ahead and press `F5` to continue.

<a name="using-libraries"></a>

### Using libraries

<a name="vcpkg"></a>

#### vcpkg

vcpkg is a free C/C++ package manager for acquiring and managing libraries. It allows us to choose from over 1500 open source libraries to download and build in a single step or add our own private libraries to simplify the build process. Maintained by the Microsoft C++ team and open source contributors.

<a name="install-vcpkg"></a>

##### Install vcpkg

Installing vcpkg is a two-step process:
first, clone the repo,

```bash
git clone https://github.com/Microsoft/vcpkg.git
```

then run the bootstrapping script to produce the vcpkg binary.

```bash
./vcpkg/bootstrap-vcpkg.sh
```

<a name="install-libraries-for-your-project"></a>

##### Install libraries for your project

```bash
vcpkg install [packages to install]
```

<a name="using-vcpkg-with-cmake"></a>

##### Using vcpkg with CMake

In order to use vcpkg with CMake outside of an IDE, you can use the toolchain file:

```bash
 cmake -B [build directory] -S . -DCMAKE_TOOLCHAIN_FILE=[path to vcpkg]/scripts/buildsystems/vcpkg.cmake 
```

Then build with:

```bash
cmake --build [build directory]
```

With CMake, you will need to find_package() to reference the libraries in your `Cmakelists.txt` files.

<a name="unit-testing"></a>

### Unit testing

<a name="google-test-gtest"></a>

#### Google Test (GTest)

Google test is a framework for writing C++ unit tests.

<a name="build-and-install-gtest"></a>

##### Build and install GTest

GoogleTest comes with a CMake build script (CMakeLists.txt) that can be used on a wide range of platforms ("C" stands for cross-platform.).
To build and install GoogleTest as a standalone project, issue the following command on the terminal

```bash
git clone https://github.com/google/googletest.git -b v1.14.0
cd googletest        # Main directory of the cloned repository.
mkdir build          # Create a directory to hold the build output.
cd build
cmake ..             # Generate native build scripts for GoogleTest.
make
sudo make install    # Install in /usr/local/ by default
```

<a name="using-gtest"></a>

##### Using GTest

Lets say we now want to test the following simple squareRoot function

```cpp
// whattotest.cpp
#include <math.h>
 
double squareRoot(const double a) {
    double b = sqrt(a);
    if(b != b) { // nan check
        return -1.0;
    }else{
        return sqrt(a);
    }
}
```

In the following code, we create two tests that test the function using a simple assertion. There exists many other assertion macros in the framework (see <https://google.github.io/googletest/primer.html>). The code contains a small main function that will run all of the tests automatically.

```cpp
// tests.cpp
#include "whattotest.cpp"
#include <gtest/gtest.h>
 
TEST(SquareRootTest, PositiveNos) { 
    ASSERT_EQ(6, squareRoot(36.0));
    ASSERT_EQ(18.0, squareRoot(324.0));
    ASSERT_EQ(25.4, squareRoot(645.16));
    ASSERT_EQ(0, squareRoot(0.0));
}
 
TEST(SquareRootTest, NegativeNos) {
    ASSERT_EQ(-1.0, squareRoot(-15.0));
    ASSERT_EQ(-1.0, squareRoot(-0.2));
}
 
int main(int argc, char **argv) {
    testing::InitGoogleTest(&argc, argv);
    return RUN_ALL_TESTS();
}
```

The next step is to compile the code. The  `CMakeLists.txt` file below to compile the tests. This file locates the google test library and links it with the test application. Note that we also have to link to the pthread library or the application won’t compile.

```cmake
cmake_minimum_required(VERSION 2.6)
 
# Locate GTest
find_package(GTest REQUIRED)
include_directories(${GTEST_INCLUDE_DIRS})
 
# Link runTests with what we want to test and the GTest and pthread library
add_executable(runTests tests.cpp)
target_link_libraries(runTests ${GTEST_LIBRARIES} pthread)
```

Compile and run the tests

```bash
cmake CMakeLists.txt
make
./runTests
```

<a name="addtional-tooling"></a>

### Addtional Tooling

<a name="clangformat"></a>

#### ClangFormat

Code formatting is an essential aspect of software development that ensures that the codebase is consistent, easy to read, and maintainable.
However, manually formatting code can be time-consuming and error-prone, especially for large projects. That's where automatic code formatting tools come in.
Clang-format is a powerful command-line tool for formatting C and C++ code. It can automatically format code according to a predefined set of rules or a custom configuration file.

<a name="installing-clang-format"></a>

##### Installing Clang-format

Before we can use Clang-format with VSCode, we need to install it on our system.

```bash
sudo apt install clang-format
```

<a name="configuring-clang-format"></a>

##### Configuring Clang-format

Clang-format can be configured using a variety of options, including

- command-line arguments
- configuration files
- editor extensions.

We will focus on using a configuration file to customize the formatting rules.
A Clang-format configuration file is a text file that specifies the formatting options for Clang-format.
The file should be named .clang-format and placed in the root directory of your project.

Here is an example configuration file:

```text
BasedOnStyle: Google
IndentWidth: 4
ColumnLimit: 120
```

This configuration file specifies that the formatting style should be based on the Google C++ style guide, the indent width should be 4 spaces, and the column limit should be 120 characters.

The Clang-format documentation provides a comprehensive list of options that can be used in the configuration file.
<a href="https://clang.llvm.org/docs/ClangFormatStyleOptions.html" target="_blank">https://clang.llvm.org/docs/ClangFormatStyleOptions.html</a>

<a name="using-clang-format-with-vscode"></a>

##### Using Clang-format with VSCode

ClangFormat is supported by VSCode C++ extension out-of-the-box.
ClangFormat settings can be found in C++ extension settings.
![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Tooling/ClangFormat/ClangFormat-vscode.png?raw=true)

<a name="cc-include-guard-proud-contributor"></a>

#### C/C++ include guard (proud contributor)

is a [VSCode](#install-visual-studio-code) extension that automatically add include guard for you so that you no longer need to remember it.
Download <a href="https://marketplace.visualstudio.com/items?itemName=akiramiyakoda.cppincludeguard" target="_blank">here</a>.

<a name="include-info-proud-maker"></a>

#### include-info (proud maker)

is a [VSCode](#install-visual-studio-code) extension that shows the included header file size
and provide a fast way to jump to those included files.
Download <a href="https://marketplace.visualstudio.com/items?itemName=HO-COOH.include-info" target="_blank">here</a>
