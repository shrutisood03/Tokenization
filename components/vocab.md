# Vocabulary in Tokenization

In the context of Large Language Models (LLMs), a **vocabulary** is the fixed set of tokens that a tokenizer can produce and that the model can understand.

Each token in the vocabulary is mapped to a unique numerical identifier (token ID), which is used internally by the model.

---

## What the Vocabulary Contains

A tokenizer’s vocabulary may include:

- Full words (e.g., `computer`)
- Subwords (e.g., `comp`, `uter`)
- Characters
- Punctuation marks
- Whitespace-prefixed tokens
- Special control tokens

The exact contents depend on the tokenizer design and training data.

---

## Vocabulary Size

Typical vocabulary sizes for LLMs range from:

- **30,000 to 50,000 tokens** for many transformer-based models
- Larger vocabularies reduce token splitting
- Smaller vocabularies increase reuse of subwords

There is a trade-off between:
- Vocabulary size
- Model complexity
- Token sequence length

---

## Token ID Mapping

Each token in the vocabulary is assigned a unique integer ID.

Example:
```
"token" → 2431
"ization" → 9821
```

During inference and training:
- Text → tokens → token IDs
- The model operates only on token IDs

---

## Out-of-Vocabulary Handling

Modern LLMs avoid traditional “out-of-vocabulary” issues by using **subword tokenization**.  
Unseen or rare words are broken down into known sub-components rather than being rejected.

---

## Summary

The vocabulary defines:
- What tokens are valid
- How text is represented numerically
- The limits of what the model can directly encode

Vocabulary design is a foundational component of tokenization and LLM behavior.

