## VSCode on Windows

### Download VSCode Installer

<https://code.visualstudio.com/download>

### Download Docker Desktop

<https://www.docker.com/products/docker-desktop/>

### Enable Subsystem for Linux

Open Powershell as Administrator (Start > Right Click "Powershell" > Run as Administrator...)

`Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux`

### Install WSL2

```powershell
wsl --install -d Ubuntu-22.04

wsl --set-version Ubuntu-22.04 2

wsl -s Ubuntu-22.04

#Note: You will prompted to create a username and password here

#Verify Version of Ubuntu-22.04 is installed and set to default
wsl -l -v
```

### Open WSL Terminal

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

#### Generate SSH Key Pair 

`ssh-keygen`

#### Add SSH Key to Github Repository

<https://docs.github.com/en/authentication/connecting-to-github-with-ssh/managing-deploy-keys>

### Install VSCode Plugins

- Docker
- DevContainers
- Indent One Space
- WSL2
