[//]: # (### IDEs)

This section will cover setting up `Visual Studio` but there are plenty of other choices out there like `Dev-C++`, `CLion`, `QtCreator`, `Cevelop (based on Eclipse)` and `Eclipse`.

<a name="setting-up-visual-studio"></a>

#### Setting up Visual Studio

You can install Visual Studio as a standalone IDE or as a whole package including compiler, toolchain and windows sdk.

<a name="full-package"></a>

##### Full package

1. <a href="https://visualstudio.microsoft.com/downloads/" target="_blank">Visual studio</a>. Choose the `Community` option.

2. Run the installer, select these workflows
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/IDE/VisualStudio/Installer.png?raw=true)

3. After installation, you are prompt to restart your computer. And then you will need to register a Microsoft Account to continue using Visual Studio.

4. Run Visual Studio, select `Create a new project` -> `Empty Project/Console App`, and select `Place solution and project in the same directory`.
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/IDE/VisualStudio/CreateProject.png?raw=true)
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/IDE/VisualStudio/CreateProject2.png?raw=true)
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/IDE/VisualStudio/CreateProject3.png?raw=true)
   The only difference between `Empty Project` and `Console App` is the latter will provide you with a "Hello world" program and that's it! All the default include directories and default linked runtime libraries are the same!

- If you choose to create `Empty Project`, right click on the `<Project Name>` -> `Add` -> `New item` -> `C++ source file` -> `Add`, like this:
  ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/IDE/VisualStudio/EmptyProject1.png?raw=true)
  ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/IDE/VisualStudio/EmptyProject2.png?raw=true)
  Then write a simple "Hello world" program and hit `ctrl+f5` to compile and run it, and you shall see this:
  ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/IDE/VisualStudio/EmptyProject3.png?raw=true)

- If you choose to create `Console App`, you shall see the already created "Hello world". Hit `ctrl+f5` to compile and run the program and you shall see this: ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/IDE/VisualStudio/ConsoleApplication.png?raw=true)

<a name="standalone-ide"></a>

##### Standalone IDE

If you install Visual Studio as a standalone IDE without installing MSVC compiler toolchains, you can use it with CMake. If you have installed MSVC compiler toolchain, you can use it with Visual Studio solution just as it's a [full install](#full-package) like above. Here I introduce how to use it with CMake, **without MSVC**.

1. <a href="https://visualstudio.microsoft.com/downloads/" target="_blank">Visual studio</a>. Choose the `Community` option.

2. Run the installer, select these workflows and deselect all the optionals on the right, like this
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/IDE/VisualStudio/InstallStandalone.png?raw=true)

3. After installation, you need to register a Microsoft Account to continue using Visual Studio.

4. Run Visual Studio, select `Create a new project` -> `CMake Project` -> select `Place Project under the same directory` -> `Create`, like this:
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/IDE/VisualStudio/CreateProject.png?raw=true)
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/IDE/VisualStudio/CMakeProject1.png?raw=true)
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/IDE/VisualStudio/CMakeProject2.png?raw=true)
5. Visual Studio will auto generate a "Hello world" project for you, and it can successfully configure the project and compile because CMake can detect the installed `GCC`. However, it will have incorrect include errors.
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/IDE/VisualStudio/CMakeProject3.png?raw=true)
6. To solve this error, click on the configuration menu -> `Manage Configurations` -> click the add button -> select `Mingw64-Debug` -> click on the previous old configuration and click delete button
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/IDE/VisualStudio/CMakeProject4.png?raw=true)
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/IDE/VisualStudio/CMakeProject5.png?raw=true)
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/IDE/VisualStudio/CMakeProject6.png?raw=true)
7. Hit `ctrl+s` to save this configuration, then the include error should go away.
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/IDE/VisualStudio/CMakeProject9.png?raw=true)

Note: If for some reason, Visual Studio doesn't detect the right MingW version, you will still get include errors. You need to edit the `CMakeSettings.json` and correct the MingW version, like this:
![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/IDE/VisualStudio/CMakeProject7.png?raw=true)
![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/IDE/VisualStudio/CMakeProject8.png?raw=true)
