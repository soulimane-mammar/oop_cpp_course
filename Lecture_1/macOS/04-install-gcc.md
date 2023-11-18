<a name="install-gcc"></a>

[//]: # (### Install GCC)

macOS comes with the Clang C/C++ compiler included with Xcode. You can check its version and ensure it's installed by running

```bash
clang++ --version
```

If you prefer using GCC, you can install it using Homebrew

<a name="install-homebrew"></a>

1. Install Homebrew (if not already installed)

   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

2. Install GCC

   ```bash
   brew install gcc
   ```

<a name="install-cmake"></a>
