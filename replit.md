# DTE Rajasthan Multilingual Chatbot

## Overview

This is a multilingual AI chatbot designed for the Directorate of Technical Education (DTE) Rajasthan. The system provides 24/7 automated assistance to students and parents in multiple languages (Hindi, English, Urdu, Punjabi, and Gujarati) for queries related to admissions, fees, scholarships, exams, and course information.

The application follows a full-stack architecture with a React frontend, Express.js backend, and PostgreSQL database for persistent storage. It integrates with OpenAI's API for natural language processing and intent recognition, while maintaining conversation logs and analytics for administrative oversight.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript and Vite for development/bundling
- **UI Library**: Shadcn/ui components built on Radix UI primitives
- **Styling**: Tailwind CSS with custom CSS variables for theming
- **State Management**: TanStack Query (React Query) for server state management
- **Routing**: Wouter for lightweight client-side routing
- **Key Components**:
  - ChatWidget: Main chat interface with multilingual support
  - AdminDashboard: Real-time analytics and monitoring
  - ConversationLog: Historical conversation viewing
  - FAQForm: Dynamic FAQ management interface

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Database ORM**: Drizzle ORM with PostgreSQL dialect
- **API Design**: RESTful endpoints for chat, analytics, and FAQ management
- **Core Services**:
  - LanguageDetectionService: Auto-detects user language from input text using script patterns and keyword matching
  - IntentRecognitionService: Maps user queries to predefined intents (fees, admissions, scholarships, etc.)
  - OpenAIService: Handles AI chat completions with multilingual system prompts
  - ConversationLogger: Logs interactions with PII redaction for privacy
- **Storage Strategy**: Dual storage implementation with in-memory fallback and PostgreSQL persistence

### Data Storage
- **Primary Database**: PostgreSQL with Neon serverless hosting
- **Schema Design**:
  - conversations: Stores chat history with session tracking, language detection, and intent classification
  - faqs: Multilingual FAQ storage with category organization and keyword indexing
  - analytics: Daily aggregated metrics for monitoring chatbot performance
- **Migration Management**: Drizzle Kit for schema migrations and database evolution

### Authentication & Security
- **PII Protection**: Automated redaction of emails, phone numbers, Aadhaar numbers, and personal identifiers in logs
- **Data Privacy**: Conversation sanitization before storage to protect user privacy
- **Session Management**: UUID-based session tracking without user authentication requirements

### Language Processing Pipeline
1. **Input Processing**: Automatic language detection using script analysis and keyword matching
2. **Intent Recognition**: Multi-language keyword mapping to classify user queries
3. **Context Management**: Session-based conversation continuity across multiple turns
4. **Response Generation**: OpenAI integration with language-specific system prompts
5. **Analytics Tracking**: Real-time metrics collection for performance monitoring

### Performance Optimizations
- **Caching Strategy**: TanStack Query for client-side caching with configurable stale times
- **Bundle Optimization**: Vite-based building with code splitting and tree shaking
- **Database Indexing**: Optimized queries for conversation retrieval and FAQ searching
- **Memory Management**: Efficient in-memory storage fallback for development environments

## External Dependencies

### AI & Language Processing
- **OpenAI API**: GPT-based chat completions for multilingual conversation handling
- **Custom Language Detection**: Script-based detection for Hindi (Devanagari), Urdu (Arabic), Punjabi (Gurmukhi), and Gujarati scripts

### Database & Storage
- **Neon Database**: Serverless PostgreSQL hosting with connection pooling
- **Drizzle ORM**: Type-safe database operations with PostgreSQL dialect support

### UI & Styling
- **Radix UI**: Accessible component primitives for complex UI interactions
- **Tailwind CSS**: Utility-first styling with custom design system integration
- **Lucide React**: Icon library for consistent visual elements

### Development & Build Tools
- **Vite**: Fast development server and optimized production builds
- **TypeScript**: Full-stack type safety and developer experience
- **Replit Integration**: Specialized plugins for Replit development environment

### Monitoring & Analytics
- **Custom Analytics**: Built-in conversation tracking and performance metrics
- **Real-time Updates**: WebSocket-style polling for live dashboard updates
- **Conversation Logging**: NDJSON format logs with privacy protection