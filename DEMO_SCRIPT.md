# School ERP - Demo Script

## 1. Introduction

Hello, today I will present my School ERP project.

This application is a full-stack school management platform built with:

- React
- TypeScript
- Vite
- Tailwind CSS
- Node.js
- Express.js
- Prisma
- PostgreSQL / Neon
- JWT authentication

The system supports three direct-login roles:

- Admin
- Teacher
- Parent

Students are managed as school records. They do not log in directly; parents use the portal to follow their linked children.

---

## 2. Login and Role-Based Access

First, I log in as an admin.

The system uses JWT authentication, and every protected request requires a valid token.

If the token is invalid or expired, the system rejects the request and asks the user to log in again.

The sidebar changes depending on the user role.

For example:

- Admin can access Users, Classes, Subjects, Schedules, Reports, Settings, and Audit Logs.
- Teacher can manage attendance, grades, assignments, and announcements for assigned classes.
- Parent has limited portal access for linked children only.

---

## 3. Admin Dashboard Overview

After login, the admin sees the Overview dashboard.

The dashboard shows:

- Academic year
- Current trimester
- Platform users
- Latest audit action
- Recent users
- Statistics
- Latest announcements
- Upcoming assignments
- Quick actions

This gives the admin a quick view of the school system status.

---

## 4. Users Management

In the Users module, the admin can:

- View users and linked school profiles in read-only mode
- Verify roles and linked records
- Confirm that students remain school records without direct login duties

User creation, update, deletion, password change, and profile-image upload are disabled in the current validated scope.
Forgotten-password handling is available as a controlled request from the login page. The system shows a generic message and guides the parent or teacher to contact school administration; it does not directly reset the password or expose whether the email exists.

---

## 5. Classes and Subjects

In the Classes module, the admin can create and delete classes.

In the Subjects module, the admin can create and delete subjects.

Subjects have coefficients, which are used later in grade calculations and reports.

The system prevents invalid coefficients and duplicate subjects.

All class and subject actions are tracked in Audit Logs.

---

## 6. Schedules

In the Schedules module, the admin can assign:

- A class
- A subject
- A teacher
- A day
- A start time
- An end time

The system validates time format and prevents schedule conflicts.

This prevents a class or teacher from having overlapping sessions.

Schedule creation, update, and deletion are saved in Audit Logs.

---

## 7. Attendance

In the Attendance module, teachers can mark students as:

- Present
- Absent
- Late

Teachers can only manage attendance for their assigned schedules.

Attendance records are saved and can be updated.

Attendance actions are also saved in Audit Logs.

---

## 8. Grades

In the Grades module, admin or teacher can enter student grades.

The page includes:

- Class selection
- Subject selection
- Period selection
- Exam type selection
- Score input
- Comments

The score must be between 0 and 20.

When a grade is saved, the system creates scoped notifications for the parent account.

Grade creation and update are saved in Audit Logs.

---

## 9. Assignments

In the Assignments module, admin or teacher can create assignments.

An assignment includes:

- Class
- Subject
- Teacher
- Title
- Description
- Due date

When an assignment is created, submissions are automatically created for students in the class.

Parents can view linked child assignments from the parent portal.

Assignment actions are saved in Audit Logs.

---

## 10. Announcements

In the Announcements module, admin or teacher can create announcements.

Announcements can target:

- Allowed system users
- Parent accounts
- Teachers
- A specific class

Announcements create notifications for the target users.

Create, update, and delete actions are saved in Audit Logs.

Deleted announcement details are saved before deletion.

---

## 11. Messages

The Messages module allows users to communicate based on permissions.

For example:

- Admin can message allowed direct-login users
- Parents and teachers can reply to allowed conversations
- Unauthorized users cannot access conversations they do not belong to

The backend returns 404 if a user tries to access a conversation where they are not a participant.

This protects private conversations.

---

## 12. Notifications

The notification system supports:

- Assignment notifications
- Announcement notifications
- Grade notifications
- Bulletin notifications
- Message notifications

Unread notification count is shown in the sidebar.

When a message notification is opened, it navigates directly to the correct conversation and marks it as read.

---

## 13. Reports

The Reports module includes:

- Attendance reports
- Grades reports
- Student reports

Reports can be exported as:

- PDF
- Excel

This helps administrators prepare official school documents.

---

## 14. Settings

In the Settings module, the admin can configure:

- School name
- School subtitle
- Academic year
- Default trimester
- Default report dates

After saving settings, the sidebar updates immediately without refreshing the page.

Settings updates are also saved in Audit Logs.

---

## 15. Audit Logs

The Audit Logs module is one of the most important admin features.

It tracks important actions such as:

- User creation, update, and deletion
- Class creation and deletion
- Subject creation and deletion
- Schedule creation, update, and deletion
- Attendance creation and update
- Grade creation and update
- Assignment creation, update, and deletion
- Announcement creation, update, and deletion
- School settings update

Each audit log contains:

- Date
- Actor
- Role
- Action
- Entity
- Entity ID
- Details

The admin can filter audit logs by:

- Action
- Entity
- Role

The admin can also click details to open a full popup and export logs to Excel.

---

## 16. Security

The project includes several security controls:

- JWT authentication
- Role-based access control
- Protected backend routes
- Password hashing with bcrypt
- Admin-only audit logs
- Admin-only settings
- Teacher scope restrictions
- Conversation participant protection
- Environment variables protected by `.gitignore`

Sensitive data like database URLs and JWT secrets are not committed to GitHub.

---

## 17. Build and Validation

The backend starts successfully on:

```txt
http://localhost:5000
```

The frontend starts successfully on:

```txt
http://localhost:5173
```

The production frontend build also succeeds:

```txt
✓ built
```

This confirms that the project is ready for final submission and demonstration.

---

## 18. Conclusion

This School ERP project provides a complete platform for managing school operations.

It includes:

- Users
- Classes
- Subjects
- Schedules
- Attendance
- Grades
- Assignments
- Announcements
- Messages
- Notifications
- Reports
- Settings
- Audit Logs

The system is role-based, secure, and ready for demonstration.

Thank you.
