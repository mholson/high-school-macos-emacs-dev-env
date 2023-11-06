# High School Web-Development & Programming Environment Setup

![Doom Emacs Setup](/assets/emacs_install_emacs-plus-doom.png)

Watch the YouTube video: [Installing emacs-plus and Doom on a Macbook Air M1 using Homebrew](https://www.youtube.com/embed/A6SxH9lUWV0?si=7_F8CXkxaoP9RtQm).

Welcome to the GitHub repository dedicated to setting up MacBook computers for teaching high school courses in web development and programming. This repository is designed to streamline the environment setup, allowing educators and students to focus on learning and teaching without the overhead of complex installation processes.

The primary goal is to create a consistent development environment across all machines using a series of scripts and configuration files. This ensures that all students have the same starting point and can work on projects with minimal setup-related issues.

## Features

**Homebrew Installation:** Homebrew, the missing package manager for macOS, which simplifies the installation of software on Apple's macOS operating system.

**Emacs-Plus and Doom Emacs:** Steps to install Emacs-Plus, a versatile version of GNU Emacs with additional features, and Doom Emacs, a configuration framework for GNU Emacs. A pre-defined Doom Emacs config directory is included to help students quickly set up an efficient and pleasant editing experience that’s tuned for the web development and programming courses.

**Anaconda for Python:** Instructions on how to use Anaconda to manage Python packages and environments, ensuring a consistent and reproducible Python setup across all machines.

**Update Procedures:** Detailed instructions on how to keep the MacBook computers updated with the latest tools and security patches.

# Setup Instructions

## Download the files from this repository

![Download the repository setup files](/assets/mho-teaching-config.png)

## Install xcode command line developer tools

``` shell
x-code-select --install
```

## Install Homebrew

> [!IMPORTANT]
> xcode command line developer tools must be installed first.

We will be using [Homebrew](https://brew.sh) to manage the software on our MacBooks.  
[Download the MacOs package installer](https://github.com/Homebrew/brew/releases/latest)

## Update your .zshrc file

We need to make sure that the command `brew` is on your PATH, which means you can run it 
from your terminal shell.  Since we are using the **zsh** shell, 
I have included an `dot.zshrc`, I have updated this file for you.

Move the file `dot.zshrc`from the files you downloaded to your home directory `SHIFT-CMD-H`.

Since `dot.zshrc` is a hidden dot file, we should toggle the Finder app to view hidden 
files by pressing `SHIFT-CMD-.`

Rename `dot.zshrc` to `.zshrc`

To have the shell apply the changes you've made to the `.zshrc` file, without having to open a new terminal session, run the following from your terminal while in your home directory.

> [!NOTE]
> Quick Tip!  You can quickly navigate to your home directory from the terminal by using the command `cd SPACE`, where `SPACE` is one space created with your space-bar.

``` shell
cd [SPACE]
source .zshrc
```

## Install Emacs-Plus

Using brew to install [emacs-plus](https://github.com/d12frosted/homebrew-emacs-plus).

Since we are installing from a GitHub repository, we will need to add this a third-party repository 
(known as a "tap") by running the `brew tap` command. This is just adding to the default list of formulae that Homebrew tracks, updates, and installs from.

brew tap d12frosted/emacs-plus
```

Now we can go ahead and install emacs-plus. Note that if you want to select a different
icon, then you can choose one for the [list of icons](https://github.com/d12frosted/homebrew-emacs-plus#icons) and replace the icon option flag, `--with-modern-papirus-icon`, with the one you want to use.

``` shell
brew install emacs-plus --with-native-comp --with-modern-papirus-icon
```

It is now time to create a link to the Emacs.app application in the Applications menu.

``` shell
ln -s /opt/homebrew/opt/emacs-plus@29/Emacs.app /Applications
```

> [!WARNING]
> DO NOT RUN EMACS YET!

In the event that you opened emacs, you will need to close it and then remove the configuration directory `.emacs.d` that was created when you started emacs for the first time.

## Install Doom Emacs

Before we install [Doom Emacs](https://github.com/doomemacs/doomemacs), we first need 
to install some software dependencies using `brew`.

``` shell
brew install fd ripgrep
```

Okay, now we can install doom emacs.
``` shell
git clone --depth 1 https://github.com/doomemacs/doomemacs ~/.config/emacs
~/.config/emacs/bin/doom install
```

Don't worry, `doom` is already on added to your `PATH` from your `.zshrc` file.

It is time to run emacs for the first time to create the configuration files.  You will also notice that the application icons are not working out of the box, do to worry ... we will fix this shortly.  But first, quit emacs by pressing `SPC q q`.

Now copy the `doom` directory from the repository files you download and move it to into your `~/.config` directory.  Note that `~` means your home directory and that the directory `.config` is hidden.  

>[!IMPORTANT]
The config for the courses that I teach is designed for setting up a MacBook with a **swedish keyboard**.

Before you open doom emacs again, we are going to make sure it is updated with the new config files in place.

``` shell
doom upgrade
doom sync
```

Now you can launch the emacs app.

``` emacs-lisp
M-x nerd-icons-install-fonts
```

Need help getting started with doom emacs, check out my [doom emacs cheetsheet](https://github.com/mholson/mho_bespoke_notes#doom-emacs-cheatsheet).
