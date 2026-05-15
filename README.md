# 🎓 AttendX — Student Attendance Management System

A complete Java Swing desktop application for managing student attendance,
built for NetBeans IDE with MySQL (XAMPP) backend.

---

## 📁 Project Structure

```
StudentAttendance/
├── build.xml                          ← NetBeans Ant build file
├── manifest.mf
├── database/
│   └── attendance_db.sql             ← Run this first in phpMyAdmin!
├── lib/
│   └── mysql-connector-j-8.0.33.jar  ← Place MySQL JDBC driver here
├── nbproject/
│   ├── project.xml
│   └── project.properties
└── src/
    └── studentattendance/
        ├── StudentAttendance.java     ← Main entry point
        ├── controller/
        │   ├── AuthController.java
        │   ├── AttendanceController.java
        │   ├── StudentController.java
        │   ├── LecturerController.java
        │   └── AdminController.java
        ├── db/
        │   └── DatabaseConnection.java
        ├── model/
        │   ├── User.java
        │   ├── Student.java
        │   ├── Lecturer.java
        │   ├── Course.java
        │   ├── Schedule.java
        │   ├── AttendanceSession.java
        │   ├── AttendanceRecord.java
        │   └── LeaveRequest.java
        ├── util/
        │   ├── UITheme.java
        │   └── PasswordUtil.java
        └── view/
            ├── LoginFrame.java
            ├── StudentDashboard.java
            ├── LecturerDashboard.java
            └── AdminDashboard.java
```

---

## ⚙️ Setup Instructions

### Step 1 — Install Prerequisites
- [NetBeans IDE 17+](https://netbeans.apache.org/)
- [XAMPP](https://www.apachefriends.org/) (for MySQL)
- JDK 11 or newer

---

### Step 2 — Get MySQL JDBC Driver

Download **mysql-connector-j-8.0.33.jar** from:
https://dev.mysql.com/downloads/connector/j/

Select: Platform Independent → ZIP → Extract the JAR file

**Place the JAR in:**
```
StudentAttendance/lib/mysql-connector-j-8.0.33.jar
```

---

### Step 3 — Setup the Database

1. Start **XAMPP** → Start **Apache** and **MySQL**
2. Open **phpMyAdmin** → http://localhost/phpmyadmin
3. Click **Import** tab
4. Choose file: `database/attendance_db.sql`
5. Click **Go**

The database `attendance_db` will be created with all tables and sample data.

---

### Step 4 — Open in NetBeans

1. Open **NetBeans IDE**
2. Go to **File → Open Project**
3. Navigate to `StudentAttendance/` folder and open it
4. NetBeans will detect it as an Ant project automatically

---

### Step 5 — Add MySQL Driver to Project

1. In NetBeans, right-click **Libraries** under the project
2. Click **Add JAR/Folder**
3. Browse to `lib/mysql-connector-j-8.0.33.jar`
4. Click **Open** → **OK**

---

### Step 6 — Run the Project

Press **F6** (Run Project) or click the green ▶ button.

---

## 🔑 Default Login Credentials

| Role     | Username | Password    |
|----------|----------|-------------|
| Admin    | admin    | password123 |
| Student  | S001     | password123 |
|     -    | UNTIL    | password123 |
|     -    | S007     | password123 |
| Lecturer | L001     | password123 |
| Lecturer | L002     | password123 |

---

## 🖥️ Features

### 👤 Student
- View class schedule
- Mark attendance using 6-character code (given by lecturer)
- View attendance history with color-coded status
- View attendance percentage per course
- Submit online leave / sick requests

### 👨‍🏫 Lecturer
- View teaching schedule
- Open attendance session (generates unique 6-char code)
- Close attendance session
- View attendance recap per course (present/late/absent/excused)
- Approve or reject student leave requests

### 🛡️ Admin
- Dashboard with system statistics
- Manage students (Add, Edit, Delete)
- View lecturers
- Manage courses (Add, Delete)
- View all class schedules

---

## 🎨 Design Theme

| Element   | Color        | Hex Code  |
|-----------|-------------|-----------|
| Primary   | Army Green  | `#5D6532` |
| Background| Beige       | `#EDE8D0` |
| Dark Accent| Deep Green | `#454A24` |
| Light BG  | Cream       | `#F8F5E8` |

UI Features: Rounded corners, gradient sidebar, color-coded status rows,
smooth anti-aliased custom buttons, card widgets, card-layout navigation.

---

## 🏗️ Architecture

```
MVC Pattern
├── Model     → data classes (User, Student, Course, etc.)
├── View      → Swing frames (Login, Student/Lecturer/AdminDashboard)
└── Controller→ business logic + JDBC queries
```

---

## 🗄️ Database Tables

| Table                | Description                        |
|---------------------|------------------------------------|
| users               | Login credentials (all roles)      |
| students            | Student profiles                   |
| lecturers           | Lecturer profiles                  |
| courses             | Course/subject catalog             |
| class_schedules     | Weekly schedule entries            |
| student_courses     | Course enrollment                  |
| attendance_sessions | Sessions opened by lecturers       |
| attendance_records  | Per-student attendance records     |
| leave_requests      | Student leave/sick requests        |

---

## ⚠️ Troubleshooting

**"MySQL JDBC Driver not found"**
→ Make sure `mysql-connector-j-8.0.33.jar` is in `lib/` and added to Libraries

**"Cannot connect to database"**
→ Check XAMPP is running, MySQL is on port 3306, and `attendance_db` exists

**Build errors in NetBeans**
→ Right-click project → **Clean and Build**

**"Table doesn't exist"**
→ Re-run `database/attendance_db.sql` in phpMyAdmin
