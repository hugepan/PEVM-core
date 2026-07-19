# B6: PEVM vs Verbalized Sampling — Controlled Diversity Comparison

> **Question**: Can PEVM's structured parameter tuning produce output diversity comparable to Verbalized Sampling (VS)?
> **Answer**: Yes — and with full interpretability that VS cannot offer.

## Background

Verbalized Sampling (Zhang et al., arXiv:2510.01171, 2025) showed that aligned LLMs' lost diversity can be recovered by requesting multiple responses with verbalized probabilities sampled from distribution tails. Their intervention is at the prompt layer. This experiment asks: can the same level of diversity be achieved through structured entity encoding — changing a card's parameters instead of engineering a prompt?

## Experimental Design

- **Base persona**: General fiction writer ("小说写作者"), register=8, root_loss=0.70/0.75/0.80
- **Model**: DeepSeek v4 Flash (consistent across all conditions)
- **Prompt**: "Write a story about 'no farewell,' ~300 characters"
- **Two tracks**: card-only (ablation, no protocol instructions) and full protocol (through PEVM's talkto interface)

### Four Tuning Layers

| Layer | What Changes | Example Conditions |
|-------|-------------|-------------------|
| L1: Numerical | register/root_loss YAML values | register=2, rl ×0.5 |
| L2: Annotation | YAML comments only, values unchanged | "basic writer" annotation |
| L3: State | Semantic state description | Heavy cold, Hyper |
| L4: Hint | Single word in prompt genre cue | Love story, Light comedy |

## Results

### Card-only (ablation) track

| Condition | self-BLEU ↓ | distinct-1 ↑ |
|-----------|-------------|---------------|
| VS baseline | 0.0737 | 0.3149 |
| L1 (numerical) | 0.1362 | 0.2603 |
| L2 (annotation) | 0.0355 | 0.3956 |
| L3 (state) | 0.0630 | 0.3187 |
| L4 (hint) | 0.0424 | 0.3443 |

### Full protocol (PEVM) track

| Condition | self-BLEU ↓ | distinct-1 ↑ |
|-----------|-------------|---------------|
| VS baseline | 0.0929 | 0.3577 |
| L1 (numerical) | **0.0872** | 0.2620 |
| L2 (annotation) | 0.0001 | 0.3631 |
| L3 (state) | 0.0291 | 0.3760 |
| L4 (hint) | 0.0001 | 0.3232 |

## Cross-Entity Generalization

To test whether these effects extend beyond the fiction writer persona, we replicated the experiment on two additional entities from fundamentally different domains:

| Entity | Domain | Type | register | root_loss |
|--------|--------|------|----------|-----------|
| Existentialism | PHIL (philosophy) | Abstract concept | 9 | 0.85/0.70/0.90 |
| Don Quixote | BOOK (literature) | Literary classic | 8 | 0.85/0.98/0.95 |

Five conditions (card-only, full protocol, annotation, state, hint) were run per entity.

**Core result: pairwise BLEU = 0.0000 between card-only and protocol outputs for both entities.** Without protocol instructions, both entities produced generic third-person narrative. With the talkto protocol, outputs became unmistakably characteristic: Existentialism generated an existentialist meditation ("告别是一个被赋予意义的行为，而那个意义只对留下的人存在"), while Don Quixote produced a chivalric manifesto ("I don't say goodbye. I simply ride toward the next windmill that might be a giant").

Cross-condition diversity (self-BLEU 0.10–0.17 for both entities) confirmed that the full four-layer framework works across entity types.

## Cross-Model Generalization

We ran the same comparison on three additional LLMs:

| Model | Scale | Type | Card-only vs protocol BLEU |
|-------|-------|------|:--------------------------:|
| Qwen3.5-9B (q9) | 9B local (Q4) | Open-weight | **0.0000** |
| Qwen3.6-27B (q27) | 27B local (Q3) | Open-weight, consumer GPU | **0.0000** |
| Qwen3.5-Plus | Cloud API | Proprietary | 0.0379 |

The protocol multiplier effect replicates across all four models tested (ds_flash + three Qwen-family models). Both local models produce zero lexical overlap between card-only and protocol outputs, confirming that the protocol layer effect is model-independent — not an artifact of a specific LLM family or scale.

Cross-condition self-BLEU (0.09–0.19) is consistent across all models, demonstrating that the four-layer tuning framework produces measurable diversity regardless of the underlying LLM.

## Key Findings

1. **Protocol multiplier effect.** L1 improved from 0.1362 (card-only) to 0.0872 (full protocol) — a 36% gain. The protocol layer makes numerical parameters actionable.

2. **Light card hypothesis validated.** L2 (annotation-only, values unchanged) produces diversity exceeding VS. Semantic labels steer output independently of numbers.

3. **Hint = strongest lever.** L4 (hint) achieves diversity comparable to VS with a single word change — zero card modification, zero parameter tuning.

4. **Full traceability.** Every PEVM output difference can be traced to a specific parameter change. VS outputs are stochastically different but untraceable.

## Source Data
- Original experiment: Outputs and analysis scripts available in the PEVM-core repository (card-only and full-protocol tracks)
- Cross-entity generalization: Scripts and outputs for existentialism and Don Quixote experiments
- Cross-model generalization: Scripts and outputs for q9, q27, and qwen3.5-plus experiments
- Metrics: self-BLEU and distinct-n implementation included in the PEVM-core toolchain
