# prompts-for-codex.md — English Prompt Pack for Codex / Copilot

> Use these prompts inside your VSCode, Cursor, or GitHub Copilot chat to generate and refine code for your **Next.js + Prisma Renovation Company App** (方案 A).  Each prompt is designed to produce production-grade, type-safe code.

---

## 🧱 1. Project-Level Prompt

```markdown
You are building a full-stack web application for a small renovation company.
The tech stack is:
- Next.js 15 (App Router) + TypeScript
- Tailwind CSS + shadcn/ui
- Prisma ORM + PostgreSQL (Supabase/Neon)
- Auth.js (NextAuth) for authentication
- UploadThing + S3-compatible storage (R2/Supabase)
- Resend (email) + Twilio (SMS)
- Sentry for error tracking, Plausible for analytics

The app includes:
- Marketing pages (SEO-friendly service, area, and case pages)
- Contact/quote request form with file upload
- Admin dashboard (leads, projects, estimates, assets, reviews)
- CRM-style pipeline (lead → appointment → project → quote)
- Simple CMS for cases and blog posts

Always write clean, production-ready code with:
- Strong typing (TypeScript)
- Zod validation for API inputs
- Prisma for DB access
- React server components and server actions when possible
- Modular structure (lib/, components/, app/api/, etc.)
```

---

## ⚙️ 2. Component Prompt

```text
Create a React client component using Next.js and TypeScript that implements a form for submitting renovation leads.
Use react-hook-form with zod validation, Tailwind classes for styling, and POST the data to /api/leads.
Include inline validation messages and a success alert.
```

---

## 🧩 3. API Route Prompt

```text
Generate a Next.js App Router API route (/api/leads/route.ts) using Prisma ORM.
It should accept a POST request with lead data (name, email, phone, city, budget, notes),
validate using zod, create a new Lead in the database,
and send an email via Resend and an SMS via Twilio to confirm receipt.
Return a JSON response with the new lead ID.
```

---

## 🗂 4. Prisma Schema Expansion Prompt

```text
Expand the existing Prisma schema to include:
- Review model (customer reviews with rating, content, source, published flag)
- ServiceArea model (for SEO landing pages)
- Case model (for project showcase with cover image, duration, materials)
Make sure all relations are properly defined with referential integrity.
```

---

## 🧠 5. Admin Dashboard Prompt

```text
Implement an Admin Dashboard page (app/(dashboard)/leads/page.tsx)
that displays leads in a Kanban board layout by status.
Use shadcn/ui components and @hello-pangea/dnd for drag-and-drop between columns.
Each card should show name, city, budget, and last update time.
```

---

## 📤 6. File Upload Prompt

```text
Create a file upload component using UploadThing with drag-and-drop support.
Limit uploads to 10MB images (jpg, png, webp).
After upload, store the resulting URL in the database using Prisma.
```

---

## 🧾 7. PDF Quote Generator Prompt

```text
Generate a server-side utility that creates a project estimate PDF
using react-pdf or puppeteer. Include client info, itemized table (name, qty, unit price, total),
and company header/footer. Export a downloadable PDF link.
```

---

## 🧰 8. Auth + RBAC Prompt

```text
Integrate Auth.js (NextAuth) with credentials and Google provider.
Extend the User model with a 'role' field ('ADMIN', 'SALES', 'FOREMAN'),
and create a middleware to restrict access to /app/(dashboard) routes to authenticated users only.
```

---

## 🔍 9. SEO & Structured Data Prompt

```text
Add structured data (JSON-LD) for LocalBusiness and Reviews
on marketing pages using Next.js Script component.
Generate canonical URLs, OpenGraph metadata, and sitemaps automatically.
```

---

## 🚀 10. Deployment Prompt

```text
Write a Vercel deployment configuration for this Next.js app.
Use environment variables for database, email, SMS, and S3 keys.
Ensure Prisma migration runs on build and that static marketing pages are ISR-enabled.
```

---

## 💡 Bonus – Quick Codex Commands

> Use these short chat prompts for Copilot Chat / Cursor:

* “Generate a zod schema and form validation for the renovation lead form.”
* “Create a server action that inserts a new project and sends an email notification.”
* “Add drag-and-drop support to the leads Kanban view.”
* “Refactor this component to use shadcn/ui Card and Button components.”
* “Add proper TypeScript types for Prisma Project entity and related API routes.”

---

