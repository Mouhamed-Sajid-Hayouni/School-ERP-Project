# School ERP - Testing Checklist

## 1. Auth

- [x] Admin login works
- [x] Teacher login works
- [x] Student login works
- [x] Parent login works
- [x] Logout works
- [x] Invalid login is rejected
- [x] Invalid token is rejected
- [x] Protected pages redirect unauthenticated users to login

---

## 2. Dashboard Navigation

### Admin

- [x] Overview visible
- [x] Users visible
- [x] Classes visible
- [x] Subjects visible
- [x] Schedules visible
- [x] Attendance visible
- [x] Grades visible
- [x] Assignments visible
- [x] Announcements visible
- [x] Messages visible
- [x] Reports visible
- [x] Audit Logs visible
- [x] Settings visible

### Teacher

- [x] Overview visible
- [x] My Schedule visible
- [x] Attendance visible
- [x] Grades visible
- [x] Assignments visible
- [x] Announcements visible
- [x] Messages visible
- [x] Admin-only tabs hidden
- [x] Audit Logs hidden
- [x] Settings hidden

### Student / Parent

- [x] My Portal visible
- [x] Messages visible
- [x] Admin tabs hidden
- [x] Teacher tabs hidden
- [x] Audit Logs hidden
- [x] Settings hidden

---

## 3. Users Management

- [x] Admin can load users list
- [x] Admin can create a user
- [x] Admin can update a user
- [x] Admin can delete a user
- [x] Duplicate email is rejected
- [x] Required fields are validated
- [x] User role is saved correctly
- [x] User actions are saved in Audit Logs

---

## 4. Classes Management

- [x] Admin can load classes
- [x] Admin can create a class
- [x] Admin can delete a class
- [x] Class name is required
- [x] Academic year is required
- [x] Duplicate class validation works
- [x] Class actions are saved in Audit Logs

---

## 5. Subjects Management

- [x] Admin can load subjects
- [x] Admin can create a subject
- [x] Admin can delete a subject
- [x] Subject name is required
- [x] Coefficient is required
- [x] Invalid coefficient is rejected
- [x] Duplicate subject validation works
- [x] Subject actions are saved in Audit Logs

---

## 6. Schedules

- [x] Admin can load schedules
- [x] Admin can create a schedule
- [x] Admin can update a schedule
- [x] Admin can delete a schedule
- [x] Schedule requires class, subject, teacher, day, start time, and end time
- [x] Invalid time range is rejected
- [x] Class schedule conflicts are rejected
- [x] Teacher schedule conflicts are rejected
- [x] Schedule actions are saved in Audit Logs

---

## 7. Attendance

- [x] Attendance page loads correctly
- [x] Admin can save attendance
- [x] Teacher can save attendance for assigned schedules
- [x] Teacher cannot save attendance outside assigned scope
- [x] Student status can be set to Present
- [x] Student status can be set to Absent
- [x] Student status can be set to Late
- [x] Attendance records can be updated
- [x] Attendance actions are saved in Audit Logs

---

## 8. Grades

- [x] Grades page loads correctly
- [x] Admin can save grades
- [x] Teacher can save grades for assigned class and subject
- [x] Teacher cannot save grades outside assigned scope
- [x] Class selection works
- [x] Subject selection works
- [x] Period selection works
- [x] Exam type selection works
- [x] Score must be between 0 and 20
- [x] Grade comments can be saved
- [x] Grade creation creates notification
- [x] Grade update works
- [x] Grade actions are saved in Audit Logs

---

## 9. Assignments

- [x] Assignments page loads correctly
- [x] Admin can create assignment
- [x] Teacher can create assignment for assigned class and subject
- [x] Teacher cannot create assignment outside assigned scope
- [x] Assignment requires class, subject, teacher, title, description, and due date
- [x] Assignment submissions are created for students
- [x] Assignment creates notifications
- [x] Assignment can be updated
- [x] Assignment can be deleted
- [x] Assignment actions are saved in Audit Logs

---

## 10. Announcements

- [x] Announcements page loads correctly
- [x] Admin can create announcement
- [x] Teacher can create allowed announcement
- [x] Announcement can target all users
- [x] Announcement can target students
- [x] Announcement can target parents
- [x] Announcement can target teachers
- [x] Announcement can target a specific class
- [x] Announcement creates notifications
- [x] Announcement can be updated
- [x] Announcement can be deleted
- [x] Deleted announcement details are preserved in Audit Logs
- [x] Announcement actions are saved in Audit Logs

---

## 11. Notifications

- [x] Notifications bell loads
- [x] Unread badge appears
- [x] Mark as read works
- [x] Badge decreases or disappears after read
- [x] Assignment creates notification
- [x] Announcement creates notification
- [x] Grade creates notification
- [x] Bulletin creates notification
- [x] Message creates notification
- [x] Message notification opens Messages page
- [x] Message notification opens the exact conversation
- [x] Message notification becomes read after opening

---

## 12. Messages

### Basic Flow

- [x] Admin can start conversation with student
- [x] Student can receive message
- [x] Student can reply
- [x] Admin can see reply
- [x] Conversation list loads
- [x] Conversation detail loads
- [x] Unread count works

### Permissions

- [x] Admin can message allowed users
- [x] Student cannot open conversation where they are not a participant
- [x] Unauthorized conversation access returns 404
- [x] Backend does not expose non-participant conversations

Security validation:

```txt
Student tried to open admin/teacher-only conversation.
Expected: 404 Conversation not found.
Actual: 404 Conversation not found.
Result: PASS.
```

---

## 13. Reports

### Attendance Report

- [x] Attendance report page loads correctly
- [x] Class filter works
- [x] Date range filter works
- [x] Attendance report generates correctly
- [x] Attendance summary shows Students
- [x] Attendance summary shows Present
- [x] Attendance summary shows Absent
- [x] Attendance summary shows Late
- [x] Attendance summary shows Total Records
- [x] Attendance table displays student rows
- [x] Empty attendance report message displays correctly
- [x] Attendance PDF export works
- [x] Attendance Excel export works

### Grades Report

- [x] Grades report page loads correctly
- [x] Class filter works
- [x] Subject filter works
- [x] Trimester filter works
- [x] Grades report generates correctly
- [x] Grades summary shows Students
- [x] Grades summary shows Graded Students
- [x] Grades summary shows Total Grades
- [x] Grades summary shows Class Average
- [x] Grades table displays student rows
- [x] Empty grades report message displays correctly
- [x] Grades PDF export works
- [x] Grades Excel export works

### Student Report

- [x] Student report page loads correctly
- [x] Class filter loads students
- [x] Student filter works
- [x] Trimester filter works
- [x] Student report generates correctly
- [x] Student summary shows General Average
- [x] Student summary shows Best Score
- [x] Student summary shows Absences
- [x] Student summary shows Grades count
- [x] Subject averages table displays correctly
- [x] Empty student report message displays correctly
- [x] Student PDF export works
- [x] Student Excel export works

### Reports UI / Export Validation

- [x] Trimester labels display as Trimester 1 / Trimester 2 / Trimester 3
- [x] Raw values like TRIMESTER_1 are not shown in report subtitles
- [x] PDF export uses correct text encoding
- [x] PDF export shows “School ERP — ...” correctly
- [x] Export PDF and Export Excel buttons are aligned correctly

---

## 14. Settings

- [x] Settings page loads correctly
- [x] Admin can update school name
- [x] Admin can update school subtitle
- [x] Admin can update academic year
- [x] Admin can update default trimester
- [x] Admin can update default report dates
- [x] Sidebar updates after saving settings
- [x] Settings update is saved in Audit Logs
- [x] Non-admin users cannot access Settings

---

## 15. Audit Logs

- [x] Audit Logs page loads correctly
- [x] Total logs card displays correctly
- [x] Latest action card displays correctly
- [x] Latest actor card displays correctly
- [x] Pagination works
- [x] Page size dropdown works
- [x] Previous button works
- [x] Next button works
- [x] Details modal opens correctly
- [x] Details modal closes correctly
- [x] Details modal displays JSON clearly
- [x] Filters work by action
- [x] Filters work by entity
- [x] Filters work by role
- [x] Empty state appears when no logs match filters
- [x] Excel export works
- [x] Audit Logs are admin-only

---

## 16. Security

- [x] JWT authentication is active
- [x] Password hashing uses bcrypt
- [x] Protected backend routes reject missing token
- [x] Protected backend routes reject invalid token
- [x] Admin-only routes reject non-admin users
- [x] Teacher scope restrictions are active
- [x] Conversation participant protection is active
- [x] Audit Logs are admin-only
- [x] Settings are admin-only
- [x] `.env` files are ignored by Git
- [x] Secrets are not committed to GitHub

Security validation:

```txt
Database URL and JWT secret are stored in environment variables.
Expected: secrets are not committed to GitHub.
Actual: .env files are ignored by .gitignore.
Result: PASS.
```

---

## 17. Build And Runtime Validation

### Backend

- [x] Backend starts successfully
- [x] Backend listens on port 5000
- [x] Backend process is visible as node.exe
- [x] Backend API is reachable locally

Expected backend output:

```txt
🚀 Server is running on http://localhost:5000
```

### Frontend

- [x] Frontend starts successfully
- [x] Frontend runs on port 5173
- [x] Frontend opens in the browser
- [x] Hot module reload works

Expected frontend output:

```txt
Local: http://localhost:5173/
```

### Production Build

- [x] Frontend production build succeeds
- [x] Build completes with “✓ built”
- [x] Large chunk warning is non-blocking

Expected build output:

```txt
✓ built
```

---

## 18. Final Git Validation

- [x] Root repository is pushed
- [x] Backend repository is pushed
- [x] Web frontend repository is pushed
- [x] Backend working tree is clean
- [x] Web working tree is clean
- [x] Root repository is clean except school-erp-mobile
- [x] school-erp-mobile changes are intentionally left untouched

Final Git status:

```txt
Root repo: clean except school-erp-mobile
Backend: clean
Web: clean
Mobile: modified, left untouched
```

---

## 19. Final Result

```txt
School ERP final web/backend validation: PASS
```