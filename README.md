# 🧠 Matsci Odia – Learning Platform Documentation

Welcome to the documentation repository for **Matsci Odia**, a modern educational platform that delivers a blended learning experience for students and empowers educators with tools to manage, assess, and teach effectively.

This repository hosts all functional and technical documentation required to build and maintain the system.

🌐 **Live Docs Site**: [https://matsci-odia.github.io/project-requirements/](https://matsci-odia.github.io/project-requirements/)

---

## 📘 Project Summary

**Matsci Odia** includes:

- A **mobile app** for students to access courses, attend live lectures, participate in tests, and communicate with teachers.
- A **web portal** for teachers and admins to manage classes, users, content, exams, and payments.
- A cloud-native backend that is scalable, secure, and extensible.

---

## 📱 Mobile App Requirements

- Platforms: Android (API 24+), iOS (iOS 12+)
- Key Features:
    - OTP & Google login
    - Join live classes (video + chat)
    - Chat per batch (subject-wise)
    - View lecture recordings
    - Take tests (MCQ & subjective)
    - Upload answer sheets

Recommended Tech:
- React Native / Flutter
- Agora or Zoom for video
- Firebase for notifications
- S3 or Cloudflare R2 for content

---

## 🧑‍💻 Web Platform Requirements

- Audience: Teachers, Admins, Super Admins
- Key Features:
    - User/course/subject management
    - Live class scheduling and moderation
    - Test & exam setup
    - Student roster management
    - Payments & coupon tracking
    - Content uploading & structure

Tech Stack:
- Frontend: React.js (with MUI or Tailwind)
- Backend: Spring Boot (REST API)
- DB: PostgreSQL (AWS RDS)
- File Storage: AWS S3
- CI/CD: GitHub Actions

---

## ⚙️ Technical Architecture

- Scalable via Kubernetes or Fargate
- Secure via HTTPS, JWT/OAuth2
- Streaming via Agora/Zoom (engineering team’s choice)
- WebSocket/MQTT for real-time messaging
- Monitored with Prometheus + Grafana / New Relic
- Optional: ML-powered recommendations, transcription

---

## 📄 Documentation Stack

- **Engine**: [MkDocs](https://www.mkdocs.org/)
- **Theme**: [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
- **Deployment**: GitHub Actions → GitHub Pages

---

## 🧪 Running Docs Locally

### Requirements:
- Python 3.7+
- `pip`

### Install MkDocs:

```shell
pip install mkdocs mkdocs-material

```

```shell
mkdocs serve
mkdocs gh-deploy
```
