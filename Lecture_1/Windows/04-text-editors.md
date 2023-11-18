<a name="text-editors"> </a>

[//]: # (### Text editors)

<a name="setting-up-vscode"></a>

#### Setting up VSCode

1. Download <a href="https://code.visualstudio.com/" target="_blank"> vscode</a>
2. Launch the installer, when you see this screen, I **strongly recommend you follow this setting**
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Editor/VSCode/Installer.png?raw=true)

3. Run vscode, in the `extension` tab, search and install the following extensions

   - Install `Microsoft C/C++` extension, It is a Language Server by Microsoft.
     ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Editor/VSCode/Extension_Cpp.png?raw=true)
   - And 2 extensions for cmake. The first one in the list is for syntax highlighting when writing cmake scirpts.
   - The second one in the list is for actually running Cmake.
     ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Editor/VSCode/Extension_Cmake.png?raw=true)

4. Go to settings, search `generator`. And set `Cmake:Generator` to `MinGW Makefiles`, like this:
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Editor/VSCode/Cmake_Setting.png?raw=true)

5. Create a folder, open it in vscode. Use `ctrl + shift + p` to open the command menu, type `cmake` and choose `CMake: Quick Start`, like this:
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Editor/VSCode/CMake_QuickStart.png?raw=true)

6. The cmake tool will scan the kits and there will be 2 kits. Select the first one.
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Editor/VSCode/CMake_Kit.png?raw=true)

7. Type a name for your project, select `Executable`, CMake tool will automatically generate a helloworld project for you. And you probably don't want to enable ctest for now, so delete everything excpet the following 3 lines:
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Editor/VSCode/CMake_Quick.png?raw=true)
   Rememeber to click `Allow` when cmake want to configure the intellisense.

8. And now you can run it and debug it, and have everything working (syntax highlighting, auto complete, header files...).
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Editor/VSCode/Cmake_Project.png?raw=true)
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Editor/VSCode/Cmake_Run.png?raw=true)
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Editor/VSCode/Cmake_Debug.png?raw=true)
