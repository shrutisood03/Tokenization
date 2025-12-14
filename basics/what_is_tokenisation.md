# What is Tokenization?

Tokenization is the process of converting raw text into smaller units called **tokens**, which are then used as input to a Large Language Model (LLM).

LLMs do not process text directly. Instead, text is transformed into tokens and then mapped to numerical identifiers. These token IDs are what the model operates on internally.

---

## Definition of a Token

A **token** is a unit of text defined by the tokenizer. Depending on the tokenizer design, a token can represent:

- A full word
- A subword
- A single character
- Punctuation or symbols
- Whitespace

Token boundaries are determined by the tokenizer, not by grammatical rules.

---

## Basic Example
```
Input Text: "Tokenization is important"
Tokens: ["Token", "ization", " is", " important"]
```

This illustrates that:

- Words can be split into multiple tokens
- Spaces may be included in tokens
- Tokenization is more flexible than word-based splitting

---

## Role of Tokenization in LLMs

Tokenization is the first step in the LLM processing pipeline.
```
Text → Tokens → Token IDs → Embeddings → Transformer Model
```
After tokenization:

- The original text is no longer visible to the model
- All computations and predictions occur at the token level

---

## Token vs Word vs Character

| Unit       | Description                              |
|------------|------------------------------------------|
| Word       | Human-defined linguistic unit             |
| Character | Individual letters or symbols             |
| Token      | Model-defined unit used for computation   |

Modern LLMs typically use **subword-level tokenization**, which provides a balance between vocabulary size and flexibility.

---

## Common Tokenization Approaches

Several tokenization strategies are commonly used in NLP and LLMs:

- Word-level tokenization
- Character-level tokenization
- Subword-level tokenization

Subword-level tokenization is often implemented using methods such as:

- Byte Pair Encoding (BPE)
- WordPiece

---

## Summary

Tokenization defines how text is segmented and represented before being processed by an LLM.  
The choice of tokenization strategy directly influences vocabulary size, input length, and model behavior.