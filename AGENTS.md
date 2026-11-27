# AGENTS.md

## Current state
- Stock Laravel 9 skeleton under XAMPP/Windows: `README.md` is boilerplate, `routes/web.php` only defines `/` → welcome, and there is no NotaSteam feature code, auth controllers/views, or master-data migration yet. Treat this as a starting skeleton, not an existing app.
- Product docs live in `agent/` (untracked), not `.agents/`: `agent/prd.md` (requirements/business rules), `agent/design.md` (Bootstrap 5 UI), `agent/task-instruction.md` (task workflow). `agent/readme.md` describes moving them to `.agents/` and adding a root `Dockerfile`; neither exists here. It also misspells `task-insturction.md` — use the actual filenames above.

## Before implementing features
- Read `agent/prd.md` and `agent/design.md` first (mandatory per `agent/task-instruction.md`). UI copy/messages are Indonesian; follow the design's Bootstrap 5.3.3 CDN approach. Bootstrap is not an npm dependency and `resources/css/app.css` is empty.
- If following that task workflow, update `.agents/tasklist.md` after each task/group: mark `[x] ✅`, add a short note of files changed, refresh `Progress: N%`, then report completion.
- The PRD leaves real ambiguities unresolved (KF-10, Kasir report access, duplicate-active-transaction rule, status labels, prices). Don't invent answers silently.

## Commands and environment
- Dev: `php artisan serve`. Assets: `npm run dev` / `npm run watch` (Mix compiles `resources/js/app.js` + `resources/css/app.css` into `public/`).
- Tests: `php artisan test` or `vendor/bin/phpunit`. No custom composer script or CI workflow; `.styleci.yml` uses the Laravel PHP 8 preset with `no_unused_imports` disabled.
- `phpunit.xml` leaves the sqlite env lines commented out, so DB-backed tests use `.env` MySQL. Local `.env` points to DB `NotaSteam`, user `root`, empty password (XAMPP); `.env.example` still says `laravel`. For isolated tests, set `DB_CONNECTION=sqlite` and `DB_DATABASE=:memory:` (or create `database/database.sqlite`) and run migrations.
- Stock migrations only create users, password_resets, failed_jobs, and personal_access_tokens.

## Auth/data gotchas
- Spec requires username/password login with Owner/Kasir roles, but the default `users` table and `App\Models\User` only have `name`, `email`, `password` and no role column. Add the needed migration/fillable fields; don't build email-based auth.
- `RouteServiceProvider::HOME` is still the skeleton value `/home`, but no `/home` route exists. Redirect by role after login instead.
- Browser pages go in `routes/web.php`; `routes/api.php` only exposes Sanctum `/user` behind a 60 req/min limiter. Don't assume a full API/auth scaffold exists.

## Domain invariants worth not breaking
- Reports and receipts count only Lunas transactions; digital/transfer payments need manual verification by Kasir; motor type comes from active master data and plate is required; there is no payment-gateway integration.
