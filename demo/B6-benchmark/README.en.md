# B6 Project Benchmarking

> PEVM is not just about "character cards." SESS (session domain) and ONTLG (ontology domain) demonstrate PEVM's real-world capability in two independent tracks — going head-to-head with well-known projects.


## Why Benchmarking

A→B→C→D answers "what PEVM is." But readers inevitably ask:

> **"How is this different from projects doing similar things?"**

B6's answer: seven benchmarks, each testing a specific claim.

| # | Benchmark | Tests | Claim |
|---|-----------|-------|-------|
| 1 | SESS vs memory/chat | Can PEVM's session cards replace raw conversation logs with structured cognitive snapshots? | ✅ Yes — 3000t per session, precision loading, welds into evolution chain |
| 2 | ONTLG vs Palantir | Can a 4-card ontology system match a billion-dollar industrial platform? | ✅ Isomorphic mapping + fusion awareness Palantir cannot do |
| 3 | Training data vs Alpaca/ShareGPT | Does PEVM produce a fundamentally different data modality? | ✅ `question × persona → response` — no flat dataset can represent this |
| 4 | agency-agents | Can a 600-line agent definition be losslessly converted to a card? | ✅ Yes — 645-line self-contained, structure + deep knowledge preserved |
| 5 | Matt Pocock skills | Can a hand-crafted skill survive the PEVM pipeline? | ✅ Passes through without quality degradation |
| 6 | pi-mono | *Compatibility check* — can a mature prompt-only system gain from PEVM? | ⚪ Marginal improvement, format compatibility confirmed |
| 7 | VS diversity | Does structured parameter tuning match Verbalized Sampling's diversity — with traceability? | ✅ self-BLEU 0.0872 vs 0.0929, every output traceable |


## Track 1: SESS Domain vs conversation/memory projects

**Benchmarking against**: Claude Memory, ChatGPT conversation history, Mem.ai, Rewind, etc.

**Core claim**: These projects all "record conversations" — but SESS records **cognition**.

| Aspect | Traditional memory | SESS card |
|--------|-------------------|-----------|
| What is recorded | Chat content (raw text) | Cognitive skeleton (trigger/turn/output/network) |
| Structure | Unstructured (full-text search) | YQF structured narrative entity |
| Relationships | Isolated fragments | Welded to prior sessions, forming a cognitive evolution chain |
| Consumability | LLM must ingest full history | ~3000t per card, precision loading |
| Lifecycle | Infinite accumulation | Has delete/archive/purge, bounded |

**One-line difference**: They store chat logs. We store cognitive increments.

**Evidence**: `sess-demo/` — SESS-001 self-introduction + actual output.


## Track 2: ONTLG Domain vs Palantir Ontology

**Benchmarking against**: Palantir Foundry's Ontology system (Object / Link / Action / Lifecycle)

**Core claim**: Palantir spent billions of dollars and over a decade building an industrial-grade ontology system. PEVM achieved isomorphic mapping with 4 cards, 3 hours, zero cost — and demonstrated "fusion awareness" that Palantir never reached.

| Dimension | Palantir Ontology | PEVM ONTLG |
|-----------|------------------|------------|
| Entity modeling | Object / Link / Action / Lifecycle | Structured narrative entity |
| Layers | Foundry → Data → Applications | ingest → ontology → application |
| Fusion awareness | ❌ Data association only | ✅ FUS fusion produces emergent cognition |
| Deployment cost | Millions | Zero (existing infrastructure) |
| Delivery time | Months to years | 3 hours for full-loop validation |

**One-line difference**: They build data association models. We build fusible cognitive entities.

**Evidence**: `ontlg-demo/` — ONTLG-041 full dialogue, round-by-round Palantir benchmarking.


## Track 3: Training Data — PEVM vs Standard Datasets

**Benchmarking against**: Stanford Alpaca, ShareGPT, Databricks Dolly

**Core claim**: All current datasets map `question → answer` flatly. PEVM produces `question × persona → response` — structured personality data no existing format can represent.

→ [training-demo/transcript.en.md](training-demo/transcript.en.md)

## Benchmark 4: agency-agents

**Core claim**: A 600-line deep agent definition can be losslessly converted to a structured PEVM card with on-demand deep knowledge refs.
→ [agency-agents-demo/README.en.md](agency-agents-demo/README.en.md)

## Benchmark 5: Matt Pocock Skills

**Core claim**: A hand-crafted high-quality skill from a domain expert can pass through the PEVM pipeline without quality degradation.
→ [mattpocock-skills-demo/README.en.md](mattpocock-skills-demo/README.en.md)

## Benchmark 6 <sup>†</sup>

**Core claim**: pi-mono (70k⭐) already has a lean, well-crafted prompt layer. PEVM compatibility confirmed — marginal structural improvement, no capability gain.
→ [pi-demo/README.en.md](pi-demo/README.en.md)

## Benchmark 7: PEVM vs Verbalized Sampling (Diversity Control)

**Core claim**: Structured parameter tuning (register/root_loss/state/hint) produces lexical diversity comparable to Verbalized Sampling's tail sampling — with full traceability that VS cannot offer.

**Protocol multiplier**: The talkto protocol layer improves numerical parameter effectiveness by 36% over card-only baselines. This effect holds across 3 entity types (writer, philosopher, literary classic) and 4 LLM families (ds_flash, q9, q27, qwen3.5-plus), with pairwise BLEU=0.0000 between card-only and protocol outputs for local models.

→ [vs-diversity/B6-VS-diversity.en.md](vs-diversity/B6-VS-diversity.en.md)

## Shared Foundation

SESS and ONTLG may look like separate tracks, but share the same PEVM core capabilities:

1. **Structured cognitive encapsulation** — Any entity (session, concept, device) can be a YQF card
2. **Structured narrative** — compresses cognitive signals into a natural reasoning chain
3. **Welding** — Cards form relationships, building knowledge networks instead of isolated silos
4. **Fusion** — Multiple cards welded together produce emergent cognitive insights

So it's not "PEVM built a SESS domain and an ONTLG domain" — it's "PEVM's structured card format + protocol stack naturally applies to both tracks. Any scenario requiring structured cognitive encoding can be covered by PEVM."

---

<sup>†</sup> pi-mono is listed as a compatibility check, not a competitive benchmark. Its existing prompt design is already exceptionally lean — the null result (marginal improvement) confirms format interoperability rather than claiming performance advantage. Placed here for honest disclosure rather than being promoted to a headline result alongside the other six benchmarks.
