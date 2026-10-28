# 🐳 Docker Setup Guide - PhytoScan AI Platform

This repository is fully containerized using **Docker** and **Docker Compose** for seamless deployment of both the **React Frontend** and **Python Flask Backend**.

---

## 🛠️ Architecture

* **Frontend Container**: Multi-stage build (`Node 20` ➔ `Nginx Alpine`) serving static React/Vite assets on port **5173**. Includes Nginx proxy configuration to forward `/api/*` to the backend.
* **Backend Container**: Python 3.11 container running Gunicorn server on port **8000**.
* **Bridge Network**: `phytoscan-network` for secure inter-container communication.

---

## 🚀 How to Run with Docker Compose

### 1. Build and Start Containers
From the project root directory, execute:

```bash
docker compose up --build -d
```

### 2. Access the Application
* **Frontend Web Application**: Open `http://localhost:5173/`
* **Backend API Health Check**: `http://localhost:8000/api/health`

### 3. Stop Containers
```bash
docker compose down
```

### 4. View Container Logs
```bash
docker compose logs -f
```

---

## 📁 Docker Directory Structure

```
Plant/
├── docker-compose.yml           # Root multi-container orchestration
├── README-DOCKER.md             # Docker documentation guide
├── Backend/
│   ├── app.py                   # Flask API service & inference endpoints
│   ├── requirements.txt         # Python dependencies
│   ├── Dockerfile               # Backend container recipe
│   └── .dockerignore            # Python ignore patterns
└── Front-end/
    ├── Dockerfile               # Multi-stage React/Nginx container build
    ├── nginx.conf               # Nginx reverse proxy configuration
    └── .dockerignore            # Node.js ignore patterns
```
