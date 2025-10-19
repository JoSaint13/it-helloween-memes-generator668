# SpookMeme AI

> Instantly create hilarious, shareable Halloween memes with AI-powered creativity

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)](https://github.com/spookmeme/ai)

## Overview

SpookMeme AI is an innovative meme generation platform specialized in creating unique, trend-setting Halloween content. Leveraging advanced AI technologies, the platform enables social media users to generate personalized, shareable memes with ease.

## Features

- ✨ AI-powered Halloween meme generation
- 🚀 Real-time thematic templates
- 💡 Social media sharing integration
- 🔒 Secure user authentication

## Tech Stack

**Frontend:**
- React 18 with TypeScript
- Vite 5.x
- Tailwind CSS
- Zustand State Management

**Backend:**
- Next.js 14
- tRPC
- PostgreSQL with Prisma ORM
- NextAuth.js

**Deployment:**
- Vercel
- Supabase
- Cloudinary

## Quick Start

### Prerequisites

```bash
node >= 18.0.0
npm >= 9.0.0
```

### Installation

```bash
# Clone the repository
git clone https://github.com/spookmeme/ai.git

# Install dependencies
cd spookmeme-ai
npm install

# Set up environment variables
cp .env.example .env
# Edit .env with your configuration

# Run development server
npm run dev
```

Visit `http://localhost:3000` to start creating Halloween memes!

## Project Structure

```
/
├── src/
│   ├── components/     # React UI components
│   ├── pages/          # Next.js pages
│   ├── utils/          # Utility functions
│   ├── styles/         # Tailwind CSS
│   └── hooks/          # Custom React hooks
├── public/             # Static assets
├── tests/              # Test files
└── prisma/             # Database schema
```

## Development

### Available Scripts

```bash
npm run dev         # Start development server
npm run build       # Build for production
npm run test        # Run unit tests
npm run lint        # Lint code
```

### Environment Variables

Required environment variables:

```env
NEXT_PUBLIC_API_URL=your-api-url
DATABASE_URL=your-postgresql-connection
NEXTAUTH_SECRET=your-auth-secret
```

## Testing

```bash
# Run unit tests
npm run test

# Run with coverage
npm run test:coverage
```

## Deployment

### Vercel Deployment

```bash
npm run build
vercel --prod
```

## Contributing

We welcome contributions! Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct and development process.

### Contributing Steps

1. Fork the repository
2. Create feature branch (`git checkout -b feature/halloween-meme-templates`)
3. Commit changes (`git commit -m 'Add new meme template generation'`)
4. Push to branch (`git push origin feature/halloween-meme-templates`)
5. Open Pull Request

## License

MIT License - see [LICENSE](LICENSE) for details.

## Support

For support, please [open an issue](https://github.com/spookmeme/ai/issues) or contact support@spookmemeai.com.

---

**Generated with 🎃 by SpookMeme AI Team**