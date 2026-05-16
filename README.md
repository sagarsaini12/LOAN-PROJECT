# Loan Management System (LMS)

A full-stack lending platform with a borrower application portal and an internal operations dashboard with role-based access control.

## Tech Stack

**Backend:** Node.js · Express.js · TypeScript · MongoDB · Mongoose · JWT · bcryptjs · Multer
**Frontend:** Next.js 15 (App Router) · TypeScript · Tailwind CSS · React Hook Form · Zod · Axios · Sonner

## Setup

### Prerequisites
- Node.js 18+
- MongoDB running locally or a MongoDB Atlas URI

### Backend
```bash
cd backend
npm install
cp .env.example .env      # fill in MONGODB_URI and JWT_SECRET
npm run seed              # creates all demo accounts
npm run dev               # http://localhost:5000
```

### Frontend
```bash
cd frontend
npm install
cp .env.example .env.local   # NEXT_PUBLIC_API_URL=http://localhost:5000/api
npm run dev                  # http://localhost:3000
```

## Demo Credentials

| Role         | Email                 | Password      |
|--------------|-----------------------|---------------|
| Admin        | admin@test.com        | Admin@123     |
| Sales        | sales@test.com        | Sales@123     |
| Sanction     | sanction@test.com     | Sanction@123  |
| Disbursement | disbursement@test.com | Disburse@123  |
| Collection   | collection@test.com   | Collect@123   |
| Borrower     | borrower@test.com     | Borrower@123  |

## Loan Lifecycle
APPLIED → SANCTIONED → DISBURSED → CLOSED (auto)
        ↘ REJECTED

## BRE Rules (server-side)
- Age: 23–50
- Monthly salary ≥ ₹25,000
- PAN: ^[A-Z]{5}[0-9]{4}[A-Z]{1}$
- Employment ≠ UNEMPLOYED

## Loan Formula
SI = (P × R × T) / (365 × 100)   [R=12, T=days]
Total Repayment = P + SI

## RBAC
Enforced on both frontend (route guards) and backend (middleware).
Each role can only access their specific module. Admin sees all.
Unauthorized API calls return HTTP 403.
