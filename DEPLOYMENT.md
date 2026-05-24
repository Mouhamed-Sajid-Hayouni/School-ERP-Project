# School ERP Project - Deployment Notes

## Repositories

- Root: School-ERP-Project
- Backend: school-erp-backend
- Web: school-erp-web
- Mobile: school-erp-mobile

## Production URLs

- Backend API: https://school-erp-api-3l16.onrender.com
- Web App: https://school-erp-web-murex.vercel.app

## Main Features Completed

- Controlled parent/teacher account request workflow
- Admin approval and rejection of pending account requests
- Read-only admin user management
- Direct user create/edit/delete/password/profile-image actions blocked
- Student records kept without direct electronic login
- Deployed backend API integration
- Web production API fallback fixed
- Mobile parent portal remains scoped to linked children

## Security Notes

- Do not commit passwords or tokens.
- Direct password changes through admin user management are disabled.
- The endpoint PUT /api/users/:id/password returns 403 in the current controlled account workflow.

## Deployment Platforms

### Backend

Platform: Render  
Service: school-erp-api  
Deploy method: Manual Deploy / latest commit

### Web

Platform: Vercel  
Project: school-erp-web  
Deploy method: automatic deployment from main branch

### Mobile

Platform: Expo  
Test method: Expo Go using npm run start

## Final Verification Checklist

- Backend health/API works
- Web app opens in production
- Admin login works with current authorized credentials
- Protected account request endpoints require an admin token
- Users page loads without Failed to fetch
- Users page remains read-only for direct account changes
- Pending account approve action works
- Pending account reject action works
- Direct profile-image upload action remains blocked
- Mobile app loads with Expo Go
- Mobile parent portal displays scoped linked-child data
- Git root is clean
- Backend, web, and mobile are on main and synced with origin

## Release Tags

- v1.0-profile-images: Legacy release for earlier profile-image display work, deployment cleanup, mobile support, and password security cleanup.
- v1.0.1-sidebar-avatar: Patch release for showing the logged-in user's stored profile image in the web sidebar.

## Latest Patch

The web sidebar displays the current user's stored profile image instead of initials when one already exists.

## Cloudinary Image Storage Patch

- v1.0.2-cloudinary-images: Patch release for persistent profile image storage.
- Legacy profile images used Cloudinary storage instead of Render local disk.
- New profileImage values are stored as Cloudinary URLs:
  https://res.cloudinary.com/...
- Old /uploads/... values should be migrated only if legacy image display is needed.
- Cloudinary credentials are stored only in Render environment variables.

## Required Render Environment Variables

- CLOUDINARY_CLOUD_NAME
- CLOUDINARY_API_KEY
- CLOUDINARY_API_SECRET

## Student Login Policy Patch

- v1.0.3-student-login-policy: Patch release for primary-school access rules.
- Students remain ERP records for classes, attendance, grades, bulletins, and parent follow-up.
- Student accounts cannot log in directly to the system.
- Parents, teachers, and admins are the direct system users.
- Direct student login returns:
  Student accounts cannot access the system directly. Please use a parent account.

## Student Record Password Policy Patch

- v1.0.4-student-record-password-policy: Patch release for student account creation rules.
- Student records can now be created without entering a login password.
- The backend generates an internal random password for student records when no password is provided.
- Student accounts still cannot log in directly.
- Parents, teachers, and admins remain the direct system users.
- Current web Users page is read-only for direct account creation.
- Parent and teacher accounts are requested through self-registration and then approved or rejected by admin.
- Student records remain school records without direct login.
