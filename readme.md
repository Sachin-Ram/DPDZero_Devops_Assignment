### 🧪 **DevOps Intern Assignment: Nginx Reverse Proxy + Docker**

### 👋 Hello, I'm Sachin Ram, and this is my submission for the DevOps intern assignment .

This project demonstrates a containerized  architecture using **Docker**, **NGINX**, and **Docker Compose** to proxy multiple backend services through a single NGINX reverse proxy.


## 📁 Project Structure

1. **Two Dockerized backend services** (can be dummy services) run on different ports.
2. An **Nginx reverse proxy** (also in a Docker container) routes:

   * `/service1` requests to backend service 1
   * `/service2` requests to backend service 2
3. All services are accessible via a single port (e.g., `localhost:82`).

---

### 📁 Suggested Project Structure

```
.
├── docker-compose.yml
├── nginx/
│ ├── nginx.conf # NGINX configuration
├── service_1/
│ ├── app.py # Go service or equivalent
│ └── Dockerfile
├── service_2/
│ ├── app.py # Python Flask service
│ └── Dockerfile
└── README.md
```
---

## ✅ Requirements Implemented

| Feature                                       | Status |
|----------------------------------------------|--------|
| Two backend services                         | ✅      |
| JSON responses per service                   | ✅      |
| NGINX reverse proxy routing                  | ✅      |
| Routing with URL prefix `/service1`, `/service2` | ✅  |
| Logging timestamp and path                   | ✅      |
| Healthchecks for services                    | ✅      |
| Single command startup                       | ✅      |
| Runs entirely with Docker (bridge network)   | ✅      |

---
---


## 🌐 Routing Overview

| Path                | Routed To         | Response                   |
|---------------------|------------------|----------------------------|
| `/service1/ping`    | `go_app:8001`    | `Json response from service1` |
| `/service2/ping`    | `python_app:8002` | `Json response from service2` |


---
---
## 🔁 NGINX Rewrite Logic (short)

```nginx
location /service1/ {
    rewrite ^/service1(/.*)$ $1 break;
    proxy_pass http://go_app;
}

location /service2/ {
    rewrite ^/service2(/.*)$ $1 break;
    proxy_pass http://python_app;
}

---

## 🚀 Quick Start

To start the entire system using Docker Compose:

```bash
docker-compose up --build

