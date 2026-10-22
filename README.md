# Naskah

Local UI for drafting and reviewing IEEE 830-1998 software requirements.
Indonesian by default, with English and separately designed light/dark themes.

Windows PowerShell:
```powershell
pnpm install
pnpm dev
# Open http://127.0.0.1:3000
```

Production:
```powershell
pnpm build
pnpm start
```

The initial ledger includes three clearly simulated example projects. Reset in
Settings to see the first-use empty state. Local project data lives in IndexedDB;
preferences use localStorage and the intake draft uses sessionStorage. This is
device/browser-local storage, not a shared account or a backup.

Implemented screens: project ledger, multi-source intake, chapter generation,
manuscript workspace, inline Markdown editing, isolated revision proposals and
word-level diffs, section approval, version history, finalization, Word export,
print-to-PDF, research summary, blind review, SUS, ROUGE import, and settings.

The mock generation engine uses deterministic Indonesian fixtures. It does not
understand arbitrary descriptions or call an LLM. The title and domain select
the representative example; revision examples for 2FA/AES-256, QRIS and audit
trails are handwritten. Other instructions become an explicitly marked clause.
Reference chunks and quality checks are simulated. Word compilation, PDF text
extraction, editing, persistence, SUS calculations, and print output are real.

Mock mode is the default. For Phase 2 copy `.env.example` to
`apps/web/.env.local`. Server secrets must never receive a `NEXT_PUBLIC_` prefix.
Live adapters are intentionally unavailable and surface a friendly error.
See [backend roadmap](docs/backend-roadmap.md).

Commands:
```powershell
pnpm typecheck
pnpm lint
pnpm test
pnpm build
pnpm audit:slop
pnpm check:contrast
pnpm test:e2e
```

E2E uses an installed Chrome by default. Set `PLAYWRIGHT_CHANNEL=msedge` for
Edge, or install Playwright Chromium and set `PLAYWRIGHT_CHANNEL=chromium`.
Run the app on port 3000 first. Screenshots are written to `docs/screenshots/`.
Developer controls are available in development, or when explicitly enabled
with `NEXT_PUBLIC_ENABLE_DEVTOOLS=true`. Production does not expose them by default.

See [design plan](docs/design-plan.md), [architecture](docs/architecture.md),
[traceability](docs/traceability.md), and [phase report](docs/phase-report.md).

Nothing in `infra`, `supabase`, `n8n`, `ingestion`, or `compiler-service` is run
by the UI. These are inert integration scaffolds. No Docker or database setup
is required to run Phase 1.
