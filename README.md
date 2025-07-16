# 🐳 Docker VM Deployment Guide

This guide provides a quick and clean walkthrough of how I set up and deploy Docker on a Linux virtual machine (VM).  
While this example uses **Ubuntu Jammy (22.04)**, it should work with most modern Debian-based distributions.


##  Prerequisites

- A Linux virtual machine (e.g., Ubuntu 22.04)
- Internet access
- Sudo/root privileges


## Step 1: Update System Packages

```bash
sudo apt update && sudo apt upgrade -y
```


## Step 2: Set Up Docker APT Repository

```bash
# Install dependencies
sudo apt-get install -y ca-certificates curl

# Create directory for Docker keyrings
sudo install -m 0755 -d /etc/apt/keyrings

# Download and store Docker's GPG key
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add Docker's APT repository
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo \"${UBUNTU_CODENAME:-$VERSION_CODENAME}\") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Update APT package index
sudo apt-get update
```


## Step 3: Install Docker Engine

```bash
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```


## Step 4: Verify Docker Installation

```bash
sudo docker run hello-world
```

You should see a welcome message from Docker confirming that everything is working correctly.
<img width="501" height="263" alt="image" src="https://github.com/user-attachments/assets/ec08304c-aafb-49be-9694-3f05eaf42a2a" />


## 📁 My Docker Stacks

- **Homelab Stack**: [ikalelol/homelabstacks](https://github.com/ikalelol/homelabstacks)
- **Business Stack**: [ikalelol/BusinessStack](https://github.com/ikalelol/BusinessStack)


##  Official Docker Documentation

For additional reference or troubleshooting, please visit the official Docker docs:

🔗 [Docker Engine on Ubuntu – Docker Docs](https://docs.docker.com/engine/install/ubuntu/)
