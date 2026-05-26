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

## API Documentation

### Newsletter Endpoint

**POST** `/api/newsletter`

Subscribe a user to the newsletter.

```json
Request:
{
  "email": "user@example.com"
}

Response (200):
{
  "success": true,
  "message": "Subscribed successfully"
}
```

### Admin User Creation

**POST** `/api/admin/create-user`

Create a new admin user (requires authentication).

```json
Request:
{
  "email": "admin@example.com",
  "password": "securePassword123"
}

Response (200):
{
  "success": true,
  "userId": "uuid"
}
```

## Configuration Guide

### Environment Variables

Create a `.env.local` file with the following:

```env
# Supabase
NEXT_PUBLIC_SUPABASE_URL=https://your-project.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key
SUPABASE_SERVICE_ROLE_KEY=your-service-role-key

# Optional: Database URL for migrations
DATABASE_URL=postgresql://user:password@localhost:5432/db_name
```

### Supabase Setup

1. Create a new project at [supabase.com](https://supabase.com)
2. Go to SQL Editor and run `supabase/schema.sql`
3. Enable email/password authentication in Auth settings
4. Copy credentials to `.env.local`

### Tailwind Configuration

Customization available in `tailwind.config.ts`:

- Color palette: `colors` section
- Typography: `fontFamily` and `fontSize`
- Spacing: `spacing` section
- Animations: `keyframes` and `animation` sections

### Framer Motion

- Page transitions in `components/PageTransition.tsx`
- Scroll animations use `Intersection Observer`
- Carousel animation in testimonials section

## Advanced Features

### 3D Scenes with React Three Fiber

Located in `components/three/`:

- **HeroScene.tsx** — Animated 3D fashion avatar (hero)
- **FeatureScene.tsx** — Feature workflow visualization
- **SectionParticles.tsx** — Background particle effects

Scenes are lazy-loaded with `React.lazy()` and `Suspense` for performance.

### Authentication Flow

1. User signs up at `/auth/signup`
2. Supabase sends confirmation email
3. User confirmed → profile auto-created via trigger
4. User can access `/dashboard`

### Middleware

`middleware.ts` protects routes:

- `/dashboard` requires authentication
- Redirects unauthenticated users to `/auth/login`

## Performance Optimizations

- Image optimization with `next/image`
- Code splitting with `React.lazy()`
- CSS minimization with Tailwind
- API routes with edge caching
- 3D scene lazy loading on viewport intersection

## Browser Support

- Chrome/Edge: Latest 2 versions
- Firefox: Latest 2 versions
- Safari: Latest 2 versions
- Mobile: iOS Safari 14+, Chrome Android

## Troubleshooting

### Supabase Connection Error

- Verify `NEXT_PUBLIC_SUPABASE_URL` format
- Check `NEXT_PUBLIC_SUPABASE_ANON_KEY` is copied correctly
- Ensure CORS is enabled in Supabase project settings

### 3D Scene Not Rendering

- Check browser WebGL support
- Clear browser cache and restart dev server
- Verify Three.js dependencies are installed

### Build Fails

```bash
# Clear Next.js cache
rm -rf .next
npm run build
```

## Contributing

Contributions welcome! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

For issues, questions, or suggestions:

- Open an issue on [GitHub](https://github.com/saira-zaman/3D-clo-website)
- Email: support@example.com

## Acknowledgments

- Design inspiration: CLO Virtual Fashion
- Icons: Lucide React
- UI Components: Tailwind CSS
- 3D Graphics: React Three Fiber & Three.js
- Backend: Supabase
- Deployment: Vercel

---

**Built with ❤️ by Saira Zaman**

**Last Updated:** May 26, 2026
