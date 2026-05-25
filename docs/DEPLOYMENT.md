
## 3) `docs/DEPLOYMENT.md`

```md
# Deployment Guide

## Overview

This project is deployed across:
- Neon for PostgreSQL
- Render for backend API
- Vercel for web frontend
- Expo EAS for mobile Android preview builds

---

## Backend Deployment (Render)

### Required Environment Variables
Set these in Render:

```env
DATABASE_URL="your_postgresql_connection_string"
JWT_SECRET="your_strong_jwt_secret"
PORT=5000