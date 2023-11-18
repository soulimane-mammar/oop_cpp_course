<a name="install-the-build-essential-package"></a>

[//]: # (### Install the build-essential package)

The build-essentials packages are the form of meta-packages that are essential to compile software. They contain the GNU/g++ compiler collection, GNU debugger, and a few more libraries and tools that are needed for compiling a program. A few other packages, like GCC, make, G++, dpkg-dev, etc., are also installed on our system when we install the build-essential packages.
This meta-package contains five different packages that are important to compile software on Debian/Ubuntu.

- **g++**: It is a GNU compiler for C++ language.
- **gcc**: It is a GNU compiler for C language.
- **make**: It is a helpful utility that is used to direct the program's compilation. The tool, i.e., make, interprets a file known as "makefile" that can guide the compiler on how to operate.
- **libc6-dev**: It is a GNU C library. It includes the header files and development directories used for compiling general C++ and C scripts.
- **dpkg-dev**: This package is used to upload, build, and unpack Debian source packages. It is helpful if we wish to package our application for a Debian-based system.

To install the build-essential package type the following command

```bash
sudo apt install build-essential -y
```

![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Linux/build_essential.png?raw=true)
