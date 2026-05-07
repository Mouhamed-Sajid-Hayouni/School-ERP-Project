# School ERP - Testing Checklist

## 1. Auth

- [x] Admin login works
- [x] Teacher login works
- [x] Student login works
- [x] Parent login works
- [x] Logout works
- [x] Invalid token is rejected

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
- [x] Settings visible
- [x] Audit Logs visible

### Teacher

- [x] Overview visible
- [x] My Schedule visible
- [x] Attendance visible
- [x] Grades visible
- [x] Assignments visible
- [x] Announcements visible
- [x] Messages visible
- [x] Admin-only tabs hidden

### Student / Parent

- [x] My Portal visible
- [x] Messages visible
- [x] Admin/teacher tabs hidden

---

## 3. Notifications

- [x] Notifications bell loads
- [x] Unread badge appears
- [x] Mark as read works
- [x] Badge decreases/disappears after read
- [x] Assignment creates notification
- [x] Announcement creates notification
- [x] Grade creates notification
- [x] Bulletin creates notification
- [x] Message creates notification
- [x] MESSAGE notification opens Messages page
- [x] MESSAGE notification opens the exact conversation
- [x] MESSAGE notification becomes read after opening

---

## 4. Messages

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

## 5. Users

- [x] Admin can create user
- [x] Admin can edit user
- [x] Admin can delete user
- [x] Email validation works
- [x] Duplicate email is rejected
- [x] Parent can be linked to student
- [x] User actions appear in Audit Logs

---

## 6. Classes

- [x] Admin can create class
- [x] Admin can delete class
- [x] Duplicate class/year is rejected
- [x] Class appears in schedules, users, grades, and reports
- [x] Class actions appear in Audit Logs

---

## 7. Subjects

- [x] Admin can create subject
- [x] Admin can delete subject
- [x] Coefficient validation works
- [x] Duplicate subject is rejected
- [x] Subject actions appear in Audit Logs

---

## 8. Schedules

- [x] Admin can create schedule
- [x] Admin can edit schedule
- [x] Admin can delete schedule
- [x] Time validation works
- [x] Schedule conflict detection works
- [x] Teacher schedule scope works
- [x] Schedule actions appear in Audit Logs

---

## 9. Attendance

- [x] Admin can save attendance
- [x] Teacher can save attendance for assigned schedule
- [x] Teacher cannot save attendance outside assigned schedule
- [x] PRESENT status works
- [x] ABSENT status works
- [x] LATE status works
- [x] Attendance update works
- [x] Attendance actions appear in Audit Logs

---

## 10. Grades

- [x] Admin can save grades
- [x] Teacher can save grades for assigned class/subject
- [x] Teacher cannot save grades outside assigned scope
- [x] Score validation works
- [x] Score must be between 0 and 20
- [x] Exam Type dropdown works
- [x] Period dropdown works
- [x] Grade update works
- [x] Grade notification is created
- [x] Grade actions appear in Audit Logs

---

## 11. Assignments

- [x] Admin can create assignment
- [x] Teacher can create assignment for assigned class/subject
- [x] Assignment submissions are created for students
- [x] Students can view assignments
- [x] Parents can view child assignments
- [x] Assignment notification is created
- [x] Assignment actions appear in Audit Logs

---

## 12. Announcements

- [x] Admin can create announcement
- [x] Teacher can create allowed announcements
- [x] Admin can edit announcement
- [x] Admin can delete announcement
- [x] Announcement audience works
- [x] Announcement notification is created
- [x] Announcement actions appear in Audit Logs
- [x] Deleted announcement details are saved in Audit Logs

---

## 13. Reports

- [x] Attendance report generates
- [x] Attendance report exports PDF
- [x] Attendance report exports Excel
- [x] Grades report generates
- [x] Grades report exports PDF
- [x] Grades report exports Excel
- [x] Student report generates
- [x] Student report exports PDF
- [x] Student report exports Excel

---

## 14. Settings

- [x] School settings load
- [x] School name updates
- [x] School subtitle updates
- [x] Academic year updates
- [x] Default trimester updates
- [x] Default report dates update
- [x] Sidebar updates after saving settings
- [x] Settings update appears in Audit Logs

---

## 15. Audit Logs

- [x] Admin can view Audit Logs
- [x] Non-admin users cannot access Audit Logs
- [x] Filters work by action
- [x] Filters work by entity
- [x] Filters work by role
- [x] Details popup opens
- [x] Details popup closes
- [x] Export Excel works
- [x] Arabic names display correctly in Excel
- [x] Latest audit action appears in Overview

---

## 16. Overview Dashboard

- [x] Overview loads successfully
- [x] Academic year card displays
- [x] Current trimester card displays
- [x] Platform users card displays
- [x] Latest audit action card displays
- [x] Recent users section displays
- [x] Refresh Overview button works
- [x] Sidebar school name loads from Settings
- [x] Sidebar school subtitle loads from Settings

---

## 17. Build Validation

### Backend

- [x] Backend starts successfully

```txt
🚀 Server is running on http://localhost:5000
```

Non-blocking warning:

```txt
SECURITY WARNING: The SSL modes 'prefer', 'require', and 'verify-ca' are treated as aliases for 'verify-full'.
```

Result: PASS.

### Frontend Dev Server

- [x] Frontend starts successfully

```txt
Local: http://localhost:5173/
```

Result: PASS.

### Frontend Production Build

- [x] Frontend production build succeeds

```txt
✓ 1751 modules transformed.
✓ built in 807ms
```

Non-blocking warning:

```txt
Some chunks are larger than 500 kB after minification.
```

Result: PASS.

---

## Final Result

```txt
Authentication: PASS
Role-based access: PASS
Dashboard navigation: PASS
Notifications: PASS
Messages: PASS
Users: PASS
Classes: PASS
Subjects: PASS
Schedules: PASS
Attendance: PASS
Grades: PASS
Assignments: PASS
Announcements: PASS
Reports: PASS
Settings: PASS
Audit Logs: PASS
Overview dashboard: PASS
Frontend dev server: PASS
Frontend build: PASS
Backend server: PASS

Overall result: PASS
```