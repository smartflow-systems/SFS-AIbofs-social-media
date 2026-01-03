# SFS-AIbofs-social-media - AI Agent Guidelines

## Project Overview

AI-powered social media management platform that combines SocialScale-style landing pages, booking system, shop, and bot demos. This is a comprehensive social media scheduler with multi-platform support (Twitter/X, LinkedIn), AI content generation, analytics, and a Flask-based admin system. The project features a React Progressive Web App with offline functionality and Express backend.

## Technology Stack

### Frontend
- **React 19.1** with TypeScript 5.9
- **Vite 7.1.3** for build tooling
- **Tailwind CSS 4.1.12** for styling
- **Lucide React** for icons
- **Progressive Web App** with service worker

### Backend
- **Node.js 18+** with Express 5.1
- **Python 3.11+** with Flask and Gunicorn
- **SQLite** database via SQLAlchemy
- **Better-SQLite3** for Node.js database access

### Key Dependencies
- **Socket.IO** for real-time features
- **Axios** for HTTP requests
- **Zod 4.1** for validation
- **Luxon** for date/time handling
- **Express-rate-limit** for API protection
- **Helmet** for security headers
- **Node-cron** for scheduled tasks

### External Integrations
- **OpenAI** for AI content generation
- **Formspree** for contact form handling
- **Stripe** for payments (shop functionality)
- **WhatsApp** for contact options

## Key Files & Directories

### Core Application
- `[server.js]` - Express server with SPA hosting and API routes
- `[app.py]` - Flask admin application with database integration
- `[main.py]` - Combined server launcher for dual Express/Flask setup

### Frontend Assets
- `[static/]` - Social AI PWA files
  - `[static/index.html]` - Main application interface
  - `[static/app.js]` - Social AI functionality
  - `[static/style.css]` - Styling with SocialScale theme
  - `[static/logo.png]` - SmartFlow branding
- `[sw.js]` - Service worker for offline functionality

### Feature Pages
- `[book.html]` - Discovery call booking system with ICS export
- `[shop.html]` - Product catalog and shopping cart
- `[bots.html]` - Bot demos (smart replies, best-time API, scheduler)
- `[book.js]` - Booking system JavaScript
- `[bots.js]` - Bot demo JavaScript

### Flask Templates
- `[templates/base.html]` - Base template with SmartFlow logo
- `[templates/landing.html]` - Marketing landing page
- `[templates/pricing.html]` - Pricing page

### Data & Assets
- `[data.json]` - Configuration and data store
- `[data.sqlite]` - SQLite database
- `[assets/]` - SVG logos and icons
- `[attached_assets/]` - Additional media files

### Client Build
- `[client/]` - React application source
- `[client/dist/]` - Built React application (served by Express)

### Testing & Scripts
- `[scripts/sanity-check.mjs]` - Project validation script
- `[scripts/audit-routes.mjs]` - Route verification script
- `[tests/e2e/]` - Playwright end-to-end tests

### Configuration
- `[package.json]` - Node.js dependencies and scripts
- `[.env.example]` - Environment variable template
- `[.replit]` - Replit deployment configuration

## Common Tasks

### Development Workflow

**Start Development Server:**
```bash
npm run dev
```

**Build React Frontend:**
```bash
npm run build
```

**Start Production Server:**
```bash
npm start
```

**Run Flask Admin:**
```bash
python app.py
```

**Combined Server Launch:**
```bash
python main.py
```

### Testing & Validation

**Install Playwright:**
```bash
npm run playwright
```

**Run E2E Tests:**
```bash
npm run test:e2e
```

**Sanity Check:**
```bash
npm run sanity
```

**Audit Routes:**
```bash
npm run audit
```

### Content Generation

**AI Post Creation:**
- Use OpenAI integration for AI-powered content
- Fallback to stub generator without API key
- Support for custom topics and tones

**Template Management:**
- Built-in templates with variable substitution
- Custom template creation
- Export templates for reuse

### Data Management

**Export Capabilities:**
- CSV export for analytics data
- ICS calendar export for scheduled posts
- Local storage backup for offline submissions

**Database Operations:**
- SQLite database at `[data.sqlite]`
- Session management via Flask
- Local storage for cart and form data

## Development Commands

```bash
# Dependencies
npm install                    # Install Node.js packages
pip install flask gunicorn     # Install Python dependencies

# Development
npm run dev                    # Development server with hot reload
npm start                      # Production server (requires build)
node server.js                 # Express server only
python app.py                  # Flask admin only
python main.py                 # Combined Express + Flask

# Building
npm run build                  # Build React app to client/dist/

# Testing
npm run test:e2e               # Playwright tests
npm run sanity                 # Project validation
npm run audit                  # Route audit

# Health Check
curl http://localhost:8787/health
# Returns: {"ok":true,"ts":1234567890}
```

## Integration Points

### SFS Ecosystem Integration
- **SmartFlow Branding:** Consistent brown/black/gold theme
- **Stripe Payments:** Ready for shop checkout integration
- **Multi-platform Social:** Twitter/X and LinkedIn support
- **AI Content:** OpenAI integration for content generation

### External Services
- **Formspree:** Contact form and booking submissions
- **WhatsApp:** Contact option integration
- **Google Calendar:** ICS export for calendar sync
- **Social Platforms:** Twitter/X and LinkedIn APIs

### Data Flow
- **Frontend → Express API:** React app communicates via REST
- **Express → Flask:** Admin routes handled by Flask
- **Local Storage:** Offline data persistence
- **Service Worker:** PWA offline functionality

## Environment Variables

```env
# Contact Configuration
CONTACT_EMAIL=hello@smartflowsystems.co.uk
WHATSAPP_NUMBER=447000000000

# Form Integration
FORMSPREE_FORM_ID=yourFormID

# Payments
STRIPE_SECRET_KEY=sk_test_...
STRIPE_PRICE_ID_BASIC=price_...
STRIPE_PRICE_ID_PRO=price_...

# AI Integration
OPENAI_API_KEY=sk-...

# Flask Configuration
SESSION_SECRET=your-session-secret
DATABASE_URL=sqlite:///instance/smartflow.db

# Server
PORT=8787
NODE_ENV=production
```

## Agent Best Practices

### File Operations
- **VERIFY** before destructive operations on `[data.sqlite]` or `[data.json]`
- **UNDO** capability for all file changes
- **Show file paths** in brackets `[path/to/file]`
- **Preserve branding** in templates and static files

### Code Safety
- Bash scripts use `set -euo pipefail`
- Always validate environment variables before API calls
- Test both Express and Flask routes independently
- Verify React build exists before serving

### Database Operations
- Backup `[data.sqlite]` before schema changes
- Use SQLAlchemy migrations for Flask database
- Validate data.json structure before modifications
- Test local storage fallbacks for offline mode

### Testing Protocol
- Run sanity check after major changes
- Test booking flow end-to-end
- Verify shop cart persistence
- Validate social media post scheduling
- Check PWA offline functionality

### Security Considerations
- Never commit `.env` files
- Sanitize user inputs in forms
- Validate API keys before deployment
- Use Helmet.js security headers
- Implement CORS properly
- Rate limit API endpoints

## SmartFlow Standards

### Theme & Design
- **Colors:** Brown/black/gold signature palette
- **Typography:** System fonts for performance
- **Dark Theme:** Primary with gold (#f5d67b) accents
- **Responsive:** Mobile-first design approach

### CI/CD
- **GitHub Actions:** Security scanning workflows
- **Deployment:** Replit-ready configuration
- **Health Check:** `GET /health → {"ok":true,"ts":1234567890}`

### Performance
- **Compression:** Enabled via Express middleware
- **Code Splitting:** Vite build optimization
- **PWA Caching:** Service worker strategy
- **Rate Limiting:** API protection

### Monitoring
- Health endpoint at `/health`
- API status logging
- Error tracking via Express middleware
- Build status validation

## Feature Highlights

### Social AI Platform
- AI content generation with topic/tone selection
- Multi-platform scheduling (Twitter/X, LinkedIn)
- Smart analytics with best-time analysis
- Engagement tracking and monthly reports
- Template system with variables

### Booking System
- Discovery call form with date/time picker
- ICS calendar file generation
- Email notifications via Formspree
- Local storage backup for offline
- WhatsApp contact integration

### Shop Features
- Product catalog (templates, add-ons, seats)
- Shopping cart with local storage
- Stripe payment integration ready
- Responsive product grid

### Bot Demos
- Smart comment replies
- Best-time posting recommendations
- Bulk calendar event creation
- API integration examples

## Browser Support

- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+
- iOS Safari and Chrome Mobile

## Deployment Notes

### Replit Deployment
- Configured in `[.replit]`
- Automatic HTTPS handling
- Environment variables via Replit Secrets
- Health checks included

### Manual Deployment
```bash
# Build and deploy
npm run build
node server.js

# With PM2
pm2 start server.js --name "smartflow-social"
```

### Production Checklist
- [ ] React build completed (`client/dist/` exists)
- [ ] Environment variables configured
- [ ] OpenAI API key added (if using AI features)
- [ ] Formspree form ID configured
- [ ] Stripe keys added (if using shop)
- [ ] Database initialized
- [ ] Health check responding
- [ ] PWA manifest configured

## Support & Documentation

**Contact:**
- Email: hello@smartflowsystems.co.uk
- WhatsApp: +44 7000 000 000

**License:** MIT

**Built by:** SmartFlow Systems
