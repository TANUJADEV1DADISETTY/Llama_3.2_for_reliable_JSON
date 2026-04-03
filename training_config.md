# LoRA Training Configuration Justification
- **Dataset**: `curated_train.jsonl` (80 highly varied examples).
- **Fine-Tuning Method**: LoRA (Low-Rank Adaptation)
- **LoRA Rank (r)**: 16. Justification: For structured output formatting matching a fixed schema rather than learning deep new domain knowledge, an r of 16 provides an excellent balance: high enough capacity to learn the JSON constraints smoothly, low enough to evade severe overfitting on a tiny dataset of 80 examples.
- **LoRA Alpha**: 32. Justification: Setting alpha to exactly 2x rank scales the adapter weights correctly against the base model weights, standardizing the learning rate effect.
- **Learning Rate**: 2e-4. Justification: Standard LR for instruction-tuned 3B parameters using LoRA.
- **Epochs**: 3. Justification: Our loss curve typically converges by epoch 2. Pushing past epoch 4 drastically increases layout hallucination/overfitting to our 80 examples.
- **Batch Size**: 4 (with gradient accumulation of 2 for effective batch size 8).
