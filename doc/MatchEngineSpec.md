# Match Engine Spec (Possession-based)

## Goals
- Deterministic simulation (seeded RNG)
- Explains outcomes via event log
- Minimal state: zones + possession + stamina + score

## Field model
- Zones: DEF, MID, ATT (for each team perspective)
- Ball position is a zone index from Team A’s perspective:
  - -1 = Team B ATT, 0 = MID, +1 = Team A ATT (or use enum)

## Possession flow
For each possession:
1) Decide action: PASS, DRIBBLE, SHOT
2) Resolve contest:
   - PASS: passer (pass) vs opponent intercept (defense)
   - DRIBBLE: dribbler (dribble) vs tackle (defense)
   - SHOT: shooter (shoot) vs goalie (goalie)
3) Apply traits (pre/post hooks)
4) Update zone/turnover/score/stamina
5) Log event with reasoning

## Stats (MVP)
- Pass, Dribble, Shoot, Defense, Goalie, StaminaMax
- CurrentStamina decreases slightly per possession involvement

## Trait system (MVP)
Traits are simple modifiers to:
- action selection weights
- stat multipliers in specific contexts
- clutch modifiers late match

## Output
MatchResult:
- ScoreA, ScoreB
- PossessionA/B counts
- ShotsA/B, ShotsOnTargetA/B
- SavesA/B
- EventLog (ordered)
- MVP (player id)
