# PEVM vs Training Data Benchmarks

> Every major training dataset today maps `question → answer` flatly.
> PEVM produces `question × persona → response` — structured personality data
> that no current dataset format can represent.

---

## The Gap

| Dataset | Format | Has persona dimension? |
|---------|--------|:---------------------:|
| Stanford Alpaca (52K) | `{instruction, input, output}` | ❌ |
| ShareGPT | `{conversations: [{from, value}]}` | ❌ |
| Databricks Dolly (15K) | `{instruction, context, response, category}` | ❌ |
| LLaMA-Factory standard | Alpaca / ShareGPT | ❌ |

All of them are flat. None can answer the same question **as different personas**.

## What PEVM Adds

| Capability | Existing datasets | PEVM |
|-----------|-----------------|:----:|
| Instruction fine-tuning (flat Q&A) | ✅ | ✅ |
| **Persona-conditioned instruction** (same question × N personas) | ❌ | ✅ |
| **Structured reasoning chain** (thesis → evidence → conclusion) | ❌ | ✅ |
| **Social relation data** (who interacts with whom, how) | ❌ | ✅ |
| **Fusion causality** (multiple sources → synthesized reasoning) | ❌ | ✅ |
| **Persona parameter tuning** (parameter change → output change) | ❌ | ✅ |

The same question ("what do you think of AI?") asked to Li Bai in 4 modes produces 4 completely different outputs — the difference comes from structured personality parameters, not prompt style.

## Current Output

Three formats (Alpaca-compatible, ShareGPT-compatible, and PEVM-extended), covering 63+ cards. **270 KB** of structured persona-conditioned data.