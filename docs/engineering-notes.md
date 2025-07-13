# Engineering Notes for Web and Mobile Development

This document provides important guidance for the engineering team building the Matsci Odia educational platform. These principles aim to ensure performance, reliability, accessibility, and long-term maintainability of both the web and mobile applications.

---

## 1. Keep the Learning Context in Mind

- **Unstable Connectivity**: Many students will connect from low-bandwidth rural areas. All live classes, chat, and content should gracefully degrade and auto-retry.
- **Low-End Devices**: Mobile apps must be optimized for devices with low RAM, old Android/iOS versions, and small screens.
- **Asynchronous Access**: Not all students can join live — make sure lectures are recorded, accessible, and playable at low resolution.

---

## 2. Web & Mobile UX Expectations

- **Prioritize Mobile-First Design**: Use responsive frameworks and touch-friendly layouts.
- **Minimize Clicks to Join**: Students should reach a live class in under 3 taps/clicks from the homepage.
- **Offline Considerations**: Handle offline states gracefully — show “You are offline” banners, cache lecture links, and queue submissions when needed.
- **Accessible UX**: Support keyboard navigation and screen readers (especially on web).

---

## 3. Code Quality & Performance

- **Component Reusability**: Use modular UI components (React/Flutter components) to reduce duplication.
- **Lazy Loading**: Load only the necessary chunks of JS or modules, especially on mobile.
- **Optimize for First Paint**: Reduce time-to-first-render for class dashboard and content pages.

---

## 4. Video & Live Class Handling

- **Adaptive Bitrate Streaming**: Must be enabled via HLS/DASH to automatically adjust based on network speed.
- **Error Recovery**: If stream disconnects, auto-reconnect without requiring app reload.
- **Bandwidth Saver Option**: Provide students with a “Low Data Mode” toggle.

---

## 5. Test & Exam Flows

- **Autosave on Form Inputs**: While writing answers, especially subjective tests, ensure the system periodically saves progress.
- **Allow Graceful Submissions**: Let students know if their submission failed, and retry in the background.
- **Secure Uploads**: Ensure file uploads (answer sheets) are virus-scanned, secure, and resumable.

---

## 6. Notifications & Messaging

- **Use Topic-Based Notifications**: Push notifications should be filtered by course, class, and batch.
- **Avoid Notification Overload**: Only notify students when it’s relevant (e.g., class starting, result uploaded).

---

## 7. Integration Tips

- **Use Environment Configs**: Avoid hardcoding URLs or secrets; use environment files for staging/prod builds.
- **Retry Logic for APIs**: Use exponential backoff for retrying critical API calls like join class, upload test, etc.

---

## 8. Analytics & Observability

- Track:
    - Join/leave events for live classes
    - Test participation
    - Course completion %
- Integrate error tracking (e.g., Sentry, Firebase Crashlytics)
- Use platform monitoring dashboards (Grafana, New Relic)

---

## 9. Security Practices

- Use HTTPS for all communications
- Never store passwords in plaintext (use OAuth/hashed methods)
- Validate all inputs from forms, especially uploads
- Protect APIs with authentication and role-based access

---

## 10. Collaboration Guidelines

- Use a common API schema across frontend and backend
- Maintain shared documentation (Postman/Swagger)
- Sync regularly with product/design team on UX feedback from students and teachers

---

## Final Word

The platform’s success depends not just on features, but on how **fast**, **reliable**, and **frustration-free** it feels—especially under poor network conditions. Always think: *Would this work smoothly for a student in a remote village on a basic phone?*

Let’s build something impactful. 💡
