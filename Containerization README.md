# Containerized Full-Stack Application

This repository contains a **containerized version** of a full-stack application using **Docker and Docker Compose**. It includes **Frontend, Backend, and MongoDB** services, all orchestrated using **Docker Compose**.

## 📌 Table of Contents
- Setup Instructions
- Network and Security Configurations
- Troubleshooting Guide
- Files Included

## 🛠 Setup Instructions

### Prerequisites
Before running the application, ensure you have:
- **Docker** and **Docker Compose** installed
- **Git** installed to clone the repository

### Steps to Run the Containers
1️⃣ **Clone the repository**:
```sh
git clone <https://github.com/Redieteshome/cloud-engineering-docker-assesement.git>
```

2️⃣ **Build and start the containers in detached mode**:
```sh
docker compose build
docker compose up -d
```

3️⃣ **Check if containers are running**:
```sh
docker ps
```
You should see three containers (**frontend, backend, and MongoDB**) running.

4️⃣ **Access the application**:
- **Frontend:** http://localhost:3000
- **Backend API:** http://localhost:5000/api/todos
- **MongoDB** is running internally on **port 27017**

5️⃣ **Run the test script** to verify everything:
```sh
bash test.sh
```

### Stopping the Containers
To stop the containers without deleting them:

```sh
docker compose down
```

To remove **all containers and volumes**:

```sh
docker compose down -v
```

---

## 🔒 Network and Security Configurations

### Network Setup
- The services communicate inside a **Docker network** created by `docker-compose.yml`.
- **Frontend** connects to **Backend** via the Docker network.
- **Backend** connects to **MongoDB** using the internal network.

### Exposed Ports
| Service   | Container Port | Exposed Port |
|-----------|--------------|--------------|
| Frontend  | 3000        | 3000        |
| Backend   | 5000        | 5000        |
| MongoDB   | 27017       | 27017       |

### Security Settings
- MongoDB does **not** expose credentials in `docker-compose.yml` (for simplicity in local development).
- In production, **environment variables** should be used for database credentials.

---

## ⚠️ Troubleshooting Guide

1️⃣ **Containers not starting?**
   - Run `docker ps -a` to check for errors.
   - Check logs using `docker logs <container_id>`.

2️⃣ **Frontend or Backend not accessible?**
   - Ensure the ports are **not blocked** by another application.
   - Restart the containers: `docker compose down && docker compose up -d`

3️⃣ **MongoDB connection issues?**
   - Run `docker exec -it <mongo_container_id> mongosh` and try `db.runCommand({ping: 1})`.

4️⃣ **Docker daemon not running?**
   - Start Docker and run `docker info` to confirm it’s running.

---

## 📂 Files Included

### 1️⃣ `Dockerfile` (Frontend, Backend, Database)
Defines how each service is built inside a Docker container.

### 2️⃣ `docker-compose.yml`
Orchestrates the **Frontend, Backend, and Database** services.

### 3️⃣ `test.sh`
A script to check if the containers are running and accessible.

### 4️⃣ `cloud_engineering_assessment_documentation3 (1).pdf`
Detailed explanation of the setup, configurations, and troubleshooting steps.

🎯 **Now, your application is containerized and ready to be demonstrated!** 🚀

