# Blockscrew Cloud9

A lightweight and customizable Cloud9 IDE environment. This image provides a clean and efficient workspace for your development needs, available in two convenient tags.

## Features

**Choose the tag that best suits your workflow:**

### `blockscrew/cloud9:latest`

🔹 **Minimalist Base**: Extremely small image size with zero pre-installed dependencies.  
🔹 **Fully Customizable**: A clean slate, allowing you to install only the dependencies you need.

### `blockscrew/cloud9:v2`

🔹 **Ready to Use**: Pre-loaded with essential development tools including:
  - Python 2 & Python 3
  - pip3
  - nvm
  - Latest Node.js v24
  - Latest npm v11
- 🔧 **Still Customizable**: Add any other tools you require on top of the existing setup.

---

## 🚀 Quick Start

## 1. Prerequisites

Ensure Docker and Docker Compose are installed and running on your system.

### Update and install Docker
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y docker.io docker-compose
```

### Enable and start the Docker service
```bash
sudo systemctl enable --now docker
```

## 2. Firewall Configuration (Optional)
If you have a firewall enabled (like UFW), allow SSH and the port you will use for Cloud9.

### Allow SSH and Cloud9 port (e.g., 8181)
```bash
sudo ufw allow 22/tcp
sudo ufw allow 8181
sudo ufw enable
sudo ufw reload
```
## 3. Prepare Workspace Directory
Create a directory to store your Cloud9 workspace files.
```bash
mkdir -p ~/cloud9 && cd ~/cloud9
```

## 🛠 Usage with Docker Compose
Create a docker-compose.yml file in your ~/cloud9 directory.

Option 1: Minimal Setup (latest)
Create a docker-compose-latest.yml:
```bash
services:
  cloud9:
    image: blockscrew/cloud9:latest
    container_name: cloud9
    environment:
      - TZ=Asia/Jakarta
      - USERNAME=user  # Set your desired username
      - PASSWORD=pass  # Set your desired password
    volumes:
      - ~/cloud9:/BOT
    ports:
      - "8181:8000"    # Map host port 8181 to container port 8000
    restart: always
```
Option 2: Ready-to-Use Setup (v2)
Create a docker-compose-v2.yml:
```bash
services:
  cloud9:
    image: blockscrew/cloud9:v2
    container_name: cloud9
    environment:
      - TZ=Asia/Jakarta
      - USERNAME=user  # Set your desired username
      - PASSWORD=pass  # Set your desired password
    volumes:
      - ~/cloud9:/BOT
    ports:
      - "8181:8000"    # You can customize the host port (8181), but the container port (8000) is fixed.
    restart: always
```

## ▶️ Running the Container
Navigate to your ~/cloud9 directory and run the following command depending on the file you created:

### For the latest version
```bash
docker-compose -f docker-compose-latest.yml up -d
```

### Or for the v2 version
```bash
docker-compose -f docker-compose-v2.yml up -d
```
🕒 Please allow 1–3 minutes for the container to initialize.

### 🌐 Accessing Cloud9
Once the container is running, access the Cloud9 IDE in your web browser at:

Remote: `http://<your_server_ip>:8181`

Local: `http://127.0.0.1:8181`

### 📦 Source Image
Available on Docker Hub:
🔗 https://hub.docker.com/r/blockscrew/cloud9