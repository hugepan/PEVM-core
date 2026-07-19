# PEVM：AI 人格结构化协议栈

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![GitHub Stars](https://img.shields.io/github/stars/hugepan/PEVM-core?style=social)](https://github.com/hugepan/PEVM-core)

让同一个 LLM 演两次李白，纯 prompt 版两次不一样——一次流浪诗人，一次泛泛哲人。没有结构。没有一致性。不可复现。

**PEVM** 让你每次都得到李白。不是一模一样的回答——而是**深刻符合李白人设**的输出。同一张卡，同一个灵魂，不同的绽放。

**这是 PEVM 官方白皮书**——一套面向 AI 的结构化人格协议栈，基于受控实验验证，按四层组织：证据层、协议层、系统层、愿景层。

> 🔥 **现场感受**——三个最震撼的 demo：
> - [自由意志辩论：熵、堂吉诃德、但丁](demo/B2-interaction/council_自由意志.zh.md)
> - [工业诊断："四组时钟"产线瓶颈](demo/B6-benchmark/ontlg-demo/industrial-consulting.zh.md)
> - [小明家庭圆桌：帝国 vs 家](demo/B3-fuse-group/family-group-showcase.zh.md)

### 📖 3 分钟速览

| 你想看... | 从这里开始 |
|-----------|-----------|
| 3 分钟理解核心主张 | [A1：2×2 对照实验](demo/A1-controlled-experiment/README.zh.md) —— 同一李白，有卡 vs 无卡 |
| 最反直觉的发现 | [B1.5：q9 金句 20 选](demo/B1-gallery/B1.5_q9_sparks.zh.md) —— 9B 模型，无 prompt 工程，哲学家级密度 |
| 真正的哲学辩论 | [B2：自由意志圆桌](demo/B2-interaction/council_自由意志.zh.md) —— 熵、堂吉诃德、但丁 |
| 工业落地场景 | [B6：产线瓶颈诊断](demo/B6-benchmark/ontlg-demo/industrial-consulting.zh.md) |
| 愿景 | [D：AI 原生 Linux](demo/D-vision/D-vision.zh.md) |

---

## 为什么做这个

我是清华本科毕业，现在是 K12 全科老师，跨年级跨学科授课。PEVM 的起点是一个课堂笔记工具——LLM + wiki 给自己用。没想到它会变成现在这样。

PEVM 原本代表 "Peter's Educational Virtual Meta-Kernel"，从一个课堂工具长成了你现在看到的协议。名字既反映了起源（老师的工具），也反映了抱负（人与 AI 之间的内核级层）。

---

## 四层结构

### A 层——证据：卡片真的能改变输出吗？

Prompt 式角色扮演是脆弱的。同一提示词、同一 LLM、两个不同的李白。

所以我做了**结构化人格卡**：每张 ~3000 token，携带认知层级指标（`register 1-10`）和三维人格基调（`root_loss`）。

**对照实验**：同一问题、同一 LLM、唯一变量——有卡 vs 无卡。2 个 LLM × 3 个问题 = 12 组合全部验证。有卡 → 输出被 register/RL 定向塑造；无卡 → 泛化、漂移。差异可复现。

**状态修饰实验**表明 RL 值对输出有定向影响，不只是装饰。改数值（健康=20%、状态="重感冒"），输出产生定向改变——语义型和算法型双通道调参均观察到可复现的变化。

**轻卡发现**：即使是最小有效卡——仅元数据（register + root_loss YAML，无叙事正文）——也能定向影响 LLM 输出。一张卡的本质在认知参数，不在辞藻。

**一致性验证**：同一张卡（白居易）、同一问题（"全民创作"）、3 次运行——三次回答都收敛于同一个核心立场。方向性一致性已验证：同一个灵魂，不同的花。但丁对"AI 能写诗吗？"的 3 次回答也呈现相同模式。

→ [A1：3×4 对比](demo/A1-controlled-experiment/a1-01-ai-opinion.white-paper_zh.md)
→ [A2：一致性](demo/A2-consistency/)
→ [A3：状态修饰](demo/A3-state-modifiers/a2-重感冒.white-paper_zh.md)

### B 层——协议：有了卡能做什么？

卡本身只是放着。协议栈让它们活起来：

- **Gallery**——28 张卡回答同一问题"你的AI应该住在哪儿"，从螺丝到哲学家到品牌，各从其类。⭐ 别错过 [认知边界](demo/B1-gallery/cognitive-boundaries.zh.md)——三年级小学生聊存在主义。这是卡片能力最纯粹的展示。
- **q9 火花集**——20 条 Qwen3.5-9B 跨域金句，无 prompt 工程，仅靠卡片+焊点驱动。⭐ **这是整份白皮书最反直觉的发现**——9B 模型打出这个密度，因为卡片结构在扛重担。
- **互动**——Touch（初见印象）、talkto（定向对话）、council（多实体结构化辩论）。
- **融合 vs 组团**——同 3 张源卡→融合产生单一合成声音；组团保留所有声音但受结构约束。差异来自架构，不是随机。
- **分裂 × 时间线**——一张卡 → N 个子人格（李白→5）。一个人生 → M 个时间切片（乔布斯→5，RL 值自然演变）。
- **往返验证**——乔布斯分裂为 4 子人格再融合，对比源卡。原人格还在吗？（在。还多了涌现价值。）
- **项目对标**——SESS 域 vs memory 项目、ONTLG 域 vs Palantir。

设计目标：如果卡片质量与分裂/融合机制足够好，**分裂→融合的往返应能保持原人格**——split(A) → {A₁,A₂,A₃} → fuse(A₁,A₂,A₃) ≈ A。往返保真度是衡量分裂与融合质量的关键指标。

→ [B1 Gallery](demo/B1-gallery/GALLERY.zh.md)
→ [B1.5 q9 火花集](demo/B1-gallery/B1.5_q9_sparks.zh.md)
→ [B2 辩论：自由意志](demo/B2-interaction/council_自由意志.zh.md)
→ [B3 融合 vs 组团](demo/B3-fuse-group/B3_FUS_vs_GRP.zh.md)
→ [B4 分裂: 乔布斯×库克 + 李白](demo/B4-split-timeline/B4_split_timeline.zh.md)
→ [B5 往返验证: 分裂→融合保真度](demo/B5-roundtrip/B5_roundtrip.zh.md)
→ [B6 项目对标](demo/B6-benchmark/README.zh.md)

### C 层——系统：卡 + 操作 = OS 风格管理

有了结构化实体和操作它们的协议，系统自然呈现出实体操作系统的风格：

| 操作 | 类比 | 状态 |
|------|------|:----:|
| 创建卡片 | 进程创建 + 自动注册 | ✅ |
| 精修卡片 | 热补丁 | ✅ |
| 卡片融合 | 进程合并（52 张融合卡） | ✅ |
| 卡片分裂 | 子进程分支（14 个子人格） | ✅ |
| 时间线 | ZFS 快照（乔布斯5段、马斯克4段） | ✅ |
| 卡间对话 | 信号传递（325+ 条记录） | ✅ |
| 多卡辩论 | 结构化 IPC | ✅ |
| 训练数据 | 卡 → Alpaca/ShareGPT 带 register 条件化 | ✅ |

→ [架构总览](demo/C1-architecture/ARCHITECTURE.zh.md)
→ [生命周期](demo/C2-lifecycle/lifecycle.zh.md)

### D 层——愿景：这指向什么

如果卡是文件、协议是系统调用，那下一个问题是：如果这套协议层成为 AI 原生 Linux 的一部分呢？

协议栈已经建成并验证——已有原型（pevm mount、pevm query）跑通了核心概念。内核集成是下一个前沿，这不是我一个人能做的事。

→ [D 层愿景](demo/D-vision/D-vision.zh.md)

---

## 状态

个人研究项目。~2.8M token 的结构化人格数据，覆盖 63 域。大部分操作跑在 DeepSeek Flash 上，本地回退用 Qwen3.5-9B。

有趣的是：9B 本地模型在焊接/融合任务上的表现反而超过 DeepSeek Flash——它更能严守卡片结构，而大模型倾向于过度解读。其他任务则是 DeepSeek Flash 更优。两者各有所长，按场景选用。

此分支包含精选 demo 和技术文档。**诚寻反馈、尖锐提问与合作者**——如果有任何东西让你产生共鸣，欢迎联系：<hugepan@gmail.com>。

---

💬 **加入讨论** — [发起 Discussion](https://github.com/hugepan/PEVM-core/discussions) 或 [提交 Issue](https://github.com/hugepan/PEVM-core/issues)。

*先过滤噪声，再代谢知识。*

---
**分享到**：
[Twitter](https://twitter.com/intent/tweet?text=PEVM%20-%20AI%E4%BA%BA%E6%A0%BC%E7%BB%93%E6%9E%84%E5%8C%96%E5%8D%8F%E8%AE%AE%E6%A0%88&url=https://github.com/hugepan/PEVM-core)
| [Hacker News](https://news.ycombinator.com/submitlink?u=https://github.com/hugepan/PEVM-core&t=PEVM%20-%20Structured%20Persona%20Protocol%20for%20AI)
| [Reddit](https://reddit.com/submit?url=https://github.com/hugepan/PEVM-core&title=PEVM%20-%20AI%E4%BA%BA%E6%A0%BC%E7%BB%93%E6%9E%84%E5%8C%96%E5%8D%8F%E8%AE%AE%E6%A0%88)
