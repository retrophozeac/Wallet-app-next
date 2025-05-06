# Wallet App

A full-stack payment application built with Next.js, Express, and PostgreSQL. This project is a monorepo managed with Turborepo, containing multiple applications and shared packages.

## Applications

### User App

A Next.js application for end users that provides the following features:
- User authentication
- Balance management
- Add money to account (onramp from banks)
- Send money to other users (P2P transfers)
- Transaction history

### Bank Webhook

An Express.js server that handles webhooks from banking partners to process deposits and update user balances.

## Project Structure

```
paytm/
├── apps/
│   ├── user-app/         # Next.js application for end users
│   ├── merchant-app/     # Next.js application for merchants
│   └── bank-webhook/     # Express server for bank webhooks
├── packages/
│   ├── db/               # Prisma database client and schema
│   ├── ui/               # Shared UI components
│   ├── store/            # Shared state management
│   ├── eslint-config/    # Shared ESLint configuration
│   └── typescript-config/ # Shared TypeScript configuration
```

## Tech Stack

- **Frontend**: Next.js, React, Tailwind CSS
- **Backend**: Next.js API routes, Express.js
- **Database**: PostgreSQL with Prisma ORM
- **Authentication**: NextAuth.js
- **State Management**: Recoil
- **Build Tool**: Turborepo
- **Language**: TypeScript

## Getting Started

### Prerequisites

- Node.js (v18 or higher)
- npm (v10.2.4 or higher)
- PostgreSQL database

### Environment Setup

1. Create a `.env` file in the root directory with the following variables:

```
DATABASE_URL="postgresql://username:password@localhost:5432/paytm"
NEXTAUTH_SECRET="your-nextauth-secret"
NEXTAUTH_URL="http://localhost:3000"
```

### Installation

1. Clone the repository
2. Install dependencies:

```bash
npm install
```

3. Set up the database:

```bash
cd packages/db
npx prisma migrate dev
npx prisma db seed
```

### Development

Run all applications in development mode:

```bash
npm run dev
```

Or run specific applications:

```bash
# User app
npm run dev --filter=docs

# Merchant app
npm run dev --filter=web

# Bank webhook
npm run dev --filter=bank-webhook
```

The applications will be available at:
- User app: http://localhost:3001
- Merchant app: http://localhost:3000
- Bank webhook: http://localhost:3003

## Features

### User Authentication

Users can sign up and log in using their phone number and password.

### Balance Management

Users can view their current balance, including locked and unlocked funds.

### Add Money (Onramp)

Users can add money to their account by selecting a bank and amount. The system creates an onramp transaction and redirects to the bank's website.

### P2P Transfers

Users can send money to other users by entering the recipient's phone number and the amount.

### Transaction History

Users can view their transaction history, including deposits and transfers.

## Database Schema

The application uses the following data models:

- **User**: Stores user information and authentication details
- **Merchant**: Stores merchant information
- **Balance**: Tracks user balances (locked and unlocked)
- **OnRampTransaction**: Records deposits from banks
- **p2pTransfer**: Records transfers between users

## Future Improvements
### Merchant App

A Next.js application for merchants to integrate with the payment system.

