# CLO3D-Inspired SaaS Landing Page

Production-ready CLO Virtual Fashion-inspired landing page built with Next.js 15, Supabase, Tailwind CSS, Framer Motion, and React Three Fiber.

## Tech Stack

- **Next.js 15** (App Router)
- **TypeScript**
- **Tailwind CSS v4**
- **Framer Motion** — scroll animations, carousel, page transitions
- **React Three Fiber** — lazy-loaded 3D hero & feature scenes
- **Supabase** — Auth, Database, Storage-ready

## Getting Started

### 1. Install dependencies

```bash
npm install
```

### 2. Configure environment variables

Copy `.env.example` to `.env.local`:

```bash
cp .env.example .env.local
```

Add your Supabase credentials:

```
NEXT_PUBLIC_SUPABASE_URL=https://your-project.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key
```

### 3. Set up Supabase database

Run the SQL in `supabase/schema.sql` in your Supabase SQL Editor. This creates:

- `profiles` table (linked to auth.users)
- `newsletter` table (email subscriptions)
- Row Level Security policies
- Auto-profile creation trigger

### 4. Run development server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

## Project Structure

```
/app
  page.tsx              # Landing page
  /auth/login           # Sign in
  /auth/signup          # Start free trial
  /dashboard            # Protected dashboard
  /api/newsletter       # Newsletter API route
/components
  Navbar.tsx
  Hero.tsx
  Features.tsx
  Testimonials.tsx
  Footer.tsx
  /three                # R3F 3D scenes (lazy loaded)
/lib
  supabaseClient.ts     # Browser Supabase client
  supabaseServer.ts     # Server Supabase client
/supabase
  schema.sql            # Database schema
```

## Deploy to Vercel

1. Push to GitHub
2. Import project in [Vercel](https://vercel.com)
3. Add environment variables:
   - `NEXT_PUBLIC_SUPABASE_URL`
   - `NEXT_PUBLIC_SUPABASE_ANON_KEY`
4. Deploy

## Features

- Pixel-perfect CLO3D-inspired UI from `websiteinfo.txt`
- Sticky glassmorphism navbar with dropdown menus
- Parallax hero with 3D fashion avatars (R3F)
- 4 feature sections (alternating layout + workflow diagram)
- Auto-playing testimonials carousel with pause control
- Dark footer with newsletter signup (Supabase)
- Email/password authentication
- Protected `/dashboard` route
- Purple chatbot widget (bottom-right)
- Fully responsive design

## Storage (Future)

Prepare Supabase Storage buckets:

- `images` — product screenshots, avatars
- `3d-assets` — GLB/GLTF models

Uncomment bucket creation lines in `supabase/schema.sql`.
