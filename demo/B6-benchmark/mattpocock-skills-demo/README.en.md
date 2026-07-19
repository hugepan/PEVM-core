# Benchmark 5: Matt Pocock Skills (TypeScript's Most Respected Skill Collection)

> **Matt Pocock is one of the most well-known educators in the TypeScript community.** His skill collection is used by 60,000+ developers and designed to be "small, easy to adapt, and composable." Running his skill through the PEVM pipeline — if the quality holds — is itself a validation of PEVM's approach.

## Target

**[Matt Pocock Skills](https://github.com/mattpocock/skills)** is a collection of AI skills for "real engineers," containing 20+ engineering skills (diagnose, tdd, code-review, prototype, etc.). Each skill is a self-contained `SKILL.md` file with YAML frontmatter and methodology body.

## What We Did

### diagnose — Debugging Methodology (117 lines)

Took one of Matt's most representative skills — `diagnose` (systematic debugging process) — through the PEVM pipeline and back to Matt's format:

```
Original → structured card → manual gap filling → format conversion → Matt-compatible skill output
```

| Dimension | Original Matt (117 lines) | PEVM Converted (99 lines) |
|:----------|:------------------------:|:------------------------:|
| 6-phase methodology | ✅ Phase 1-6 | ✅ Phase 1-6, consistent |
| Feedback loop techniques | ✅ 10 techniques | ✅ 10 techniques |
| Falsifiable hypotheses | ✅ | ✅ |
| Correct seam concept | ✅ | ✅ |
| Cleanup checklist | ✅ | ✅ More structured |
| Engineering sayings | "This is the skill." | ✅ Preserved + 2 new added |
| Tool references | git bisect, Playwright | ✅ All preserved |
| Performance regression branch | ✅ Separate section | ✅ Integrated into Phase 3 |

**Conclusion**: The PEVM-converted skill matches the original in content and methodology, with slight improvements in structural clarity (cleaner checklist format, more explicit phase headers). For a high-quality hand-crafted skill from a domain expert, achieving "no degradation" is itself a validation of the PEVM pipeline's quality.

→ Proof: Original at `~/awesome-gh/mattpocock-skills/skills/engineering/diagnose/`, PEVM version at `同级 `mattpocock-skills-comparison.en.md``

## Honestly

Matt's skills are already well-crafted. PEVM's value isn't "making them better" — it's "producing equivalent quality through structured cards + automated conversion." If Matt wanted to maintain his skill collection using PEVM's card format, he'd gain structured management without sacrificing output quality — which matters for large-scale skill collections.
