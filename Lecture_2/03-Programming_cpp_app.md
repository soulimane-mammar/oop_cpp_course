#### Steps in Building an Executable

The basic steps in creating applications in C++ are the following:

1. Write C++ code using a text editor, which is commonly a code editor or an integrated development environment (IDE). (Refer to <a href="">Lecture 1</a> for instructions on installing a suitable development environment).
2. Compile code using a C++ compiler that creates a machine language version contained in
“object files.”
3. Link the object files by using a linker to get an executable (.exe in Windows, for
example).

In the compilation step of C++, code in .cpp files is transformed into processor-executable bytecode. The compiler processes one code file at a time, producing an object file (.o or .obj extension), while disregarding dependencies on code in other files.

#### Analyzing Errors and Debugging

Applications, especially large or complex ones written in any language, including C++, often require multiple runs to identify and address errors, referred to as bugs. In addition to programming, compiling, and linking, software development includes debugging, where programmers analyze and rectify code errors. Quality development environments provide tools and features to facilitate the debugging process.

#### Programming Your First C++ Application

Enter the following listing in your favorite text editor/ide and save it as `hello.cpp`

```cpp
1: #include <iostream>
2: int main()
4: {
5:    std::cout << “Hello World!” << std::endl;
6:    return 0;
7: }
```

This simple application does nothing more than display the customary “Hello World!”
greeting on the screen using `std::cout`. `std::endl` instructs `cout` to end that line by inserting a line break, and the application exits by returning `0` to the operating system.

> Compilers are strict, and if you mistakenly put a `:` at the end of a statement where a `;` is required, you can expect a compilation failure accompanied by an error message!

#### Building and Executing Your First C++ Application

If you’re using the `g++` compiler by GCC, you can open the terminal, navigate to the directory containing `hello.cpp`, and invoke the compiler and linker by using the command line:

```bash
g++ -o hello hello.cpp
```

Alternatively, if you are using the `clang++` compiler use the following line:

``` bash
clang++ -o hello Hello.cpp
```

If you’re using macOS with Xcode, then you can build and run your application by selecting
Product, Run.

If you’re using Microsoft Visual Studio on Windows, press `Ctrl+F5` to run your program
directly via the IDE. This compiles, links, and executes your application.

When you execute `./hello` or `hello.exe`, you get the following output:

```
Hello World!
```
