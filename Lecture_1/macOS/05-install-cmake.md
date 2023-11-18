<a name="install-cmake"></a>

[//]: # (### Install CMake)

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

![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/macOS/cmake_dmg_installer.png?raw=true)
![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/macOS/cmake_app.png?raw=true)
