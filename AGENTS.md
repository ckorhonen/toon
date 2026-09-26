# TOON development guide

`packages/toon/` contains the encoder/decoder; `packages/cli/` contains command-line conversion; `docs/` is VitePress; `benchmarks/` contains token and provider accuracy experiments. Read `SPEC.md`, the relevant package README and adjacent tests before changing format behavior. Preserve lossless round trips and streaming/error contracts.

Use Node 24 as in `.github/workflows/ci.yml` and the pinned `pnpm@10.33.4`. From the root run `pnpm install --frozen-lockfile`. CI gates are `pnpm lint`, `pnpm test:types`, and `pnpm test`; for a bounded non-watch run use `pnpm --filter @toon-format/toon test --run` or the CLI package equivalent. `pnpm build` builds package outputs. Use `pnpm docs:dev` and `pnpm docs:build` for documentation work; the CLI package has its own `dev` script.

Do not regenerate unrelated `automd` content. Benchmark accuracy runs load provider configuration and make external calls; release/deploy workflows publish artifacts. Keep those effects separate from parser tests and within explicit authorization.

## Completing work

Follow the nearest repository instructions and existing patterns; preserve unrelated edits. Make routine reversible choices within the request and continue through implementation, relevant checks, and repair of failures caused by the change. Ask only for material product decisions, missing prerequisites, or actions outside the authorization. Deployment, publishing, credentials, destructive operations, and live external effects need authorization for that scope.

Choose checks for the affected behavior and existing required gates; do not broaden into unrelated cleanup. For instruction-only edits, inspect source references and run `git diff --check -- AGENTS.md` (include any other changed instruction paths). Report changed paths, actual check results, and unverified runtime behavior. If blocked, give the exact failed command or missing prerequisite, separate baseline failures, and continue independent authorized work.
