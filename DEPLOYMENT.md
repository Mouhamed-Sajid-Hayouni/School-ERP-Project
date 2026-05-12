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

- User profile image upload
- Profile images displayed on web
- Profile images displayed on mobile
- Deployed backend API integration
- Web production API fallback fixed
- Mobile profile header layout improved
- Expo package versions updated
- Admin password update endpoint added
- Admin password change field added to web UI

## Security Notes

- Do not commit passwords or tokens.
- Admin password was changed after testing.
- Password changes are handled through:
  PUT /api/users/:id/password

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
- Admin login works with new password
- Old admin password no longer works
- Users page loads without Failed to fetch
- Existing profile images display
- Upload Photo works
- Uploaded image stays after refresh
- Mobile app loads with Expo Go
- Mobile profile image displays
- Git root is clean
- Backend, web, and mobile are on main and synced with origin

## Release Tags

- v1.0-profile-images: Stable release for profile image upload/display, deployment cleanup, mobile support, and password security cleanup.
- v1.0.1-sidebar-avatar: Patch release for showing the logged-in user's real profile image in the web sidebar.

## Latest Patch

The web sidebar now displays the current user's uploaded profile image instead of initials.

## Cloudinary Image Storage Patch

- v1.0.2-cloudinary-images: Patch release for persistent profile image storage.
- Profile images are now uploaded to Cloudinary instead of Render local disk.
- New profileImage values are stored as Cloudinary URLs:
  https://res.cloudinary.com/...
- Old /uploads/... profile images should be re-uploaded once.
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
