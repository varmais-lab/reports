# SumanTV Weekly Review System

Internal tool for weekly department revenue/expenditure review meetings.
Backend: Supabase project `sumantv-weekly-reports` (ap-south-1, Mumbai).

## Files
| File | Purpose |
|---|---|
| `index.html` | Landing page |
| `department-report.html` | Department heads submit weekly numbers (PIN-gated) |
| `admin-dashboard.html` | Management view: all 5 departments in one page (Admin PIN-gated) + live config (Maintenance %, PIN resets) |
| `style.css` | Shared styles |

## Departments
Women · Health · Devotion · News · Business

## How it works
1. Department head opens Submit Report, picks department, enters PIN.
   PINs are verified server-side in Supabase (bcrypt-hashed) — never stored in this code.
2. Weekly numbers save straight to the shared database. No files, no uploads.
3. Admin Dashboard reads the same database live — submissions appear instantly.
4. Admins change Maintenance % or reset department PINs from the dashboard directly.

## Calculations
- Revenue Total = YouTube + Facebook + Advertisement + Courses
- Maintenance Cost = Team Salaries × Maintenance % (fixed per department by Finance)
- Op-Ex Total = Team Salaries + Maintenance Cost
- P&L = Revenue Total − Op-Ex Total

## Deploy
Push these 4 files to the root of the `reports` GitHub Pages repo.
Delete from the repo if still present: `women.json`, `health.json`, `devotion.json`,
`news.json`, `business.json`, `config.json`, `sumantv-weekly-data-sample.json`,
`sumantv-weekly-review.html` (all obsolete — replaced by Supabase).

## PINs
Distributed separately (never commit PINs to this repo).
Forgot a department PIN? Reset it from the Admin Dashboard.
Forgot the Admin PIN? It can be re-hashed directly in Supabase SQL editor.
