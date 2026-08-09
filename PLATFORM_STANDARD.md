# Platform Standard — App

## Default platform

Chris's default application platform is:

- **Vercel** — application hosting, preview deployments, and production deployment surface.
- **Supabase** — backend/data platform, including PostgreSQL, authentication, storage, realtime, and server-side data services where the product needs them.

This is the default. Do not spend a new project's planning budget re-deciding hosting and backend from scratch.

## Deviation rule

Use a different hosting/backend platform only when a real product or technical requirement makes Vercel/Supabase unsuitable and the owner explicitly approves the deviation.

A preference for another library, agent familiarity, or speculative scale concern is not enough.

## Guardrails

- Never expose Supabase service-role or other privileged secrets to browser/client code.
- Browser-accessible Supabase data requires an explicit authorization model and appropriate Row Level Security (RLS) where applicable.
- Database/schema changes use durable migrations; do not hand-edit production state as the normal development method.
- Preview/test work must not silently mutate production data.
- Vercel environment variables are scoped deliberately by environment; secrets never belong in source control.
- Production deployment remains a controlled action. A successful preview/build does not authorize production release.
- Supabase features are used because the product needs them; do not add auth, realtime, storage, Edge Functions, or extra tables merely because the platform provides them.
- Keep business/domain rules testable outside provider-specific glue where practical so Vercel/Supabase integration does not become the entire architecture.

## Normal interpretation

For a new app, assume **Vercel + Supabase** unless the owner says otherwise. The intake should focus on what the product needs from that platform, not whether to replace it.