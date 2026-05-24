
## 2) `docs/ARCHITECTURE.md`

```md
# Architecture Overview

## System Summary

The School ERP System is a multi-interface platform composed of:
- a web admin/teacher dashboard
- a mobile parent portal for linked-child follow-up
- a shared backend API
- a PostgreSQL relational database

## High-Level Architecture

```text
Web App (Vercel) --------\
                          \
Mobile App (Expo APK) -----> Express API (Render) -----> PostgreSQL (Neon)
                          /
Admin / Teacher ----------/