# Wyw-Mono

## Summary
A monorepo (`apps/api` NestJS, `apps/devpath` Next.js, `apps/cli`,
`apps/inference`, `apps/mcp-server`, `apps/productivity`, `apps/server`, plus
a separate `webFE`) built as a verified-skill attestation engine — real
ingestion → classification → cryptographic proof pipeline. Its own audit
document describes it, in its own words, as "two systems that mostly don't
talk to each other."

## Key Points
- Real, verified, working: `revenue.service.ts` (Redis-backed windowed
  metering), `ollama-embedding.provider.ts` (calls Ollama over Tailscale —
  free local embeddings, not mocked), BullMQ processors
  (`career-mirror.processor.ts`, `observer.processor.ts`,
  `proof-generation.processor.ts`) — all confirmed present and real via
  direct file read, 2026-09-04.
- Real, verified gap: `eval.service.ts` line 52 returns
  `0.85 + Math.random() * 0.15` — the eval score is fabricated, not computed.
  RAGAS evaluation pipeline is genuinely not built (also listed in
  `CLAUDE.md`'s own Known Gaps).
- `apps/api` (NestJS, TypeORM, 175+ tests) and `apps/devpath` (the app that
  actually deploys) are two disconnected full-stack systems in one repo —
  `apps/devpath` writes to Postgres directly via raw queries, largely
  bypassing `apps/api`. Needs a canonical-system decision before more gets
  built on top of either.
- Last real commit verified: 2026-08-20 (`chore: untrack non-essential
  markdown, fix llm-proxy typecheck`) — a prior claim that it was "10 weeks
  stale, last commit June 22" was checked and is factually wrong.
- Auth story has a real, named security gap: SHA-256 password hashing with
  no salt, no work factor (per a prior architecture audit, not yet
  independently re-verified line-by-line by this entry).
- Product differentiator (goal-oriented workflow, evaluated on effort vs.
  value/revenue generated) has no system design written yet — PR-history
  ingestion is one evidence source for it, not the mechanism itself.
- Same employment-clause gate as [[Shashank GS]] applies here directly: any
  real GTM/sales motion (e.g. a staffing-agency pitch) is blocked until that
  clause is confirmed, since this is the repo with the actual commercial
  candidate product.

## Related
- [[Shashank GS]]
- [[ShadowAI]]
- [[Decisions]]

## Sources
- wyw-mono repo — apps/api/src/observer/revenue.service.ts,
  apps/api/src/vector/ollama-embedding.provider.ts,
  apps/api/src/observer/eval.service.ts — verified directly, 2026-09-04
- wyw-mono/CLAUDE.md
- founder-workspace/11_knowledge_platform_sprints/WYW_MONO_SELF_AUDIT.md
