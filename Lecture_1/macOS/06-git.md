<a name="git"></a>

[//]: # (### Git)

<a nme="install-git"></a>

#### Install Git

There are several ways to install Git on a Mac. In fact, if you've installed XCode (or it's Command Line Tools), Git may already be installed. To find out, open a terminal and enter `git --version.`

```bash
git --version
git version 2.7.0 (Apple Git-66)
```

Apple actually maintain and ship their own fork of Git, but it tends to lag behind mainstream Git by several major versions. You may want to install a newer version of Git using one of the methods below

<a name="git-for-mac-installer"></a>

##### Git for Mac Installer

The easiest way to install Git on a Mac is via the stand-alone installer:

1. Download the latest <a href="https://sourceforge.net/projects/git-osx-installer/files/" target="_blank">Git for Mac installer.</a>

2. Follow the prompts to install Git.

3. Open a terminal and verify the installation was successful by typing `git --version`
4. Configure your Git username and email using the following commands, replacing Soulimane's name with your own. These details will be associated with any commits that you create

   ```bash
   git config --global user.name "Soulimane MAMMAR"
   git config --global user.email "soulimane.mammar@gmail.com"
   ```

<a name="install-git-with-homebrew"></a>

##### Install Git with Homebrew

If you have [installed Homebrew](#install-homebrew) to manage packages on OS X, you can install Git by issuing the following command:

```bash
brew install git
```
