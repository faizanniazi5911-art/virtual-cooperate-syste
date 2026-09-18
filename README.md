# Company Portal Backend

This backend is the foundation for the private company portal. It is designed for:

- Role-based access for Admin, HR, Mentor, Employee, and Intern users.
- PostgreSQL data storage through Prisma.
- JWT access tokens and refresh tokens.
- Secure password hashing.
- Core operating workflows: projects, tasks, submissions, files, attendance, payments, certificates, notifications, and audit logs.

## Setup

1. Copy `.env.example` to `.env`.
2. Update `DATABASE_URL` and token secrets.
3. Install dependencies.
4. Run Prisma generation and migration.

```bash
npm install
npm run prisma:generate
npm run prisma:migrate
npm run dev
```

## Local PostgreSQL

The default `.env.example` expects PostgreSQL on:

```text
postgresql://postgres:postgres@localhost:5432/company_portal?schema=public
```

If Docker is installed, start the included database with:

```bash
docker compose up -d postgres
```

If Docker is not installed, install PostgreSQL locally, create a database named `company_portal`, and use the password `postgres` or update `.env` to match your local credentials.

Then run:

```bash
npm run prisma:migrate
npm run prisma:seed
```

Seeded login accounts use this password:

```text
Password123!
```

## API Base

Default development URL:

```text
http://localhost:4000/api
```

## Core Routes

- `GET /api/health`
- `POST /api/auth/login`
- `POST /api/auth/refresh`
- `POST /api/auth/logout`
- `GET /api/auth/me`
- `GET /api/users`
- `GET /api/projects`
- `GET /api/tasks`
- `GET /api/submissions`
- `GET /api/documents`

The route layer is intentionally thin. The next step should add service modules and connect these endpoints to real database operations.
