# Tokenizer Models

A **tokenizer model** defines the rules and algorithms used to split input text into tokens based on a predefined vocabulary.

It determines how raw text is segmented before being converted into token IDs.

---

## Purpose of Tokenizer Models

Tokenizer models are designed to:

- Reduce vocabulary size
- Handle rare or unseen words
- Balance sequence length and representation quality
- Provide consistent token boundaries

---

## Common Tokenizer Approaches

### 1. Word-Level Tokenization
- Splits text by spaces or word boundaries
- Simple but inefficient for large vocabularies
- Struggles with unseen words

---

### 2. Character-Level Tokenization
- Treats each character as a token
- No out-of-vocabulary issues
- Produces very long token sequences

---

### 3. Subword-Level Tokenization
- Splits words into frequently occurring subunits
- Most commonly used approach in modern LLMs

---

## Popular Subword Tokenizer Models

### Byte Pair Encoding (BPE)
- Starts with characters and merges frequent pairs
- Commonly used in transformer-based models

### WordPiece
- Selects subwords based on likelihood
- Used in several NLP models

### Unigram Language Model
- Uses probabilistic token selection
- Chooses the most likely token sequence

---

## Example of Subword Tokenization

```
Input: "unbelievable"
Tokens: ["un", "believ", "able"]
```

This approach allows efficient handling of rare and compound words.

---

## Summary

Tokenizer models define:
- How text is split
- Which tokens are produced
- How flexible the tokenizer is with new inputs

They play a key role in model efficiency and behavior.