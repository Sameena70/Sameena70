# Sameena Kausar

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

Most recently, I built RenewGrid as my MCA final project: a full-stack e-waste recycling and rewards platform with a 13-state pickup lifecycle, an AI price estimator that reads admin-configured pricing rules from the database, QR-based collector verification, JWT dual-token authentication, and a background reward engine that calculates CO2 savings automatically on pickup completion.

---

## Technical Focus

- **Languages:** Python, JavaScript, SQL
- **Backend:** FastAPI, REST APIs, SQLAlchemy, Alembic, JWT, bcrypt
- **Frontend:** React 19, TailwindCSS, Vite, React Router, HTML, CSS
- **Databases:** PostgreSQL, MySQL
- **Architecture & Patterns:** Repository Pattern, Service Layer, Role-Based Access Control (RBAC), State Machines
- **Tools:** Git, GitHub, Node.js, VS Code

---

## Featured Project

### [RenewGrid - FastAPI · React · PostgreSQL · AI Estimation](https://github.com/Sameena70/RenewGrid)

RenewGrid is an e-waste lifecycle management platform covering the full pickup journey, with role-based access control, a complete audit trail on every status transition, and automated reward and CO2 tracking on completion.

I designed a **14-table PostgreSQL schema**, built the FastAPI backend with a **six-module repository layer** and a service layer that keeps all business logic out of the routers, and built the React 19 SPA with **four separate role dashboards** and protected routing enforced at both the API and frontend layers.

### What I implemented

- **AI pricing engine:** On each waste submission, the service queries active `PricingRule` rows from the database for the item category, applies base price + per-kg rate multiplied by a condition factor (1.0 working, 0.6 partial, 0.3 broken), and falls back to hardcoded rates across **seven waste categories** when no admin rule exists. CO2 and credit point estimates run at the same time

- **13-state pickup lifecycle:** The lifecycle runs from PENDING through ASSIGNED, ACCEPTED, IN_PROGRESS, PROOF_UPLOADED, COLLECTED, DELIVERED, PROCESSING, to COMPLETED or RECYCLED. Every transition is validated against the current state and written to a `pickup_status_history` table with actor ID, timestamp, and note. CANCELLED and REJECTED are terminal states

- **JWT authentication:** Access and refresh tokens are signed with **two separate secrets** via python-jose. Passwords are hashed with bcrypt directly (passlib 1.7.4 is incompatible with bcrypt 4.x). The login endpoint is rate-limited to **5 requests per minute** via slowapi

- **RBAC with 4 roles:** User, Collector, Recycler, and Admin are enforced at the API through FastAPI dependency injection and at the frontend through `ProtectedRoute` components. Each role has its own dashboard with no route overlap

- **QR code verification:** The server generates a QR code per pickup. The user shows it on screen. The collector scans it via html5-qrcode before the status can advance to the next stage

- **Reward and CO2 engine:** A BackgroundTask is triggered on pickup completion. It awards **10 points per kg** and records CO2 at **0.5 kg per kg**. An idempotency guard checks for an existing reward before creating a new one. Sends an in-app notification to the producer on success

- **Transactional email:** A password reset HTML email is sent via smtplib as a BackgroundTask. STARTTLS on port 587, Gmail-compatible. The token expires in **30 minutes**. All credentials come from environment variables

- **Admin analytics:** Aggregates platform-wide data across users, waste volume, status breakdown, CO2, revenue, and geography. Includes trend forecasting, pricing rule management, manual reward assignment, and PDF export

### Explore the implementation

[Backend README](https://github.com/Sameena70/RenewGrid/blob/main/backend/README.md) ·
[AI Pricing Engine](https://github.com/Sameena70/RenewGrid/blob/main/backend/app/services/waste_service.py) ·
[Pickup Lifecycle](https://github.com/Sameena70/RenewGrid/blob/main/backend/app/models/core.py) ·
[Reward Engine](https://github.com/Sameena70/RenewGrid/blob/main/backend/app/services/reward_service.py) ·
[JWT & Security](https://github.com/Sameena70/RenewGrid/blob/main/backend/app/core/security.py) ·
[Admin Service](https://github.com/Sameena70/RenewGrid/blob/main/backend/app/services/admin_service.py)

---

## Other Projects

### [Book Reselling System - Python · MySQL · HTML · CSS](https://github.com/Sameena70/Book-Reselling-System-python-mysql)

A buy-and-sell platform for second-hand books. Python backend, MySQL for the data layer, HTML/CSS frontend.

### [Smart Garbage Management System - Python · MySQL · HTML · CSS](https://github.com/Sameena70/Smart-Garbage-Management-system-python-mysql-)

Tracks garbage collection schedules and waste volume by location. Python backend, MySQL storage, HTML/CSS reporting interface.

---

## Experience

### Web Development Intern, InternPe Online

- Built full-stack web applications using HTML, CSS, and Express.js
- Worked across frontend and backend, handling both UI and server-side logic

---

## Education

**Master of Computer Application (MCA)**  
Dr. B. V. Hiray College of Management and Research Center  
`2024 – 2026` · 7.91 CGPA

**Bachelor of Science in Computer Science**  
J.A.T. Arts Science and Commerce College of Women  
`2021 – 2024` · 8.24 CGPA

---

## Certifications

- **Python Programming**, GUVI
- **AI for India 2.0**, GUVI
- **Backend Web Development**, DevTown
- **Web Development Internship**, InternPe
- **Python Specialization (3 months)**, Sony Entertainment Television
- **Power BI With AI**, SkillEcted
- **Advanced Excel With AI**, SkillEcted

---

<p align="center">
  <a href="https://www.linkedin.com/in/sameena70">LinkedIn</a>
  ·
  <a href="mailto:sameenakausar070@gmail.com">Email</a>
  ·
  <a href="https://github.com/Sameena70/RenewGrid">RenewGrid</a>
</p>
