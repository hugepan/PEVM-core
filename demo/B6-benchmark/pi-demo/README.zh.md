# 对标 3：pi-mono（70k ⭐ AI 编码 Agent）

> **pi-mono 的 70k ⭐ 来自 TypeScript 执行引擎，不是来自 markdown prompt。** PEVM 不碰执行引擎——我们只看看在 prompt 层能不能做点微优化。

## 对标对象

**[pi-mono](https://github.com/earendil-works/pi)**（原名 badlogic/pi-mono），作者 Mario Zechner。一个 AI 编码 agent CLI，与 Claude Code 同类。

**一个重要的事实：** pi-mono 的代码库中，TypeScript 运行时占了约 52,000 行，而 agent 人设 + 纪律文件（`system-prompt.ts` + `AGENTS.md`）加起来只有约 315 行。70k stars 买的是 TS 运行时——工具调用、session 管理、provider 适配。

| 层 | 是什么 | 规模 | 我们的关注 |
|:---|:---|:---:|:---------:|
| 🏗 运行时 | TypeScript：工具/TUI/状态/provider | ~52,000 行 | ❌ 不是我们的目标 |
| 📝 内容层 | prompt/skill/agent 人设（markdown） | ~315 行 | ✅ **我们试着优化一下** |

## 我们做了什么

两个实验，想看看 PEVM 的结构化卡片格式能否在 prompt 层带来一些改善。

### 实验 1：Skill 文件对比

取 pi 内置的 `pr.md`（PR 审查 skill），走 PEVM 管道再转回 pi 格式：

```
pi pr.md → 结构化卡片 → 格式转换 → pi 兼容 skill 文件
```

**同一 LLM × 同一 PR × 不同 skill 文件 → 对照审查质量。**

| 维度 | pi 原生 pr.md | PEVM 转换后 |
|:------|:-------------:|:-----------:|
| 结构 | 平铺步骤列表 | 5 段分区（处理流程/输入/输出/依赖/安全规则） |
| Safety Rules | 混在步骤中 | 独立段落，更清晰 |
| Changelog 例外 | 混在步骤中 | 集中到安全规则段 |
| 错误处理 | 隐式 | 显式列出（标签失败、API 超时、版本兼容） |

**结论：PEVM 转换后的 skill 在结构组织上更清晰，但核心审查能力没有变化——毕竟底层的 LLM 和执行引擎是一样的。**

→ 验证材料：[pi-skill-comparison.zh.md](pi-skill-comparison.zh.md)

### 实验 2：Agent 人设对比

取 pi 的 agent 定义（`system-prompt.ts` + `AGENTS.md`），走 PEVM 管道再转回 pi 格式：

```
pi agent 定义 → 结构化卡片 → 格式转换 → pi 兼容 agent prompt
```

| 维度 | pi 原生 | PEVM 转换后 |
|:------|:------:|:-----------:|
| 身份声明 | 一句话 | 三段（身份 + 边界 + 拒绝清单） |
| 纪律组织 | 散落在 AGENTS.md 各段（162 行） | 集中为 5 段 |
| Inviolable Rules | 无独立段落 | 单独列出 |
| 拒绝声明 | 隐式（"除非用户要求"） | 显式（"明确拒绝"） |

**结论：PEVM 转换后的 agent 定义在组织方式上更集中，但内容本身和原生版本没有本质差异——所有规则都在 AGENTS.md 里定义了，我们只是重新排列了一下。**

→ 验证材料：[pi-agent-comparison.zh.md](pi-agent-comparison.zh.md)

## 老实说

这两个实验的改善是**真实但有限的**。pi-mono 的 prompt 层本来就很精简——315 行定义了一个完整的编码 agent 行为，这本身就是优秀的设计。PEVM 的结构化卡片能做的，只是在这个基础上做一些组织上的微调：

- 把散落的规则集中起来
- 给边界条件一个显式的位置
- 让 Safety Rules 更容易被 LLM 注意到

这些改善不会让 pi 的 agent"变强"——因为 pi 的能力在 TS 运行时里，不在 prompt 里。但在项目规模变大、prompt 变多的时候，这种结构化管理方式可能会有帮助。

## 一句语差异

> **pi-mono 有 70k ⭐ 的执行引擎——PEVM 可以在它的 prompt 层做一些结构化的整理工作。**

## 这证明了什么

1. **PEVM 的卡片格式可以互通**——能把 pi 的 skill 和 agent 定义转成结构化卡片，再转回 pi 格式，内容无损
2. **结构化整理有边际收益**——在 prompt 层做结构优化能改善可读性和边界可见性，但不改变能力本身
3. **零侵入**——不需要改 pi 的一行 TS 代码

## 共享基础

本对标与 B6 其他对标共享同一套底层能力：

1. **结构化认知封装** — 任何实体（skill、agent 定义、审查流程）都可以是一张结构化卡片
2. **格式互转** — 卡片格式 ⇄ 目标项目格式，双向转换无损
3. **内容整理** — 结构化元数据在转换回目标格式时，可以沉淀为更好的内容组织
