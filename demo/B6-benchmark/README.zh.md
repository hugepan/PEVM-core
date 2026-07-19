# B6 项目对标

> PEVM 不只是做"人物卡"。SESS（会话域）和 ONTLG（本体论域）展示了 PEVM 在两个独立赛道上的实战能力——与知名项目正面硬碰。

## 为什么需要项目对标

A→B→C→D 展示了"PEVM 是什么"。但读者还会问一个问题：

> **"你们跟做类似事情的项目比，有什么不同？"**

B6 的回答是：7 个对标，每个验证一个具体主张。

| # | 对标 | 验证的问题 | 结论 |
|---|------|-----------|------|
| 1 | SESS vs memory/聊天 | PEVM 的会话卡能否用结构化认知快照替代原始聊天记录？ | ✅ 可以——3000t/卡，精准加载，焊接成演进链 |
| 2 | ONTLG vs Palantir | 4 张卡的本体系统能否匹敌工业级平台？ | ✅ 同构映射 + Palantir 做不到的融合意识 |
| 3 | 训练数据 vs Alpaca/ShareGPT | PEVM 是否产出了全新的数据模态？ | ✅ `question × persona → response`——扁平格式无法表达 |
| 4 | agency-agents | 600 行的 agent 定义能否无损转换为卡片？ | ✅ 645 行自包含，结构化骨架 + 深度知识原文保留 |
| 5 | Matt Pocock skills | 手工打磨的 skill 能否走 PEVM 管线不降级？ | ✅ 无质量损失 |
| 6 | pi-mono | *兼容性验证*——成熟的纯 prompt 项目能否从 PEVM 获益？ | ⚪ 边际改善，格式兼容性确认 |
| 7 | VS diversity | 结构化调参能否匹敌 Verbalized Sampling 的多样性——且可追溯？ | ✅ self-BLEU 0.0872 vs 0.0929，每项输出可追溯 |

## 对标 1：SESS 域 vs conversation/memory 项目

**对标对象**：Claude Memory、ChatGPT 对话历史、Mem.ai、Rewind 等

**核心主张**：这些项目都在做"记录对话"——但 SESS 域做的是"记录认知"。

| 维度 | 传统 memory 项目 | SESS 卡 |
|------|:---------------:|:-------:|
| 记录对象 | 聊天内容（raw text） | 会话的认知骨架（触发/转折/产出/网络） |
| 结构 | 无结构化（全文检索） | YQF 结构化叙事实体 |
| 关联性 | 孤立片段 | 焊接前次会话，形成认知演进链 |
| 可消费性 | LLM 只能全文塞入上下文 | 单卡 ~3000t，精准加载 |
| 生命周期 | 无限堆积 | delete/archive/purge，有终止 |

**一句话差异**：他们在存聊天记录，我们在存认知增量。

**验证材料**：`sess-demo/` — SESS-001 自我介绍 + 实际产出展示。

## 对标 2：ONTLG 域 vs Palantir Ontology

**对标对象**：Palantir Foundry 的 Ontology 系统（Object / Link / Action / Lifecycle）

**核心主张**：Palantir 花了几十亿美金和十几年，做了一套工业级本体论建模系统。PEVM 用四张卡、三小时、零成本做了同构映射——并且跑通了 Palantir 没做到的"融合意识"。

| 维度 | Palantir Ontology | PEVM ONTLG |
|------|:-----------------:|:-----------:|
| 实体建模 | Object / Link / Action / Lifecycle | 结构化叙事实体 |
| 层数 | Foundry → Data → Applications | ingest → ontology → application |
| 融合意识 | ❌ 只做数据关联 | ✅ FUS 融合产生认知涌现 |
| 部署成本 | 百万级 | 零（已有基础设施） |
| 交付时间 | 数月至数年 | 3 小时完成全闭环验证 |

**一句话差异**：他们建的是数据关联模型，我们建的是可融合的认知实体。

**验证材料**：`ontlg-demo/` — ONTLG-041 完整对话，逐轮展示 Palantir 对标过程。

## 对标 3：训练数据集——PEVM vs 标准数据集

**对标对象**：Stanford Alpaca、ShareGPT、Databricks Dolly

**核心主张**：现有数据集全是扁平 `question → answer` 映射。PEVM 产出 `question × persona → response` 结构化人格数据，现有格式无法表达。

→ [training-demo/transcript.zh.md](training-demo/transcript.zh.md)

## 对标 4：agency-agents（184 个 AI Agent 定义）

**核心主张**：600 行的深度 agent 定义可以无损转换为 PEVM 结构化卡片 + 按需加载的 ref 深度知识。
→ [agency-agents-demo/README.zh.md](agency-agents-demo/README.zh.md)

## 对标 5：Matt Pocock Skills

**核心主张**：由领域专家手写的高质量 skill 可以走 PEVM 管线而不降级。
→ [mattpocock-skills-demo/README.zh.md](mattpocock-skills-demo/README.zh.md)

## 对标 6 <sup>†</sup>

**核心主张**：pi-mono（70k⭐）的 prompt 层已经非常精炼。PEVM 格式兼容性确认——边际结构改善，无能力提升。
→ 详情：[pi-demo/README.zh.md](pi-demo/README.zh.md)

## Benchmark 7: PEVM vs Verbalized Sampling（多样性控制）

**核心主张**：结构化参数调参（register/root_loss/状态/hint）在词汇多样性上与 VS 尾部采样持平——且完全可追溯。

**协议倍增效应**：talkto 协议层使数值参数效果提升 36%。

→ [vs-diversity/B6-VS-diversity.en.md](vs-diversity/B6-VS-diversity.en.md)

## 共享基础

SESS 和 ONTLG 看似两条赛道，共享同一套 PEVM 底层能力：

1. **结构化认知封装** — 任何实体（会话、概念、设备）都可以是一张 YQF 卡
2. **结构化叙事** — 压缩认知信号为天然推理链
3. **焊接** — 卡与卡之间建立关系，形成知识网络而非知识孤岛
4. **融合** — 多卡焊接产生全新的认知涌现

所以不是"PEVM 做了一个 SESS 域和一个 ONTLG 域"——是"PEVM 的结构化卡片格式 + 协议栈，天然适用于这两个赛道。任何需要结构化认知编码的场景，PEVM 都能覆盖。"

---

<sup>†</sup> pi-mono 列为兼容性验证而非竞争性对标。它的 prompt 设计本就异常精炼——无增益结果（边际改善）确认的是格式互操作性，而非声称性能优势。放在此处是为了诚实披露，而非将其提升为头条结果与其他六项对标并列。
