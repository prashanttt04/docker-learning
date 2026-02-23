🐳 Docker Learning Repository

This repository represents my structured hands-on learning of Docker, covering containerization, image management, networking, volumes, Docker Compose, and publishing images to Docker Hub.

I have successfully built and published a Docker image on Docker Hub:

👉 Docker Hub Image: prashantttt04/estapp

📌 What is Docker?

Docker is a containerization platform that packages applications and their dependencies into lightweight, portable containers that run consistently across environments.

❓ Why Do We Need Docker?

Environment consistency

Eliminates dependency conflicts

Lightweight compared to Virtual Machines

Faster startup time

Simplified deployment

Microservices-friendly architecture

🖼 Docker Images & Containers
🔹 Docker Image

Read-only template

Built using Dockerfile

Contains app code + dependencies

🔹 Docker Container

Running instance of image

Isolated execution environment

Shares host OS kernel

💻 Docker Installation

Docker requires a Linux kernel.

On Windows/macOS:

Docker Desktop adds a lightweight hypervisor

Runs a minimal Linux distribution internally

Enables containers to run on non-Linux systems

📚 Important Docker Commands
📦 Image Commands
docker pull IMAGE_NAME
docker pull IMAGE_NAME:version
docker images
docker rmi IMAGE_NAME
🚀 Container Commands
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
🔌 Port Mapping
docker run -p <host_port>:<container_port> IMAGE_NAME

Example:

docker run -p 3000:3000 my-node-app

Allows external access to container services.

🌱 Environment Variables
docker run -e NODE_ENV=production IMAGE_NAME

Pass configuration values inside container.

🛠 Troubleshooting Commands
docker logs CONT_ID
docker exec -it CONT_ID /bin/bash
docker exec -it CONT_ID /bin/sh

Used for debugging running containers.

🆚 Docker vs Virtual Machine
System Layers

Application Layer
↓
Host OS Kernel
↓
Hardware

Docker

Uses Host OS Kernel

Virtualizes Application Layer only

Lightweight

Fast boot

Virtual Machine

Virtualizes Kernel + Application

Heavy

Slower

🧱 Dockerfile Instructions (Dockerizing App)

Common Dockerfile keywords:

FROM → Base image

WORKDIR → Set working directory

COPY → Copy files

RUN → Execute build commands

CMD → Default run command

EXPOSE → Declare container port

ENV → Set environment variable

🔨 Build Image
docker build -t prashantttt04/testapp .

docker build → Build image

-t → Tag image

prashantttt04/testapp → Image name

📤 Push Image to Docker Hub
docker push <image_name>

I have published:

prashantttt04/estapp
🌐 Docker Networking
docker network ls
docker network create my-network
docker network connect my-network CONT_NAME

Containers in same network communicate using container names.

💾 Docker Volumes
List Volumes
docker volume ls
Create Volume
docker volume create VOL_NAME

By default created at:

C:\ProgramData\docker\volumes
Remove Volume
docker volume rm VOL_NAME
Remove Unused Volumes
docker volume prune
🔗 Ways to Connect Volume to Container
1️⃣ Named Volume
docker run -v VOL_NAME:CONT_DIR

Docker-managed

Reusable

Persistent

2️⃣ Anonymous Volume
docker run -v MOUNT_PATH

Random name

Persistent

Harder to manage

3️⃣ Bind Mount
docker run -v HOST_DIR:CONT_DIR

Maps host directory directly

Mostly for development

🧩 Volume Mount Syntax
-v <host_path>:<container_path>
🧱 Layering of Docker Images

Each Dockerfile instruction creates a layer

Layers are cached

Improves build performance

Reduces rebuild time

🐳 Docker Compose

Used for multi-container applications.

Start Services
docker compose -f fileName.yaml up -d

-f fileName.yaml → Specify compose file

up → Create & start containers

-d → Detached mode

Stop & Remove Services
docker compose -f fileName.yaml down

Removes:

Containers

Networks created by Compose

Default network

🚀 Dockerizing Node.js Application
Dockerfile Example
FROM node:18
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["node", "server.js"]
🎯 Key Learnings

Docker architecture

Images & containers

Port mapping

Environment variables

Dockerfile instructions

Docker Compose

Volume types

Networking

Docker vs VM

Publishing images

Troubleshooting containers
