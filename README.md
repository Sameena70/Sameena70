# Sameena Kausar — Full-Stack Software Engineer

Open to **Software Engineer · Full-Stack Developer · Backend Developer · Junior Developer** opportunities

<p>
  <a href="https://www.linkedin.com/in/sameena70">
    <img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn">
  </a>
  <a href="mailto:sameenakausar070@gmail.com">
    <img src="https://img.shields.io/badge/Email-D14836?style=flat-square&logo=gmail&logoColor=white" alt="Email">
  </a>
  <a href="https://github.com/Sameena70/RenewGrid">
    <img src="https://img.shields.io/badge/RenewGrid-181717?style=flat-square&logo=github&logoColor=white" alt="RenewGrid">
  </a>
</p>

I work primarily with **Python, FastAPI, React, PostgreSQL, and REST APIs**.

Most recently, I built RenewGrid as my final-year Computer Science project. It is a full-stack e-waste recycling platform that connects producers, collectors, and recycling facilities through a single system. I handled the database schema, the FastAPI backend with a repository and service layer, a React 19 SPA with four role-based dashboards, a 12-state pickup lifecycle, AI price estimation, QR-based verification, and an automated reward engine.

---

## Technical Focus

- **Languages:** Python · JavaScript · Java · C · C++
- **Backend:** FastAPI · REST APIs · JWT authentication · SQLAlchemy · Alembic · slowapi · smtplib
- **Frontend:** React 19 · React Router v7 · Vite · TailwindCSS · Leaflet · html5-qrcode · jsPDF
- **Databases:** PostgreSQL · SQL
- **Architecture:** Repository pattern · Service layer · RBAC · State machines · Background tasks
- **Tools:** Git · GitHub · Node.js · VS Code

---

## Skills

[![Skills](https://skillicons.dev/icons?i=python,fastapi,react,postgres,js,html,css,tailwind,git,github,vite,nodejs,java,cpp,vscode)](https://skillicons.dev)

---

## Featured Project

### [RenewGrid — FastAPI · React · PostgreSQL · AI Estimation](https://github.com/Sameena70/RenewGrid)

RenewGrid is a full-stack e-waste recycling and rewards platform I built from scratch as my final-year Computer Science project. The system connects e-waste producers, pickup collectors, and recycling facilities under one platform. I designed the database, built the backend API, and built the frontend with four separate dashboards for each role.

### What I implemented

- **Full-stack architecture:** Designed a 14-table PostgreSQL schema, built the FastAPI backend using a repository pattern with one repository per domain and a service layer that keeps all business logic out of the routers, and built the React 19 SPA with role-based protected routing at both the API and frontend layers
- **AI pricing engine:** Reads admin-configured pricing rules from the database per waste category and applies a base price, a per-kg rate, and a condition multiplier for working, partial, or broken items. Falls back to hardcoded category rates when no active rule exists
- **12-state pickup lifecycle:** Built a pickup status state machine from PENDING through ASSIGNED, IN_PROGRESS, PROOF_UPLOADED, COLLECTED, DELIVERED, PROCESSING, to COMPLETED. Every transition is validated against the current state and written to an immutable pickup_status_history table with actor ID, timestamp, and an optional note
- **JWT authentication:** Dual-token system with short-lived access tokens and 7-day refresh tokens. All protected routes go through a get_current_user FastAPI dependency. Login is rate-limited to 5 requests per minute via slowapi to block brute-force attempts
- **RBAC with 4 roles:** Admin, User, Collector, and Recycler are enforced at the API through FastAPI dependency injection and at the frontend through ProtectedRoute wrappers. Each role has its own dashboard with no route overlap
- **QR code verification:** The server generates a QR code per pickup. The user shows it on screen and the collector scans it with their camera via html5-qrcode before the pickup status can advance. This prevents misidentification between jobs
- **Reward and CO2 engine:** A background task runs on pickup completion, awards 10 points per kg collected, and calculates CO2 saved at 0.5 kg per kg of waste. It checks for an existing reward before inserting so it is safe to call more than once. It also sends an in-app notification to the producer
- **Transactional email:** Password reset HTML emails are sent via Python smtplib as a FastAPI BackgroundTask. The setup is Gmail-compatible with STARTTLS and tokens expire after 30 minutes. All credentials are read from environment variables
- **Collector proof upload:** Collectors upload a photo as proof of collection. The file is validated by MIME type and capped at 5 MB, stored under uploads/proofs/ with a UUID-prefixed filename, and linked to the pickup through a dedicated CollectorProof model
- **Admin analytics dashboard:** Aggregates platform-wide data including user counts, waste volume, pickup status breakdown, CO2 saved, and revenue. Includes trend forecasting, area analytics, pricing rule management, manual reward point assignment, and PDF report export
