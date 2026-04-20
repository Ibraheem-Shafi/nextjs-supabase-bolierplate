# Next.js Boilerplate Supabase Connection

Boilerplate with both client-side and server-side Supabase setup for Next.js App Router, aligned with RLS-first best practices.

## Included

- Browser Supabase client for auth/UI data (`lib/supabase/client.ts`)
- Server Supabase client for route handlers/server components (`lib/supabase/server.ts`)
- Optional admin client pattern (service role, server-only) (`lib/supabase/server.ts`)
- Environment validation helpers (`lib/supabase/env.ts`)
- Demo client usage (`components/supabase-client-status.tsx`)
- Demo server route (`app/api/supabase/server-check/route.ts`)

## Environment Variables

1. Copy `.env.example` to `.env.local`
2. Fill in values from your Supabase project:

```bash
NEXT_PUBLIC_SUPABASE_URL=...
NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY=...
SUPABASE_SERVICE_ROLE_KEY=...
```

Legacy compatibility:
- `NEXT_PUBLIC_SUPABASE_ANON_KEY` is also accepted if you use older Supabase naming.

Security notes:
- `NEXT_PUBLIC_*` values are safe for the browser.
- `SUPABASE_SERVICE_ROLE_KEY` must stay server-only.
- Never use service role key in client components.

## Run

```bash
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

## Boilerplate Usage

- Server-side check in page render uses `getSupabaseServerClient()`.
- Client-side check button uses `getSupabaseBrowserClient()`.
- API route check endpoint: `GET /api/supabase/server-check`.

## Best Practice Direction

- Keep business logic and external API calls on server routes/actions.
- Use browser Supabase client only for UI/auth/simple CRUD.
- Enforce authorization in Supabase RLS policies, not in frontend checks.
