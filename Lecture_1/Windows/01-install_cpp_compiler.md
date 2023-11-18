[//]: # (### Download & Install a C++ compiler)
This section will cover the installation of `GCC`, `Clang` and `MSVC`.

- [GCC \& Clang](#gcc--clang)
  - [Download \& Install MSYS2](#download--install-msys2)
  - [Install GCC](#install-gcc)
  - [Install Clang](#install-clang)
  - [What is MSYS2 and Why?](#what-is-msys2-and-why)
- [MSVC](#msvc)

<a name="gcc--clang"></a>

#### GCC & Clang

<a name="download--install-msys2"></a>

##### Download & Install MSYS2

<a href="https://www.msys2.org/" target="_blank">Download here</a>

Just launch the installer and keep clicking "Next"

<a name="install-gcc"></a>

##### Install GCC

If you also want to install `clang`, skip this part and go directly to [Install Clang](#install-clang), because GCC is a dependency of Clang (on MSYS2) and will be automatically installed when you install clang.

1. Run MSYS2, type the following command:

```bash
pacman -Syu
```

`pacman` is the package manager used by MSYS2. `-S` means "sync". `-y` means "download fresh package databases from the server". `-u` means "upgrade installed packages".

This command will update the packages info, so you get the latest packages. It will prompt you like this, and you type `y` and hit enter.
![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Compiler/MSYS2/1.png?raw=true)

1. Then it will prompt you `To complete this update all MSYS2 processes including this terminal will be closed. Confirm to proceed [Y/n]`, type `y` and hit enter, and it will close the window after the update is done.
2. Relaunch MSYS2 from your start menu. Type:

```bash
pacman -S mingw-w64-x86_64-gcc
```

like this, type `y` and hit enter to install gcc
![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Compiler/MSYS2/2.png?raw=true)

And then type:

```bash
pacman -S mingw-w64-x86_64-make
```

And type `y` to also install `make`.

And then type:

```bash
pacman -S mingw-w64-x86_64-gdb
```

And type `y` to also install `gdb`.

5. Now search for `environment variable` and open it
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Compiler/MSYS2/3.png?raw=true)

6. Click `Environment Variables`, find `Path` in `System variables`, double click to open the setting.
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Compiler/MSYS2/4.png?raw=true)

7. Click `New` and copy `C:\msys64\mingw64\bin` to the new entry.
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Compiler/MSYS2/5.png?raw=true)

8. Click `OK` to close all windows. Now you finished installing GCC. Open any shell such as `cmd` and type in `gcc --version` and you shall see the following: ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Compiler/gcc/gcc-version.png?raw=true)

<a name="install-clang"></a>

##### Install Clang

Installing Clang will also automatically install `GCC` (on MSYS2).

1. Run MSYS2, type the following command:

```bash
pacman -Syu
```

`pacman` is the package manager used by MSYS2. `-S` means "sync". `-y` means "download fresh package databases from the server". `-u` means "upgrade installed packages".

This command will update the packages info, so you get the latest packages. It will prompt you like this, and you type `y` and hit enter.
![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Compiler/MSYS2/1.png?raw=true)

3. Then it will prompt you `To complete this update all MSYS2 processes including this terminal will be closed. Confirm to proceed [Y/n]`, type `y` and hit enter, and it will close the window after the update is done.

4. Relaunch MSYS2 from your start menu. Type:

```bash
pacman -S mingw-w64-x86_64-clang mingw-w64-x86_64-clang-tools-extra
```

like this, type `y` and hit enter to install clang
![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Compiler/clang/clang.png?raw=true)

And then type:

```bash
pacman -S mingw-w64-x86_64-make
```

And type `y` to also install `make`.

And then type:

```bash
pacman -S mingw-w64-x86_64-gdb
```

And type `y` to also install `gdb`.

5. Now search for `environment variable` and open it
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Compiler/MSYS2/3.png?raw=true)

6. Click `Environment Variables`, find `Path` in `System variables`, double click to open the setting.
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Compiler/MSYS2/4.png?raw=true)

7. Click `New` and copy `C:\msys64\mingw64\bin` to the new entry.
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Compiler/MSYS2/5.png?raw=true)

8. Click `OK` to close all windows. Now you finished installing clang. Open any shell such as `cmd` and type in `clang --version` and you shall see the following: ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Compiler/clang/clang-version.png?raw=true)

Note: `Clang` and `GCC` is installed to the same directory, eg. under `C:\msys64\mingw64\bin`. Don't be confused by the directory `C:\msys64\clang64`. It is an empty folder.

<a name="what-is-msys2-and-why"></a>

##### What is MSYS2 and Why?

> MSYS2 is a collection of tools and libraries providing you with an easy-to-use environment for building, installing and running native Windows software.

But basically, we use its implementation of MingW(Minimalist GNU for Windows), which is a collection of common developing tools seen on GNU/Linux operating systems.

<a name="msvc"></a>

#### MSVC

MSVC is Microsoft Visual C++ compiler. And you do NOT have to install Visual Studio in order to get MSVC. However, if you also want Visual Studio, skip to [setting up visual studio](#setting-up-visual-studio) directly.

1. Download <a href="https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019" target="_blank">MSVC</a>, select `Build Tools for Visual Studio 2019`
2. Launch the installer and select these workflows
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Compiler/MSVC/Installer.png?raw=true)
3. You have finished installing MSVC. Click `Launch` and type `cl` and you should see this:
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Compiler/MSVC/InstallFinish.png?raw=true)

Do NOT try to add `MSVC` directly to system `PATH` because each compiler toolchain for different architecture has its own version.

This command prompt is specific to 64bit Windows architecture and has set some temporary environment variables. You can find it in `Start` -> `Visual Studio 2019` -> `Developer Command Prompt for VS 2019` like this: ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Compiler/MSVC/Location.png?raw=true)

After MSVC is installed, cmake can detect it as a compiler.
![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Compiler/MSVC/Cmake_VSCode.png?raw=true)
![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Compiler/MSVC/Cmake_Clion.png?raw=true)

<a name="download--install-cmake"></a>
