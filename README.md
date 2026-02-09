# Auto Soccer Gacha (Unity + Supabase)

## Core idea
A solo-dev-friendly soccer gacha game where matches are simulated via possessions (like turns).
The match engine is pure C# and deterministic (seeded RNG).

## Non-negotiables
- MVP is 5v5 or 7v7, 3-zone field model
- No physics-based FIFA simulation in MVP
- Match engine must be pure C# (no Unity dependencies)
- Deterministic with seed for reproducibility/testing

## AI agent workflow rules
- Any change to gameplay logic must update:
  - docs/MatchEngineSpec.md and docs/GDD.md
- Any backend change must update:
  - docs/APIContract.md and backend migrations/policies
- Keep code small and shippable. Avoid “perfect architecture”.

## Milestones
1. Console-run match sim + tests
2. Unity UI loop (offline)
3. Gacha + progression (offline)
4. Supabase auth + save + server-side gacha roll
