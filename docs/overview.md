# Introduction

This document outlines the software requirements for the development of an Matsci Odia learning platform aimed at providing a comprehensive educational experience for students. The platform will allow students to access courses, attend live lectures, participate in discussions, take exams, and interact with teachers.

---

## 2. User Requirements

### 2.1 Student Requirements

#### Authentication and Profile Management
- Students should be able to register and login using multiple providers such as Google and custom signup.
- Phone number and email should be unique identifiers and mandatory for registration.

#### Course Browsing and Selection
- Students can browse through available courses categorized into Class 9, Class 10, Class 11, Class 12, and Diploma Courses.
- Courses can be categorized into Free and Paid, with different pricing options.
- Each course may contain single subjects or packaged with multiple subjects:
    - IT Course – IT
    - BIPCM – Biology, Physics, Chemistry, Mathematics
    - PCMI – Physics, Chemistry, Mathematics, IT

#### Course Enrollment and Access
- Students can purchase courses based on their interests.
- Free courses can be accessed for attending live lectures and viewing recordings.

#### Live Lectures
- Students can attend scheduled live lectures.
- Features include:
    - Chat, raise hands, and control streaming quality (default 320p)
    - Speak with the teacher when allowed to unmute
    - Multiple students can communicate simultaneously
    - Teachers can block students from chat and voice
    - Share screens, use whiteboards, and present PDFs, Docs, Videos, etc.
    - Teachers can run polls (MCQ), show leaderboard

#### Recordings Access
- Students can access past and uploaded live session recordings
- Recordings should be auto-saved and accessible

#### Exams and Tests
- Objective and Subjective exams
- Raise exam/test related queries in-app

#### Help Requests *(Good to Have)*
- Students can raise help requests
- Teachers can respond live

---

### 2.2 Admin Requirements

#### Scheduling
- Admin can schedule live classes, tests, exams, and webinars

#### Course and Subject Management
- Admin can create and manage courses and subjects

#### User Management
- Admin can manage teacher accounts

#### Teacher Privileges
- Teachers can have admin rights
- Multiple admins can exist

---

## 3. Non-Functional Requirements

### Security
- Enforce secure login using OAuth and OTP-based mechanisms
- All communication must be encrypted using HTTPS/TLS
- Store sensitive information (e.g., passwords, payment data) using strong encryption standards (e.g., bcrypt, AES-256)
- Implement role-based access control (RBAC) for restricting user capabilities

### Scalability
- The system must support **5+ concurrent live classes**, each handling **1,000+ students** simultaneously without affecting performance
- Backend services should be auto-scalable using cloud-native orchestration (e.g., Kubernetes or serverless functions)
- Content delivery (live streams, video recordings, documents) must be optimized via **global CDNs**
- Real-time chat and interaction systems should scale to handle bursts of usage, especially during exams or lectures
- System must support future growth: up to **100,000+ daily active users**

### Reliability and Availability
- Ensure **99.9% uptime** with high availability configurations (multi-zone deployments, failover clusters)
- Implement retry mechanisms and queue buffering (e.g., message queues) to handle spikes in load
- Graceful degradation strategies should ensure platform responsiveness even under partial failures
- Data backup strategy must include automated nightly backups and on-demand snapshots

### Performance
- Live streaming must support **adaptive bitrate streaming (ABR)** to accommodate students with low bandwidth
- Load time for any page (including dashboard and course content) must be **< 2 seconds** on average
- Real-time interactions (chat, polls, raise hand) must reflect actions within **250ms latency**
- Caching strategies (browser, server-side, and CDN) should be implemented for static content

### Usability
- The user interface should be optimized for:
    - Desktop, tablet, and mobile devices (responsive design)
    - Touch and keyboard navigation
    - Screen reader accessibility (WCAG 2.1 Level AA compliance)
- Navigation should be intuitive with minimal clicks to reach key features like joining a class, viewing recordings, or accessing test materials
- The app should provide offline indicators and retry behavior when the connection is unstable

### Observability and Monitoring
- System must expose health checks, error logs, and metrics for real-time monitoring
- Integrate with centralized logging (e.g., ELK/EFK stack) and alerting systems (e.g., Prometheus + Grafana, New Relic)
- Automatically track latency, CPU usage, memory usage, and queue depth for all microservices

### Compliance and Data Protection
- Adhere to GDPR and local data protection laws for student and teacher data
- Allow users to delete their accounts and associated data (Right to be Forgotten)
- Maintain an audit trail of significant user actions (logins, content access, test submissions)


---

## 4. Good to Have

### API Interface
- API support for third-party integrations (e.g., scheduling systems)

---

## 5. Conclusion

This document captures all the core and extended software requirements for the Matsci Odia platform, ensuring that it delivers an effective, scalable, and user-friendly experience for students and administrators alike.
