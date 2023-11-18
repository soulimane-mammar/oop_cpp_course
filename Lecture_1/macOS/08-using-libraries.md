<a name="using-libraries"></a>

[//]: # (### Using libraries)

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
