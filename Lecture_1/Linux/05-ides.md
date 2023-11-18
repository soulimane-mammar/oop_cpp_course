<a name="ides"></a>

[//]: # (### IDEs)

Linux provides a wealth of options for C++ Integrated Development Environments (IDEs), allowing you to choose the tool that best suits your needs. Popular choices include Code::Blocks, Eclipse, and CLion.
In the following we'll explore the process of setting up **Code::Blocs**

<a name="code-blocs"></a>

#### Code::Blocks

Code::Blocks is a free C/C++ and Fortran IDE built to meet the most demanding needs of its users. It is designed to be very extensible and fully configurable.

##### Install using the APT package manager

The best way to install CodeBlocks on a Debian/Ubuntu based system is to use its native package manager APT.

```bash
sudo apt install codeblocks
```

![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Linux/codeblocks.png?raw=true)

To have more features through this IDE you can install some additional plugins available through the packages called codeblocks-contrib.

```bash
sudo apt install codeblocks-contrib
```

![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Linux/codeblocks_contrib.png?raw=true)

##### Install using Flatpak

If the above-given method is not working for you then use the Flatpak. It is a universal package manager that we can use to easily install using the default system repository of Ubuntu 22.04 or 20.04.

```bash
sudo apt install flatpak
```

After installing the Flatpak, add its FlatHub repository as well.

```bash
sudo flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

Once you have added the repo, restart your PC to integrate the Flatpak properly into the system.

```bash
sudo reboot
```

Now, run the given command to install the Code::block IDE on the system.

```bash
flatpak install flathub org.codeblocks.codeblocks
```

![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Linux/code_blocks_flatpak.png?raw=true)

Run Code::Block

```bash
codeblocks &
```

![](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/screenshots/Linux/codeblocs_ide.png?raw=true)
