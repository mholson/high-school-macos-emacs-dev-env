# High School Web-Development & Programming Environment Setup

![Doom Emacs Setup](/assets/emacs_install_emacs-plus-doom.png)

Welcome to the GitHub repository dedicated to setting up MacBook computers for teaching high school courses in web development and programming. This repository is designed to streamline the environment setup, allowing educators and students to focus on learning and teaching without the overhead of complex installation processes.

The primary goal is to create a consistent development environment across all machines using a series of scripts and configuration files. This ensures that all students have the same starting point and can work on projects with minimal setup-related issues.

## Features

**Homebrew Installation:** Homebrew, the missing package manager for macOS, which simplifies the installation of software on Apple's macOS operating system.

**Emacs-Plus and Doom Emacs:** Steps to install Emacs-Plus, a versatile version of GNU Emacs with additional features, and Doom Emacs, a configuration framework for GNU Emacs. A pre-defined Doom Emacs config directory is included to help students quickly set up an efficient and pleasant editing experience that’s tuned for the web development and programming courses.

**Anaconda for Python:** Instructions on how to use Anaconda to manage Python packages and environments, ensuring a consistent and reproducible Python setup across all machines.

**Update Procedures:** Detailed instructions on how to keep the MacBook computers updated with the latest tools and security patches.

# Setup Instructions


> [!NOTE]
> Video on how to install Homebrew and Doom Emacs 
> ![YouTube Video Setting up Doom Emacs](https://youtu.be/A6SxH9lUWV0)

## Download the files from this repository



## Install xcode command line developer tools

``` shell
x-code-select --install
```


## Install Homebrew

> [!IMPORTANT]
> xcode command line developer tools must be installed first.

We will be using [Homebrew](https://brew.sh) to manage the software on our MacBooks.  
[Download the MacOs package installer](https://github.com/Homebrew/brew/releases/latest)

Once Homebrew is installed, you can copy the `dot.zshrc` file 


ln -s /opt/homebrew/opt/emacs-plus@29/Emacs.app /Applications
