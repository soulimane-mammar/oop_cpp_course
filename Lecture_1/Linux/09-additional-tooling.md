<a name="addtional-tooling"></a>

[//]: # (### Addtional Tooling)

<a name="clangformat"></a>

#### ClangFormat

Code formatting is an essential aspect of software development that ensures that the codebase is consistent, easy to read, and maintainable.
However, manually formatting code can be time-consuming and error-prone, especially for large projects. That's where automatic code formatting tools come in.
Clang-format is a powerful command-line tool for formatting C and C++ code. It can automatically format code according to a predefined set of rules or a custom configuration file.

<a name="installing-clang-format"></a>

##### Installing Clang-format

Before we can use Clang-format with VSCode, we need to install it on our system.

```bash
sudo apt install clang-format
```

<a name="configuring-clang-format"></a>

##### Configuring Clang-format

Clang-format can be configured using a variety of options, including

- command-line arguments
- configuration files
- editor extensions.

We will focus on using a configuration file to customize the formatting rules.
A Clang-format configuration file is a text file that specifies the formatting options for Clang-format.
The file should be named .clang-format and placed in the root directory of your project.

Here is an example configuration file:

```text
BasedOnStyle: Google
IndentWidth: 4
ColumnLimit: 120
```

This configuration file specifies that the formatting style should be based on the Google C++ style guide, the indent width should be 4 spaces, and the column limit should be 120 characters.

The Clang-format documentation provides a comprehensive list of options that can be used in the configuration file.
<a href="https://clang.llvm.org/docs/ClangFormatStyleOptions.html" target="_blank">https://clang.llvm.org/docs/ClangFormatStyleOptions.html</a>

<a name="using-clang-format-with-vscode"></a>

##### Using Clang-format with VSCode

ClangFormat is supported by VSCode C++ extension out-of-the-box.
ClangFormat settings can be found in C++ extension settings.
![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Tooling/ClangFormat/ClangFormat-vscode.png?raw=true)

<a name="cc-include-guard-proud-contributor"></a>

#### C/C++ include guard (proud contributor)

is a [VSCode](#install-visual-studio-code) extension that automatically add include guard for you so that you no longer need to remember it.
Download <a href="https://marketplace.visualstudio.com/items?itemName=akiramiyakoda.cppincludeguard" target="_blank">here</a>.

<a name="include-info-proud-maker"></a>

#### include-info (proud maker)

is a [VSCode](#install-visual-studio-code) extension that shows the included header file size
and provide a fast way to jump to those included files.
Download <a href="https://marketplace.visualstudio.com/items?itemName=HO-COOH.include-info" target="_blank">here</a>
