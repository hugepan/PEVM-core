# 对标 4：agency-agents（184 个 AI Agent 定义）

> **agency-agents 是目前最大的开源 AI agent 定义集合之一。** 每个 agent 都有完整的身份声明、沟通风格、关键规则和领域知识。我们拿其中最有挑战性的一个——600 行的 Multi-Agent Systems Architect——走了 PEVM 管线。

## 对标对象

**[agency-agents](https://github.com/msitarzewski/agency-agents)**（作者 msitarzewski）是一个拥有 184 个 AI agent 定义的开源项目，覆盖工程、设计、金融、营销等领域。每个 agent 是一个自包含的 `.md` 文件，带 YAML frontmatter + 多段正文。

## 我们做了什么

### Multi-Agent Systems Architect（600 行）

从项目中选了一个最深度的 agent（Multi-Agent Systems Architect，600 行），走 PEVM 管线再转回 agency-agents 格式：

```
原文 → 结构化卡片 → 手动补缺（10 个深度知识章节拆为 ref）→ 格式转换 → agency 兼容输出
```

| 维度 | 原版 | PEVM 转换后 |
|:------|:-----|:-----------|
| 总篇幅 | 600 行（平铺14章） | 645 行（自包含单文件：50行结构化骨架 + 590行深度知识原文，+45行来自新增的Core Mission和架构蓝图章节） |
| 身份声明 | ✅ | ✅ |
| 沟通风格 | ✅ | ✅ |
| 关键规则 | 8 条 | 8 条（表述不同但含义一致） |
| 深度知识 | 10 个章节（500+ 行） | 完整保留（原文内联在比较文档中） |
| 可读性 | 松散，600 行平铺 | 645 行自包含文件：前 50 行骨架 + 后 590 行深度知识原文 |

**结论：PEVM 能把 600 行的松散 agent 定义浓缩为 50 行的结构化骨架 + 590 行深度知识原文（自包含单文件），内容无损但组织方式不同。对于需要快速理解 agent 核心原则的场景，结构化版本更高效。**

→ 验证材料：原版 600 行位于 `~/awesome-gh/agency-agents/engineering/`，PEVM 转换版见 同目录下的 `agency-agents-comparison.zh.md`

## 老实说

600 行到 645 行的重组不是"魔法"——原版有大量重复的模式化展开（每个能力章节都是定义→原理→示例三步曲），PEVM 的结构化组织方式把这些展开收拢为每节 2-4 行的浓缩表述。如果你需要完整的展开细节，比较文档中直接包含了完整原文。这是一种不同的组织哲学：骨架随身带，深度知识按需取。
