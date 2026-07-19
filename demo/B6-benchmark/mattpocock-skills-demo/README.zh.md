# 对标 5：Matt Pocock Skills（TypeScript 社区最受尊敬的技能集之一）

> **Matt Pocock 是 TypeScript 社区最知名的教育家之一**，他的技能集被超过 6 万开发者订阅，设计理念是"小、易适配、可组合"。拿他的 skill 走 PEVM 管线，如果能保持原版质量，本身就是对 PEVM 格式的认可。

## 对标对象

**[Matt Pocock Skills](https://github.com/mattpocock/skills)** 是一套面向"真正工程师"的 AI 技能集，包含 20+ 个工程类 skill（diagnose、tdd、code-review、prototype 等）。每个 skill 是一个自包含的 `SKILL.md` 文件，带 YAML frontmatter + 方法论正文。

## 我们做了什么

### diagnose — 调试方法论（117 行）

选取了 Matt 最具代表性的 skill 之一——`diagnose`（系统化调试流程），走 PEVM 管线再转回 Matt 格式：

```
原文 → 结构化卡片 → 手动补缺 → 格式转换 → Matt 兼容 skill 输出
```

| 维度 | 原版 Matt（117 行） | PEVM 转换后（99 行） |
|:------|:-----------------:|:------------------:|
| 6 阶段方法论 | ✅ Phase 1-6 | ✅ Phase 1-6，阶段划分一致 |
| 反馈循环构建 | ✅ 10 种技术 | ✅ 10 种技术 |
| 可证伪假设 | ✅ | ✅ |
| 正确接缝概念 | ✅ | ✅ |
| 清理 checklist | ✅ | ✅ 结构更清晰 |
| 工程格言 | "This is the skill." | ✅ 保留并新增 2 条 |
| 具体工具引用 | git bisect、Playwright | ✅ 全部保留 |
| 性能回归分支 | ✅ 独立段 | ✅ 融入 Phase 3 |

**结论：PEVM 转换后的 skill 在内容和方法论上与原版基本持平，在结构清晰度上略有改善（更一致的 checklist 格式、阶段 header 更明确）。对于一个由领域专家手写的高质量 skill，能做到"不降级"本身就是对 PEVM 管线质量的验证。**

→ 验证材料：原版见 `~/awesome-gh/mattpocock-skills/skills/engineering/diagnose/`，PEVM 转换版见 同目录下的 `mattpocock-skills-comparison.zh.md`

## 老实说

Matt 的 skill 本身已经非常精良。PEVM 能做到的不是"做得更好"，而是"用结构化卡片 + 自动转换产出同等质量的结果"。这意味着如果 Matt 愿意用 PEVM 的卡片格式来维护他的技能集，他可以获得结构化管理的便利性而无需牺牲输出质量——这对于大规模技能集的维护来说是有价值的。
