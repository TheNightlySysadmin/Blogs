# Setting Up Docker on Ubuntu and RHEL-Based Distributions: A Step-by-Step Guide - The Nightly Sysadmin
Docker has become an essential tool for modern software development and deployment, offering the ability to containerize applications for consistent and efficient performance across different environments. Whether you’re a developer, a system administrator, or simply someone curious about containers, setting up Docker is your first step into the world of containerization.

In this guide, we will walk you through the installation of Docker on two popular Linux families: Ubuntu and RHEL-based distributions (such as CentOS and Rocky Linux). Both are widely used in production environments and offer robust support for Docker. By the end of this guide, you’ll have a working Docker installation and be ready to start running your first containers.

* * *

Prerequisites
-------------

Before we start, ensure you have the following:

1.  **A running Linux system**: This guide covers Ubuntu 20.04 or later and RHEL-based distributions.
2.  **A user account with sudo privileges**.
3.  **Internet access**.

* * *

Step 1: Update Your System
--------------------------

Before installing Docker, it’s essential to update your system to ensure you have the latest security patches and software.

### Ubuntu:

```
sudo apt update && sudo apt upgrade -y
```


### RHEL-Based Distributions:

```
sudo dnf update -y
```


* * *

Step 2: Install Required Packages
---------------------------------

Docker requires several prerequisites to be installed first.

### Ubuntu:

```
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common lsb-release
```


### RHEL-Based Distributions:

```
sudo dnf install -y yum-utils device-mapper-persistent-data lvm2
```


* * *

Step 3: Add Docker’s Official GPG Key and Repository
----------------------------------------------------

### Ubuntu:

1.  **Add Docker’s GPG Key**:

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```


2.  **Set up the Docker Repository**:

```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```


### RHEL-Based Distributions:

1.  **Add Docker’s Repository**:

```
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```


* * *

Step 4: Install Docker Engine
-----------------------------

### Ubuntu:

1.  **Update the package index**:

```
sudo apt update
```


2.  **Install Docker**:

```
sudo apt install -y docker-ce docker-ce-cli containerd.io
```


3.  **Verify the installation**:

```
docker --version
```


### RHEL-Based Distributions:

1.  **Install Docker**:

```
sudo dnf install -y docker-ce docker-ce-cli containerd.io
```


2.  **Start Docker**:

```
sudo systemctl start docker
```


3.  **Verify the installation**:

```
docker --version
```


* * *

Step 5: Manage Docker as a Non-Root User
----------------------------------------

By default, Docker commands require root privileges. To allow a non-root user to run Docker commands:

### Common Steps for Both Ubuntu and RHEL-Based Distributions:

1.  **Create the Docker group**:

```
sudo groupadd docker
```


2.  **Add your user to the Docker group**:

```
sudo usermod -aG docker $USER
```


3.  **Apply the changes**:

```
newgrp docker
```


4.  **Test Docker without sudo**:

```
docker run hello-world
```


This command downloads and runs a test container to ensure Docker is working correctly.

* * *

Step 6: Enable Docker to Start on Boot
--------------------------------------

To ensure Docker starts automatically after a system reboot:

### Ubuntu:

```
sudo systemctl enable docker
```


### RHEL-Based Distributions:

```
sudo systemctl enable docker
```


* * *

Optional: Install Docker Compose
--------------------------------

Docker Compose simplifies managing multi-container applications. To install Docker Compose:

### Common Steps for Both Ubuntu and RHEL-Based Distributions:

1.  **Download the latest version**:

```
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```


2.  **Apply executable permissions**:

```
sudo chmod +x /usr/local/bin/docker-compose
```


3.  **Verify the installation**:

```
docker-compose --version
```


* * *

Conclusion
----------

Congratulations! You’ve successfully installed Docker on both Ubuntu and RHEL-based distributions. You can now use Docker to containerize applications, streamline development workflows, and enhance your server’s capabilities. Explore Docker’s extensive documentation to learn more about what you can achieve with this powerful tool.