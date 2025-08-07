# Lead Capture Application

React-based lead capture web application built with Vite, TypeScript, Tailwind CSS, shadcn-ui components, and Supabase backend. The application provides a modern, animated landing page with a lead capture form.

Always reference these instructions first and fallback to search or bash commands only when you encounter unexpected information that does not match the info here.

## Working Effectively

**Bootstrap and setup the repository:**
- `npm install` -- installs all dependencies. Takes ~60 seconds. NEVER CANCEL. Set timeout to 120+ seconds.

**Build commands:**
- `npm run build` -- production build. Takes ~5 seconds. Creates optimized bundle in `dist/`.
- `npm run build:dev` -- development build with source maps. Takes ~6 seconds. Larger bundle size but easier debugging.

**Development and testing:**
- `npm run dev` -- starts development server on http://localhost:8080. Ready in ~300ms. NEVER CANCEL.
- `npm run preview` -- serves production build on http://localhost:4173. Use after `npm run build`.
- `npm run lint` -- runs ESLint. Takes ~2 seconds. **WARNING: Currently has 3 errors, 7 warnings. Build still works despite linting issues.**

## Validation

**CRITICAL: Manual validation requirement after making changes:**
- Always run through the complete lead capture user flow:
  1. Navigate to http://localhost:8080
  2. Fill out the form with test data:
     - Name: "Test User"
     - Email: "test@example.com" 
     - Industry: Select any option from dropdown
  3. Click "Get Early Access" button
  4. Verify success message appears: "Welcome aboard! 🎉"
  5. Take screenshot to confirm UI renders correctly

**Pre-commit validation:**
- Always run `npm run lint` (accept current warnings/errors - they don't break functionality)
- Always run `npm run build` to ensure production build works
- Always test the complete user flow described above

## Common Tasks

**Technology stack understanding:**
- **Frontend**: React 18 + TypeScript + Vite + Tailwind CSS
- **UI Components**: shadcn-ui (Radix UI primitives)
- **State Management**: Zustand (`src/lib/lead-store.ts`)
- **Forms**: react-hook-form with zod validation
- **Routing**: react-router-dom
- **Styling**: Tailwind CSS with custom animations and gradients
- **Backend**: Supabase (database + functions)

**Key directories and files:**
- `src/pages/` -- main application pages (Index.tsx, NotFound.tsx)
- `src/components/` -- reusable components including LeadCapturePage, LeadCaptureForm, SuccessMessage
- `src/components/ui/` -- shadcn-ui component library
- `src/lib/` -- business logic (lead-store.ts, validation.ts, utils.ts)
- `src/hooks/` -- custom React hooks
- `supabase/` -- database migrations and functions
- `dist/` -- build output (excluded from git)

**Application architecture:**
- Single-page application with animated landing page
- Lead capture form with name, email, and industry fields
- Success state with animated confirmation
- Background GIF animation with overlay effects
- Responsive design with mobile support

**Database schema (Supabase):**
- `leads` table with columns: id, name, email, submitted_at, session_id, created_at, updated_at
- RLS policies allow public read/write access for lead submissions
- Automatic timestamp triggers for updated_at

**Known limitations:**
- Supabase backend may not be fully configured in development environment
- Form submission will show success message but may fail to save to database (expected in local dev)
- ESLint has some warnings/errors but they don't prevent building or functionality
- No test suite currently exists

## Timeout and Build Expectations

**NEVER CANCEL the following commands:**
- `npm install` -- 60+ seconds (set timeout: 120 seconds minimum)
- Any long-running development commands
- If commands appear to hang, wait at least 60 seconds before considering alternatives

**Quick commands (< 10 seconds):**
- `npm run build` -- ~5 seconds
- `npm run build:dev` -- ~6 seconds  
- `npm run lint` -- ~2 seconds
- `npm run dev` startup -- ~300ms to ready

## Common File Outputs

### Repository root contents:
```
.git/
.gitignore
README.md
bun.lockb
components.json
eslint.config.js
index.html
package-lock.json
package.json
postcss.config.js
public/
src/
supabase/
tailwind.config.ts
tsconfig.app.json
tsconfig.json
tsconfig.node.json
vite.config.ts
```

### Key package.json scripts:
```json
{
  "scripts": {
    "dev": "vite",
    "build": "vite build", 
    "build:dev": "vite build --mode development",
    "lint": "eslint .",
    "preview": "vite preview"
  }
}
```

### src/ directory structure:
```
src/
├── App.tsx               # Main app component with routing
├── main.tsx             # Application entry point
├── index.css            # Global styles
├── components/          # React components
│   ├── LeadCapturePage.tsx
│   ├── LeadCaptureForm.tsx
│   ├── SuccessMessage.tsx
│   └── ui/              # shadcn-ui components
├── hooks/               # Custom React hooks
├── lib/                 # Business logic and utilities
│   ├── lead-store.ts    # Zustand state management
│   ├── validation.ts    # Form validation schemas
│   └── utils.ts         # Utility functions
└── pages/               # Page components
    ├── Index.tsx        # Main landing page
    └── NotFound.tsx     # 404 page
```