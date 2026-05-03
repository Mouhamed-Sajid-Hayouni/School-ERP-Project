# School ERP - Deployment Notes

Deployment guide for the School ERP project.

This project uses:

- Backend: Render
- Web frontend: Vercel
- Database: Neon PostgreSQL
- Mobile builds: Expo EAS

---

## 1. Required Environment Variables

### Backend

Set these variables in Render:

- DATABASE_URL
- JWT_SECRET
- PORT

Recommended value:

- PORT=5000

Example:

- DATABASE_URL should point to the Neon PostgreSQL database.
- JWT_SECRET should be a strong private string.
- PORT can be 5000, or Render can provide its own port.

### Frontend

Set this variable in Vercel:

- VITE_API_BASE_URL

Example:

- VITE_API_BASE_URL=https://your-backend-name.onrender.com

### Mobile

Set the API base URL in the mobile app configuration or environment file.

Example:

- API_BASE_URL=https://your-backend-name.onrender.com

---

## 2. Database Deployment - Neon

1. Create a Neon project.
2. Create a PostgreSQL database.
3. Copy the database connection string.
4. Add the connection string to the backend environment as DATABASE_URL.
5. Run Prisma commands from the backend project.

Commands:

- cd school-erp-backend
- npx prisma generate
- npx prisma db push

Validation:

- Database tables should be created.
- Backend should connect successfully.
- GET /api/health should return database connected.

Expected health result:

- status: ok
- api: running
- database: connected

---

## 3. Backend Deployment - Render

### Render Service Type

Use:

- Web Service

### Root Directory

Use:

- school-erp-backend

### Build Command

Use:

- npm install
- npx prisma generate

If Render supports only one build command, use:

- npm install && npx prisma generate

### Start Command

Use:

- npm run dev

For production later, consider creating a production start command, but the current project uses ts-node through the dev script.

### Environment Variables

Add:

- DATABASE_URL
- JWT_SECRET
- PORT

### Health Check

After deployment, open:

- https://your-backend-name.onrender.com/api/health

Expected result:

- status: ok
- api: running
- database: connected

---

## 4. Web Frontend Deployment - Vercel

### Vercel Project

Import the repository into Vercel.

### Root Directory

Use:

- school-erp-web

### Build Command

Use:

- npm run build

### Output Directory

Use:

- dist

### Environment Variables

Add:

- VITE_API_BASE_URL

Example value:

- https://your-backend-name.onrender.com

### Validation

After deployment:

1. Open the Vercel website URL.
2. Login as admin.
3. Confirm dashboard loads.
4. Confirm notifications load.
5. Confirm reports load.
6. Confirm settings load.
7. Confirm messages load.

---

## 5. CORS

The backend currently uses CORS.

When deployed, confirm that the frontend can call the backend.

If requests are blocked by CORS, update the backend CORS configuration to allow the Vercel frontend URL.

Example allowed origins:

- http://localhost:5173
- https://your-vercel-app.vercel.app

---

## 6. Production API URL

In local development:

- VITE_API_BASE_URL=http://localhost:5000

In production:

- VITE_API_BASE_URL=https://your-backend-name.onrender.com

Important:

After changing VITE_API_BASE_URL in Vercel, redeploy the frontend.

---

## 7. Prisma Deployment Notes

Run these after schema changes:

- npx prisma generate
- npx prisma db push

Use db push for the current project workflow.

Future improvement:

- Use Prisma migrations for production change history.

---

## 8. Backend Validation Checklist

After deploying backend:

- Backend URL opens
- GET / works
- GET /api/health works
- Database status is connected
- Login works
- Protected routes reject invalid token
- Notifications route works
- Messages route works
- Reports routes work
- Settings routes work

---

## 9. Frontend Validation Checklist

After deploying frontend:

- Website opens
- Login page works
- Admin login works
- Teacher login works
- Student login works
- Parent login works
- Sidebar loads
- Notifications bell loads
- Messages page loads
- Reports page loads
- Settings page loads
- Export buttons work
- Logout works

---

## 10. Mobile Deployment - Expo EAS

The mobile app is located in:

- school-erp-mobile

Recommended commands:

- cd school-erp-mobile
- npm install
- npx expo start

For EAS builds:

- eas login
- eas build:configure
- eas build --platform android

Before building, confirm the mobile app points to the deployed backend API URL.

---

## 11. Common Deployment Issues

### Backend cannot connect to database

Check:

- DATABASE_URL is correct
- Neon database is active
- Prisma client was generated
- npx prisma db push was run
- /api/health response

### Frontend cannot call backend

Check:

- VITE_API_BASE_URL is correct
- Backend is deployed and running
- CORS allows the frontend domain
- Vercel was redeployed after environment variable changes

### Login fails in production

Check:

- JWT_SECRET exists in Render
- DATABASE_URL points to the correct database
- User exists in production database
- Backend logs for authentication errors

### Reports export opens blank page

Check:

- Browser allows popups
- Report was generated before clicking Export PDF
- Data exists for the selected class/date/trimester

### Notifications do not load

Check:

- User is logged in
- Token exists in localStorage
- Backend /api/my-notifications works
- Database connection is healthy

---

## 12. Current Stable Local Validation

Frontend:

- cd school-erp-web
- npm run build
- Build passed successfully

Backend:

- cd school-erp-backend
- npm run dev
- Server runs on http://localhost:5000

Health:

- GET /api/health
- Database connected

---

## 13. Recommended Production Improvements

Before final public deployment:

1. Add a production backend start script.
2. Add Prisma migrations instead of only db push.
3. Restrict CORS to known frontend URLs.
4. Add stronger logging for backend errors.
5. Add automated tests for auth and permissions.
6. Add route-based code splitting to reduce frontend bundle size.
7. Add screenshots to README.md.
8. Add seed data for demo accounts if needed.

---

## 14. Deployment Status

Current deployment readiness:

- Frontend build: ready
- Backend run: ready
- Database health: ready
- Reports: ready
- Messages: ready
- Settings: ready
- Documentation: in progress

Overall status:

School ERP is ready for first deployment preparation.