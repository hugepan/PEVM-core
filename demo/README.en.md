# Demos

All demonstrations are organized in four layers and one benchmark:

> **Generation parameters** (models, temperature, seed policy): [GENERATION_METADATA.md](GENERATION_METADATA.md)

---

## A — Evidence

| Directory | Content | Language |
|-----------|---------|----------|
| [A1-controlled-experiment](A1-controlled-experiment/) | 3×4 comparison: with card vs without, across 2 LLMs × 3 questions | EN + ZH |
| [A2-consistency](A2-consistency/) | Same card × same question × 3 runs: directional consistency verified | EN + ZH |
| [A3-state-modifiers](A3-state-modifiers/) | State modifier tests: heavy cold / 20% power / consultant mode | EN + ZH |

## B — Protocol

| Directory | Content | Language |
|-----------|---------|----------|
| [B1-gallery](B1-gallery/) | 28 cards answer the same question: "Where should your AI live?" | EN + ZH |
| [B1.5-q9-sparks](B1-gallery/B1.5_q9_sparks.en.md) | 20 golden quotes from Qwen3.5-9B — cross-domain, structured-card-powered | EN + ZH |
| [B2-interaction](B2-interaction/) | Touch (first impressions), talkto, and 3 council debates | EN + ZH |
| [B3-fuse-group](B3-fuse-group/) | Same 3 source cards → fuse vs group: structural comparison | EN + ZH |
| [B4-split-timeline](B4-split-timeline/) | Personality split (Li Bai → 5) + timeline (Jobs → 5 stages) | EN + ZH |

## B5 — Round-trip: Split → Fuse Fidelity

| Directory | Content | Language |
|-----------|---------|----------|
| [B5-roundtrip](B5-roundtrip/) | Split Jobs → fuse back → compare with original | EN + ZH |

## B6 — Benchmarking

| Directory | Content | Language |
|-----------|---------|----------|
| [B6-benchmark](B6-benchmark/) | SESS vs memory, ONTLG vs Palantir, training data, PEVM vs Verbalized Sampling | EN + ZH |

## C — System

| Directory | Content | Language |
|-----------|---------|----------|
| [C1-architecture](C1-architecture/) | Four-layer architecture overview | EN + ZH |
| [C2-lifecycle](C2-lifecycle/) | Entity lifecycle: OS-inspired card management | EN + ZH |

## D — Vision

| Directory | Content | Language |
|-----------|---------|----------|
| [D-vision](D-vision/) | AI-native Linux protocol layer: direction + working prototypes | EN + ZH |
