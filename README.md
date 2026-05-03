# School ERP System

Integrated ERP platform for managing a Tunisian public school across web, backend, and mobile preview.

## Project Lead

**Mouhamed Sajid Hayouni**

---

## Current Status

The School ERP platform is in a strong working state.

Validated areas include:

- Web admin dashboard
- Teacher workspace
- Student portal
- Parent portal
- Notifications
- Messages
- Reports
- PDF exports
- Excel exports
- School settings
- Backend health check
- Frontend production build

Current phase: **Phase 8 - Stabilization, reporting, settings, and production readiness**

---

## Stack

### Backend

- Node.js
- Express.js
- TypeScript
- Prisma Client
- PostgreSQL / Neon
- JWT authentication
- bcryptjs
- Prisma PostgreSQL adapter

### Web Frontend

- React
- Vite
- TypeScript
- Tailwind CSS
- lucide-react
- xlsx
- Browser print-based PDF export

### Mobile

- React Native
- Expo
- Expo Router
- AsyncStorage
- EAS Build

### Hosting Targets

- Backend: Render
- Web: Vercel
- Database: Neon
- Mobile builds: Expo EAS

---

## Repository Structure

- `school-erp-backend/` - Backend Express API
- `school-erp-web/` - Web frontend
- `school-erp-mobile/` - Mobile preview app
- `docs/` - Documentation
- `TESTING_CHECKLIST.md` - Manual validation checklist
- `README.md` - Project overview

---

## Roles

The system supports four roles:

- ADMIN
- TEACHER
- STUDENT
- PARENT

---

## Role Capabilities

### Admin

Admin has full access to:

- Overview
- Users
- Classes
- Subjects
- Schedules
- Attendance
- Grades
- Assignments
- Announcements
- Messages
- Reports
- School settings

### Teacher

Teacher has scoped access to:

- Teacher overview
- Own schedule
- Attendance for own schedules
- Grades for own classes and subjects
- Own assignments
- Teacher/class announcements
- Messages

Teacher cannot access admin-only tabs such as users, classes, subjects, reports, or settings.

### Student

Student can access:

- My Portal
- Weekly timetable
- Grades
- Attendance / absences
- Assignments
- Announcements
- Notifications
- Messages
- Bulletin export

### Parent

Parent can access:

- My Portal
- Linked child information
- Child timetable
- Child grades
- Child attendance / absences
- Child assignments
- Announcements
- Notifications
- Messages
- Bulletin export

---

## Main Features

### Authentication

- Admin login
- Teacher login
- Student login
- Parent login
- JWT-protected API routes
- Logout

### Users

- Create users
- Edit users
- Delete users
- Assign roles
- Create student profiles
- Create teacher profiles
- Create parent profiles
- Link parent to student

### Classes

- Create classes
- View class students
- Delete classes
- Link students to classes

### Subjects

- Create subjects
- Set subject coefficient
- Delete subjects

### Schedules

- Create schedule entries
- Edit schedule entries
- Delete schedule entries
- Link class, subject, and teacher
- Teacher schedule view is scoped to own schedules

### Attendance

- Mark attendance by schedule and date
- Track present, absent, and late statuses
- Teacher can mark attendance only for own schedules
- Admin can access attendance reports

### Grades

- Add and update grades
- Support trimester periods: TRIMESTER_1, TRIMESTER_2, TRIMESTER_3
- Teacher grade access is scoped
- Student and parent receive grade notifications
- Student summaries and bulletins are generated

### Assignments

- Admin can create, edit, and delete assignments
- Teacher can manage own assignments
- Student assignments are visible in portal
- Parent assignments are visible in portal
- Student can mark assignment as done
- Parent can mark assignment as done
- Assignment notifications are created automatically

### Announcements

Admin can create announcements for:

- All users
- Students
- Parents
- Teachers
- Specific class

Teacher can create announcements for:

- Teachers
- Specific class

Teacher cannot create announcements for:

- All users
- Students globally
- Parents globally

Announcement notifications are created automatically.

### Notifications

The notification system supports:

- Notification bell
- Unread badge
- Mark as read
- Quiet polling
- Assignment notifications
- Announcement notifications
- Grade notifications
- Bulletin notifications
- Message notifications

Supported notification types:

- ASSIGNMENT
- ANNOUNCEMENT
- GRADE
- BULLETIN
- MESSAGE

Message notifications can open the exact related conversation.

### Messages

Private internal messaging system.

Supported behavior:

- Admin can message users
- Teacher can message allowed users
- Student can message allowed users
- Parent can message allowed users
- Conversation list
- Conversation detail view
- Replies
- Unread counts
- Message notifications
- Message notification opens exact conversation

Security behavior:

- A user cannot open a conversation where they are not a participant.
- Unauthorized conversation access returns 404 Conversation not found.

### Student / Parent Portal

The portal includes:

- Student information
- Class information
- Timetable
- Grades
- Attendance
- Assignments
- Announcements
- Notifications
- Bulletin export

### Reports

Reports module supports:

- Attendance report
- Grades report
- Student full report

Exports:

- Attendance PDF
- Attendance Excel
- Grades PDF
- Grades Excel
- Student PDF
- Student Excel

Reports use defaults from School Settings:

- Default trimester
- Default report start date
- Default report end date

### School Settings

Admin can configure:

- School name
- School subtitle
- Academic year
- Default trimester
- Default report start date
- Default report end date

Settings are used by:

- Sidebar school identity
- Reports default trimester
- Reports default date range

---

## Backend API

Backend local URL:

- `http://localhost:5000`

Health endpoint:

- `GET /api/health`

Expected health response:

- status: ok
- api: running
- database: connected
- timestamp: ISO date string

---

## Important Backend Routes

### Auth

- `POST /api/login`
- `POST /api/register`

### Users

- `GET /api/users`
- `PUT /api/users/:id`
- `DELETE /api/users/:id`

### Classes

- `GET /api/classes`
- `POST /api/classes`
- `GET /api/classes/:id`
- `DELETE /api/classes/:id`

### Subjects

- `GET /api/subjects`
- `POST /api/subjects`
- `DELETE /api/subjects/:id`

### Schedules

- `GET /api/schedules`
- `POST /api/schedules`
- `PUT /api/schedules/:id`
- `DELETE /api/schedules/:id`

### Attendance

- `GET /api/attendance/:scheduleId`
- `POST /api/attendance`

### Grades / Bulletin

- `GET /api/grades/:classId/:subjectId?period=...`
- `POST /api/grades`
- `GET /api/student-summary/:studentId`
- `GET /api/student-bulletin/:studentId`
- `POST /api/notify-bulletin/:studentId`

### Assignments

- `GET /api/assignments`
- `POST /api/assignments`
- `PUT /api/assignments/:id`
- `DELETE /api/assignments/:id`
- `GET /api/my-assignments`
- `PUT /api/assignment-submissions/:id`

### Announcements

- `GET /api/announcements`
- `POST /api/announcements`
- `PUT /api/announcements/:id`
- `DELETE /api/announcements/:id`
- `GET /api/my-announcements`

### Notifications

- `GET /api/my-notifications`
- `PUT /api/notifications/:id/read`

### Messages

- `GET /api/messages/recipients`
- `GET /api/messages/conversations`
- `GET /api/messages/conversations/:id`
- `POST /api/messages/conversations`
- `POST /api/messages/conversations/:id/messages`
- `PUT /api/messages/conversations/:id/read`

### Reports

- `GET /api/reports/attendance`
- `GET /api/reports/grades`

### School Settings

- `GET /api/settings/school`
- `PUT /api/settings/school`

### Health

- `GET /api/health`

---

## Environment Variables

### Backend

Create this file:

- `school-erp-backend/.env`

Required variables:

- `DATABASE_URL="your_postgresql_connection_string"`
- `JWT_SECRET="your_jwt_secret"`
- `PORT=5000`

### Web Frontend

Create this file:

- `school-erp-web/.env`

Required variable:

- `VITE_API_BASE_URL="http://localhost:5000"`

---

## Backend Setup

Go to backend folder:

- `cd school-erp-backend`

Install dependencies:

- `npm install`

Generate Prisma client:

- `npx prisma generate`

Push schema to database:

- `npx prisma db push`

Start backend:

- `npm run dev`

Expected result:

- `Server is running on http://localhost:5000`

---

## Frontend Setup

Go to frontend folder:

- `cd school-erp-web`

Install dependencies:

- `npm install`

Start frontend:

- `npm run dev`

Frontend runs on:

- `http://localhost:5173`

---

## Frontend Production Build

Run from the frontend folder:

- `cd school-erp-web`
- `npm run build`

Validated successful result:

- `1750 modules transformed`
- `built successfully`

Current note:

- Large chunk warning is not blocking.
- Code splitting can be improved later.

---

## Backend Run Validation

Run from the backend folder:

- `cd school-erp-backend`
- `npm run dev`

Validated successful result:

- Nodemon starts correctly.
- ts-node starts `src/index.ts`.
- Server runs on `http://localhost:5000`.

Health check validated:

- `/api/health` returns API running and database connected.

---

## Known Notes

### PostgreSQL SSL Warning

The backend may show a PostgreSQL SSL warning about SSL modes.

This warning is currently non-blocking.

### Frontend Bundle Warning

Vite may show a warning that some chunks are larger than 500 kB after minification.

This warning is currently non-blocking.

Future improvement:

- Add route-based code splitting.
- Use dynamic imports for large modules.
- Split reports/messages into lazy-loaded pages.

---

## Testing

Manual testing is documented in:

- `TESTING_CHECKLIST.md`

Validated areas:

- Auth
- Role navigation
- Notifications
- Messages
- Message permissions
- Assignments
- Announcements
- Attendance
- Grades
- Bulletins
- Reports
- PDF exports
- Excel exports
- School settings
- Backend health
- Frontend build

---

## Recommended Next Improvements

Do not add a large new module immediately.

Recommended next steps:

1. Clean formatting in edited files.
2. Add small loading and empty states where missing.
3. Add deployment notes.
4. Add screenshots to this README.
5. Add frontend code splitting later.
6. Add automated tests later.

---

## Current Project Status

School ERP is stable and feature-complete for the current scope.

Current validation status:

- Frontend build passes.
- Backend runs.
- Database health check passes.
- Core modules are validated.