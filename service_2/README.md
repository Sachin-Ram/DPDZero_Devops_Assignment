### 📘 Service 2 – Python Flask API

This is a lightweight HTTP service written in Python using Flask. It exposes two simple endpoints and is designed to be used behind a reverse proxy like Nginx.

---

### 🔧 Endpoints

| Method | Path     | Description      | Response Example                      |
| ------ | -------- | ---------------- | ------------------------------------- |
| GET    | `/ping`  | Health check     | `{"status": "ok", "service": "2"}`    |
| GET    | `/hello` | Greeting message | `{"message": "Hello from Service 2"}` |

---

#### Run with Python:

```bash
uv run app.py
```

This will start the server on port `8002`.

---


Then visit:

* [http://localhost:8002/ping](http://localhost:8002/ping)
* [http://localhost:8002/hello](http://localhost:8002/hello)

---

## Build and Run Docker

#### Build the Docker Image for Service 1

```bash
cd ./service_2
docker build -t image-name .
```
#### Run Service 1 on Port 8001
```bash
docker run -p 8002:8002 image-name
```
