# 🏠 HostelHub — Hostel Room Allocation & Complaint System

> **Software Project Management (SPM) — Project Submission**  
> Topic: Hostel Room Allocation & Maintenance Complaint Tracking System

---

## 📌 Project Overview

**HostelHub** is a web-based Hostel Management System designed to automate the room allocation process and streamline maintenance complaint tracking for student hostels. It replaces manual registers and spreadsheets with a centralized, role-based digital platform.

### 🎯 Problem Statement
Managing hostel rooms manually leads to:
- Allocation conflicts and double-booking
- Slow resolution of maintenance complaints
- Poor communication between students and wardens
- No audit trail or transparency

### ✅ Solution
A full-stack web system with:
- **Automated Room Allocation** based on student preferences
- **Complaint Filing & Tracking** with priority management
- **Role-based Dashboards** for Students, Wardens, Maintenance Staff, and Admins

---

## 👥 System Roles

| Role | Capabilities |
|------|-------------|
| 🎓 Student | Apply for room, view allocation, file & track complaints |
| 🏛️ Warden | Approve allocations, manage complaints, post notices |
| 🔩 Maintenance Staff | View assigned complaints, update resolution status |
| 🖥️ Administrator | Full system access, analytics, user management |

---

## 🗂️ Repository Structure

```
hostel-room-allocation-complaint-system/
│
├── index.html              # Main UI (Home, Rooms, Complaints, Dashboard)
├── style.css               # Stylesheet (Dark luxury theme)
├── README.md               # Project documentation (this file)
│
├── diagrams/
│   ├── use_case_diagram.png        # UML Use Case Diagram
│   ├── er_diagram.png              # Entity-Relationship Diagram
│   ├── dfd_level0.png              # Data Flow Diagram (Level 0)
│   ├── dfd_level1.png              # Data Flow Diagram (Level 1)
│   ├── class_diagram.png           # Class Diagram
│   ├── sequence_diagram.png        # Sequence Diagram (Room Allocation)
│   └── activity_diagram.png        # Activity Diagram (Complaint Flow)
│
└── report/
    └── SPM_Project_Report.pdf      # Full project report
```

---

## ⚙️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | HTML5, CSS3, JavaScript (Vanilla) |
| Backend | PHP 8.x |
| Database | MySQL |
| Server | Apache (XAMPP) |
| Version Control | Git & GitHub |

---

## 🗃️ Key Modules

### 1. Room Allocation Module
- Students fill a preference form (block, room type, roommate preference)
- System checks availability and allocates a room automatically
- Admin can override or manually reassign
- Generates an allocation confirmation
- Waitlist management for fully-occupied blocks

### 2. Complaint Management Module
- Students raise complaints with category, priority, and description
- Warden receives notification and assigns to maintenance staff
- Staff updates status: `Pending → Assigned → In Progress → Resolved`
- Students can view real-time complaint status
- Complaints older than 3 days are auto-escalated

### 3. Admin Dashboard
- Occupancy analytics (total, occupied, available, maintenance)
- Complaint resolution rate and category breakdown
- Activity log of all system events
- User management (CRUD for students, wardens, staff)

---

## 🗄️ Database Schema (Simplified)

```sql
-- Students
CREATE TABLE students (
  student_id VARCHAR(20) PRIMARY KEY,
  name VARCHAR(100),
  email VARCHAR(100),
  year INT,
  branch VARCHAR(50),
  phone VARCHAR(15)
);

-- Rooms
CREATE TABLE rooms (
  room_no VARCHAR(10) PRIMARY KEY,
  block CHAR(1),
  floor INT,
  type ENUM('single','double','triple'),
  status ENUM('available','occupied','maintenance')
);

-- Allocations
CREATE TABLE allocations (
  alloc_id INT AUTO_INCREMENT PRIMARY KEY,
  student_id VARCHAR(20),
  room_no VARCHAR(10),
  alloc_date DATE,
  semester VARCHAR(20),
  FOREIGN KEY (student_id) REFERENCES students(student_id),
  FOREIGN KEY (room_no) REFERENCES rooms(room_no)
);

-- Complaints
CREATE TABLE complaints (
  complaint_id INT AUTO_INCREMENT PRIMARY KEY,
  student_id VARCHAR(20),
  room_no VARCHAR(10),
  category VARCHAR(50),
  description TEXT,
  priority ENUM('low','medium','high'),
  status ENUM('pending','assigned','in_progress','resolved'),
  filed_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  resolved_at TIMESTAMP,
  FOREIGN KEY (student_id) REFERENCES students(student_id)
);
```

---

## 📊 SPM Artefacts

### Diagrams Included
- **Use Case Diagram** — All actor-system interactions
- **ER Diagram** — Database entity relationships
- **DFD Level 0 & 1** — Data flow across the system
- **Class Diagram** — OOP structure of the system
- **Sequence Diagram** — Room allocation flow
- **Activity Diagram** — Complaint lifecycle

### Project Management Aspects
- **SDLC Model Used:** Agile (Scrum with 2-week sprints)
- **Tools:** GitHub (version control), Trello (task management)
- **Risk Management:** Identified 5 key risks with mitigation strategies
- **Estimation:** Function Point Analysis used for effort estimation

---

## 🚀 How to Run Locally

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/hostelhub.git
   ```
2. Open `index.html` in your browser for the static UI demo.
3. For full functionality, set up XAMPP and import the database schema.

---

## 📋 GitHub Files Checklist

| File | Status | Description |
|------|--------|-------------|
| `index.html` | ✅ | Main UI with all modules |
| `style.css` | ✅ | Stylesheet |
| `README.md` | ✅ | This documentation |
| `diagrams/use_case_diagram.png` | 📌 Add | UML Use Case |
| `diagrams/er_diagram.png` | 📌 Add | ER Diagram |
| `diagrams/dfd_level0.png` | 📌 Add | Level 0 DFD |
| `diagrams/dfd_level1.png` | 📌 Add | Level 1 DFD |
| `diagrams/class_diagram.png` | 📌 Add | Class Diagram |
| `diagrams/sequence_diagram.png` | 📌 Add | Sequence Diagram |
| `diagrams/activity_diagram.png` | 📌 Add | Activity Diagram |
| `report/SPM_Project_Report.pdf` | 📌 Add | Full Report |

---

## 👨‍💻 Team Members

| Name | Role |
|------|------|
| [Your Name] | Full Stack + Documentation |
| [Team Member 2] | Backend + Database |
| [Team Member 3] | Diagrams + Report |

---

## 📄 License
This project is submitted for academic purposes as part of the **Software Project Management** course.

---

*Made with ❤️ for SPM Project Submission — 2025*
