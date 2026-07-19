---
layout: default
title: PEVM — Structured Persona Protocol for AI
---

# PEVM: Structured Persona Protocol for AI

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![GitHub Stars](https://img.shields.io/github/stars/hugepan/PEVM-core?style=social)](https://github.com/hugepan/PEVM-core)

Ask the same LLM to play Li Bai twice, and the prompt-only version drifts — one time a wandering poet, the next a generic philosopher. No structure. No consistency. No replicability.

**PEVM** gives you Li Bai every time. Not identical outputs — but outputs that are *deeply, insightfully aligned* with who Li Bai is. Same card, same soul, different flowers.

**This is the official PEVM whitepaper** — a structured persona protocol for AI, grounded in controlled experiments and documented across four layers: evidence, protocol, system, and vision.

> 🔥 **See it in action** — three most striking demos:
> - [Free Will debate: Entropy, Don Quixote, and Dante](demo/B2-interaction/council_自由意志.en.md)
> - [Industrial diagnosis: "four clocks" on a production line](demo/B6-benchmark/ontlg-demo/industrial-consulting.en.md)
> - [Xiao Ming family council: empire vs family](demo/B3-fuse-group/family-group-showcase.en.md)

### 📖 What's inside (3-minute tour)

| If you want... | Start here |
|----------------|-----------|
| The core claim in 3 minutes | [A1: 2×2 controlled experiment](demo/A1-controlled-experiment/README.en.md) — same Li Bai, with vs without card |
| The most counterintuitive result | [B1.5: q9 Sparks](demo/B1-gallery/B1.5_q9_sparks.en.md) — 9B model, no prompt engineering, philosopher-level density |
| Real philosophy, not roleplay | [B2: Free Will council](demo/B2-interaction/council_自由意志.en.md) — Entropy, Don Quixote, and Dante debate free will |
| Industrial use case | [B6: Production line diagnosis](demo/B6-benchmark/ontlg-demo/industrial-consulting.en.md) — four clocks, one bottleneck |
| The vision | [D: AI-native Linux](demo/D-vision/D-vision.en.md) — what if cards become files? |

---

## Why this exists

I'm a Tsinghua University graduate, now a K12 teacher covering every subject across all grades. PEVM started as a note-taking tool — an LLM + wiki for my classroom. I never expected it to become this.

PEVM originally stood for "Peter's Educational Virtual Meta-Kernel." It began as a classroom experiment and grew into the protocol described here. The name reflects both the origin (a teacher's tool) and the aspiration (a kernel-like layer between humans and AI).

---

## The four layers

### Layer A — Evidence: do cards actually change outputs?

Prompt-based roleplay is fragile. Same prompt, same LLM, two different Li Bais.

So I created **structured persona cards**: ~3000 tokens each, carrying a cognitive level indicator (`register 1-10`) and a three-dimensional personality baseline (`root_loss`).

**Controlled experiment**: same question, same LLM, one variable — with or without card. 12 combinations across 2 LLMs × 3 questions. With card → output consistently shaped by register/RL values. Without card → generic, drifting. The difference is reproducible.

**State modifier tests** show RL values have a directional effect on output, not merely decorative. Change the numbers (health = 20%, mood = "heavy cold"), and the output shifts directionally — both semantic and algorithmic modulation produce observable, reproducible shifts.

**Light card discovery**: Even the minimal viable card — just metadata (register + root_loss YAML, no narrative body) — produces directional influence on LLM output. A card's essence is in its cognitive parameters, not its prose.

**Consistency test**: Same card (Bai Juyi), same question ("everyone's a creator"), 3 runs — all three answers orbit the same core stance. Directional consistency verified: same soul, different flowers. Same results with Dante on "can AI write poetry?"

→ [A1: 3×4 comparison](demo/A1-controlled-experiment/a1-01-ai-opinion.white-paper_en.md)
→ [A2: consistency](demo/A2-consistency/)
→ [A3: state modifiers](demo/A3-state-modifiers/a2-重感冒.white-paper_en.md)

### Layer B — Protocol: what can you do with cards?

Cards alone just sit there. The protocol stack brings them to life:

- **Gallery** — 28 cards, same question ("Where should your AI live?"), from a screw to a philosopher to a brand. Each answers from its nature. ⭐ Don't miss [Cognitive Boundaries](demo/B1-gallery/cognitive-boundaries.en.md) — a third-grader discussing existentialism. It's the purest demonstration of what cards can do.
- **q9 Sparks** — 20 cross-domain golden quotes from Qwen3.5-9B, generated without prompt engineering — only cards + welds. ⭐ **This is the most counterintuitive result in the white paper** — a 9B model Punching this high because the card structure carries the load.
- **Interaction** — Touch (first impressions), talkto (directed conversation), council (multi-entity structured debate).
- **Fuse vs Group** — Same 3 source cards → fuse creates a single synthesized voice; group preserves all voices under shared structure. The difference is structural, not random.
- **Split × Timeline** — Jobs at 5 life stages debate Cook about Apple's soul. Li Bai's 3 inner faces argue where AI should live. Real philosophy, not roleplay.
- **Round-trip** — Split Jobs into 4 sub-personas, fuse them back, compare with original. Does the original survive? (Yes. With emergent value.)
- **Benchmarking** — PEVM compared with conversation/memory projects (SESS) and ontology systems (ONTLG vs Palantir).

Design goal: if card quality and mechanisms are sufficient, **split → fuse round-trip should preserve the original persona** — split(A) → {A₁,A₂,A₃} → fuse(A₁,A₂,A₃) ≈ A. Fidelity of this round-trip is a benchmark for both operations.

→ [B1 Gallery](demo/B1-gallery/GALLERY.en.md)
→ [B1.5 q9 Sparks](demo/B1-gallery/B1.5_q9_sparks.en.md)
→ [B2 Council: Free Will](demo/B2-interaction/council_自由意志.en.md)
→ [B3 Fuse vs Group](demo/B3-fuse-group/B3_FUS_vs_GRP.en.md)
→ [B4 Split: Jobs × Cook + Li Bai](demo/B4-split-timeline/B4_split_timeline.en.md)
→ [B5 Round-trip: Split → Fuse Fidelity](demo/B5-roundtrip/B5_roundtrip.en.md)
→ [B6 Benchmark: SESS + ONTLG + Training Data](demo/B6-benchmark/README.en.md)

### Layer C — System: cards + operations = OS-inspired management

Once you have structured entities and operations on them, the system naturally looks like an entity management OS:

| Operation | Analogy | Status |
|-----------|---------|--------|
| Card creation | Process creation with auto-registration | ✅ |
| Card refinement | Hot patching | ✅ |
| Card fusion | Process merging (52 fusion cards) | ✅ |
| Card splitting | Sub-process forking (14 sub-personas) | ✅ |
| Timeline | ZFS snapshot (Jobs 5 stages, Musk 4) | ✅ |
| Card-to-card chat | Signal passing (325+ records) | ✅ |
| Multi-card debate | Structured IPC | ✅ |
| Training data | Cards → Alpaca / ShareGPT with register conditioning | ✅ |

→ [Architecture](demo/C1-architecture/ARCHITECTURE.en.md)
→ [Lifecycle](demo/C2-lifecycle/lifecycle.en.md)

### Layer D — Vision: where this points

If cards = files and protocols = system calls, then the next question is: what if this protocol layer becomes part of an AI-native Linux?

The protocol stack is built and verified — working prototypes (pevm mount, pevm query) already demonstrate the core ideas. The kernel integration is the next frontier, and it's not mine to build alone.

→ [D-vision](demo/D-vision/D-vision.en.md)

---

→ [Browse all demos](demo/)

---

## Status

Personal research project. ~2.8M tokens of structured persona data across 63 domains. All operations run on DeepSeek Flash (local fallback via Qwen3.5-9B).

Interestingly, the 9B local model (Qwen3.5) outperforms DeepSeek Flash on fusion/welding tasks — it stays more disciplined with the structured card data, while the larger model tends to over-interpret. Most other tasks benefit from DeepSeek Flash's broader reasoning. We use both, each where it excels.

This branch contains curated demos and technical documentation. I'm actively looking for **feedback, sharp questions, and collaborators** — if any part resonates, [reach out](mailto:hugepan@gmail.com).

---

💬 **Join the discussion** — [start a discussion](https://github.com/hugepan/PEVM-core/discussions) or [open an issue](https://github.com/hugepan/PEVM-core/issues).

*Filter noise first. Metabolize knowledge second.*

---
**Share on**:
[Twitter](https://twitter.com/intent/tweet?text=PEVM%20-%20Structured%20Persona%20Protocol%20for%20AI&url=https://github.com/hugepan/PEVM-core)
| [Hacker News](https://news.ycombinator.com/submitlink?u=https://github.com/hugepan/PEVM-core&t=PEVM%20-%20Structured%20Persona%20Protocol%20for%20AI)
| [Reddit](https://reddit.com/submit?url=https://github.com/hugepan/PEVM-core&title=PEVM%20-%20Structured%20Persona%20Protocol%20for%20AI)
