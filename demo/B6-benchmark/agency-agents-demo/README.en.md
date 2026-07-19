# Benchmark 4: agency-agents (184 AI Agent Definitions)

> **agency-agents is one of the largest open-source collections of AI agent definitions.** Each agent has a complete identity declaration, communication style, critical rules, and domain knowledge. We took the most challenging one — a 600-line Multi-Agent Systems Architect — through the PEVM pipeline.

## Target

**[agency-agents](https://github.com/msitarzewski/agency-agents)** by msitarzewski, a collection of 184 AI agent definitions covering engineering, design, finance, marketing, and more. Each agent is a self-contained `.md` file with YAML frontmatter and multiple sections.

## What We Did

### Multi-Agent Systems Architect (600 lines)

Took the deepest agent from the collection through the PEVM pipeline and back to agency-agents format:

```
Original → structured card → manual gap filling (10 deep knowledge sections as refs) → format conversion → agency-compatible output
```

| Dimension | Original | PEVM Converted |
|:----------|:---------|:--------------|
| Total length | 600 lines (flat 14 sections) | 645 lines (self-contained: 50-line skeleton + 590-line deep knowledge; +45 lines from new Core Mission & Architecture Blueprint sections) |
| Identity | ✅ | ✅ |
| Communication style | ✅ | ✅ |
| Critical rules | 8 rules | 8 rules (same intent, different wording) |
| Deep knowledge | 10 sections (500+ lines) | Fully preserved (inlined in comparison doc) |
| Readability | Dense, 600-line flat file | 645-line self-contained: first 50 lines skeleton + 590 lines deep knowledge |

**Conclusion**: PEVM reorganizes a 600-line loosely-structured agent definition into a 645-line self-contained file: 50 lines structured skeleton + 590 lines deep knowledge inline. Equivalent content, better organized.
