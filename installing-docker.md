# Installing Docker

Goal: Docker daemon, Docker CLI, REST API

# **Install Docker Engine on Ubuntu**

Reference: [https://docs.docker.com/engine/install/ubuntu/](https://docs.docker.com/engine/install/ubuntu/)

## **Prerequisites:**

### **OS requirements:**

To install Docker Engine, you need the 64-bit version of Ubuntu.

### ****Uninstall old versions:****

Uninstall any such older versions before attempting to install a new version.

```bash
sudo apt-get remove docker docker-engine docker.io containerd runc
```

If no older version is present, below is the output:

![Untitled](images/installing-docker/Untitled.png)

## ****Installation using the repository****

Before you install Docker Engine for the first time on a new host machine, you need to set up the Docker repository. Afterward, you can install and update Docker from the repository.

Set up the repository:

1. Update the `apt` package index and install packages to allow `apt` to use a repository over HTTPS:

```bash
sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

1. Add Docker’s official GPG key:

```bash
sudo mkdir -m 0755 -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

1. Use the following command to set up the repository:

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

## **Install Docker Engine**

1. Update the `apt` package index to refresh the apt cache:

```bash
sudo apt-get update
```

  Receiving a GPG error when running `apt-get update`?

```bash
sudo chmod a+r /etc/apt/keyrings/docker.gpg
sudo apt-get update
```

1. Selecting the docker repository as the default one

```bash
apt-cache policy docker-ce
```

1. Install Docker Engine, containerd, and Docker Compose.

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

1. Check the status of Docker

```bash
sudo systemctl status docker
```

![Untitled](images/installing-docker/Untitled%201.png)

1. Add current user `muritala` to the Docker group to be able to run the docker command.

```bash
sudo usermod -aG docker muritala
```

1. Log out and then in for change to take effect.

```bash
exit
```

1. After logging in, check docker version to check if docker client can talk to the docker daemon or server.

```bash
docker --version
```

![Untitled](images/installing-docker/Untitled%202.png)