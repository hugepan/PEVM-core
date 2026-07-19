# ONTLG 域 · 本体论建模

> **对标**：Palantir Foundry Ontology（Object / Link / Action / Lifecycle）
> **问题**：PEVM 的 ONTLG 域跟 Palantir 的本体论系统有什么本质不同？
> **答案**：Palantir 做数据关联，PEVM 做可融合的认知实体。

## 背景

Palantir 的核心能力：把现实世界的实体（设备、人员、流程）建模为可操作的"本体"——定义它们是什么、怎么关联、能触发什么动作。这套系统花了十几年、几十亿美金构建。

PEVM 的 ONTLG 域：用四张卡、三小时、零成本，完成了同构映射。不是"平替"——是证明了"PEVM 的结构化卡片格式天然能做本体论建模，而且比 Palantir 多了一层融合意识"。

## 验证材料

**工程深度**：[engineering-depth.zh.md](engineering-depth.zh.md) — 同一会话中发现的三个根因 bug 复盘。展示了真实决策过程和系统演化。

**工业诊断**（最能体现 ONTLG 实际价值）：
- [产线瓶颈分析](industrial-consulting.zh.md) — 4融-刀具×工件×三坐标测量机×数控机床，以 consultant 模式诊断产线瓶颈。识别出"四组时钟"的同步缺失，给出了量化的改进建议。
- [分阶段实施方案](industrial-consulting-plan.zh.md) — 4团-同组源卡，输出结构化的三阶段实施方案。展示了同一组源卡在 fuse vs group 两种架构下产出不同形式的咨询报告。

## 关键技术参数

- **LLM**：ds_flash
- **卡域**：ONTLG（本体论域）
- **投入**：3 小时，4 张卡，60+ commits
- **产出**：三层闭环（ingest → ontology → application）
