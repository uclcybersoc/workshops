# Installation Guide

This document is designed to help you set up everything you need to participate in CTF competitions. Whether you're a beginner just starting out or already experienced, this guide provides instructions to prepare your system for solving a wide range of cyber security challenges.

## Overview

- [Linux](#linux)
- [Python Environments](#python-environments)
- [Docker](#docker)
- [Tools by Category](#tools)

## Linux

### Linux VM - Windows

1. Install VirtualBox: [Downloads – Oracle VirtualBox](https://www.virtualbox.org/wiki/Downloads) <br>
or <br>
Install VMware Player: [Desktop Hypervisor Solutions | VMware](https://www.vmware.com/products/desktop-hypervisor/workstation-and-fusion)
2. Download a Linux image of your choice <br>

> Recommended: <br>
> - Kali: [Get Kali | Kali Linux](https://www.kali.org/get-kali/#kali-virtual-machines) <br>
(preloaded with tools such as Burp Suite, Nmap, and Metasploit; easy package management; robust performance; quite heavyweight) <br>
> - Ubuntu: [Download Ubuntu Desktop | Ubuntu](https://ubuntu.com/download/desktop) <br>
(beginner-friendly, customizable, install only tools you need, longer setup time) <br>
[How to run an Ubuntu Desktop virtual machine using VirtualBox 7 | Ubuntu](https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox#1-overview)
> 
3. Extract the image
4. Open the VM using the downloaded image
5. Configure VM settings: recommended to allocate at least 4GB of RAM and 2 CPUs
6. Launch

### Windows Subsystem for Linux

WSL allows you to run a Linux distribution directly on Windows without the need for a VM or dual booting. It provides a Linux environment to run common tools like Python, Bash, and other security tools while still being able to work within Windows.

https://docs.microsoft.com/en-us/windows/wsl/install

### Linux VM - Mac

1. Download UTM: https://mac.getutm.app/
2. Install UTM: go to your Downloads folder, open the .dmg file for UTM, and drag the UTM icon into your Applications folder
3. Download a Linux image: https://mac.getutm.app/gallery/kali-2023
4. Extract the image
5. Open UTM from Applications or Spotlight search
6. Create a new VM: click “Open…” at the bottom under “Existing,” and select the .utm file
7. Launch


## Python Environments

Python environments, are isolated spaces where you can install and manage Python packages independently of your system's default Python setup. They are useful for CTFs because many challenges require specific libraries or tools, which might conflict with global installations. Using environments ensures that your dependencies are contained and can be easily reset or tailored for different tasks.

There’s a lot of different tools, such as pyenv, venv, pipx, conda, etc.

### pyenv

Pyenv is a tool for managing multiple python versions on your system, allowing you to switch between them easily.

https://github.com/pyenv/pyenv?tab=readme-ov-file#getting-pyenv 

After installing pyenv, you can install a python version like this:
```
pyenv install <version>
```

and switch between versions like this:
```
pyenv shell <version> -- select just for current shell session
pyenv local <version> -- automatically select when you’re in the current dir
pyenv global <version> -- select globally for your user account
```

### pipx

pipx is a tool for installing and running python applications in isolated environments, ensuring they don’t interfere with your system-wide packages.

https://github.com/pypa/pipx?tab=readme-ov-file 

To ensure pipx uses the correct python environment, follow this guide:

https://gabnotes.org/how-use-pipx-pyenv/ 

### poetry

Poetry is a python package manager that is used to manage dependencies and
virtual environments. You can install it using pipx:

https://python-poetry.org/docs/#installation 

## Docker

Docker is a platform that allows you to create, deploy, and run applications in isolated environments called containers. These containers package all the dependencies, libraries, and tools needed to run a program, ensuring consistency across different systems.

https://docs.docker.com/get-docker/ 

## Tools

These are just a few of the most common tools used in each category.

### Rev

- Ghidra: https://ghidra-sre.org/

or

- IDA Pro: https://www.hex-rays.com/products/ida/ 

### Pwn

- Ghidra: https://ghidra-sre.org/
- GDB: http://www.gdbtutorial.com/tutorial/how-install-gdb
  - pwndbg (GDB plugin): https://github.com/pwndbg/pwndbg
- pwntools: https://github.com/Gallopsled/pwntools

### Web

- Burp Suite: https://portswigger.net/burp
- Wireshark: https://www.wireshark.org/

### Crypto

There’s a Docker container with all the tools you need.

Linux and WSL
```
docker run -it --platform linux/amd64 -p 127.0.0.1:8888:8888 -v $(pwd):/home/sage/ctf hyperreality/cryptohack:latest
```

MacOS (sagemath container missing some more advanced tools)
```
docker run -it --platform linux/amd64 -p 127.0.0.1:8888:8888 -v $(pwd):/home/sage/ctf sagemath/sagemath:latest "sage -n jupyter -#NotebookApp.token='' --no-browser --ip='0.0.0.0' -# port=8888"
```
