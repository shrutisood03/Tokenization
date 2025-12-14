
# 🤖 Tokenizer Comparison: BERT vs GPT

This document compares key tokenization behaviors across different Large Language Model (LLM) families—specifically BERT (WordPiece) and GPT (Byte Pair Encoding)—using practical code examples from the Hugging Face `transformers` library.

The comparison focuses on:

* Token splitting behavior
* Vocabulary differences
* Output token formats

---

## 🛠️ Setup

### Installation

Install the necessary dependencies:

```bash
pip install transformers
````

### Module Imports

Import the required tokenizer classes:

```python
from transformers import BertTokenizer, GPT2Tokenizer
```

-----

## 1️⃣ BERT Tokenizer (WordPiece)

BERT utilizes the **WordPiece** tokenization algorithm. It operates with a fixed vocabulary, typically forces lowercasing, and uses explicit markers for subwords.

### Initialize Tokenizer

We use the uncased base model for this example:

```python
bert_tokenizer = BertTokenizer.from_pretrained("bert-base-uncased")
```

### Example 1: Basic Text Tokenization

```python
text = "Tokenization matters"

tokens = bert_tokenizer.tokenize(text)
token_ids = bert_tokenizer.convert_tokens_to_ids(tokens)

print(f"Tokens: {tokens}")
print(f"Token IDs: {token_ids}")
```

**Output (Example):**

```
Tokens: ['token', '##ization', 'matters']
Token IDs: [19204, 3989, 14616]
```

**Key Observations:**

  * **Subword Prefix:** Subwords are prefixed with `##`.
  * **Case Handling:** The input text is automatically **lowercased**.
  * **Whitespace:** Whitespace is used as a separator but is **not preserved** in the tokens.

### Example 2: Rare Word Handling

This shows how an unknown or rare word is broken down into known subword pieces:

```python
text = "unbelievable"

tokens = bert_tokenizer.tokenize(text)
print(f"Tokens: {tokens}")
```

**Output:**

```
Tokens: ['un', '##bel', '##iev', '##able']
```

### Special Tokens

BERT requires specific special tokens for tasks like classification and sequence separation:

```python
bert_tokenizer.all_special_tokens
```

**Example Output:**

```
['[PAD]', '[UNK]', '[CLS]', '[SEP]', '[MASK]']
```

-----

## 2️⃣ GPT Tokenizer (Byte Pair Encoding)

GPT-style models (like GPT-2) use **byte-level BPE (BBPE)**. This method is designed to be universal, preserving case and explicitly marking spaces.

### Initialize Tokenizer

We use the standard GPT-2 model:

```python
gpt_tokenizer = GPT2Tokenizer.from_pretrained("gpt2")
```

### Example 1: Basic Text Tokenization

```python
text = "Tokenization matters"

tokens = gpt_tokenizer.tokenize(text)
token_ids = gpt_tokenizer.encode(text)

print(f"Tokens: {tokens}")
print(f"Token IDs: {token_ids}")
```

**Output (Example):**

```
Tokens: ['Token', 'ization', 'Ġmatters']
Token IDs: [30642, 1634, 11834]
```

**Key Observations:**

  * **Whitespace Marker:** The character `Ġ` (U+0120) represents a **leading space** and is explicitly included in the token.
  * **Case Handling:** **Case is preserved** (Note the capitalized 'Token').
  * **Subword Prefix:** There are no `##` markers; the subword structure is inferred from the token boundaries.

### Example 2: Rare Word Handling

The BPE algorithm breaks the word into the largest possible known subword units:

```python
text = "unbelievable"

tokens = gpt_tokenizer.tokenize(text)
print(f"Tokens: {tokens}")
```

**Output:**

```
Tokens: ['un', 'bel', 'ievable']
```

### Special Tokens

GPT models rely on a smaller, different set of special tokens, often using the same token for multiple boundary functions:

```python
gpt_tokenizer.special_tokens_map
```

**Example Output:**

```python
{'bos_token': '<|endoftext|>', 'eos_token': '<|endoftext|>', 'unk_token': '<|endoftext|>', 'pad_token': None}
```

-----

## 3️⃣ Direct Comparison: Key Differences

We compare the token lists for a hyphenated and punctuated phrase.

### Input Text

```python
text = "AI-driven security!"
```

### BERT Tokenization

```python
bert_tokenizer.tokenize(text)
```

**Output:**

```
['ai', '-', 'driven', 'security', '!']
```

### GPT Tokenization

```python
gpt_tokenizer.tokenize(text)
```

**Output:**

```
['AI', '-', 'driven', 'Ġsecurity', '!']
```

-----

## 🎯 Summary of Tokenizer Differences

| Feature | BERT (WordPiece) | GPT (BBPE) |
| :--- | :--- | :--- |
| **Algorithm** | WordPiece | Byte-Level BPE |
| **Case Handling** | Primarily **Lowercased** (e.g., `bert-base-uncased`) | **Case is Preserved** |
| **Whitespace Marker** | Implicit (Tokens are split by spaces) | **Explicit** (`Ġ` prefix for leading space) |
| **Subword Marker** | `##` prefix | None |
| **Special Tokens** | `[CLS]`, `[SEP]`, `[MASK]`, `[UNK]` | `<|endoftext|>` (often for BOS/EOS/UNK) |
