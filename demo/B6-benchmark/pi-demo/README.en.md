# Benchmark 3: pi-mono (70k ⭐ AI Coding Agent)

> **pi-mono's 70k ⭐ come from its TypeScript execution engine, not from its markdown prompts.** PEVM doesn't touch the execution engine — we only look at whether structured formatting can bring marginal improvements to the prompt layer.

## Target

**[pi-mono](https://github.com/earendil-works/pi)** (formerly badlogic/pi-mono), by Mario Zechner. An AI coding agent CLI.

**An important fact:** pi-mono's codebase has ~52,000 lines of TypeScript runtime, but only ~315 lines of agent persona + discipline files (`system-prompt.ts` + `AGENTS.md`). The 70k stars buy you the TS runtime — tool calling, session management, provider adapters.

| Layer | What | Size | Our focus |
|:------|:-----|:----:|:---------:|
| 🏗 Runtime | TypeScript: tools/TUI/session/provider | ~52,000 lines | ❌ Not our target |
| 📝 Content | prompts/skills/agent persona (markdown) | ~315 lines | ✅ **We try to polish here** |

## What We Did

Two experiments to see if PEVM's structured card format can improve the prompt layer.

### Experiment 1: Skill File Comparison

Take pi's built-in `pr.md` (PR review skill) through the PEVM pipeline and back to pi format:

```
pi pr.md → structured card → format conversion → pi-compatible skill file
```

**Same LLM × Same PR × Different skill file → Compare review quality.**

| Dimension | pi native pr.md | PEVM converted |
|:----------|:---------------:|:--------------:|
| Structure | Flat step list | 5 sections (Flow/Input/Output/Dependencies/Safety) |
| Safety Rules | Mixed into steps | Separate section, cleaner |
| Changelog exception | Mixed into steps | Consolidated in Safety Rules |
| Error handling | Implicit | Explicitly listed (label failure, API timeout, version check) |

**Conclusion**: The PEVM-converted skill is better organized, but the core review capability is unchanged — the same LLM and execution engine power both versions.

→ Proof: [pi-skill-comparison.en.md](pi-skill-comparison.en.md)

### Experiment 2: Agent Persona Comparison

Take pi's agent definition (`system-prompt.ts` + `AGENTS.md`) through the PEVM pipeline and back to pi format:

```
pi agent definition → structured card → format conversion → pi-compatible agent prompt
```

| Dimension | pi Native | PEVM Converted |
|:----------|:---------:|:--------------:|
| Identity | One sentence | Three parts (identity + boundaries + refusal list) |
| Discipline | Scattered in AGENTS.md (162 lines) | Concentrated into 5 sections |
| Inviolable Rules | No separate section | Listed explicitly |
| Refusal statement | Implicit ("unless asked") | Explicit ("I explicitly refuse to") |

**Conclusion**: The PEVM-converted agent is better organized, but the content is the same as the original — all rules were already defined in AGENTS.md, we just rearranged them.

→ Proof: [pi-agent-comparison.en.md](pi-agent-comparison.en.md)

## Honestly

The improvements from these two experiments are **real but modest**. pi-mono's prompt layer is already lean and well-designed — 315 lines define a complete coding agent behavior. What PEVM's structured cards can do is marginal:

- Consolidate scattered rules into focused sections
- Give boundary conditions an explicit position
- Make Safety Rules more visible to the LLM

These improvements don't make pi's agent "stronger" — pi's capability lives in the TS runtime, not in the prompt. But as project scale grows and prompts multiply, this kind of structured management could become more valuable.

## One-Line Difference

> **pi-mono has a 70k ⭐ execution engine — PEVM can bring some structural organization to its prompt layer.**

## What This Proves

1. **PEVM's card format is interoperable** — pi's skills and agent definitions can be losslessly converted to structured cards and back
2. **Structural organization has marginal benefits** — better readability and boundary visibility, but capability unchanged
3. **Zero-invasion** — no changes needed to pi's TS code

## Shared Foundation

This benchmark shares the same underlying capabilities with other B6 benchmarks:

1. **Structured cognitive encoding** — any entity (skill, agent definition, review process) can be a structured card
2. **Format interconversion** — card format ⇄ target project format, bidirectional lossless
3. **Content organization** — structured metadata can precipitate as better content organization when converting back to the target format
