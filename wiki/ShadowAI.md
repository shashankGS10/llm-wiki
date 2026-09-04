# ShadowAI

## Summary
[[Shashank GS]]'s personal portfolio site — a job-search instrument aimed at
a hiring engineering manager, not a generic showcase. Started as a single
Next.js app; `origin/main` was rearchitected into a pnpm workspace with a
`backend/` (NestJS) + `frontend/` split on 2026-08-30 (commit `7fbf54f`).
That backend is currently a shallow scaffold — a health check and three
empty entities, no business logic.

## Key Points
- Design system is a closed vocabulary: exactly 10 color tokens, no
  gradients/shadows/border-radius, three named fonts. Enforced via
  `DESIGN_SYSTEM.md` and `CLAUDE.md`, not a suggestion.
- `lib/rag/*` — a RAG answer-generation module — is built and tested but
  wired to nothing live. `/chat` deliberately 404s; the page's own code
  comment says "There is no chat backend."
- **Live landmine, unresolved as of this entry:** PR #38
  (`claude/founder-market-fit-chapter-39pynk`) deletes `lib/rag/*` as "dead
  code" — true when that PR was written, but a later handoff calls that
  exact code the tested foundation for a planned track. The PR is currently
  `dirty` (can't merge by accident), but resolving that conflict without
  this context risks deleting live-planned work.
- Backend scaffold (post-rearchitecture): `backend/src` has `health/` plus
  three entities (User, Persona, Conversation) with hand-written migrations
  — no live DB has ever been connected in any verified build environment.
  Commit message itself flags it unfinished (Vercel root-directory setting
  not yet updated, would 404 on deploy as-is).
- Two incompatible auth stories exist at once: `next-auth`/`bcryptjs` still
  sit in `frontend/package.json` from the pre-rearchitecture plan, while the
  backend has zero real auth implemented.
- `data/profile.private.ts` is git-tracked and contains real salary figures
  and negotiation strategy — repo privacy is the only thing protecting it;
  going public requires purging it from git history, not just `HEAD`.
- Zero live users by product design — it's a resume a stranger reads, not a
  product a stranger uses.

## Related
- [[Shashank GS]]
- [[Wyw-Mono]]
- [[Decisions]]

## Sources
- shadowai/CLAUDE.md
- shadowai/GAPS.md
- shadowai git log (origin/main, commit 7fbf54f) — verified directly, 2026-09-04
- PR #38 diff — verified directly via GitHub, 2026-09-04
