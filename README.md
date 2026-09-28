<p align="center">
  <b>Ilham Maulana</b><br />
  <code>mxxham</code>
</p>

<p align="center">
  <b>Software engineer building warehouse, inventory and logistics systems.</b><br />
  <sub>How a specific unit of stock gets picked, from which bin, for which shipment.</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/Next.js-15-000000?logo=next.js&logoColor=white" alt="Next.js" />
  <img src="https://img.shields.io/badge/NestJS-E0234E?logo=nestjs&logoColor=white" alt="NestJS" />
  <img src="https://img.shields.io/badge/Supabase-3FCF8E?logo=supabase&logoColor=white" alt="Supabase" />
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white" alt="PostgreSQL" />
  <img src="https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/PHP-777BB4?logo=php&logoColor=white" alt="PHP" />
  <img src="https://img.shields.io/badge/Kotlin-7F52FF?logo=kotlin&logoColor=white" alt="Kotlin" />
</p>

<p align="center">
  <a href="https://github.com/mxxham/WMS"><img src="https://img.shields.io/badge/Featured-WMS%20%C2%B7%20CKB%20Warehouse-blueviolet" alt="Featured project" /></a>
  <img src="https://img.shields.io/badge/Location-Indonesia-red?style=flat-square" alt="Indonesia" />
</p>

---

## What I work on

Most of what I build sits in the gap between a spreadsheet and a warehouse floor: **allocation rules, stock accuracy, and the audit trail that proves the stock is where the system says it is.**

The recurring problem is FEFO. A lubricant warehouse stores several thousand bins of a few hundred SKUs, and nearly every unit has a batch and an expiry date. Picking the wrong unit is not a cosmetic bug — it is product that gets written off. So the allocation has to be **deterministic, tie-broken consistently, and safe to re-plan** when reality on the floor disagrees with the plan.

That constraint is what shapes most of my work: prefer an auditable, boring, verifiable design over a clever one.

---

## Featured — WMS · CKB Warehouse

Built for **PT Cipta Krida Bahari · WSM SUB 2, Surabaya**, operating a Shell lubricant warehouse.

One application, one database, one stock ledger — **2,570 bins · 106 SKUs · 1,790 stock rows** in a single reconciled ledger.

| 🏷️ Bin labelling | 📱 Scanning | 🧊 3D stock | 🧠 FEFO allocation | 🌊 Waves |
|---|---|---|---|---|
| Location labels in 5 strip sizes (80×85 mm), QR + Code 128, generated as vectors | Camera or USB scanner, auto-focus and Enter to advance | All 2,570 bins in one draw call, rendered on demand | Reservation, deterministic tie-break, and a safe re-plan when the floor disagrees | Idempotent posting into an append-only `movements` ledger |

Alongside the core allocation loop it also covers the parts that decide whether a warehouse can be trusted: **rack audits, blind pick audits, and shipment acceptance with stock correction** — the loop that closes when a physical count contradicts the plan.

**Stack:** Next.js 15 · TypeScript 5 · Supabase (Postgres) · Tailwind · Radix UI · three.js + React Three Fiber · `bwip-js` · `html5-qrcode` · `exceljs` / `xlsx` · `jspdf`

→ [`mxxham/WMS`](https://github.com/mxxham/WMS)

---

## Also built

| Project | What it is |
|---|---|
| [`k-one-v2`](https://github.com/mxxham/k-one-v2) | The same warehouse problem rebuilt on **NestJS + TypeScript + PostgreSQL 16 + Redis 7**, with a BullMQ worker, React + Vite frontend, and Jest/Supertest + Vitest coverage. Ported from the PHP original, then extended with department-based roles, stock hold/quarantine, and wave planning. |
| [`visionguard-ai`](https://github.com/mxxham/visionguard-ai) | **Warehouse pest detection** — a real-time dashboard over CCTV and webcam streams, running **YOLOv8-nano** behind a **FastAPI** service with WebSockets, PostgreSQL, React 18 and Recharts. |
| [`finance-tracker`](https://github.com/mxxham/finance-tracker) | **FinTrack** — full-stack personal finance app (Next.js 15, PostgreSQL, JWT auth) with transactions, budgets and charts. <sub>[live demo](https://finance-tracker-indol-pi-64.vercel.app)</sub> |
| [`k-one`](https://github.com/mxxham/k-one) · [`allocator_app`](https://github.com/mxxham/allocator_app) | The earlier **PHP / MySQL** generations of the warehouse system — the version `k-one-v2` was ported from. |
| [`E2EE_Apps`](https://github.com/mxxham/E2EE_Apps) | **Kotlin / Android** client for an end-to-end encrypted messaging project. |
| [`Assignment-Software-Engineer`](https://github.com/mxxham/Assignment-Software-Engineer) | A large TypeScript codebase — see the repo for its own documentation. |

---

## How I work

- **The ledger is the source of truth.** If it isn't in `movements`, it didn't happen.
- **Idempotent or it doesn't ship.** Re-running a posting must be safe, because it will be re-run.
- **Make the plan safe to abandon.** Re-planning has to be a supported operation, not an emergency.
- **Verify against the physical world.** Blind audits exist because a system's confidence is not evidence.

---

<p align="center">
  <sub>Built with Next.js, TypeScript, Supabase and Postgres — <code>mxxham</code></sub>
</p>
