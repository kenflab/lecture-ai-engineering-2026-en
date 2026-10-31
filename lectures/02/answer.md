# Lecture 02 Answers

## Exercises

- Model and settings used (from `config` in `result.json`): Qwen/Qwen3.5-0.8B (lora_r=16, lora_alpha=32, lr=0.0002, num_train_epochs=20, warmup_steps=6)
- Did you run training yourself (`executed_training_myself`): Yes (completed all cells up to section 7 on Google Colab GPU)
- Before training: `format_rate` = 0.952 / `content_rate` = 0.381
- After training: `format_rate` = 1.000 / `content_rate` = 0.905
- Questions that regressed: None (`[]`)
- Failures remaining after training and their types: 2 failures out of 21. Both were content/grounding errors:
  - Evasion through a confirmation request despite evidence being present (Question 6: asserted need for confirmation when format restriction was in FAQ).
  - Assertion without evidence (Question 20: generated office hour hours instead of flagging that appointment necessity was ungrounded).
  - Broken format: 0 cases.
- Results of knowledge questions (section 6; classification before → after training) and observations:
  - Pre-training: Answered general knowledge questions directly or gave partial guesses.
  - Post-training: Appropriately flagged out-of-domain questions with `needs_review: true` while outputting strict JSON format.
- What changed and what stayed the same with training:
  - Changed: Strict adherence to JSON schema (100%) and reliable grounding classification (`needs_review`).
  - Stayed the same: Core language capability and factual limitations outside the provided context.

## Homework

- Level attempted: Basic
- Settings or data changed: Increased LoRA rank `lora_r` from 16 to 32 (`lora_alpha` kept at 32).
- Results (comparison tables or numbers):

| Metric | Original (`lora_r=16`) | Modified (`lora_r=32`) |
| :--- | :--- | :--- |
| `format_rate` (after) | 1.000 (21/21) | 1.000 (21/21) |
| `content_rate` (after) | 0.905 (19/21) | 0.905 (19/21) |
| Final Training Loss | ~0.015 | 0.01505 |
| Training Time | ~200 s | 204 s |

- Discussion of when fine-tuning is and is not suitable:
  - **Suitable**:
    - Enforcing strict output formats, schema conformance (e.g., JSON), or response tone.
    - Adapting models to domain-specific syntax or specialized task structures where low inference latency is required.
  - **Not suitable**:
    - Injecting fast-evolving factual knowledge or vast databases (retrieval-augmented generation is more cost-effective and accurate).
    - Scenarios with insufficient training data, as models easily hallucinate or overfit rather than acquiring actual knowledge.
    