# Tokenization Case Studies in LLMs

This repository contains **two case studies** illustrating how tokenization affects the behavior and performance of large language models (LLMs). Each case study includes examples, token sequences, Python code, and insights.

---

## Case Study 1 — GPT-3 and Byte-Level BPE

**Scenario:** GPT-3 uses byte-level BPE to process diverse internet text including emojis, symbols, and non-Latin characters.

**Example Input:**
```
Hello 👋, welcome to AI!
```

**Tokenization (Byte-Level BPE):**

| Token | Meaning |
|-------|---------|
| H | H |
| e | e |
| l | l |
| l | l |
| o | o |
|   | space |
| 👋 | emoji |
| , | comma |
|   | space |
| w | w |
| e | e |
| l | l |
| c | c |
| o | o |
| m | m |
| e | e |
|   | space |
| t | t |
| o | o |
|   | space |
| A | A |
| I | I |
| ! | exclamation |

**Python Hugging Face Example:**
```python
from transformers import GPT2Tokenizer

tokenizer = GPT2Tokenizer.from_pretrained("gpt2")  # GPT-3 uses similar BPE
text = "Hello 👋, welcome to AI!"
tokens = tokenizer.tokenize(text)
print(tokens)
print(tokenizer.convert_tokens_to_ids(tokens))

```

```
Input Text → Byte-Level BPE Tokenizer → Token IDs → Model Input
"Hello 👋" → ['H','e','l','l','o',' ', '👋'] → [72,101,108,...] → Embeddings
```

