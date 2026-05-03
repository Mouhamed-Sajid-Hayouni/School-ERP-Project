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