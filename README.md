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

I work primarily with **Python, FastAPI, React, PostgreSQL, REST APIs, and JWT-based authentication**.

Computer Science graduate who designed and built RenewGrid — an AI-powered e-waste lifecycle management platform — from scratch as a final-year project. I handled everything: database schema design, a layered FastAPI backend using the repository pattern, a React 19 SPA with four completely isolated role dashboards, a 12-state pickup state machine with an immutable audit trail, AI price estimation, QR-based collector verification, and an automated reward and CO₂ tracking engine.

---

## Technical Focus

- **Languages:** Python · JavaScript · Java · C · C++
- **Backend:** FastAPI · REST APIs · JWT (access + refresh tokens) · SQLAlchemy · Alembic · slowapi · smtplib
- **Frontend:** React 19 · React Router v7 · Vite · TailwindCSS · Leaflet · html5-qrcode · jsPDF
- **Databases:** PostgreSQL · SQL · SQLAlchemy ORM
- **Architecture:** Repository pattern · Service layer · RBAC · State machines · Background tasks · File upload handling
- **Tools:** Git · GitHub · Node.js · npm · VS Code

---

## Featured Project

### [RenewGrid — FastAPI · React · PostgreSQL · AI Estimation](https://github.com/Sameena70/RenewGrid)

RenewGrid is a full-stack e-waste recycling and rewards platform I designed and built entirely from scratch as my final-year Computer Science project. The system connects e-waste producers, pickup collectors, and recycling facilities under a single platform. I handled the full stack — from PostgreSQL schema design and FastAPI backend architecture to the React 19 SPA with four completely isolated role-based dashboards.

### What I implemented

- **Full-stack architecture from scratch:** Designed a 14-table PostgreSQL schema, built the entire FastAPI backend using a repository pattern (one repository per domain) and a service layer that keeps all business logic out of routers, and implemented the React 19 SPA with protected role routing enforced at both the API and frontend layers
- **AI pricing engine:** Reads admin-configured `PricingRule` rows from the database per category and applies a base price, per-kg rate, and condition multiplier (working / partial / broken); falls back to hardcoded category rates when no active rule exists for a given category
- **12-state pickup lifecycle:** Implemented a pickup status state machine (`PENDING → ASSIGNED → IN_PROGRESS → PROOF_UPLOADED → COLLECTED → DELIVERED → PROCESSING → COMPLETED`) with every transition validated against the current state and persisted to an immutable `pickup_status_history` audit table with actor ID, timestamp, and an optional note
- **JWT authentication system:** Dual-token system with short-lived access tokens and 7-day refresh tokens; all protected routes verified through a `get_current_user` FastAPI dependency; login endpoint rate-limited to 5 requests/minute via slowapi to block brute-force
- **RBAC — 4 isolated roles:** Admin, User, Collector, and Recycler enforced at the API through FastAPI dependency injection and at the frontend through `ProtectedRoute` wrappers — each role accesses a completely separate dashboard with no route overlap
- **QR code verification:** Server generates a QR code per pickup; the user displays it on-screen; the collector scans it with their device camera using html5-qrcode before the status can advance — preventing misidentification
- **Reward & CO₂ engine:** Background task triggered on pickup completion that awards 10 pts/kg and calculates CO₂ saved at 0.5 kg/kg; idempotent — checks for an existing reward before inserting; dispatches an in-app notification to the producer on success
- **Transactional email:** Password-reset HTML emails dispatched via Python smtplib as a FastAPI `BackgroundTask`; STARTTLS/Gmail-compatible; 30-minute token expiry; all SMTP credentials read from environment variables
- **Collector proof upload:** Collectors upload a photo as evidence of collection; validated by MIME type and size (5 MB cap); stored under `uploads/proofs/` with a UUID-prefixed filename and linked to the pickup record via a dedicated `CollectorProof` model
- **Admin analytics dashboard:** Platform-wide aggregates across users, waste volume, pickups by status, CO₂ saved, and revenue; includes trend forecasting, geographic area analytics, AI pricing rule management, manual reward point assignment, and PDF report export

---

## GitHub Activity

<p>
  <img src="https://github-readme-stats.vercel.app/api?username=Sameena70&show_icons=true&theme=dark&hide_border=true&count_private=true&include_all_commits=true" alt="GitHub Stats">
  <br>
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Sameena70&layout=compact&theme=dark&hide_border=true&langs_count=6" alt="Top Languages">
</p>
