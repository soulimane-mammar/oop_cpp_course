[//]: # (## Unit Testing)

<a href="https://en.wikipedia.org/wiki/Unit_testing" target="_blank">What is unit testing? </a>

<a name="google-test"></a>

### Google Test

<a href="https://github.com/google/googletest" target="_blank">google test</a> is a famous and widely supported by IDEs/text editors unit testing framework for C++.

You can get google test by these ways

- Using `vcpkg`: Following setting up `vcpkg`, we can easily install the library by

  ```bash
  vcpkg install gtest:x64-windows
  ```

  Note that if your application is targeted to 32 bit, use this command instead

  ```bash
  vcpkg install gtest
  ```

- Using `MSYS2`: Note that this can only be used with `GCC & Clang` compiler from `MSYS2`.

  ```bash
  pacman -S pacman -S mingw-w64-x86_64-gtest
  ```

After installing the library,

- If you use Visual Studio (MSBuild Project), you just need to `#include <gtest/gtest.h>` like a normal C++ source file and either:

  - Provide a `main` function at the bottom of your source file

    ```cpp
    int main(int argc, char **argv)
    {
        ::testing::InitGoogleTest(&argc, argv);
        return RUN_ALL_TESTS();
    }
    ```

    ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Gtest/../UnitTest/GTest/VSBuild.png?raw=true)
  - Don't provide a `main` function, then you need to link additional libraries in the linker settings.

    1. Right click on your project -> `Properties` -> `Linker` -> `AdditionalDependencies`,
       Make sure this configuration is `Debug` and `x64`
       (or x86 depend on the architect or your installed Gtest library)
       and add these 2 lines

    ```text
    gtestd.lib
    $(VcpkgRoot)installed\$(VcpkgTriplet)\debug\lib\manual-link\gtest_maind.lib
    ```

    ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/UnitTest/GTest/VSBuildMain.png?raw=true)

    1. Click the configuration menu to `Release` and also add these 2 lines, like this

    ```text
    gtest.lib
    $(VcpkgRoot)installed\$(VcpkgTriplet)\lib\manual-link\gtest_main.lib
    ```

    ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/UnitTest/Gtest/VSBuildMainRelease2.png?raw=true)

    Then you should be able to write the test source file without the `main` function, and build in both configurations like this

    - Debug build
      ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/UnitTest/GTest/VSBuildMainDebug.png?raw=true)
    - Release build
      ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/UnitTest/GTest/VSBuildMainRelease.png?raw=true)

- If you use CMake, regardless of whether you installed `Google Test` library from `vcpkg` or `MSYS2`,
  you can make use of `CTest` built-in to Cmake as a test runner to run your google test,
  which is supported by most IDE/editors you will see below.
  A minimum `CMakeLists.txt` is like:

```cmake
cmake_minimum_required(VERSION 3.10.0)

project(<project name> VERSION 0.1.0)

find_package(GTest CONFIG REQUIRED)
enable_testing()
include(GoogleTest) #for gtest_discover_tests() function

add_executable(<test target name> test.cpp) #This is the testing executable
target_link_libraries(<test target name> PRIVATE GTest::gtest GTest::gtest_main) #Link it to the google test library
gtest_discover_tests(<test target name>)  #integrate google test with ctest to this testing executable
```

- Or you simply want a testing executable, so you don't bother with `CTest`.

```cmake
cmake_minimum_required(VERSION 3.10.0)

project(<project name> VERSION 0.1.0)

find_package(GTest CONFIG REQUIRED)
add_executable(<test target name> test.cpp) #This is the testing executable
target_link_libraries(<test target name> PRIVATE GTest::gtest GTest::gtest_main) #Link it to the google test library
```

![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/UnitTest/GTest/MSYS2.VSCode.png?raw=true)

<a name="integration-with-vscode"></a>

#### Integration with VSCode

You need to use [`CTest`](#google-test) (the first version of the minimum `CMakeLists.txt`) as your test runner to get the integration working.

1. Install the <a href="https://marketplace.visualstudio.com/items?itemName=fredericbonnet.cmake-test-adapter" target="_blank"> CMake Test Explorer</a> extension (proud contributor)
2. Open VSCode settings, go to `Extension` -> `CMake Test Explorer` section, and change these following settings:
   - Build Config: `${buildType}`
   - Build Dir: `${buildDirectory}`
   - Select Cmake Integration
     ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/UnitTest/GTest/VSCodeIntegration.png?raw=true)
3. After that, build your project once and then click the `refresh test` button, this plugin should find all the testing suites and test cases in your test files.
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/UnitTest/GTest/VSCodeIntegration2.png?raw=true)
4. Then you can easily manage or debug all your test cases or each individual test in this panel.
   ![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/UnitTest/GTest/VSCodeIntegration3.png?raw=true)

---

<a name="source-control"></a>
