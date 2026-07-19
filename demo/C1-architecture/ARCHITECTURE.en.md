# PEVM Architecture

> A cognition protocol stack — translating between human mental models and AI-native representations.
> Not a framework. A data format + protocol stack + reference implementation.

---

## 1. What Is PEVM

PEVM sits between human mental models and LLM consumption:

```
human mental model → [PEVM protocol layer] → LLM consumption
```

At its core, PEVM is defined by two things:

1. **A structured card format** — encodes any entity (person, concept, company, object) into ~3000 tokens any LLM can consume. Each card carries a cognitive level indicator (`register 1-10`) and a three-dimensional personality baseline (`root_loss`), enabling fine-grained persona control without prompt engineering.

2. **A protocol stack** — operations on cards: fusion (weld multiple cards into a new entity), debate (multi-card structured council), scenario simulation (apply a card to a real-world task), timeline (slice a person across life stages), and render (convert internal format to human-facing output).

The guiding principle: **good data format > good prompt > good persona**. PEVM turns "making AI understand a concept" from a prompt engineering problem into a data format problem.

---

## 2. Four-Layer Architecture

PEVM is organized into four layers, each with a distinct responsibility:

```
┌──────────────────────────────────────────────────────────────┐
│  Layer D: Vision — AI-native OS (speculative)                │
│  Research direction: FUSE filesystem for cards,              │
│  LLM system daemon, semantic-drift-aware kernel hooks        │
├──────────────────────────────────────────────────────────────┤
│  Layer C: System — Entity lifecycle management               │
│  Create → fuse → split → timeline → delete                  │
│  Training data factory · system monitoring · CLI toolchain   │
├──────────────────────────────────────────────────────────────┤
│  Layer B: Protocol — operations on cards                     │
│  Fusion · Council · Scenario Apply · Mount · Render         │
├──────────────────────────────────────────────────────────────┤
│  Layer A: Format — structured card data                      │
│  register/root_loss · structured narrative · safety mechanisms     │
│  ~3000 tokens per card, any LLM can consume                  │
└──────────────────────────────────────────────────────────────┘
    │
    ▼
┌──────────────────────────────────────────────────────────────┐
│  LLM inference layer (cloud or local)                        │
└──────────────────────────────────────────────────────────────┘
```

**Key constraint**: Lower layers have no knowledge of upper layers. Layer A (data format) has no concept of "protocols." Layer B (protocols) does not care which LLM backend is running. This separation guarantees that each layer can evolve independently.

### Layer A: Structured Card Data

A card is a self-contained markdown file with three sections:

- **Metadata header** — cognitive level (register 1-10), three-dimensional personality baseline (root_loss), entity relationships, inter-card tension signals
- **Structured narrative** — a pruned causal chain that preserves signal at every stage of development
- **Safety mechanisms** — guardrails that prevent hallucination drift and enforce persona boundaries

Design constraints: ≤3328 tokens per card (structural elements excluded). Each card must be consumable by any LLM in a single context window.

### Layer B: Protocol Stack

Protocols are operations on cards. Just as Unix has open/read/write on files, PEVM has fusion/debate/apply on cards:

| Protocol | Function |
|----------|----------|
| **Fusion (weld)** | Merge N cards → new entity with a synthesized personality |
| **Council** | N-card structured debate — round-by-round convergence |
| **Scenario Apply** | Entity acts on real-world tasks (matchmaking, due diligence, strategy consulting) |
| **Mount** | Attach external resources (raw materials, reference documents) to a card at runtime |
| **Render** | Convert internal format to human-facing output (technical report, social media, gallery) |

### Layer C: Entity Lifecycle

Cards follow a complete lifecycle managed by CLI tools:

| Operation | Description | Status |
|-----------|-------------|--------|
| Create | Generate a new card from raw material | ✅ Pipeline |
| Refine | Incremental improvement with reference materials | ✅ In use |
| Fuse | Merge multiple cards into a fusion entity | ✅ 52 fusion cards |
| Split | Generate sub-personas from a master card | ✅ Delivered |
| Timeline | Slice a person across different life stages | ✅ 9 timeline slices |
| Talkto | Single-card persona simulation | ✅ 325+ records |
| Council | Multi-card structured debate | ✅ Multiple topics |
| Audit | Self-check for structural integrity | ✅ Pipeline |
| Delete | Remove a card | ✅ Delivered |

### Layer D: Vision (Speculative)

Research direction — what happens when the protocol stack is embedded into an operating system:

- Card filesystem mounted into Linux VFS
- LLM as a system daemon (kernel-level inference)
- Semantic drift detection as an AI-native watchdog mechanism
- Noise filtering as an AI-native syslog

Not a current claim. A researched direction for collaborators.

---

## 3. Data Flow

```
raw material
    │
    ▼
① card ingest: register stub → card generation (LLM produces card) → registry write-back
    │
    ▼
② structured card (organized by domain)
    │
    ├── talkto    → single-card persona response
    ├── council   → multi-card structured debate
    ├── apply     → scenario-based reasoning
    ├── fuse      → merge cards → new entity
    ├── split     → sub-persona generation
    ├── timeline  → life-stage slicing
    ├── render    → format conversion for human readers
    └── delete    → cleanup
    │
    ▼
③ output: interaction records / rendered formats / training data
```

---

## 4. Design Principles

1. **Lower layers don't know upper layers exist** — The data format has no concept of protocols. Protocols don't care which LLM backend runs. This keeps each layer independently replaceable.

2. **Local-first** — The local LLM fallback (available on consumer GPUs) is not a feature — it's an architecture decision. Everything must work without cloud dependency.

3. **Short, dense tension signals > long descriptions** — Fusion quality depends on precise tension signals between cards. A single-line opposition ("thread vs beam — freedom vs load-bearing") consistently outperforms multi-paragraph academic descriptions.

4. **Good data format > good prompt > good persona** — Cards are structured data, not prompt templates. The format itself enforces consistency that no prompt can guarantee.

5. **Sovereignty is architecture-level** — Not a feature flag, not a toggle. The system is private by structure: card data stays on local storage, inference can run locally, and the format is self-contained.

6. **Output constraints are centralized** — Terminology rules, data boundaries, and safety filters are defined once and referenced everywhere, never duplicated.

---

## 5. Development Velocity

A telling data point: the timeline feature (splitting a person across life stages) went from concept to working implementation in **5+5+5 minutes** (infrastructure, implementation, debugging). Not because it was easy — because PEVM's architecture is designed such that new operations on cards follow the same patterns as existing ones. Split, timeline, fusion, group — each new protocol builds on the same orthogonal primitives.

This velocity is not accidental. It's the direct result of the lower-layer-ignorance principle: when you add a new protocol, you don't touch the data format. When you add a new operation, you don't touch existing protocols.

## 6. Current System Scale

The following metrics reflect PEVM's production state:

| Metric | Scale |
|--------|-------|
| Domains | 63 knowledge categories |
| Cards | ~950 registered entities |
| Tools | 50+ CLI commands |
| Interaction records | 400+ talkto/council sessions |
| Training data formats | 3 (Alpaca, ShareGPT, PEVM-extended) |