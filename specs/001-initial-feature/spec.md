# Technical Specification for SpookMeme AI

## 1. Technology Stack

### Frontend
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite 5.x
- **State Management**: Zustand
- **Routing**: React Router v6
- **UI Library**: Tailwind CSS + Shadcn/ui
- **Form Handling**: React Hook Form + Zod
- **Data Fetching**: TanStack Query v5

### Backend
- **Runtime**: Node.js 20 LTS
- **Framework**: Next.js 14 (App Router)
- **Language**: TypeScript
- **Database**: PostgreSQL 15 with Prisma ORM
- **Authentication**: NextAuth.js with JWT
- **API Type**: tRPC

### Infrastructure & DevOps
- **Hosting**: Vercel
- **Database Hosting**: Supabase
- **File Storage**: Cloudinary
- **CI/CD**: GitHub Actions
- **Monitoring**: Sentry
- **Analytics**: PostHog

## 2. System Architecture

### Architecture Pattern
Server-Side Rendered (SSR) with Next.js Fullstack Approach

### Component Diagram
```
┌─────────────────────────────────────────┐
│           User's Browser                │
│  ┌─────────────────────────────────┐   │
│  │   Next.js React Application     │   │
│  │   - Server & Client Components  │   │
│  │   - Routing                     │   │
│  └─────────────┬───────────────────┘   │
└────────────────┼───────────────────────┘
                 │ HTTPS
                 ▼
┌─────────────────────────────────────────┐
│         Next.js API Routes              │
│  ┌─────────────────────────────────┐   │
│  │   Server-side Logic             │   │
│  │   - Authentication              │   │
│  │   - Data Transformations        │   │
│  └─────────────┬───────────────────┘   │
└────────────────┼───────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────┐
│          Data Layer                     │
│  ┌──────────────┐  ┌──────────────┐   │
│  │  PostgreSQL  │  │  Redis Cache │   │
│  │  (Prisma)    │  │  (Sessions)  │   │
│  └──────────────┘  └──────────────┘   │
└─────────────────────────────────────────┘
```

## 3. Data Models

### User Model
```typescript
model User {
  id            String    @id @default(cuid())
  email         String    @unique
  name          String?
  passwordHash  String
  avatar        String?
  role          UserRole  @default(USER)
  createdAt     DateTime  @default(now())
  updatedAt     DateTime  @updatedAt
  memes         Meme[]
}

enum UserRole {
  USER
  ADMIN
  CREATOR
}
```

### Meme Model
```typescript
model Meme {
  id            String    @id @default(cuid())
  userId        String
  user          User      @relation(fields: [userId], references: [id])
  imageUrl      String
  textOverlay   String?
  theme         MemeTheme
  likes         Int       @default(0)
  isPublic      Boolean   @default(true)
  createdAt     DateTime  @default(now())
}

enum MemeTheme {
  CLASSIC_HORROR
  CUTE_SPOOKY
  ZOMBIE
  VAMPIRE
  WITCH
}
```

## 4. API Design

### Authentication Endpoints
```
POST   /api/auth/signup
POST   /api/auth/login
POST   /api/auth/logout
GET    /api/auth/me
POST   /api/auth/reset-password
```

### Meme Generation Endpoints
```
POST   /api/memes/generate     - AI-powered meme creation
GET    /api/memes              - List memes
GET    /api/memes/:id          - Get specific meme
PUT    /api/memes/:id          - Update meme
DELETE /api/memes/:id          - Delete meme
```

## 5. Security Implementation

### Authentication Flow
1. JWT-based authentication
2. HttpOnly secure cookies
3. Rate limiting (5 attempts/15 min)
4. Strong password validation
5. CSRF protection
6. Secure headers implementation

## 6. Performance Optimization

### Targets
- LCP < 2.5s
- FID < 100ms
- CLS < 0.1
- API Response < 300ms

### Strategies
- Code splitting
- Image optimization
- Redis caching
- Database indexing
- Aggressive static asset caching

## 7. Development Phases

### Phase 1 (Weeks 1-2)
- Project setup
- Authentication system
- Basic UI components
- Database schema

### Phase 2 (Weeks 3-4)
- Core meme generation logic
- AI integration
- Frontend views
- API endpoints

### Phase 3 (Weeks 5-6)
- Error handling
- Performance optimization
- Responsive design
- Testing

### Phase 4 (Weeks 7-8)
- Final testing
- Bug fixes
- Documentation
- Launch preparation

## 8. Scalability Roadmap
- 1K Users: Current architecture
- 10K Users: Add read replicas, CDN
- 100K Users: Microservices consideration
- 1M Users: Distributed architecture

---

**Technical Review Signatures:**
- Architecture Lead: _______________
- Security Review: _______________
- DevOps Review: _______________