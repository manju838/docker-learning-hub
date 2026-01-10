---
layout: page
title: Getting Started
nav_order: 3
---

# Getting Started with Docker
{: .fs-9 }

Set up your environment and run your first container
{: .fs-6 .fw-300 }

---

## 🔧 Installation

### Step 1: Install Docker Engine

Choose your operating system:

#### **Windows**
1. Download [Docker Desktop for Windows](https://docs.docker.com/desktop/install/windows-install/)
2. Run the installer
3. Restart your computer
4. Verify installation: `docker --version`

#### **macOS**
1. Download [Docker Desktop for Mac](https://docs.docker.com/desktop/install/mac-install/)
2. Drag Docker to Applications
3. Launch Docker Desktop
4. Verify installation: `docker --version`

#### **Linux (Ubuntu/Debian)**
```bash
# Update package index
sudo apt-get update

# Install Docker
sudo apt-get install docker-ce docker-ce-cli containerd.io

# Verify installation
docker --version
```

---

## 🚀 Your First Container

Let's run your first Docker container!

```bash
# Pull and run a simple hello-world container
docker run hello-world
```

**What just happened?**
1. Docker searched for the `hello-world` image locally
2. Didn't find it, so downloaded it from Docker Hub
3. Created a new container from that image
4. Ran the container and displayed a message

---

## 📦 Clone This Repository

```bash
# Clone the repository
git clone https://github.com/manju838/docker-learning-hub.git

# Navigate to the project
cd docker-learning-hub
```

---

## 🎯 Next Steps

Now that you're set up, proceed to:

1. [Fundamentals](/fundamentals/) - Learn Docker basics
2. [Traffic Light Challenge](/about/#-the-traffic-light-challenge) - Start the hands-on project
3. [Networking](/networking/) - Understand container networking

---

## ❓ Troubleshooting

### Docker daemon not running
```bash
# Start Docker service (Linux)
sudo systemctl start docker

# Or restart Docker Desktop (Windows/Mac)
```

### Permission denied
```bash
# Add your user to docker group (Linux)
sudo usermod -aG docker $USER
# Log out and back in for changes to take effect
```

### Command not found
- Ensure Docker is installed correctly
- Check your PATH environment variable
- Restart your terminal
