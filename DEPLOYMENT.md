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
