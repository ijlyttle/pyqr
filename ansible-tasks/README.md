# pyqr - ansible

The goal is to get a virtual machine up-and-running; this could be:

  - WSL2 hosted on a PC
  - Docker container

At present, this supports Ubuntu (focal and jammy).

## Host machines

If you are running Docker on an Ubuntu machine, everything should *just work*.

### MacOS

If you are running on macOS M1, this presents a particular challenge: you are using an `arm64` architecture, but these images are built using an `amd64` architecture. There is a workaround, but I haven't tried it yet:

- requires MacOS Ventura
- Docker Desktop, with [Rosetta emulation activated](https://github.com/docker/roadmap/issues/384#issuecomment-1380882630)

### WSL

Following the [Microsoft documentation](https://learn.microsoft.com/en-us/windows/wsl/install#install-wsl-command), from Windows:

> Open PowerShell or Windows Command Prompt in administrator mode by right-clicking and selecting "Run as administrator", enter the `wsl --install` command, then restart your machine.

For our purposes, let's install Ubuntu 22.04:

 ```
 wsl --install Ubuntu-22.04
 ```

This system will exist only on this PC, but will be administered separately from this PC. 
As such, choose a user name and password that is sensible to you. 

To test out the new installation, from your Windows prompt:

```
wsl
```

This should bring up a new prompt, from which you can check the OS:

```
cat /etc/issue
```

For me, this responds with:

```
Ubuntu 22.04.1 LTS \n \l
```

which is good news. 
You can exit to Windows using:

```
exit
```

## Installation

### Ununtu

### MacOS
```bash
xcode-select --install
```

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/fc4a19b38608451cabe6ceaa8ffb4fa1300854c8/install.sh)"
```

```bash
brew install ansible
```

## Usage

```bash
ansible-playbook local.yml -K --tags [R, python, quarto] 
```