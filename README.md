# gill-supabase-template

This is a Next.js app containing:

- Tailwind and Shadcn UI for styling
- [Gill](https://gill.site/) Solana SDK
- Shadcn [Wallet UI](https://registry.wallet-ui.dev) components
- **Supabase Authentication** with Solana wallet integration
- **Environment Validation** (T3 Stack style)
- **TanStack Query** for API state management
- **Prisma** for database operations
- **Protected Routes** with authentication middleware

## Features

### 🔐 **Wallet Authentication**

- Sign in with Solana wallets (Phantom, Solflare, etc.)
- Supabase integration with Web3 authentication
- Automatic session management and token refresh
- Protected routes for authenticated users

### 🛡️ **Environment Validation**

- T3 Stack style environment variable validation using Zod
- Build-time validation prevents deployment with missing/invalid environment variables
- Type-safe environment variables throughout the application

### 🚀 **API Layer**

- TanStack Query for optimized API calls
- Type-safe API client with error handling
- Optimistic updates for better UX
- React Query Devtools for debugging

### 🗄️ **Database**

- Prisma ORM with PostgreSQL
- User management with wallet address storage
- Automatic migrations and type generation

## Getting Started

### Prerequisites

1. **Supabase Project**: Create a project at [supabase.com](https://supabase.com)
2. **PostgreSQL Database**: Set up a database (can use Supabase's built-in database)

### Installation

#### Create an app using this template

```shell
npx create-solana-dapp@latest -t gh:solana-foundation/templates/gill/gill-supabase-template
```

#### Install Dependencies

```shell
npm install
```

#### Environment Setup

1. Copy the example environment file:

```shell
cp .env.example .env.local
```

2. Fill in your environment variables:

```env
# Database
DATABASE_URL="postgresql://username:password@localhost:5432/mydb?schema=public"

# Supabase
NEXT_PUBLIC_SUPABASE_URL="https://your-project.supabase.co"
NEXT_PUBLIC_SUPABASE_ANON_KEY="your-anon-key"
```

#### Database Setup

1. Generate Prisma client:

```shell
npx prisma generate
```

2. Run database migrations:

```shell
npx prisma migrate dev
```

#### Start the app

```shell
npm run dev
```

## Environment Variables

The app uses strict environment validation. All required variables must be set or the build will fail:

- `DATABASE_URL`: PostgreSQL connection string
- `NEXT_PUBLIC_SUPABASE_URL`: Your Supabase project URL
- `NEXT_PUBLIC_SUPABASE_ANON_KEY`: Your Supabase anonymous key

## Authentication Flow

1. **Connect Wallet**: User connects their Solana wallet
2. **Sign Message**: User signs an authentication message
3. **Supabase Auth**: Session created in Supabase
4. **Database Storage**: User record stored/updated in Prisma database
5. **Protected Access**: User can access protected routes like `/account`

## API Endpoints

- `POST /api/auth/wallet` - Authenticate and store wallet user

## Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run start` - Start production server
- `npx prisma studio` - Open Prisma database GUI
- `npx prisma migrate dev` - Run database migrations
