# Family Tree

Laravel application for managing family trees (genealogy: people and their relationships).

## Stack

- PHP 8.3+ (local: 8.4 via Herd Lite), Laravel 13
- Database: SQLite by default (`database/database.sqlite`), configured in `.env`
- Frontend: Blade + Vite 8 + Tailwind CSS 4 (`@tailwindcss/vite`)
- Tests: PHPUnit 12 (`tests/Feature`, `tests/Unit`)
- Code style: Laravel Pint

## Commands

```sh
composer setup          # first-time setup: install deps, .env, key, migrate, build assets
composer dev            # run dev server + Vite + queue + logs together
php artisan serve       # app server only (http://127.0.0.1:8000)
npm run dev             # Vite dev server only
npm run build           # production asset build

composer test           # run full test suite
php artisan test --filter=SomeTest   # run a single test

vendor/bin/pint         # format PHP code
vendor/bin/pint --test  # check formatting without changing files

php artisan migrate     # run migrations
php artisan migrate:fresh --seed   # rebuild DB from scratch with seeders
```

## Conventions

- Follow standard Laravel structure: models in `app/Models`, controllers in `app/Http/Controllers`, routes in `routes/web.php`, views in `resources/views`.
- Generate files with `php artisan make:*` (e.g. `make:model Person -mfc`) instead of creating them by hand.
- Every schema change goes through a new migration; never edit a migration that has already been run on a shared database.
- Validate request input with Form Request classes (`make:request`).
- Use Eloquent relationships for family links (parents, children, spouses) rather than raw queries.
- Add or update a Feature test for every new route or behavior change.
- Run `vendor/bin/pint` and `composer test` before committing.

## Notes

- `.env` and `database/*.sqlite` are git-ignored; copy `.env.example` for a fresh setup.
- `AGENTS.md` is the Laravel skeleton bootstrap file for other agents; this file is the source of truth for Claude Code.
