# 🐋 Docker
***

Docker is a containerization platform that enables developers to package applications and their dependencies into lightweight, portable containers. These containers can run consistently across different environments, from development laptops to production servers, solving the "it works on my machine" problem.

## What is Docker?

Docker uses operating system-level virtualization to deliver software in packages called containers. Unlike traditional virtual machines that virtualize entire operating systems, containers share the host OS kernel while maintaining isolation between applications. This makes containers much more efficient in terms of resource usage and startup time.

## Key Features

**Portability**: Containers run consistently across different environments, eliminating deployment issues caused by environment differences.

**Resource Efficiency**: Containers use fewer resources than virtual machines since they share the host OS kernel rather than running separate operating systems.

**Scalability**: Easy horizontal scaling by spinning up multiple container instances, with built-in orchestration tools for managing container clusters.

**Isolation**: Applications run in isolated environments, preventing conflicts between different applications and their dependencies.

**Version Control**: Docker images can be versioned, allowing easy rollbacks and consistent deployments across environments.

**Ecosystem**: Large ecosystem of pre-built images available on Docker Hub, accelerating development and deployment processes.

## Installation

### Ubuntu Linux (Using Convenience Script)

The convenience script is the fastest way to install Docker on Ubuntu for development environments:

```bash
# Download and run the convenience script
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh

# Add your user to the docker group (optional, to run without sudo)
sudo usermod -aG docker $USER

# Log out and back in, or run:
newgrp docker

# Verify installation
docker run hello-world
```

### Windows with WSL2

Docker Desktop for Windows with WSL2 backend provides the best Windows experience:

**Prerequisites:**
- Windows 10 version 1903+ or Windows 11
- WSL2 installed and enabled
- A Linux distribution installed in WSL2

**Installation Steps:**

1. **Install WSL2** (if not already installed):
```powershell
# Run in PowerShell as Administrator
wsl --install
# Restart your computer
```

2. **Download and Install Docker Desktop:**
   - Download Docker Desktop from [docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop/)
   - Run the installer and follow the setup wizard
   - During installation, ensure "Use WSL 2 instead of Hyper-V" is selected

3. **Configure WSL2 Integration:**
   - Open Docker Desktop settings
   - Go to Resources → WSL Integration
   - Enable integration with your WSL2 distributions
   - Apply & Restart

4. **Verify Installation:**
```bash
# In WSL2 terminal
docker --version
docker run hello-world
```

### macOS

Download Docker Desktop from the official website and install:

```bash
# Verify installation
docker --version
docker run hello-world
```

## Core Concepts

**Images**: Read-only templates used to create containers. Think of them as blueprints or snapshots of applications with all their dependencies.

**Containers**: Running instances of Docker images. Containers are lightweight, isolated environments where applications execute.

**Dockerfile**: Text file containing instructions to build Docker images. Defines the application environment, dependencies, and configuration.

**Docker Hub**: Cloud-based registry service for sharing Docker images. Contains thousands of pre-built images for common applications and services.

**Volumes**: Persistent data storage mechanism that allows data to persist beyond container lifecycle.

**Networks**: Docker's networking system that enables communication between containers and external systems.

## Basic Docker Commands

### Working with Images

```bash
# Pull an image from Docker Hub
docker pull ubuntu:20.04

# List local images
docker images

# Build image from Dockerfile
docker build -t myapp:latest .

# Remove image
docker rmi image_name:tag
```

### Managing Containers

```bash
# Run a container
docker run ubuntu:20.04

# Run container interactively
docker run -it ubuntu:20.04 /bin/bash

# Run container in background (detached)
docker run -d nginx

# Run with port mapping
docker run -p 8080:80 nginx

# List running containers
docker ps

# List all containers (including stopped)
docker ps -a

# Stop container
docker stop container_id

# Remove container
docker rm container_id
```

### Container Operations

```bash
# Execute command in running container
docker exec -it container_id /bin/bash

# View container logs
docker logs container_id

# Copy files between host and container
docker cp file.txt container_id:/path/to/destination
docker cp container_id:/path/to/file .

# Inspect container details
docker inspect container_id
```

## Working with Volumes

```bash
# Create named volume
docker volume create myvolume

# Run container with volume mount
docker run -v myvolume:/data ubuntu:20.04

# Mount host directory
docker run -v /host/path:/container/path ubuntu:20.04

# List volumes
docker volume ls

# Remove volume
docker volume rm myvolume
```

## Docker Compose

Docker Compose simplifies multi-container applications using YAML configuration:

```yaml
# docker-compose.yml
version: '3.8'
services:
  web:
    build: .
    ports:
      - "8000:8000"
    volumes:
      - .:/code
    depends_on:
      - db
  db:
    image: postgres:13
    environment:
      POSTGRES_PASSWORD: password
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

```bash
# Start services
docker-compose up

# Start in background
docker-compose up -d

# Stop services
docker-compose down

# View logs
docker-compose logs
```

## Dockerfile Best Practices

```dockerfile
# Use official base images
FROM node:16-alpine

# Set working directory
WORKDIR /app

# Copy package files first (for better caching)
COPY package*.json ./

# Install dependencies
RUN npm ci --only=production

# Copy application code
COPY . .

# Create non-root user
RUN addgroup -g 1001 -S nodejs
RUN adduser -S nextjs -u 1001
USER nextjs

# Expose port
EXPOSE 3000

# Define startup command
CMD ["npm", "start"]
```

## Networking

```bash
# Create custom network
docker network create mynetwork

# Run container on specific network
docker run --network mynetwork nginx

# List networks
docker network ls

# Inspect network
docker network inspect mynetwork
```

## Security Best Practices

**Use Official Images**: Start with official images from trusted sources and keep them updated.

**Run as Non-Root**: Create and use non-privileged users in containers whenever possible.

**Scan Images**: Regularly scan images for vulnerabilities using tools like `docker scan`.

**Limit Resources**: Set memory and CPU limits to prevent resource exhaustion.

**Use Secrets**: Store sensitive data using Docker secrets or external secret management systems.

**Keep Images Small**: Use multi-stage builds and minimal base images to reduce attack surface.

## Troubleshooting

```bash
# Check Docker daemon status
sudo systemctl status docker

# View Docker daemon logs
journalctl -u docker.service

# Check disk usage
docker system df

# Clean up unused resources
docker system prune

# Clean up everything (use with caution)
docker system prune -a --volumes
`