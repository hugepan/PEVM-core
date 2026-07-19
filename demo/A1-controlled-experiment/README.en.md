# A1: Controlled Experiment — Does the Card Change Output?

> **TL;DR**: Yes. Same role (Li Bai), same question, same LLM — with vs without a PEVM card. The card consistently shifts output style, stance, and depth. Effect holds across 2 models (ds_flash, q9) and 3 different questions.

## Experiments

| File | Question | Models |
|------|----------|--------|
| [a1-01-ai-opinion.white-paper_en.md](a1-01-ai-opinion.white-paper_en.md) | "What do you think of AI?" | ds_flash, q9 |
| [a1-02-open-closed.white-paper_en.md](a1-02-open-closed.white-paper_en.md) | "Open source or closed source?" | ds_flash, q9 |
| [a1-03-changan.white-paper_en.md](a1-03-changan.white-paper_en.md) | "Would you still go to Chang'an?" | ds_flash, q9 |

**Card**: Li Bai (register=9, root_loss=0.60/0.75/0.95)

**Generation parameters**: See [GENERATION_METADATA.md](../GENERATION_METADATA.md)
