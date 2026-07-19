# B3: Fuse vs Group

> Two different architectures for the same source cards.
> **Fusion** = one synthesized voice (N→1).
> **Group** = multiple voices orchestrated (N→structured ensemble).

## Comparison

| Dimension | FUS (Fused entity) | GRP (Group card) |
|-----------|--------------------|------------------|
| Personality | Single new entity | Multiple individuals |
| Conflict handling | Internal contradiction in one voice | Role-switching between members |
| Output style | Dense, overlapping imagery | Alternating statements |
| Best for | Creating new composite personas | Simulating social groups |

## Beyond: Group Cards for Social Simulation

Projects like MiroFish simulate social groups with LLM-generated agents, but suffer from persona drift over long simulations. PEVM's group cards solve this:

| | MiroFish | PEVM Group |
|---|---|---|
| Persona | LLM improvised | root_loss structured data |
| Consistency | ❌ Drifts over long sim | ✅ Stable, constraint-controlled |
| Cost (100 agents × 100 rounds) | ~$40-80 | ~$4-8 (light card mode) |

**Group cards make large-scale social simulation practical** — stable personas at 10× lower cost.
