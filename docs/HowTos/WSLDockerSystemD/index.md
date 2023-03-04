---
layout: single
title: WSL2 DockerD and SystemD
toc: ture
---

## Intro (why not Dock Desktop)
### Docker Desktop
Dock Desktop is a nice casual user all in one solution. Just install it and play/use docker. Typically it all works direct. It contains some customisation, integration with a user interface. Recent versions also use WSL on windows. It is done with two dedicated WSL images (one for dokcer and a other one for FS mounting optimisations). All this looks fine, my reasons not to use Docker Desktop are:

1. for Commercal use Docker (the company and not the technology) introduce a licence model. 
1. I like learn and understand this and that more. 

### WSL (II) and SystemD
When MS released WSL II I jused loved it. The Performance, Resource effechentsy and FS integration is just grade. But after some days/weeks I realsed WSL is Linux but not full Linux. SystemD, the currently defactore standard Linux Service Manager, was not supported. So no Linux Server like any Http and Docker couldent start as an System Service. It was only possible to start them over a User Session. Some smart developers/hacker released git repos, scripts and programmes to enanle a limited SystemD functionality. I personally never got it to work.
Some month back MS anounced end of september in 2022 the SystemD support ([Link](https://devblogs.microsoft.com/commandline/systemd-support-is-now-available-in-wsl/)). And some month before also WSLg (Gui support for X11 and Wayland) and android ... also impressend stuff.

## Install and Configuration (WSL/Linux/Ubuntu)
I use and tested it with Ubuntu 22.04 als WSL image and Windows 10 (22H2) as host OS. Docker is not avalibe in the stzandard package repose so ther is some extra steps required (Step 1 - 4). 

### Step 1 - Install additional packaes 
```bash
sudo apt.get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
```

### Step 2 - Add Docker Repo Public Key 
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add
```

### Step 3 - Trused Docker Public Key
```bash
sudo apt-key fingerprint 0EBFCD88
```

result should looke like

```
Warning: apt-key is deprecated. Manage keyring files in trusted.gpg.d instead (see apt-key(8)).
pub   rsa4096 2017-02-22 [SCEA]
      9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
uid           [ unknown] Docker Release (CE deb) <docker@docker.com>
sub   rsa4096 2017-02-22 [S]
```

### Step 4 - Add Docker Repo
```bash
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

### Step 5 - Install Docker
```bash
sudo apt-get install docker-ce  docker-ce-cli containerd.io
```

### Step 6 - Add the current user (you) to the Docker Group
```bash
sudo usermod -aG docker ${USER}
```

### Step 7 - FS premission 
```bash
sudo chmod 666 /var/run/docker.sock
```

### Step 8 - Add TCP as prtocol to the DockerD
```bash
sudo vi /etc/systemd/system/multi-user.target.wants/docker.service
```

search for "ExecStart" and add "-H tcp://127.0.0.1:2376" after "-H fd://". In my case the full line looks like:
```
...
ExecStart=/usr/bin/dockerd -H fd:// -H tcp://127.0.0.1:2376 --containerd=/run/containerd/containerd.sock
...
```

### Step 9 - Reload config and restart DockerD
```bash
sudo systemctl daemon-reload
sudo systemctl restart docker
```

## Configuration on Windows 
Docker on Windows use npipe as protocoll. But this is not supported on Linux. Docker Desktop install for this on Windows a simple protocoll translation service. I found on GitHub a simple protocoll translater writte in rust. But for now I change on Docker the docker prtocoll from npipe to TCP IT.

### Step 1 - add and change the Docker prtocol to TCP/IP
```bash
docker context create docker-wsl --default-stack-orchestrator=swarm --docker host=tcp://:2376
docker context use docker-wsl
docker context list
```

## Limitations
### 1. DockerD (auto)start
Also with SystemD support DockerD will only start after a WSL/Ubuntu login 

### 2. WSL / Ubuntu Statup Time
With SystemD and configgerd services the first WSL/Ubuntu login taks a liittel bit longer. From no time to ~2 sec on my PC.

### 3. Visual Studio Code Devcontainers 
I also need to configure the transport prtocoll to tcp://:2376. This is done in VS Code Settings 

```json
{
    ...
       "docker.environment": {
        "DOCKER_HOST": "tcp://:2376"
    },
    ...
}
```

this configuration is fine but I also faced issues with the different Windows and Linux Pathes. I only get it soled with a absoluted hardcoded workspace mound path in the ".devcontainer\devcontainer.json" file. **UGLY**. It is also not recommended to store source files on your a Windows folder and acess this folder from WSL/Ubuntu. But this is my current approatch and Docker Desktop intoduce for this the second WSL image and the VS Code and Devcontainer integration works out of the box.
```json
{
    ...
	"workspaceMount": "type=bind,source=/mnt/c/Users/kremer/dev/web,target=/workspaces/web"
    ...
}

```