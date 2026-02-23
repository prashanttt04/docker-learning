# 🐳 Docker Learning Repository

This repository represents my structured hands-on learning of **Docker**, covering:

- Containerization  
- Image management  
- Networking  
- Volumes  
- Docker Compose  
- Publishing images to Docker Hub  

---

## 🚀 Docker Hub Profile

🔗 **My Docker Hub Account:**  
https://app.docker.com/accounts/prashantttt04

---

## 🚀 Published Docker Image

I have successfully built and published a Docker image on Docker Hub:

**Image:**  
prashantttt04/estapp

---

## 📌 What is Docker?

Docker is a containerization platform that packages applications and their dependencies into lightweight, portable containers that run consistently across environments.

---

## ❓ Why Do We Need Docker?

- Environment consistency  
- Eliminates dependency conflicts  
- Lightweight compared to Virtual Machines  
- Faster startup time  
- Simplified deployment  
- Microservices-friendly architecture  

---

## 🖼 Docker Images & Containers

### 🔹 Docker Image
- Read-only template  
- Built using Dockerfile  
- Contains application code + dependencies  

### 🔹 Docker Container
- Running instance of an image  
- Isolated execution environment  
- Shares host OS kernel  

---

## 💻 Docker Installation

Docker requires a Linux kernel.

On Windows/macOS:
- Docker Desktop adds a lightweight hypervisor  
- Runs a minimal Linux distribution internally  
- Enables containers to run on non-Linux systems  

---

## 📚 Important Docker Commands

### 📦 Image Commands
```bash
docker pull IMAGE_NAME
docker pull IMAGE_NAME:version
docker images
docker rmi IMAGE_NAME
```

### 🚀 Container Commands
```bash
docker run IMAGE_NAME
docker run -it IMAGE_NAME
docker run -d IMAGE_NAME
docker run --name CONT_NAME -d IMAGE_NAME
docker run -d -e MYSQL_ROOT_PASSWORD=secret --name mysql-latest mysql
docker stop CONT_NAME
docker start CONT_NAME
docker rm CONT_NAME
docker ps
docker ps -a
```

---

## 🔌 Port Mapping

```bash
docker run -p <host_port>:<container_port> IMAGE_NAME
```

Example:
```bash
docker run -p 3000:3000 my-node-app
```

Allows external access to container services.

---

## 🌱 Environment Variables

```bash
docker run -e NODE_ENV=production IMAGE_NAME
```

Pass configuration values inside the container.

---

## 🛠 Troubleshooting Commands

```bash
docker logs CONT_ID
docker exec -it CONT_ID /bin/bash
docker exec -it CONT_ID /bin/sh
```

Used for debugging running containers.

---

## 🆚 Docker vs Virtual Machine

| Feature | Docker | Virtual Machine |
|----------|---------|----------------|
| Virtualization Level | Application Layer | Kernel + Application |
| Uses Host OS Kernel | Yes | No |
| Weight | Lightweight | Heavy |
| Boot Time | Fast | Slower |

---

## 🧱 Dockerfile Instructions (Dockerizing an App)

Common Dockerfile keywords:

- `FROM` → Base image  
- `WORKDIR` → Set working directory  
- `COPY` → Copy files  
- `RUN` → Execute build commands  
- `CMD` → Default run command  
- `EXPOSE` → Declare container port  
- `ENV` → Set environment variable  

---

## 🔨 Build Image

```bash
docker build -t prashantttt04/testapp .
```

---

## 📤 Push Image to Docker Hub

```bash
docker push <image_name>
```

Published image:
```
prashantttt04/estapp
```

---

## 🌐 Docker Networking

```bash
docker network ls
docker network create my-network
docker network connect my-network CONT_NAME
```

Containers in the same network can communicate using container names.

---

## 💾 Docker Volumes

### List Volumes
```bash
docker volume ls
```

### Create Volume
```bash
docker volume create VOL_NAME
```

### Remove Volume
```bash
docker volume rm VOL_NAME
```

### Remove Unused Volumes
```bash
docker volume prune
```

---

## 🔗 Ways to Connect Volume to Container

### 1️⃣ Named Volume
```bash
docker run -v VOL_NAME:CONT_DIR
```

### 2️⃣ Anonymous Volume
```bash
docker run -v MOUNT_PATH
```

### 3️⃣ Bind Mount
```bash
docker run -v HOST_DIR:CONT_DIR
```

---

## 🧩 Volume Mount Syntax
```bash
-v <host_path>:<container_path>
```

---

## 🧱 Docker Image Layering

- Each Dockerfile instruction creates a layer  
- Layers are cached  
- Improves build performance  
- Reduces rebuild time  

---

## 🐳 Docker Compose

### ▶ Start Services
```bash
docker compose -f fileName.yaml up -d
```

### ⛔ Stop & Remove Services
```bash
docker compose -f fileName.yaml down
```

Removes:
- Containers  
- Networks created by Compose  
- Default network  

---

## 🚀 Dockerizing Node.js Application

### Example Dockerfile
```dockerfile
FROM node:18
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["node", "server.js"]
```

---

## 🎯 Key Learnings

- Docker architecture  
- Images & containers  
- Port mapping  
- Environment variables  
- Dockerfile instructions  
- Docker Compose  
- Volume types  
- Networking  
- Docker vs VM  
- Publishing images  
- Troubleshooting containers  
