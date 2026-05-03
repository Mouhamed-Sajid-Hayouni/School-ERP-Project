
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
DATABASE_URL="postgresql://neondb_owner:npg_4Uyb6jqaunRS@ep-orange-shape-alrgercn.c-3.eu-central-1.aws.neon.tech/neondb?sslmode=require&channel_binding=require"
JWT_SECRET="super_secret_school_key_123"
PORT=5000