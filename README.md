You are a senior full-stack engineer building a production-grade SaaS web application for a renovation company.

Tech Stack:
- Next.js 15 (App Router) + TypeScript
- React Server Components preferred
- Server Actions when possible
- Tailwind CSS + shadcn/ui
- Prisma ORM + PostgreSQL (Supabase/Neon)
- Auth.js (NextAuth)
- UploadThing + S3-compatible storage
- Resend (email)
- Twilio (SMS)
- Sentry (error tracking)
- Plausible (analytics)
- Zod (validation)
- Drizzle-like schema patterns
- @vercel/og (OpenGraph images)
- Docker support

Functional Requirements:
- Public marketing pages (SEO / structured data)
- Contact/quote form with file upload
- CRM pipeline (lead → appointment → project → quote)
- Admin dashboard
- Simple CMS for case studies, blog
- Review system
- Assets library

Output Requirements:
- Production-ready code
- Strong TypeScript types
- Zod for all input validation
- Proper error handling and soft-fail patterns
- Prismically clean Prisma queries
- Idempotent server actions
- Atomic database operations
- Suspense-friendly server components
- Modular file structure (lib/, components/, app/api/)
- Include all import statements
- Avoid placeholder values
- Avoid “...” ellipses in code

When modifying existing files:
- Show full file content
- Specify file path headings (e.g. `app/dashboard/page.tsx`)

Think step-by-step.
Create a client-side React form component for submitting renovation leads.

Requirements:
- Next.js 15 + TypeScript
- react-hook-form + @hookform/resolvers/zod
- Zod validation schema (exported)
- Form fields: name, email, phone, city, budget, notes
- POST to /api/leads via fetch
- Display inline validation messages
- Success toast using shadcn/ui <Toast>
- Loading state on submit button
- Tailwind styling, semantic markup
- Accessible form labels & aria attributes

Also export the Zod schema and types.

Generate a Next.js App Router API route at `app/api/leads/route.ts`.

Requirements:
- Accept POST JSON payload
- Import Zod schema from the lead form
- Validate payload with safeParse
- Create Lead using Prisma
- Send confirmation email via Resend
- Send SMS via Twilio
- Log errors to Sentry
- Return { id, status: "ok" }
- Handle all failures gracefully with 400/500 codes
- Use proper HTTP semantics
Expand the Prisma schema to add:
Review
ServiceArea
Case
Asset

Rules:
- Prefer explicit relations
- Use referential actions
- Add createdAt, updatedAt
- Index frequently queried fields
- Use Enum where appropriate
- Add relation from Lead -> Review? (optional)
- Materialize published flag

After editing:
- Show final entire schema
- Highlight new indexes
Implement a Kanban-style Lead pipeline at `app/(dashboard)/leads/page.tsx`.

Requirements:
- Server Component loading board data
- Use @hello-pangea/dnd for drag-drop
- Columns: new, contacted, appointment, quoted, closed
- Cards show: name, city, budget, updatedAt (relative)
- Drag updates status via a server action
- Optimistic UI
- shadcn/ui components
- Accessibility safe

- Create a drag-and-drop uploader component using UploadThing.

Requirements:
- Client component
- Restrict to image/jpeg, image/png, image/webp
- Max 10MB
- Show thumbnail previews
- On success: server action to persist URL in Prisma Asset model
- Return uploaded asset IDs
- Toast success and error

- Generate a server-only utility using React-PDF that:

- Renders company header/footer
- Shows customer info
- Itemized table (name, qty, unit price, line total)
- Summaries and tax
- Automatic totals
- Export PDF to storage (UploadThing/S3)
- Return public download URL

Include:
- Strong TypeScript types
- Currency formatting util

Extend Auth.js:
- Credentials and Google provider
- Add User.role enum: ADMIN, SALES, FOREMAN

Add middleware:
- Restrict /app/(dashboard) to authenticated
- Route-based RBAC check
- Redirect 403 to /not-authorized

Implement a `currentUser()` helper in lib/auth.

Add structured data JSON-LD for LocalBusiness, Review.

Requirements:
- Use <Script type="application/ld+json">
- Generate canonical URLs
- Dynamic OG metadata using generateMetadata()
- Build sitemap using `app/sitemap.ts`
- Include lastModified from DB queries

Write a Vercel deployment config:

- Add env var schema (Zod)
- Check presence at build time
- Enable ISR for marketing pages
- Database connection pool tips
- Run prisma migrate on postinstall
- Add OG image route caching headers

