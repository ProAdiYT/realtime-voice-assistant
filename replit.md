# Neural Voice Agent

## Overview

This is a real-time conversational AI voice agent application built with React, Express, and PostgreSQL. The application provides a futuristic interface for voice-based interactions with an AI assistant named NEXUS. Users can speak to the AI using voice input, receive text and audio responses, and view conversation history stored in a database.

The application features a dark, cyberpunk-inspired UI design with electric cyan accents, custom fonts (Orbitron and Rajdhani), and visual components for displaying agent status and audio waveforms.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework**: React 18 with TypeScript and Vite as the build tool

**Routing**: Wouter for lightweight client-side routing

**UI Framework**: Custom component library based on Radix UI primitives with shadcn/ui styling patterns (New York style variant)

**Styling**: 
- TailwindCSS v4 for utility-first styling
- Custom CSS variables for theming (dark futuristic theme with cyan primary color)
- CSS custom properties for colors, fonts, and spacing

**State Management**:
- TanStack Query (React Query) for server state management and API data fetching
- Local React state with hooks for component-level state

**Voice Features**:
- Web Speech API for speech recognition (fallback implementation)
- Deepgram integration (optional, with server-provided API token)
- Text-to-speech synthesis capabilities

**Key Frontend Patterns**:
- Custom hooks for reusable logic (mobile detection, toast notifications)
- Component composition with Radix UI primitives
- Centralized API client with error handling
- TypeScript for type safety throughout the application

### Backend Architecture

**Framework**: Express.js with TypeScript running on Node.js

**Development Mode**: 
- Vite middleware integration for HMR (Hot Module Replacement) during development
- Custom error overlay plugin for runtime error display

**Production Mode**:
- ESBuild bundling for optimized server code
- Static file serving from built client assets
- Allowlist-based dependency bundling to reduce cold start times

**API Design**:
- RESTful endpoints under `/api` prefix
- OpenAI GPT-3.5-turbo integration for conversational AI responses
- Conversation and message management endpoints
- Proxy pattern for external API calls (OpenAI)

**Middleware Stack**:
- JSON body parsing with raw body capture for webhook verification
- URL-encoded form data support
- Custom request logging with timing information

**Key Backend Patterns**:
- HTTP server factory pattern for WebSocket support readiness
- Environment-based configuration
- Structured logging with timestamps and source identification

### Data Storage

**Database**: PostgreSQL via Neon serverless driver

**ORM**: Drizzle ORM for type-safe database queries and migrations

**Schema Design**:
- **Conversations table**: Stores conversation metadata with UUID primary keys
  - `id`: Auto-generated UUID
  - `title`: Conversation title (defaults to "New Conversation")
  - `createdAt`: Timestamp of creation
  
- **Messages table**: Stores individual messages within conversations
  - `id`: Auto-generated UUID
  - `conversationId`: Foreign key to conversations (cascade delete)
  - `role`: Message role (user/assistant/system)
  - `content`: Message text content
  - `timestamp`: Message creation time

**Data Access Pattern**:
- Repository pattern via `DatabaseStorage` class implementing `IStorage` interface
- Abstraction layer separating business logic from data access
- Zod schema validation for data insertion

**Migration Strategy**: 
- Drizzle Kit for schema migrations
- Schema definitions in TypeScript co-located with application code
- Push-based workflow for schema synchronization

### External Dependencies

**AI Services**:
- **OpenAI API**: GPT-3.5-turbo for conversational AI responses
  - Configured via `OPENAI_API_KEY` environment variable
  - Direct API integration with custom system prompt
  - Fallback to mock responses on API failure

**Database Services**:
- **Neon Serverless PostgreSQL**: Primary data storage
  - Configured via `DATABASE_URL` environment variable
  - HTTP-based connection for serverless compatibility

**Optional Voice Services** (infrastructure present, not fully implemented):
- **Deepgram**: Speech-to-text transcription (server can provide API tokens)
- **Text-to-Speech Service**: Audio synthesis endpoint (`/api/tts`)

**Development Tools**:
- **Replit Vite Plugins**: Runtime error modal, cartographer, dev banner
- Custom meta images plugin for OpenGraph image URL updates

**UI Dependencies**:
- **Radix UI**: Headless component primitives for accessibility
- **Lucide React**: Icon library
- **Class Variance Authority**: Type-safe variant styling
- **TailwindCSS**: Utility-first CSS framework
- **Embla Carousel**: Carousel component library

**Build & Development**:
- **Vite**: Frontend build tool and dev server
- **ESBuild**: Server code bundling for production
- **TSX**: TypeScript execution for development and build scripts
- **TypeScript**: Type checking and compilation

**Font Loading**:
- Google Fonts: Orbitron (display) and Rajdhani (sans-serif) font families