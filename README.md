# High School Web-Development & Programming Environment Setup

![Doom Emacs Setup](/assets/emacs_install_emacs-plus-doom.png)

Watch the YouTube video (August 2023 Edition): [Installing emacs-plus and Doom on a Macbook Air M1 using Homebrew](https://www.youtube.com/embed/A6SxH9lUWV0?si=7_F8CXkxaoP9RtQm).

Welcome to the GitHub repository designed to simplify MacBook (swedish keyboards) setups for the high school web development and programming courses that I teach.

The purpose is to provide an installation procedure that facilitates a smooth and efficient setup process for educators and students alike, minimizing the initial overhead typically associated with editing configuration files during installation.  At the same time, it should help the student incrementally become more aware of the development environment they are settign up (not just running an install script).


## Features

**Homebrew Installation:** Homebrew, the missing package manager for macOS, which simplifies the installation of software on Apple's macOS operating system.

**Emacs-Plus and Doom Emacs:** Steps to install Emacs-Plus, a version of GNU Emacs with additional features, and Doom Emacs, a configuration framework for Emacs. A boilerplate Doom Emacs configuration directory is included as part of this repository to ensure a student with no programming experience can quickly setup a development environment that is tuned for the web development and programming courses they are taking. It also acts as backup in the event that something goes wrong while editing their configuration files later.

**Anaconda for Python:** Instructions on how to setup Anaconda to manage Python packages and environments, ensuring a consistent and reproducible Python setup across all machines.

**Node Package Manager (npm) for Javascript:**  A one line brew install in the terminal to setup the JavaScript package manager and command-line client. 

**Update Procedures:** Detailed instructions on how to keep the MacBook computers updated with the latest tools and security patches.

# Setup Procedure

## Step 1: Download the files from this repository

![Download the repository setup files](/assets/mho-teaching-config.png)

## Step 2: Install xcode command line developer tools

``` shell
x-code-select --install
```

## Step 3: Install Homebrew

> [!IMPORTANT]
> xcode command line developer tools must be installed first.

We will be using [Homebrew](https://brew.sh) to manage the software on our MacBooks.  
[Download the MacOs package installer](https://github.com/Homebrew/brew/releases/latest)

## Step 4: Add the .zshrc Config File 

We need to make sure that the command `brew` is on your PATH, which means you can run it 
from your terminal shell.  Since we are using the **zsh** shell, 
I have included an `dot.zshrc`, I have updated this file for you.

Move the file `dot.zshrc`from the repository files you downloaded to your home directory using *Finder*.  To quickly change into the HOME directory use the following keyboard shortcut:`SHIFT`+`CMD`+`H`.

Since `dot.zshrc` is a hidden dot file, we should toggle the **Finder** app to view hidden 
files by pressing `SHIFT`+`CMD`.

Rename `dot.zshrc` to `.zshrc`

To have the shell apply the changes you've made to the `.zshrc` file, without having to open a new terminal session, run the following from your terminal while in your home directory.

> [!NOTE]
> Quick Tip!  You can quickly navigate to your home directory from the terminal by using the command `cd [SPC]`, where `[SPC]` is one space created with your space-bar key.

``` shell
cd[SPC]
source .zshrc
```

## Install Emacs-Plus

Using brew to install [emacs-plus](https://github.com/d12frosted/homebrew-emacs-plus).

Since we are installing from a GitHub repository, we will need to add this a third-party repository 
(known as a "tap") by running the `brew tap` command. This is just adding to the default list of formulae that Homebrew tracks, updates, and installs from.

``` shell
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

> [!IMPORTANT]
> The config for the courses that I teach is designed for setting up a MacBook with a **swedish keyboard**.

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

## Specific Packages for Web Development

Doom emacs will be using `tidy-html5`to format html 
code.  We will also be making use of javascript and to run this code within org-mode code blocks using babel, we will download [npm](https://www.npmjs.com)

``` shell
brew install tidy-html5 npm
```

## Install Anaconda.

![Anaconda Install](assets/anaconda-m-macos-download.png)

It is now time to install [Anaconda](https://www.anaconda.com/download) to maintain our python installation.

> [!WARNING]
> Make sure you choose the correct Apple architecture.

Once the install is complete we will also want to
add it to our `PATH`.  Start by navigating to where the conda command is located and then running `conda init`

``` shell
cd ~/anaconda3/bin
conda init
```

### Packages Specific for Programming

``` shell
conda install -c conda-forge textual
```

## Install GitHub Desktop 

After downloading the [Github Desktop](https://central.github.com/deployments/desktop/desktop/latest/darwin-arm64) application, make sure you move it to your `Applications` directory before running it for the first time.  Make sure you setup GitHub with your school email address.

# Updates

## Update Homebrew 

``` shell
brew update
brew upgrade
brew cleanup
```

## Update Conda

``` shell
conda clean --all
conda update anaconda-navigator
conda update conda
conda update --all
conda clean --all
```

## Update npm 
``` shell
npm update
```
## Update Doom Emacs 

``` shell
doom upgrade 
doom sync
```

If you run in to any trouble you can always call the doctor,

``` shell
doom doctor 
```
