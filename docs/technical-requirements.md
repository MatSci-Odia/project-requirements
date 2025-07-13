# 📌 Technical Requirements – Matsci Odia Learning Platform

This document outlines the expected technical architecture and platform requirements for the development of the Matsci Odia online education system, including web and mobile applications.

---

## 🧩 1. Platform Overview

The platform consists of:

- A **Mobile App** for students (Android & iOS)
- A **Web Portal** for teachers and admins
- A cloud-based backend for service orchestration and media storage
- Live class integration with a streaming provider

---

## 📱 2. Mobile Application (Students)

### Supported Platforms
- Android (API 24+)
- iOS (iOS 12+)

### Key Features
- OTP and Google sign-in
- Course browsing and enrollment
- Join live classes with video and chat
- Raise hand and speak (controlled by teacher)
- Access lecture recordings
- Attempt MCQ/Subjective tests
- Upload answer sheets
- Batch-specific chat rooms

### Recommended Tech
- **Framework**: React Native *(single codebase)* or Flutter
- **Video SDK**: Agora / Zoom *(for stability & mute control)*
- **Storage**: AWS S3 / Cloudflare R2 *(for videos, notes, and tests)*
- **Notifications**: Firebase (Android), APNs (iOS)
- **Offline Mode**: Cache recent content for slow/no internet

### 🚀 Suggestions
- Use **adaptive bitrate streaming** to support low-bandwidth students
- Implement **background retry queue** for exam uploads
- Compress and optimize assets for low-end phones

---

## 🧑‍💻 3. Admin / Teacher Web Portal

### Key Features
- Schedule and run live sessions
- Upload class content (PDF, DOC, Video, etc.)
- Create and evaluate quizzes and exams
- Manage users (teachers/students)
- Access dashboards and usage metrics
- Apply and manage coupons/subscriptions

### Recommended Tech Stack
| Layer        | Tech Stack                         |
|-------------|------------------------------------|
| Frontend     | React.js (with Tailwind or MUI)    |
| Backend      | Spring Boot (Java), RESTful APIs   |
| DB           | PostgreSQL on AWS RDS              |
| Streaming    | Agora / Zoom / Jitsi (pluggable)   |
| File Storage | AWS S3 or Cloudflare R2            |
| CI/CD        | GitHub Actions                     |

### 💡 Suggestions
- Use **Role-Based Access Control (RBAC)** with Spring Security
- Organize content in S3 using course→batch→session structure
- Enable **pre-signed uploads** for student answer sheets
- Use **pagination, filters, and caching** for high-volume pages
- Add **CSV export/import** for managing large student rosters

---

## 🔒 4. Security

### Essentials
- All endpoints secured with JWT or OAuth2
- Passwordless auth via OTP (login link/phone code)
- HTTPS enforced across all layers
- Secure multipart upload for large files
- Audit logs for all admin actions
- Encrypt PII at rest and in transit

### 🚨 Suggestions
- Use **rate-limiting** and CAPTCHA for public APIs (e.g. login)
- Add **IP/location logging** for admin access
- Integrate with **Vault or AWS Secrets Manager** for secure config

---

## 🚀 5. Performance & Scalability

### Requirements
- App load < 3s on 3G connections
- Handle 5+ parallel classes with 1000+ students each
- Low-latency chat and audio (under 300ms)
- Dynamic scaling of services and media delivery

### Suggestions
- Use **CDN** (CloudFront, Cloudflare) for static & video content
- Scale backend via **Kubernetes** or **ECS Fargate**
- Use **Redis caching** for course data and test metadata
- Employ **WebSocket** or **MQTT** for real-time chat

---

## 📦 6. Infrastructure

| Component      | Suggested Service                  |
|----------------|-------------------------------------|
| Hosting        | AWS / GCP / Azure                   |
| CI/CD          | GitHub Actions                      |
| DB             | AWS RDS (PostgreSQL), daily backup  |
| Object Storage | AWS S3, lifecycle policy enabled    |
| Domain         | Route53 / Cloudflare DNS            |
| Monitoring     | Prometheus + Grafana / New Relic    |

### DevOps Suggestions
- Use **Terraform** or IaC for infrastructure provisioning
- Set up **stage & prod** environments with clear config
- Enable **autoscaling & alerting**

---

## 📊 7. Analytics and Observability

### Requirements
- Track user behavior: logins, class joins, test activity
- Monitor backend latency and availability
- Alert on service failures and high load

### Tools
- **Frontend**: Google Analytics + Custom Events
- **Backend**: Prometheus, Loki, Grafana
- **Error Tracking**: Sentry or Firebase Crashlytics

---

## 📌 8. Engineering Notes

- All APIs must be versioned (e.g. `/api/v1/...`)
- Use OpenAPI (Swagger) for backend contract documentation
- Structure repos into mono-repo or clearly named services
- Use `.env` files with `.example` templates
- Store large file uploads via S3 **pre-signed URLs**
- Provide **dark mode toggle** for better UX
- Maintain strong automated test coverage (unit + integration)

---

## 📘 Summary

| Area               | Stack / Tool                      |
|--------------------|-----------------------------------|
| Mobile App         | React Native / Flutter            |
| Web Frontend       | React + Tailwind / MUI            |
| Backend Services   | Spring Boot + JWT                 |
| Database           | PostgreSQL (RDS)                  |
| File Storage       | AWS S3                            |
| Live Video         | Agora / Zoom SDK                  |
| DevOps             | GitHub Actions + Docker           |
| Analytics          | Google Analytics + Prometheus     |
| Real-time Comm     | WebSocket / MQTT                  |

---

## 💡 Optional Future Features

- Offline access to downloaded lectures
- Gamified quiz results and streak tracking
- Course recommendations using ML
- Native LMS plugin compatibility (SCORM/xAPI)
- Video transcription and subtitle generation

