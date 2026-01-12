# FedEx-Smart-Hackathon

# End-to-End DCA Management Platform

An end-to-end **Debt Collection Agency (DCA) Management Platform** built as part of the **FedEx SMART Hackathon**.
The system enables enterprises (e.g., FedEx) to manage overdue cases, assign them to DCAs, monitor SLA compliance, and use AI-assisted prioritization—while DCAs execute collections through a controlled, auditable workflow.

---

## 🧩 Project Structure

```
root/
│
├── backend/        # Flask + PostgreSQL backend
│   ├── app/
│   ├── migrations/
│   ├── run.py
│   ├── requirements.txt
│   └── .env
│
├── frontend/       # Vue 3 + Vite frontend
│   ├── src/
│   ├── index.html
│   ├── package.json
│   └── vite.config.js
│
└── README.md
```

---

## 🚀 Features Overview

### Enterprise (FedEx-side)

* Bulk upload debt cases (CSV / Excel)
* AI-based **priority scoring** & **recovery probability**
* Assign cases to DCAs with **automatic SLA start**
* Monitor SLA status (Running / Breached / Completed)
* Approve or reject DCA escalations
* Close, dispute, or write-off cases
* Analytics dashboard (Aging & Priority charts)
* Full **audit trail** for compliance

### DCA

* View assigned cases only
* Add notes and activity logs
* Update case status
* Request escalations
* SLA auto-completion on activity

---

## 🛠️ Tech Stack

### Backend

* **Python 3.10+**
* **Flask** (Application Factory pattern)
* **Flask-SQLAlchemy**
* **Flask-Migrate (Alembic)**
* **PostgreSQL**
* Session-based authentication
* Rule-based AI scoring engine

### Frontend

* **Vue 3**
* **Vite**
* **Vue Router**
* **Axios**
* Session-based auth (cookies)

---

## ⚙️ Prerequisites

Make sure you have the following installed:

* Python **3.10 or higher**
* Node.js **18+**
* PostgreSQL **13+**
* Git

---

## 🧪 How to Run the Application (Local Setup)

### 1️⃣ Clone the Repository

```bash
git clone <your-github-repo-url>
cd <repo-root>
```

---

## 🔧 Backend Setup

### 2️⃣ Create and Activate Virtual Environment

```bash
cd backend
python -m venv venv

# Windows
venv\Scripts\activate

# macOS / Linux
source venv/bin/activate
```

---

### 3️⃣ Install Backend Dependencies

```bash
pip install -r requirements.txt
```

---

### 4️⃣ Configure Environment Variables

Create a `.env` file inside the `backend/` folder:

```env
SECRET_KEY=your-secret-key
DATABASE_URL=postgresql://username:password@localhost:5432/dca_db
```

> Ensure the PostgreSQL database (`dca_db`) already exists.

---

### 5️⃣ Run Database Migrations

```bash
flask db upgrade
```

This will create all required tables:

* users
* organizations
* debt_cases
* SLA tracking
* audit logs
* AI predictions
* assignments, escalations, closures, etc.

---

### 6️⃣ Start the Backend Server

```bash
python run.py
```

Backend will run on:

```
http://localhost:5000
```

---

## 🎨 Frontend Setup

### 7️⃣ Install Frontend Dependencies

Open a new terminal:

```bash
cd frontend
npm install
```

---

### 8️⃣ Run Frontend Development Server

```bash
npm run dev
```

Frontend will run on:

```
http://localhost:5173
```

---

## 🔐 Authentication Notes (Hackathon Mode)

* Login is **email-based only** (no passwords).
* Roles are enforced server-side:

  * `ENTERPRISE`
  * `DCA`
* Sessions are stored using Flask cookies.

> You must pre-create users and organizations in the database.

---

## 🧪 Sample Data Setup (Optional)

Recommended minimum records:

* One **Enterprise organization**
* One **DCA organization**
* One Enterprise user
* One DCA user
* One active SLA definition

This enables full end-to-end flow.

---

## 📊 AI & SLA Logic (High Level)

* AI uses deterministic, explainable rules:

  * Aging bucket
  * Escalation history
  * Amount risk
  * Historical recovery rate
* SLA starts on assignment
* SLA pauses on dispute
* SLA completes on:

  * Notes
  * Escalation requests
  * Case closure
* SLA breaches are logged with audit records

---

## 🧱 Architecture Principles

* Clear **Enterprise vs DCA isolation**
* Backend as **single source of truth**
* No business logic duplication in frontend
* Fully auditable workflows
* Production-extensible design

---

## 🏁 Status

✔ Backend complete
✔ Frontend complete
✔ End-to-end flow working
✔ Hackathon-ready & production-extensible

---

## 📄 License

This project is created for **educational and hackathon purposes**.

---

## 🙌 Acknowledgement

Built as part of **FedEx SMART Hackathon** to demonstrate:

* Enterprise-grade workflow modeling
* Compliance-first design
* AI-assisted operational decisioning
