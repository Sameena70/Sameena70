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

MCA graduate (2026) and BSc Computer Science (2024). I built RenewGrid from scratch as my master's final project: a full-stack e-waste recycling and rewards platform connecting producers, collectors, and recycling facilities through a single system. I also interned at InternPe Online as a Web Development Intern, building full-stack web applications with HTML, CSS, and Express.js.

---

## Education

- **Master of Computer Application** — Dr. B. V. Hiray College of Management and Research Center (2024–2026)
- **BSc Computer Science** — J.A.T. Arts Science and Commerce College of Women (2021–2024) · 8.24 CGPA
- **Higher Secondary Certificate** — J.A.T. High School and Junior College, Malegaon (2021) · 85%

---

## Technical Focus

- **Languages:** Python, JavaScript, Java, C, C++
- **Backend:** FastAPI, REST APIs, JWT (python-jose), bcrypt, SQLAlchemy, Alembic, slowapi, smtplib
- **Frontend:** React 19, React Router v7, Vite, TailwindCSS, Leaflet, html5-qrcode, jsPDF, HTML, CSS
- **Databases:** PostgreSQL, MySQL, SQL
- **Patterns:** Repository pattern, service layer, RBAC, state machines, background tasks
- **Tools:** Git, GitHub, VS Code, Node.js, Power BI, Excel

---

## Featured Project

### [RenewGrid — FastAPI · React · PostgreSQL · AI Estimation](https://github.com/Sameena70/RenewGrid)

RenewGrid is a full-stack e-waste recycling and rewards platform I built from scratch as my MCA final project.

I designed a 14-table PostgreSQL schema, built the FastAPI backend with a six-module repository layer and a service layer that keeps all business logic out of the routers, and built the React 19 SPA with four separate role dashboards and protected routing enforced at both the API and frontend layers.

### What I implemented

- **AI pricing engine:** Reads active `PricingRule` rows from the database per waste category. Applies base price + per-kg rate multiplied by a condition factor (1.0 working, 0.6 partial, 0.3 broken). Falls back to hardcoded rates across seven categories when no admin rule exists. CO2 and credit point estimates run at the same time
- **13-state pickup lifecycle:** Runs from PENDING through ASSIGNED, ACCEPTED, IN_PROGRESS, PROOF_UPLOADED, COLLECTED, DELIVERED, PROCESSING, to COMPLETED or RECYCLED. Every transition is validated and written to a `pickup_status_history` table with actor ID, timestamp, and note. CANCELLED and REJECTED are terminal states
- **JWT authentication:** Access and refresh tokens signed with separate secrets via python-jose. Calls bcrypt directly for password hashing. Login rate-limited to 5 requests per minute via slowapi
- **RBAC with 4 roles:** User, Collector, Recycler, and Admin enforced at the API through FastAPI dependency injection and at the frontend through `ProtectedRoute` components
- **QR code verification:** Server generates a QR code per pickup. User shows it on screen. Collector scans it via html5-qrcode before the status can advance
- **Reward and CO2 engine:** BackgroundTask triggered on completion. Awards 10 points per kg, CO2 at 0.5 kg per kg. Idempotent guard prevents duplicates. Sends in-app notification to the producer on success
- **Transactional email:** Password reset email sent via smtplib as a BackgroundTask. STARTTLS on port 587, Gmail-compatible. Token expires in 30 minutes
- **Admin analytics:** Platform-wide aggregates for users, waste volume, status breakdown, CO2, revenue, and geography. Includes trend forecasting, pricing rule management, reward assignment, and PDF export

---

## Other Projects

**[Book Reselling System](https://github.com/Sameena70/Book-Reselling-System-python-mysql)** — Python, MySQL, HTML, CSS  
Buy and sell second-hand books. Python backend, MySQL for the data layer, HTML/CSS frontend.

**[Smart Garbage Management System](https://github.com/Sameena70/Smart-Garbage-Management-system-python-mysql-)** — Python, MySQL, HTML, CSS  
Tracks garbage collection schedules and waste data across locations. Python backend, MySQL storage, HTML/CSS reporting views.

---

## Certifications

- Python Programming — GUVI
- AI for India 2.0 — GUVI
- Backend Web Development — DevTown
- Web Development Internship — InternPe
- Python Specialization (3 months) — Sony Entertainment Television
- Power BI With AI — SkillEcted
- Advanced Excel With AI — SkillEcted
