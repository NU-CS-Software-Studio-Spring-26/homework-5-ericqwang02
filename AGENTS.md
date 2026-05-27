# Project context

CS 397 homework: a **Todo** CRUD app built with **Ruby 3.4.1** and **Rails 8.1**.

## Stack

- **Backend:** Rails 8 (MVC), Active Record, SQLite3 (`storage/*.sqlite3`)
- **Server:** Puma (`bin/rails server` or `bin/dev`)
- **Views:** ERB in `app/views/`; JSON via Jbuilder where present
- **Frontend:** Hotwire (Turbo + Stimulus), JavaScript via importmap (`config/importmap.rb`, `app/javascript/`)
- **Assets:** Propshaft; CSS in `app/assets/stylesheets/application.css`
- **Background/cache:** Solid Queue, Solid Cache, Solid Cable (no Redis required locally)
- **Tests:** Minitest in `test/` (unit, controller, system with Capybara/Selenium)

## Commands

- Setup: `bin/setup`
- Run server: `bin/dev` or `bin/rails server`
- DB: `bin/rails db:prepare`, migrations via `bin/rails db:migrate`
- Tests: `bin/rails test` and `bin/rails test:system` (CI runs `bin/rails db:test:prepare test test:system`)
- Lint: `bin/rubocop`
- Security: `bin/brakeman`, `bin/importmap audit`

## Conventions

- Follow standard Rails layout: models in `app/models/`, controllers in `app/controllers/`, views in `app/views/`.
- Prefer migrations + `db/schema.rb` over hand-editing the schema.
- Match existing RuboCop Rails Omakase style; keep changes minimal and focused.
- Do not commit secrets: `.env`, `config/master.key`, `.kamal/secrets`.
- No Node/npm unless explicitly added; use importmap for JS dependencies.

## Don'ts

- No new gems without explicit approval.
- No `skip_before_action :verify_authenticity_token` or global CSRF disables.
- No secrets in repo: `.env`, `master.key`, credentials keys, Kamal secrets.
- No hand-editing `db/schema.rb`; use migrations only.
- No switching DB (Postgres) or adding Redis without approval; stay on SQLite + Solid*.
