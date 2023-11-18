[//]: # (### Download & Install CMake)

You can either install CMake by using the official installer or using a package manager like `MSYS2`,
which you used to install `GCC` and `Clang`.

- Using the installer:

  1. <a href="https://cmake.org/download/" target="_blank">Download here</a>, choose the `Windows win64-x64 Installer` option

  2. Launch the insatller, when you see this screen, choose `Add CMake to the system PATH for all users`
     ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/CMake_Installer.png?raw=true)
     Now you finished installing cmake.

- Using `MSYS2`:
  1. Run `MSYS2` and type this command and type `Y` to install

  ```bash
  pacman -S mingw-w64-x86_64-cmake
  ```

  2. Search for `environment variable` and open it -> `Environment Variables`, find `Path` in `System variables`, double click to open the setting -> click `New` and copy `C:\msys64\usr\bin` to the new entry.
     ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/SourceControl/Git.png?raw=true)

<a name="what-is-cmake-and-why"></a>

#### What is CMake and Why?

CMake is a cross-platform build-system generator, which generates build files (some files dictating how your source files should be built) for your platform.

For example, on Windows by default, it generate `Visual Studio Solutions` (which is some files dicating how your source files should be built, native to `Visual Studio`) if you have Visual Studio installed. On Linux by default, it generates `Unix Makefiles` (which is some files dictating how your source files should be built, native to `make`).

Note:
> It is a bug if your C/C++ project does NOT provide CMake support.

---

<a name="ides"></a>
