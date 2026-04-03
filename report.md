# Prompting vs. Fine-Tuning Analysis

When dealing with structured extraction tasks, our experiment cleanly highlights the threshold where prompt engineering begins to yield diminishing returns. Prompt engineering, even with severe constraint language ("DO NOT use markdown", "only valid JSON"), still suffered a base model parse success rate of just 35%. While intense few-shot prompting raised this to ~66% on a subset, it vastly inflated the token context window and still broke down on edge cases.

Fine-tuning inverted this entirely. With just 80 heavily curated examples modifying mere adapter weights via LoRA, parse consistency skyrocketed to 95%. LoRA taught the model to treat the JSON schema as an unshakeable structural requirement, while leaving the base model's semantic reasoning capabilities (its ability to recognize a company name or a tax line) intact.

**When to use Prompt Engineering:**
Prototyping, low-volume pipelines, or scenarios where output schema changes daily. If parsing failure is acceptable or requires human-in-the-loop review anyway, prompting is cheaper to start.

**When to use Fine-Tuning:**
Production enterprise pipelines where API automation requires 99% parse reliability. When every token counts (few-shot context windows are expensive), Fine-Tuning front-loads the cost. The fine-tuned 3B parameter model performs as consistently as GPT-4 for this narrow task, saving massive compute costs long-term.
