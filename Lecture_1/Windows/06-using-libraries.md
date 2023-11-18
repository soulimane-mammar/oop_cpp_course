[//]: # (### Using libraries)

<a name="setting-up-vcpkg"></a>

#### Setting up vcpkg

`vcpkg` is a C/C++ package manager, which makes using libraries much easier (almost as easy as using `pip` in python).

1. Open a shell(`cmd`) and go to the directory where you want `vcpkg` to be installed. (Something like `C:\` or `C:\dev`)
2. Type this command:

   ```bash
   git clone https://github.com/microsoft/vcpkg
   ```

3. Type this command:

   ```bash
   .\vcpkg\bootstrap-vcpkg.bat
   ```

4. Type this command:

   ```bash
   .\vcpkg\vcpkg.exe integrate install
   ```

<a name="finding-and-installing-a-library"></a>

#### Finding and Installing a library

- To find a library, use `vcpkg search <library>`
- To install a library, use `vcpkg install <library>:x64-windows` or `vcpkg install <library>:x86-windows`

> [!NOTE] > `vcpkg` will build 32 bit libraries by default on Windows (although it's 64 bit on Linux by default), which is NOT probably what you want, so you want to speficy the architecture by adding `:x64-windows`.

<a name="using-a-library"></a>

#### Using a library

After you install the library in `vcpkg`, you either:

- Use `Visual Studio` without **ANY ADDITIONAL CONFIGURATION**
- Use `cmake` with the instruction provided by `vcpkg` when you install the library.

Below is a complete example of using `vcpkg` to install and use the [boost](https://www.boost.org/) library.

1. Install the library in `vcpkg` with `vcpkg install <Library Name>`, like this:

   ```bash
   vcpkg install boost:x64-windows
   ```

   And you should see the following
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/vcpkg/vcpkg_install.png?raw=true)

2. Note that on Windows, `vcpkg` builds libraries using `MSVC`, so you should also use `MSVC` in order to link sucessfully. Header-only libraries like `boost` may be used with other compilers like `GCC`.

Afrer the library finishes installing, you can either:

- Use it in Visual Studio without doing any additional configuration
  ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/vcpkg/vcpkg_VisualStudioIntegration.png?raw=true)
  **Note: Configure the solution achitectural target correctly according to your library. Visual Studio empty project defaults to `x86` but you may installed `x64` library.**

- Or use it in VSCode/CLion with cmake and cmake tool chain file. See the docs [here](https://github.com/microsoft/vcpkg#using-vcpkg-with-cmake)
