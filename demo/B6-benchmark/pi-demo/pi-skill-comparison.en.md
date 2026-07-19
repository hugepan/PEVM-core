# Skill Comparison: PR Review

> **Setup**: Same LLM (DeepSeek-v4-Flash) × Same PR (pi-mono [#6632](https://github.com/earendil-works/pi/pull/6632): fix RPC extension results) × Different skill prompts.
>
> Control: pi native `pr.md`
> Experiment: pi native `pr.md` → structured card → format conversion → `skill.pi.md`

## Native pi pr.md Output (excerpt)

```
PR: https://github.com/earendil-works/pi/pull/6632

### What it does
This PR fixes RPC extension output and error correlation...

### Good
- Core mechanism is clean and correctly correlates concurrent RPC commands
- Backward compatibility respected, assertSuccess helper added

### Bad
- No README/docs updated despite public RPC protocol changes
- requestId set for all errors, not just command errors

### Ugly
- Manual mock duplicates production logic
- Type-narrowing relies on Extract but still casts

### Tests
- 1545 tests passed
- Gap: no concurrent RPC prompt test
```

## PEVM skill.pi.md Output (excerpt)

```
**Processing Flow**
- Add inprogress label on receiving PR URL
- Read full PR: title, description, issues, changed files
- Analyze diff against main branch
- Check linked issues for status consistency
- Replace inprogress with reviewed label

**Input Requirements**
- PR URL must be accessible, target must be a GitHub project
- Project must have main branch as comparison baseline

**Output Format**
- PR URL → What it does / Good / Bad / Ugly / Tests / Open questions
- Each section must contain at least one concrete finding or "none found"

**Safety Rules**
- Changelog changes are exempt from structured review
- Label operation failure does not block the main flow
- Missing PR description must be declared as incomplete in What it does
```

## Key Differences

| Dimension | Native | PEVM |
|:----------|:------:|:----:|
| Review depth | 4 Good / 2 Bad / 2 Ugly / 2 gaps / 3 Qs | Equivalent depth |
| Structure | Flat list | 5 sections (Flow/Input/Output/Dependencies/Safety) |
| Safety Rules | None | 5 hard constraints |
| Error handling | Implicit | Explicit (label failure, API timeout, version check) |
| "None found" clause | Absent | Required per section |
