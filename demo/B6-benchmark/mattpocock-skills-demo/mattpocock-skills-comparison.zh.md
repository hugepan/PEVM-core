# Matt Pocock Skills 对比验证：diagnose

> **来源**：[mattpocock/skills](https://github.com/mattpocock/skills)
> **被测对象**：`skills/engineering/diagnose/SKILL.md`（117 行）
> **PEVM 路径**：原文 → 结构化卡片 → schema matt → 自包含 skill 文件

## 原版摘要

6 阶段调试方法论：Build feedback loop → Reproduce → Hypothesise → Instrument → Fix + regression test → Cleanup + post-mortem。含 10 种反馈循环构建技术，强调可证伪假设和正确接缝。

## PEVM 版本摘要

99 行自包含单文件，6 阶段完整保留，每阶段附加 checklist，结构清晰度略有改善。

## 关键差异

| 维度 | 原版 Matt（117 行） | PEVM（99 行） |
|:------|:-----------------:|:-------------:|
| 方法论完整性 | ✅ 6 阶段 | ✅ 6 阶段 |
| 反馈循环技术 | ✅ 10 种 | ✅ 10 种 |
| 可证伪假设 | ✅ | ✅ |
| 正确接缝概念 | ✅ | ✅ |
| 清理 checklist | ✅ | ✅ 结构更清晰 |
| 工程格言 | "Refuse to give up" | ✅ 保留并新增 |
| 具体工具引用 | git bisect、Playwright | ✅ 全部保留 |

**结论：方法论和内容完整性持平。PEVM 版结构略有改善。**

## 原版文件

[GitHub: mattpocock/skills/diagnose/SKILL.md](https://github.com/mattpocock/skills/blob/main/skills/engineering/diagnose/SKILL.md)

## PEVM 全量输出（99 行）

```
---
name: diagnose
description: Systematic six-phase debugging process for non-deterministic bugs, based on feedback loops and testable hypotheses. Trigger: flaky tests, hard-to-reproduce errors, regression hunting.
---

# The Debug Feedback Loop Skill

Never skip a phase without explicit justification. Each phase has a quality gate: you must pass Phase N before entering Phase N+1. The first principle is that feedback loops are the currency of debugging—without a reliable signal, all assumptions are empty.

This skill applies to any software debugging scenario where the bug is non-deterministic or where the root cause is unclear. It assumes you have access to the codebase, a test environment, and basic tooling (version control, a test runner, a debugger). The process is iterative: if Phase 3 invalidates all hypotheses, loop back to Phase 2.

## Phase 1 — Reproduce Confirmation

**This is the phase where you turn “it sometimes breaks” into “here is exactly when it breaks.”**

If you cannot reproduce the bug reliably, you cannot debug it. The goal is a fast, deterministic, auto-run pass/fail loop. Build it before anything else.

1. Reproduce using the user’s description. Run the minimal reproduction script multiple times to confirm consistency.
2. Capture the exact symptom: error message, stack trace, output diff, timing deviation.
3. For non-deterministic bugs, loop 100 times, parallelize, add stress, narrow the time window—aim for at least 50% reproduction rate. Use `git bisect run` with a bisection harness when the bug appears between two known states.
4. If all techniques fail, explicitly state that no reliable signal exists. Request a HAR dump, core dump, timestamped screen recording, or temporary instrumentation permissions. Do not enter Phase 2 without a signal.

- [ ] Reproduction triggers the exact same symptom every time (or with predictable frequency)
- [ ] Reproduction is isolated—no extraneous state (test database, mocked time, fixed seed)

> Engineering saying: “A 30-second flaky loop is barely better than no loop. A 2-second deterministic loop is a superpower.”

## Phase 2 — Hypothesis Generation

**This is the phase where you stop guessing and start predicting.**

Generate 3–5 falsifiable hypotheses. Each must state a prediction: “If X is the cause, then changing Y will make the bug disappear.”

1. Rank hypotheses by likelihood. Use your domain knowledge and the user’s context.
2. Prefer simple hypotheses (Occam’s razor). For example, a race condition in an event handler is more likely than a cosmic bit flip.
3. List hypotheses in a clear order. Present them to the user if they have domain insight.

- [ ] Each hypothesis states a prediction that can be tested in Phase 3
- [ ] Hypotheses are mutually exclusive where possible (e.g., bug is either in cache invalidation OR in stale data, not both)

## Phase 3 — Instrumentation Verification

**This is the phase where you prove or disprove each prediction with a single variable change.**

Every probe maps to one hypothesis. Change exactly one thing at a time.

1. Prefer a debugger/REPL over logs—it gives immediate, interactive feedback. If you must log, use unique prefixes like `[DEBUG-a4f2]` so you can clean them later.
2. For performance bugs: establish a baseline measurement first. Use a timing harness, profiler, or query plan. Measure before you bisect.
3. For UI bugs: use Playwright/Puppeteer to drive the browser and assert DOM/console/network state.
4. If a probe disproves a hypothesis, cross it off. If it confirms, you have found the root cause.

- [ ] Each probe isolates exactly one variable
- [ ] All `[DEBUG-*]` markers are noted for removal in Phase 5
- [ ] No more than one change per probe

## Phase 4 — Fix

**This is the phase where you apply the confirmed root cause with a regression test.**

Write the regression test *before* you apply the fix. The test must fail with the current code and pass after the fix.

1. Identify the correct “seam” for the test: a point in the code where you can inject the bug’s trigger path. If no proper seam exists, document it—this is an architecture issue, not a lack of testing.
2. Apply the minimal fix. Do not refactor unrelated code.
3. Run the regression test and confirm it passes.

- [ ] Regression test fails against the buggy code
- [ ] Regression test passes against the fixed code
- [ ] No extraneous changes introduced

## Phase 5 — Cleanup & Regression

**This is the phase where you remove all traces of the investigation and lock the fix.**

The fix is not complete until the debugging scaffolding is gone and the full test suite passes.

1. Run the original reproduction script from Phase 1—it should no longer trigger the bug.
2. Run the full regression suite (unit, integration, e2e) to ensure no side effects.
3. Remove all `[DEBUG-*]` markers, temporary log statements, and prototype code.
4. Delete any disposable harness files or move them to a `/archive` folder.

- [ ] Original reproduction no longer reproduces the bug
- [ ] All `[DEBUG-*]` markers removed
- [ ] Regression suite passes with zero failures
- [ ] No leftover temporary files

## Phase 6 — Document & Archive

**This is the phase where you make the next debugger’s job easier.**

Write a commit message that records the correct hypothesis and the root cause. This prevents the bug from being re-introduced and teaches the team.

1. Commit message template: “fix: [brief description] – [hypothesis confirmed] because [root cause].”
2. Ask: “Was the regression test properly seamed?” If the seam was too shallow (e.g., you had to mock too much), create an architecture improvement ticket.
3. If the fix revealed a missing seam, suggest the improvement *after* the fix is committed—you now have better information.

- [ ] Commit message documents the correct hypothesis and root cause
- [ ] Architecture improvement issue created if the seam was inadequate
- [ ] PR/commit linked to the original bug report or issue

> Engineering saying: “The best debugging result is not just a fix—it’s a permanent improvement to the codebase’s testability.”
```
