# Dance To The Beat — Website Project

Premium marketing/lead-generation website for **Dance To The Beat**, an Indian semi-classical dance academy led by Shatabdi Banerjee ("Move to Express, Dance to Inspire"). Built with Next.js 16 (App Router), TypeScript, Tailwind CSS v4, Framer Motion, React Hook Form, and Zod; deployed on Netlify.

This repository is organized as a phase-based documentation set (00–07) followed by the actual application (08-source-code). Each numbered folder is a complete, self-contained deliverable — later folders depend on earlier ones as source of truth and do not redefine decisions already made upstream.

---

## Project Goal

Increase student admissions (offline and online) by building trust through the teacher's expertise, showcasing student work, and driving every visitor toward one action: **Book a Free Trial Class**.

## Tech Stack

**Framework & Runtime**
- **Next.js 16.2.10** (App Router, Turbopack) — Server Components by default, static prerendering
- **React 19.2.4** / **React DOM 19.2.4**
- **TypeScript 5** — strict mode

**Styling & Design**
- **Tailwind CSS v4** (via `@tailwindcss/postcss`) — theme tokens (colors, spacing, shadows, type scale) extended in `globals.css`
- **Google Fonts** via `next/font` — Playfair Display, Cormorant Garamond, Yatra One, Poppins

**Animation**
- **Framer Motion** `^12.42.2` — page/section reveals, the loading-screen rotation, mobile menu, carousels

**Forms & Validation**
- **React Hook Form** `^7.81.0` + **Zod** `^4.4.3` + **@hookform/resolvers** `^5.4.0` — Admission Enquiry and Contact forms

**Icons**
- **Lucide React** `^1.23.0` — UI icons (this version dropped brand/logo icons, so Instagram/Facebook/YouTube glyphs were hand-built as inline SVGs)

**Tooling**
- **ESLint 9** (`eslint-config-next`)
- **npm** — package manager

**Hosting & Deployment**
- **Netlify** — via `@netlify/plugin-nextjs`, configured through `netlify.toml` (base directory `08-source-code`)
- **GitHub** — version control, connected to Netlify for CI deploys

Not in the stack: no CMS, no analytics, no backend/database — the site is fully static/server-rendered with no persistence layer, and form submissions are currently client-side only (no email/CRM integration wired up yet).

*Verified directly against `08-source-code/package.json`, `netlify.toml`, and the installed `lucide-react` package.*

Hostinger (shared hosting) was evaluated and rejected — it lacks the Node.js/SSR support this stack requires. (The original architecture docs that first justified this decision were removed from `06_Development` during the build phase — see the note under Folder Structure. The Netlify setup itself is documented fresh in `07_Deployment/netlify-deployment.md`.)

---

## Folder Structure

```
Dance-Academy-Website/
│
├── 00_Project_Management/
│   └── project-spec.json
│
├── 01_Branding/
│   ├── brand-guidelines.md
│   ├── design-system.md
│   ├── ui-spec.md
│   ├── theme.json
│   └── design-tokens.json
│
├── 02_Information_Architecture/
│   ├── information-architecture.md
│   ├── sitemap.md
│   ├── navigation-spec.md
│   ├── user-flows.md
│   ├── page-specifications.md
│   └── content-structure.md
│
├── 03_Wireframes/
│   ├── wireframes.md
│   ├── homepage-wireframe.md
│   ├── about-wireframe.md
│   ├── dance-styles-wireframe.md
│   ├── gallery-wireframe.md
│   ├── admission-wireframe.md
│   ├── contact-wireframe.md
│   └── responsive-layouts.md
│
├── 04_UI_Components/
│   ├── component-library.md
│   ├── button-spec.md
│   ├── card-spec.md
│   ├── form-spec.md
│   ├── gallery-spec.md
│   ├── testimonial-spec.md
│   ├── faq-spec.md
│   ├── footer-spec.md
│   └── animation-spec.md
│
├── 05_Assets/
│   ├── Logo/            (Logo.png, name.png)
│   ├── Teacher/
│   ├── Hero/
│   ├── Gallery/
│   ├── Videos/
│   ├── Testimonials/
│   ├── Certificates/
│   ├── Backgrounds/
│   ├── Icons/
│   ├── Loading/          (Loading Screen.png)
│   └── Documents/
│
├── 06_Development/
│   └── performance-strategy.md
│
├── 07_Deployment/
│   ├── netlify-deployment.md
│   ├── deployment-checklist.md
│   └── release-notes.md
│
├── 08-source-code/
│   └── (Next.js 16 application — built and live)
│
├── netlify.toml
├── README.md
└── LICENSE
```

> **Note:** `05_Content` (page copy) and most of `06_Development` were removed from the working tree during the build phase and are not currently tracked. `07_Deployment`'s original files (`github-guide.md`, `vercel-deployment.md`, `deployment-checklist.md`, `qa-checklist.md`, `release-notes.md`) were similarly lost, but the folder has since been repopulated with fresh, accurate documentation reflecting the actual Netlify-based deployment. `04_UI_Components` is also missing its original `hero-spec.md`, `navbar-spec.md`, `loading-screen-spec.md`, and `iconography-spec.md` files. The folder numbering above reflects what's actually on disk today, not the original 00–09 plan.

---

## What's In Each Folder

| Folder | Contents | Status |
|---|---|---|
| `00_Project_Management` | The single structured source of truth for business requirements, contact info, tech stack, and scope (`project-spec.json`) | Complete |
| `01_Branding` | Brand personality, voice, visual tone, and the full design token system (colors, type, spacing, shadow, motion) | Complete |
| `02_Information_Architecture` | Site structure, navigation, user flows, per-page content hierarchy, and the empty-state rules governing all TBD content | Complete |
| `03_Wireframes` | ASCII wireframes for all 6 primary pages plus responsive behavior rules | Complete |
| `04_UI_Components` | Behavioral/accessibility/animation spec for the surviving reusable UI components | Partial — 4 spec files removed (see note above) |
| `05_Assets` | Media files — logo (received), loading screen art (received), teacher photos, gallery, videos, testimonials, certificates, icons, backgrounds | Mostly TBD — only Logo and Loading Screen assets received |
| `06_Development` | Technical architecture docs | Partial — only `performance-strategy.md` survives |
| `07_Deployment` | Netlify deployment guide (setup + incident log), pre-launch checklist, release notes | Complete — rewritten to reflect the actual Netlify setup |
| `08-source-code` | The actual Next.js application | Built and live — Next.js 16, TypeScript, Tailwind v4, deployed via Netlify |

## Documentation Principles

- **No fabrication.** Any content or asset not yet supplied (gallery images, testimonials, teacher photos, awards, social handles) has a defined, honest empty state — never a placeholder, stock substitute, or invented fact. See `02_Information_Architecture/content-structure.md §2`.
- **Single source of truth per concern.** Business facts live only in `project-spec.json`; visual tokens live only in `design-tokens.json`/`theme.json`; every other document references these rather than restating or redeciding them.
- **Documentation before code.** Phases 00–07 were completed and cross-verified before any application code was written in `08-source-code`.

## Known Open Items

- **Form submissions have no backend.** Admission Enquiry and Contact forms validate and show a confirmation panel, but nothing is actually sent or stored — no email/CRM integration is wired up yet. This is the most significant gap before real launch; see `07_Deployment/deployment-checklist.md`.
- Teacher photos, gallery images, videos, testimonials, awards/certificates, event posters — all TBD (`project-spec.json → assets`)
- Domain registrar not yet selected; DNS not yet pointed to Netlify
- Admission Enquiry confirmation panel response-time (SLA) copy not yet confirmed (originally flagged in `05_Content/admission-copy.md`, since removed — implemented without a specific SLA claim, per the no-fabrication rule)
- Email/newsletter provider not yet selected — deferred by decision, not blocking
- Mission, Vision, Years of Experience, and Social Media sections are explicitly out of scope for this build (removed by decision)

Full pre-launch checklist: `07_Deployment/deployment-checklist.md`.

## Getting Started

```bash
cd 08-source-code
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000). The site is deployed via Netlify, building from the `08-source-code` base directory (see `netlify.toml`). Full deployment setup and troubleshooting history: `07_Deployment/netlify-deployment.md`.

## License

See `LICENSE`.