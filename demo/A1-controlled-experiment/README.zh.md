# A1：受控实验——卡片是否改变输出？

> **TL;DR**：是。同一角色（李白）、同一问题、同一 LLM——有/无 PEVM 卡片。卡片持续改变输出的风格、立场和深度。效果在 2 个模型（ds_flash, q9）和 3 个不同问题上一致。

## 实验列表

| 文件 | 问题 | 模型 |
|------|------|------|
| [a1-01-ai-opinion.white-paper_zh.md](a1-01-ai-opinion.white-paper_zh.md) | "你怎么看 AI？" | ds_flash, q9 |
| [a1-02-open-closed.white-paper_zh.md](a1-02-open-closed.white-paper_zh.md) | "开源还是闭源？" | ds_flash, q9 |
| [a1-03-changan.white-paper_zh.md](a1-03-changan.white-paper_zh.md) | "还去长安吗？" | ds_flash, q9 |

**卡片**：李白（register=9, root_loss=0.60/0.75/0.95）

**生成参数**：详见 [GENERATION_METADATA.md](../GENERATION_METADATA.md)
