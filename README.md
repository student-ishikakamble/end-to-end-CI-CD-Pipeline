

## 📌 End-to-End CI/CD Pipeline using Jenkins, Docker & GitHub

### 🚀 Project Overview

This project demonstrates a complete CI/CD pipeline where code changes pushed to GitHub automatically trigger Jenkins builds using webhooks. Jenkins builds a Docker image and deploys the application inside a container.

---

## 🧱 Architecture

```text
GitHub (Code Push)
        ↓
GitHub Webhook
        ↓
Ngrok Public URL
        ↓
Jenkins Pipeline Trigger
        ↓
Docker Image Build
        ↓
Docker Container Deployment
        ↓
Application Running on Port 8080
```

---

## ⚙️ Tech Stack

* Jenkins (CI/CD automation)
* Git & GitHub (Version control)
* Docker (Containerization)
* Flask (Python web app)
* Ngrok (Webhook exposure)

---

## 📁 Project Structure

```text
end-to-end-CI-CD-Pipeline/
│
├── app.py              # Flask application
├── requirements.txt    # Dependencies
├── Dockerfile          # Container setup
└── Jenkinsfile         # CI/CD pipeline
```

---

## 🚀 CI/CD Pipeline Stages

### 1️⃣ Checkout Code

Jenkins pulls latest code from GitHub

### 2️⃣ Build Docker Image

```bash
docker build -t ci-cd-app .
```

### 3️⃣ Stop Old Container

```bash
docker rm -f ci-cd-container || true
```

### 4️⃣ Run New Container

```bash
docker run -d -p 8080:8080 --name ci-cd-container ci-cd-app
```

---

## 🔗 Webhook Integration

GitHub → Jenkins trigger via ngrok:

```text
https://<ngrok-url>/github-webhook/
```

---

## 🎯 How to Run

1. Push code to GitHub
2. Jenkins automatically triggers
3. Docker builds image
4. App runs on:

```text
http://localhost:8080
```

---

## 🎉 Output

```json
{
  "message": "CI/CD Pipeline Working Successfully 🚀"
}
```

---

## 👨‍💻 Author

Student DevOps Engineer – Ishika Kamble

