## VSCode on Windows

VSCode DevContainer Configuration using WSL2 on Windows.

This guide is meant to get someone who has little knowledge using DevContainers that are included in Github Repositories.

### Prerequisites

#### Download VSCode Installer

<https://code.visualstudio.com/download>

#### Download Docker Desktop

<https://www.docker.com/products/docker-desktop/>

### Install WSL2

#### Enable Subsystem for Linux

Open Powershell as Administrator (Start > Right Click "Powershell" > Run as Administrator...)

`Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux`

#### Install Ubuntu 22.04 Subsystem

Open Powershell as Administrator (Start > Right Click "Powershell" > Run as Administrator...)

Follow these steps to install the Ubuntu 22.04 Subsystem:

Download/Install:

`wsl --install -d Ubuntu-22.04`

Set Default Version of WSL to '2':

`wsl --set-version Ubuntu-22.04 2`

Set Default WSL Runtime to Ubuntu-22.04:

`wsl -s Ubuntu-22.04`

Note: You will prompted to create a username and password here. I use username: 'vscode' with a strong password that I will remember.

Verify Version of Ubuntu-22.04 is installed and set to default

`wsl -l -v`

#### Open WSL Terminal

Type `wsl` in powershell or Open `wsl` from start menu.

### Update Python

Run these commands in the WSL Terminal to update and install python3 packages.

#### Update `apt` repositories

`sudo apt update`

#### Perform Full Upgrade on WSL System

`sudo apt full-upgrade`

#### Install Python3

`sudo apt install python3 python3-pip`

#### Verify the python3 version

`python3 --version`

### Open VSCode with DevContainer

Create your own .devcontainer directory with `devcontainer.json` and `Dockerfile` configurations, but typically these come included in a Github repository.

Example respository:
<https://github.com/chris-mendoza/chris-mendoza.github.io>

Once the .devcontainer directory and files have been configured, open Visual Studio Code from within the WSL2 Terminal:

```bash
git clone git@github.com:chris-mendoza/chris-mendoza.github.io.git
cd chris-mendoza.github.io
code .
```

Once VSCode opens, you will be prompted to re-open the files from within a DevContainer. If this is the first time opening a specific directory, you will also need to "Trust the authors" if you do indeed trust them.

### Github Configuration

#### Generate SSH Key Pair

`ssh-keygen`

#### Add SSH Key to Github Repository

<https://docs.github.com/en/authentication/connecting-to-github-with-ssh/managing-deploy-keys>

### Recommended VSCode Plugins

- Docker
- DevContainers
- Indent One Space
- WSL2

### Deeper Reading

#### VSCode Dev Containers

<https://code.visualstudio.com/docs/devcontainers/containers>

#### Windows Subsystem for Linux (WSL)

<https://learn.microsoft.com/en-us/windows/wsl/about>
