# حاسباتي - موقع حاسبات متنوع

موقع ويب عربي متعدد الحاسبات يتيح للمستخدمين إجراء حسابات يومية متعلقة بالعمر، حقوق العمال، الحمل، والضريبة.

## Run & Operate

- `pnpm --filter @workspace/calculators run dev` — run the frontend (port assigned by workflow)
- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9
- Frontend: React + Vite + Tailwind CSS + shadcn/ui
- Font: Tajawal (Arabic Google Font)
- Routing: Wouter
- Forms: react-hook-form + zod
- API: Express 5 (for future backend features)
- DB: PostgreSQL + Drizzle ORM (provisioned when needed)

## Where things live

- `artifacts/calculators/` — React frontend (all 5 calculators)
- `artifacts/calculators/src/pages/` — one file per calculator page
- `artifacts/calculators/src/components/layout/` — shared navbar
- `artifacts/api-server/` — Express API server
- `lib/api-spec/openapi.yaml` — API contract source of truth

## Calculators (MVP)

1. **حاسبة العمر** (`/age`) — Real-time age calculator (years, months, weeks, days, live seconds ticker)
2. **نهاية الخدمة** (`/eos`) — End-of-service reward calculator with resignation rules
3. **الإجازة السنوية** (`/leave`) — Annual leave entitlement & financial compensation calculator
4. **حاسبة الحمل** (`/pregnancy`) — Pregnancy due date & gestational age calculator
5. **ضريبة القيمة المضافة** (`/vat`) — VAT calculator (inclusive/exclusive)

## Architecture decisions

- Frontend-only for MVP: all calculator logic is pure client-side TypeScript — no backend needed
- Arabic RTL throughout: `dir="rtl"` set on `<html>` element, Tajawal font
- All calculations match the original HTML files' logic exactly
- Results are hidden until user clicks calculate, revealed with framer-motion animation

## User preferences

- Arabic language interface (RTL)
- MVP approach — iterative development
- Uses the provided HTML files as functional reference for all calculation logic

## Gotchas

- Google Fonts @import must be the FIRST line in index.css (before @import "tailwindcss")
- setInterval in age calculator must be cleared before starting a new one
- toLocaleString('ar-EG') for Arabic number formatting
