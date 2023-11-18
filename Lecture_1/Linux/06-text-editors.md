<a name="text-editors"></a>

[//]: # (### Text Editors)

There is a wealth of choices in text editors for C++ develpment that support advanced features such as code completion and name refactoring. To name just a few, we have:

- Atom
- Visual Studio Code
- Subime Text
- Vim

<a name="install-visual-studio-code"></a>

#### Install Visual Studio Code

Visual Studio Code is probably one of the best choices for beginners today. It has a nice UI, offers some basic IDE features like completion and jumping to definitions

The easiest way to install Visual Studio Code for Debian/Ubuntu based distributions is to download and install the <a href="https://go.microsoft.com/fwlink/?LinkID=760868" class="external-link" target="_blank">.deb package (64-bit)</a>, either through the graphical software center if it's available, or through the command line with:

```bash
sudo apt install ./<file>.deb
```

Visual Studio Code is also officially distributed as a Snap package in the Snap Store and you can install it by running

```bash
sudo snap install --classic code
```

Using Fatpak is another way to install Visual Studio Code

```bash
flatpak install flathub com.visualstudio.code
```

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

The CMake Tools extension can create the files for a basic CMake project for you. Open the Command Palette (`Ctrl+Shift+P`) and run the CMake: Quick Start command:
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

1. Open the Command Palette (`Ctrl+Shift+P`) and run CMake: Select a Kit. The extension will automatically scan for kits on your computer and create a list of compilers found on your system.
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

To run and debug your project, open `main.cpp` and put a breakpoint on the `std::cout` line. Then open the Command Palette (`Ctrl+Shift+P`) and run **CMake: Debug**. The debugger will stop on the `std::cout` line:
![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Linux/cmake-debug.png?raw=true)
Go ahead and press `F5` to continue.
