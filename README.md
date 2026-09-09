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

I am a Computer Science graduate who built RenewGrid as a final-year project. It is a full-stack e-waste recycling and rewards platform. I designed the database, built the FastAPI backend using a repository and service layer pattern, and built the React 19 frontend with four separate role dashboards. The system runs an AI price estimator on every waste submission, manages a 13-state pickup lifecycle with a full audit trail, and generates reward points and CO2 savings automatically when a pickup completes.

---

## Technical Focus

- **Languages:** Python, JavaScript, Java, C, C++
- **Backend:** FastAPI, REST APIs, JWT authentication (python-jose), bcrypt, SQLAlchemy, Alembic, slowapi, smtplib
- **Frontend:** React 19, React Router v7, Vite, TailwindCSS, Leaflet, html5-qrcode, jsPDF
- **Databases:** PostgreSQL, SQL
- **Patterns:** Repository pattern, service layer, RBAC, state machines, background tasks
- **Tools:** Git, GitHub, Node.js, VS Code

---

## Skills

[![Skills](https://skillicons.dev/icons?i=python,fastapi,react,postgres,js,html,css,tailwind,git,github,vite,nodejs,java,cpp,vscode)](https://skillicons.dev)

---

## Featured Project

### [RenewGrid — FastAPI, React, PostgreSQL, AI Estimation](https://github.com/Sameena70/RenewGrid)

RenewGrid is a full-stack e-waste recycling platform I built from scratch as my final-year Computer Science project. The system connects e-waste producers, pickup collectors, and recycling facilities. I designed a 14-table PostgreSQL schema, built the backend with a six-module repository layer and a service layer that keeps all business logic out of the routers, and built a React 19 SPA with protected routing for four separate roles.

### What I implemented

- **AI pricing engine:** On each waste submission, the service queries active `PricingRule` rows from the database for the item's category. It applies a base price, a per-kg rate, and a condition multiplier (1.0 for working, 0.6 for partial, 0.3 for broken). When no admin rule exists for a category, it falls back to hardcoded rates across seven waste categories. CO2 and credit point estimates are calculated at the same time

- **13-state pickup lifecycle:** The `PickupStatus` enum defines 13 values. The production flow runs from PENDING through ASSIGNED, ACCEPTED, IN_PROGRESS, PROOF_UPLOADED, COLLECTED, DELIVERED, PROCESSING, to COMPLETED or RECYCLED. Every transition is validated against the current state and written to a `pickup_status_history` table with the actor user ID, timestamp, and an optional note

- **JWT authentication:** Access tokens and refresh tokens are signed with two separate secrets using python-jose. Password hashing calls bcrypt directly because passlib 1.7.4 is incompatible with bcrypt 4.x. The login endpoint is rate-limited to 5 requests per minute via slowapi

- **RBAC with 4 roles:** The `UserRole` enum defines user, collector, recycler, and admin. FastAPI dependency functions enforce the role at the API layer. On the frontend, `ProtectedRoute` components check the stored role before rendering any dashboard

- **QR code verification:** The server generates a QR code for each pickup. The user shows it on screen and the collector scans it with their device camera via html5-qrcode. The scan must succeed before the collector can advance the pickup status

- **Reward and CO2 engine:** When a pickup reaches COMPLETED, a FastAPI BackgroundTask runs `create_reward_for_pickup`. It awards 10 points per kg collected and records CO2 saved at 0.5 kg per kg. It opens its own database session, checks for an existing reward first to avoid duplicates, and creates an in-app notification for the producer on success

- **Collector proof upload:** The collector uploads a photo as proof of collection. The file is validated by MIME type (JPEG, PNG, WebP, GIF) and capped at 5 MB. It is stored under `uploads/proofs/` with a UUID-prefixed filename and linked to the pickup through a dedicated `CollectorProof` model

- **Transactional email:** Password reset HTML emails are dispatched via Python smtplib as a FastAPI BackgroundTask. The setup uses STARTTLS on port 587 and is compatible with Gmail App Passwords. Reset tokens expire after 30 minutes. All credentials are read from environment variables

- **Admin analytics:** The admin dashboard aggregates users, waste volume, pickups by status, CO2 saved, revenue, and geographic area. It includes trend forecasting, pricing rule management, manual reward point assignment, and PDF report export
