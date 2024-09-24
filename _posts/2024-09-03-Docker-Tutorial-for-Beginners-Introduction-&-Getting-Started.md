---
title: "Docker Tutorial for Beginners – Introduction & Getting Started"
excerpt: "Docker Tutorial for Beginners – Introduction & Getting Started"

header:
  image: "../assets/images/posts/2024-09-03-Docker-Tutorial-for-Beginners-Introduction-&-Getting-Started/cover.jpg"
  teaser: "../assets/images/posts/2024-09-03-Docker-Tutorial-for-Beginners-Introduction-&-Getting-Started/cover.jpg"
  caption: "Mastering Docker is like taming the sea of containers—once you control it, scaling becomes a breeze. - Abdul Rahman"
  categories: [Kubernetes, AWS, EC2, Docker]
  
---
# Introduction 

## Docker and Containers – Simplified
Docker is a tool that helps you create, deploy, and manage applications inside containers. Containers are lightweight and include everything needed to run an application, such as libraries and dependencies, ensuring the application works the same everywhere.

Here’s a breakdown:

**Docker Image**: A template or blueprint for your application. It includes the application and everything needed to run it.
**Container**: A running instance of a Docker image. It works like an isolated mini-computer running your application.
**Docker Hub**: A public repository where you can find Docker images to use.
**Dockerfile**: A file containing the instructions to build a Docker image.


## Overview
Docker allows developers to package applications into containers—standardized units that contain everything needed to run code, including libraries, system tools, and settings.

---

## Prerequisites
1. **An EC2 Instance** running Ubuntu (at least 15GB of storage).If you haven't set up an EC2 instance yet, check out my previous [Blog->Guide to creating an EC2 instance](https://abdulrahmanh.com/blog/How-to-Create-an-AWS-EC2-Instance) before proceeding.
2. **SSH access** to the instance.

## Part 1: Installing Docker

### Step 1: Update the Package Index
Before installing Docker, ensure your package list is up to date.
```bash
sudo apt-get update
```

### Step 2: Install Required Dependencies
```bash
sudo apt-get install -y ca-certificates curl gnupg lsb-release
```

### Step 3: Add Docker’s Official GPG Key
```bash
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

### Step 4: Set up Docker’s Stable Repository
```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### Step 5: Install Docker
```bash
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io
```

### Step 6: Verify Docker Installation
Test if Docker was installed correctly by running a test container:
```bash
docker run hello-world
```

---

## Part 2: Managing Docker

### Step 1: Pulling an Image from Docker Hub
```bash
docker pull httpd
```

### Step 2: Running a Container
```bash
docker run -itd -p "8080:80" httpd
```

### Step 3: List Running Containers
```bash
docker ps
```

### Step 4: Accessing the Container
```bash
docker exec -it CONTAINER_ID /bin/bash
```

### Step 5: Stopping a Container
```bash
docker stop CONTAINER_ID
```

---

## Part 3: Advanced Docker Usage

### Creating a Dockerfile

1. **Create a Directory** for your project:
    ```bash
    mkdir myproject
    cd myproject
    ```
    
2. **Create a Dockerfile**:
    ```bash
    vi Dockerfile
    ```

3. **Add the Following Instructions**:
    ```Dockerfile
    FROM ubuntu:latest
    RUN apt-get update && apt-get install -y nginx
    CMD ["nginx", "-g", "daemon off;"]
    ```

4. **Build the Docker Image**:
    ```bash
    docker build -t mynginx .
    ```

### Volumes and Persistence
To keep data persistent even if the container is deleted, Docker allows you to use **volumes**:

1. **Create a Volume**:
    ```bash
    docker volume create myvol
    ```

2. **Run a Container with Volume Mounting**:
    ```bash
    docker run -itd -v myvol:/usr/share/nginx/html -p 8080:80 nginx
    ```

### Push an Image to Docker Hub
1. **Log in to Docker Hub**:
    ```bash
    docker login
    ```

2. **Tag the Image**:
    ```bash
    docker tag mynginx yourusername/mynginx
    ```

3. **Push the Image**:
    ```bash
    docker push yourusername/mynginx
    ```

---

## Conclusion
With this guide, you should be able to install Docker, manage containers, create custom images, and even share them on Docker Hub. Keep practicing and try to create different kinds of applications in Docker containers!

---

For more advanced Docker guides and blog posts, visit [www.abdulrahmanh.com](http://www.abdulrahmanh.com).
