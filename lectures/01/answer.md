# Lecture 01 Answers

## Exercises

- Model's answer to the course-specific question (the 3 homework levels; a summary is fine): 
- What you noticed when comparing it with the correct meaning in the glossary: 
- Token counts you displayed (input / output): 

## Homework

- Level attempted: Basic
- What you did: Ran the same prompt ("What is LoRA?") 3 times across two models (`gemini-3.5-flash-lite` and `gemini-3.5-flash`) to compare outputs.
- Results:
  **gemini-3.5-flash-lite (3 runs)**
  - Run 1: Used an "acetate sheet over a painting" analogy. Focused on 99% parameter reduction and broad use cases.
  - Run 2: Used a "sticky notes on a textbook" analogy. Highlighted specific file sizes (10-100MB) and hardware efficiency.
  - Run 3: Used a "skyscraper" analogy. Introduced matrix decomposition mathematically ($W, A, B$).

  **gemini-3.5-flash (3 runs)**
  - Run 1: Used a "post-it notes" analogy. Explained rank decomposition matrices and zero inference latency.
  - Run 2: Used a "sidecar brain" analogy. Detailed matrix math ($\Delta W, A, B$) and modularity.
  - Run 3: Reused the textbook/sticky note analogy. Structured with clear technical steps (Freezing, Low-Rank Decomposition).

- Observations and questions:
  1. **Intra-model variation**: Each run produced a completely different analogy (paintings, textbooks, skyscrapers, sidecars) to explain the same core concept, showing high creative variance in formatting while keeping facts consistent.
  2. **Inter-model differences**: The `flash` outputs were slightly more structured, consistently integrating technical mechanisms (rank decomposition matrices, $\Delta W$) alongside the analogies. *(Note: The terminal logs printed `[model] gemini-3.5-flash-lite` for all 6 runs, suggesting the `AIE_MODEL` environment variable might not have been parsed correctly by the application script, which explains the strong similarities between both batches).*