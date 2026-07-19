# Generation Metadata

This document records the generation parameters used for the experiments and demonstrations in this white paper. It is provided to improve reproducibility and transparency without disclosing card internal content.

## Models

| Alias | Full Name | Type | Parameters |
|-------|-----------|------|------------|
| ds_flash | DeepSeek v4 Flash | Cloud API | Unknown (proprietary) |
| q9 | Qwen3.5-9B | Local (gguf) | 9B, Q4_K_M |
| q27 | Qwen3.6-27B | Local (gguf) | 27B, Q3_K_M |
| qwen3.5-plus | Qwen3.5-Plus | Cloud API | Unknown (proprietary) |

## Default Generation Parameters

For all experiments unless otherwise noted:

| Parameter | Value |
|-----------|-------|
| temperature | 0.7 |
| top_p | 0.9 |
| max_tokens | 1024 |
| seed | Not fixed (random per call) |

## Per-Section Details

### A1: Controlled Experiment

| Setting | Value |
|---------|-------|
| Design | 2×2: model (ds_flash, q9) × condition (bare, PEVM) |
| Model | ds_flash (main), q9 (cross-model) |
| Temperature | 0.7 |
| Generations per condition | 1 (illustrative) |
| Prompt | "Write a story about 'no farewell,' approximately 300 characters." |
| Card | Fiction Writer (register=8, root_loss=0.70/0.75/0.80) |

### A2: Consistency Test

| Setting | Value |
|---------|-------|
| Model | ds_flash |
| Temperature | 0.7 |
| Generations per card | 3 (same question, same card) |
| Card 1 | Bai Juyi — plain language poet |
| Card 2 | Dante Alighieri — Florentine poet |
| Question 1 | "Everyone's a creator" (Bai Juyi) |
| Question 2 | "Can AI write poetry?" (Dante) |

### A3: State Modifiers

| Setting | Value |
|---------|-------|
| Model | ds_flash |
| Temperature | 0.7 |
| Generations per state | 1 |
| States tested | heavy cold, 20% power, consultant |
| Card | Li Bai (register=8) |

### B1: Gallery

| Setting | Value |
|---------|-------|
| Model | ds_flash (primary), q9 (B1.5 sparks) |
| Temperature | 0.7 |
| Generations per card | 1 |
| Cards | 28 gold cards across 11 domains |
| Note | B1.5_q9_sparks generated exclusively by Qwen3.5-9B |

### B2: Interaction (talkto / council)

| Setting | Value |
|---------|-------|
| Model | ds_flash |
| Temperature | 0.7 |
| Generation strategy | Single continuous conversation (no resampling) |
| Turn management | Protocol-defined: sequential (talkto) or round-robin (council) |

### B3: Fuse vs Group

| Setting | Value |
|---------|-------|
| Model | ds_flash |
| Temperature | 0.7 |
| Fuse strategy | N cards → structured prompt aggregation → single output |
| Group strategy | N cards → multi-voice orchestration with turn policy |

### B4: Split & Timeline

| Setting | Value |
|---------|-------|
| Model | ds_flash |
| Temperature | 0.7 |
| Split strategy | Core card → sub-personas by dimension |
| Timeline strategy | Core card → time-slice variants with state modifiers |
| Cases | Steve Jobs (timeline + split), Li Bai (split) |

### B5: Round-Trip Fidelity

| Setting | Value |
|---------|-------|
| Model | ds_flash |
| Temperature | 0.7 |
| Design | split(A) → {A₁..A₄} → fuse({A₁..A₄}) → compare(A, A') |
| Probing questions | 2 (Q1, Q2) |
| Generations per condition | 1 (illustrative) |

### B6: Benchmark

| Setting | Value |
|---------|-------|
| Models | ds_flash, q9, q27, qwen3.5-plus |
| Temperature | 0.7 |
| VS baseline | k=5, p<0.10 tail sampling |
| L1 (numerical) | 4 conditions (default, register_20, rl_50, rl_20) |
| L2 (annotation) | 2 conditions (reg_annot_down, rl_annot_up) |
| L3 (state) | 2 conditions (heavy cold, hyper) |
| L4 (hint) | 2 conditions (love story, light comedy) |
| Cross-entity | 5 conditions × 2 entities (Existentialism, Don Quixote) |
| Cross-model | 4 models × same conditions |
| Baseline validation | 3 entities × structured+unstructured, 5 rounds |
| AMC8 accuracy | 30 problems × 4 conditions |

## Important Notes

- **Seed not fixed.** All generations used default API seeding (random per call). This means exact outputs are not bitwise reproducible, but the directional effects (diversity patterns, protocol multiplier) are statistically robust as demonstrated by the 5-round replication (p<0.001) and cross-model replication (pairwise BLEU=0.0000 for local models).
- **Card internal content is not disclosed** in this white paper. Only the machine-readable metadata (register, root_loss values) and the model outputs are published.
- For questions about specific generation parameters not listed here, please open an issue or contact the author.
