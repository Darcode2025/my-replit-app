# replit.md

## Overview

This is a full-stack financial market data and analysis application called "WSM Finance". It's built with a modern tech stack featuring React frontend, Express backend, and PostgreSQL database. The application provides comprehensive financial market data, stock analysis, portfolio management, and research insights.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

The application follows a monorepo structure with clear separation between client and server code:

- **Frontend**: React SPA with TypeScript, built with Vite
- **Backend**: Express.js REST API with TypeScript
- **Database**: PostgreSQL with Drizzle ORM
- **Styling**: Tailwind CSS with shadcn/ui components
- **State Management**: TanStack Query for server state
- **Routing**: Wouter for client-side routing

## Key Components

### Frontend Architecture
- **Component Library**: shadcn/ui components built on Radix UI primitives
- **Styling**: Tailwind CSS with custom WSM brand colors (red, blue, green)
- **State Management**: TanStack Query handles all server state and API calls
- **Routing**: Wouter provides lightweight client-side routing
- **Build Tool**: Vite for fast development and optimized builds

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Database ORM**: Drizzle ORM for type-safe database operations
- **Database**: PostgreSQL (configured for Neon serverless)
- **Session Storage**: PostgreSQL session store with connect-pg-simple
- **API Structure**: RESTful endpoints organized by resource type

### Database Schema
The application uses the following main entities:
- `users`: User authentication and profile data
- `articles`: Financial news and analysis articles
- `portfolios`: User portfolio containers
- `portfolio_stocks`: Individual stock holdings within portfolios
- `stock_data`: Real-time stock market data
- `newsletter_subscriptions`: Email newsletter subscriptions
- `article_requests`: User-requested article topics

## Data Flow

1. **Client Requests**: React components use TanStack Query to fetch data
2. **API Layer**: Express routes handle HTTP requests and validation
3. **Business Logic**: Server-side logic processes requests and interacts with database
4. **Database**: Drizzle ORM provides type-safe database operations
5. **Response**: JSON responses sent back to client with proper error handling

## External Dependencies

### Frontend Dependencies
- React 18 with TypeScript
- Vite for build tooling
- TanStack Query for server state management
- Wouter for routing
- Tailwind CSS for styling
- shadcn/ui component library
- Radix UI primitives

### Backend Dependencies
- Express.js framework
- Drizzle ORM for database operations
- @neondatabase/serverless for PostgreSQL connection
- Zod for runtime validation
- connect-pg-simple for session storage
- @sendgrid/mail for email functionality

### Development Tools
- TypeScript for type safety
- ESBuild for server bundling
- PostCSS for CSS processing
- Drizzle Kit for database migrations

## Deployment Strategy

The application is designed for deployment on Replit with the following characteristics:

- **Development**: Uses `tsx` to run TypeScript server directly
- **Production**: Server is bundled with ESBuild into `dist/index.js`
- **Database**: Configured for Neon PostgreSQL serverless
- **Static Assets**: Frontend builds to `dist/public`
- **Environment**: Requires `DATABASE_URL` environment variable

The build process creates both client and server bundles, with the server serving the built React application in production mode.

## Recent Changes: Latest modifications with dates

### July 18, 2025
- **Enhanced Admin Dashboard**: Fixed analytics charts with proper interactive data visualization
- **User Account Management**: Added comprehensive user account management for admins
  - View all registered users with account details
  - Delete user accounts with protection for admin account
  - Clean admin interface with user status indicators
- **Newsletter Subscription Management**: Added delete functionality for newsletter subscriptions
  - Admins can remove subscriptions with trash button
  - Proper confirmation and error handling
- **Advanced Article Publishing System**: Complete article management with media support
  - Fixed JSON serialization issue in article publishing
  - Added image upload functionality with file picker
  - Support for featured images and inline images within content
  - Automatic ticker symbol hyperlinking (e.g., AAPL becomes clickable link)
  - Enhanced content editor with cursor position tracking
  - Preview functionality for uploaded images
- **Real-time Ticker Strip**: Enhanced top bar with live market data
  - Cycles through major indexes (S&P 500, Dow Jones, NASDAQ, Russell 2000)
  - Displays real-time prices, changes, and percentages
  - Includes major stocks (AAPL, MSFT, GOOGL, AMZN, TSLA, META, NVDA, NFLX)
  - Auto-refreshes every 30 seconds with cycling display every 5 seconds
- **Image Upload Infrastructure**: Complete file upload system
  - Multer-based image upload with file type validation
  - 5MB file size limit with support for JPEG, PNG, GIF, WebP
  - Static file serving for uploaded images
  - Secure upload endpoints with authentication

### July 17, 2025
- **Enhanced Chart Data**: Fixed 1-day and 1-week chart data loading with proper intraday intervals
- **Email System Overhaul**: Migrated from SendGrid to Nodemailer for better control
  - Now sends notifications to wallstreetmosaic@gmail.com instead of shadar000@isd284.com
  - Includes detailed HTML email templates with professional styling
  - Fallback console logging when Gmail credentials are not configured
  - Supports both authenticated SMTP and development logging modes
- **Article Request System**: Complete email-based article request functionality
  - Beautiful confirmation animation with bouncing checkmark
  - Optional email field for user notifications
  - Tracks request count in database with proper deduplication
  - Sends detailed notifications with stock information and requester details
- **Newsletter Subscription System**: Full newsletter management implementation
  - Subscribe/unsubscribe functionality with database storage
  - Email notifications for new subscriptions and unsubscriptions
  - Newsletter subscriber management API endpoints
  - Beautiful newsletter signup component in sidebar
  - Handles duplicate emails gracefully with subscription reactivation
- **Database Schema Updates**: Added newsletter_subscriptions table with proper indexes
- **Improved Search**: Updated search to show only stocks starting with typed letters (prefix matching)
- **Interactive Charts**: Implemented real-time charts with Yahoo Finance data for all timeframes
- **Stock Details Enhancement**: Added comprehensive stock pages with live price tracking and metrics