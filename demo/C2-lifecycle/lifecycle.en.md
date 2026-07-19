# C3 Entity Lifecycle — OS-Inspired Card Management

> **Core insight**: Every card follows one main lifecycle:
> `ingest → add → edit → live → delete`
>
> Derived operations (fuse/group/split/timeline) are not lifecycle stages — they **replicate** new entities from a source card. Each derived entity walks its own independent lifecycle. Source card is not consumed.


## Main Lifecycle

Every card walks through five stages from birth to termination:

```
ingest ──→ add ──→ edit ──→ live ──→ delete
(source)  (born)  (tune)   (use)   (terminate)
```

### Step 1: ingest — raw material intake

Before a card exists, its source material is loose text: biography snippets, interview transcripts, architectural descriptions, research papers. These raw materials are collected into a staging area.

**Tool**: Manual file placement. No automated ingest — material collection is pre-card work that requires human judgment.

### Step 2: add — card generation

From raw material to structured persona. This is PEVM's core transformation — "text to personality":

```
① Registry writes a placeholder personality baseline (default neutral)
② LLM reads raw material → infers precise cognitive level + personality parameters
③ Precise parameters auto-written to registry (registry = process table)
④ Optionally refine narrative structure + safety mechanisms
⑤ Optionally compress to budget (≤3328 tokens)
⑥ Self-check for structural integrity
⑦ Attach source material to card for future reference
```

**Tool**: Card creation

**Key metrics**: 10-30 min end-to-end; output ~3000 tokens per card; registry auto-populated, immediately referencable by other cards.

### Step 3: edit — continuous refinement

Cards are not born complete. `edit` is the most frequent operation — quality upgrades, information updates, relationship adjustments.

| Operation | Purpose |
|-----------|---------|
| Content refine | LLM-assisted rewrite of narrative sections |
| Budget compress | Trim to within token budget |
| Type upgrade | Elevate card quality tier (standard → selected → premium) |
| Add relationship edges | Build cross-card connections |
| Add tension signals | Mark inter-card oppositions for richer fusion |
| Tune personality baseline | Direct adjustment of cognitive level or personality parameters |
| Self-check | Single-card structural health check |
| Mount resources | Attach source/reference materials at runtime |

### Step 4: live — card in use

This is why cards exist — to be consumed in real scenarios:

| Mode | Output | Verification |
|------|--------|-------------|
| Single-card persona simulation | In-character response to any question | ✅ Comparative experiments (controlled A/B tests) |
| State-modified simulation | Same persona with altered state (fatigue / reduced capacity / analyst mode) | ✅ Multiple state modifiers verified |
| Multi-card structured debate | N-role round-by-round debate with convergence | ✅ Multiple debate topics |
| Scenario application | Entity acts as expert consultant (matchmaking, due diligence, strategy) | ✅ Dozens of apply records across domains |
| Format rendering | Output formatted for different audiences (technical report, social media, gallery) | ✅ Full rendering pipeline verified |

### Step 5: delete — entity termination

The end of a card's lifecycle — file cleanup + registry entry removal.

| Mode | Effect | Use case |
|------|--------|----------|
| Preview (default) | Show what will be deleted | Confirm identity |
| Permanent delete | Remove file + registry entry | Full removal |
| Archive | Move to cold storage | Soft-delete, restorable |
| Full purge | Also clean associated derived data | Complete cleanup |

**Principles**: Preview by default (accidental-delete protection); double confirmation required; derived cards are independent (deleting a fusion card doesn't touch source cards).


## Derived Operations (Optional)

Derived operations create **new entities** from one or more source cards. Each new entity gets its own registry entry, its own file, and its own independent lifecycle — source card is never consumed or locked.

```
                    ┌── fuse ────→ fusion card (N sources → 1 new entity)
                    │
  source card ──────┼── group ───→ group card (N sources → structured ensemble)
                    │
                    ├── split ────→ sub-persona cards (1 source → N inner faces)
                    │
                    └── timeline ──→ timeline cards (1 source → N life stages)
```

### fuse — fusion (N→1)

Merge N source cards into a single new entity with a synthesized personality. The fusion card speaks as one voice, internally holding the tension between its sources.

**Output**: Complete persona card (initial reaction / stance / core concern / core opportunity / action tendency / motto).

**Personality calculation**: Cognitive level = arithmetic mean of sources; personality baseline = weighted average (heavier weight on higher-register sources).

**Key capability**: Cross-domain fusion — a physicist, a musician, and an architect can be fused into a single entity that speaks with all three perspectives.

**Verified**: Same 3 sources run through fuse vs group paths produce dramatically different outputs — proving the difference is structural, not random.

### group — ensemble (N→structured ensemble)

Same N source cards, different architecture — each retains its voice, constrained by group structure. The group speaks as multiple voices orchestrated.

**vs fuse**: fusion = one voice (synthesis); group = many voices (orchestration). Both are valid for different use cases.

### split — personality split (1→N)

Discover the multiple inner faces of a single person, then generate independent cards for each face.

**Examples**: A poet might split into "divine poet" (transcendent), "office seeker" (worldly), and "drunken knight" (rebellious) — each with its own cognitive level, personality baseline, and relationships. A tech founder might split into "obsessive maker", "reality distorter", and "interface revolutionary."

**Key finding**: The same relationship is evaluated completely differently across sub-persona cards — the system genuinely re-evaluates from each sub-persona's perspective.

### timeline — time slices (1→N·longitudinal)

The same person at different life stages, each captured as an independent card. Timeline slices reveal how personality evolves over time.

**Examples**: A founder's journey from college dropout → visionary → exiled → return → peak; an inventor's path from awakening → near-death experience → world-changing ambition.

**Structure**: Each slice is a full card with its own cognitive level and personality parameters — the values change naturally across stages, reflecting real growth.

### Derived Card Lifecycle

Every derived card, once created, walks its own independent lifecycle:

```
fuse/split/timeline/group
    ↓
  add (registry auto-entry)
  edit (refine, compress, add relationships)
  live (talkto, council, apply, render)
  delete (independent from source)
```

**Key constraints**:
- Delete a fusion card → source cards untouched
- Delete a source card → derived cards untouched (they have their own registry entries)
- Same source card can participate in multiple fusions, multiple splits, multiple timelines


## OS Analogy Mapping

| PEVM operation | OS equivalent | Why |
|---------------|--------------|-----|
| Card creation | `fork` + `exec` | Create process from template, assign PID (registry entry) |
| Card refinement | Hot patch | Update without restart |
| Type upgrade | `renice` | Elevate process priority |
| Mount resources | `LD_PRELOAD` | Runtime resource attachment |
| Single-card chat | Signal | Send message to a process |
| Multi-card debate | IPC | Multi-process structured communication |
| Health check | System monitor | Process health inspection |
| Fusion | Process merge | N processes → 1 merged |
| Split | Controlled fork | N sub-processes from 1 parent |
| Timeline | ZFS snapshot | Versioned state checkpoints |
| Delete | `kill` | Terminate + PID reclamation |
