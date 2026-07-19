# A3: State Modifiers

> **Question**: Are the personality parameters (root_loss) causal or just decorative?
> **Answer**: Causally correlated. Change the numbers, the output shifts directionally — observable and reproducible.

## The Experiment

Same character (Li Bai), same LLM (ds_flash), same question — but with modified states:

| State / Mode | What it does | Effect on output |
|-------|-------------------|-----------------|
| Heavy cold | Semantic state modifier | More terse, lower energy, but still on-character |
| 20% power | Algorithmic state modifier | Less creative elaboration, more direct answers |
| Consultant | Role modifier — `--role consultant` flag | Shifts output from first-person persona to third-person analysis; same card, same question, two modes compared side by side |

→ See full outputs: [Heavy cold](a2-重感冒.white-paper_en.md) · [20% power](a2-20%.white-paper_en.md) · [Consultant (Standard vs Consultant mode)](a2-02-open-closed.white-paper_en.md) · [中文版](README.zh.md)

## Beyond the Experiment

State modifiers are not just a technical demo. They point to something larger: **a persona card that can reflect real-time state** — work mode, rest mode, focused mode, available mode. A card that knows "I'm tired today" and adjusts accordingly.

Combined with social protocols, this becomes **a new kind of profile card**: not a static bio, but a living presence that reflects the user's current state. Status modifiers = social protocol infrastructure.

→ See also: [B6: PEVM vs Verbalized Sampling — Controlled Diversity Comparison](../B6-benchmark/vs-diversity/B6-VS-diversity.en.md)
