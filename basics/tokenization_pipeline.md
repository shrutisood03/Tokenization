# Tokenization Pipeline for LLMs

This pipeline transforms raw text into numerical tokens that can be processed by Large Language Models (LLMs). Each step is crucial for ensuring consistency, efficiency, and quality in model input.

| Step | Name                      | Description                                                                                                   | Example Input/Output                                      |
|------|---------------------------|--------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| 1    | **Text Normalization**    | Converts text to a standard format: lowercasing, Unicode normalization, and standardizing special characters. | Input: `HELLO World!!`<br>Output: `hello world!!`         |
| 2    | **Pre-tokenization**      | Splits text on whitespace and separates punctuation to create basic units (tokens).                           | Input: `Hello, world!`<br>Output: `[Hello, ,, world, !]`  |
| 3    | **Subword Segmentation**  | Breaks tokens into subwords using algorithms like BPE or WordPiece, allowing handling of unseen words.        | Input: `[unhappy, ness]`<br>Output: `[un, happy, ness]`   |
| 4    | **Token-to-ID Mapping**   | Maps each token or subword to a unique integer ID, creating a numerical representation for the model.         | Input: `[un, happy, ness]`<br>Output: `[312, 1456, 908]`  |
| 5    | **Post-processing**       | Adds special tokens (e.g., `[CLS]`, `[SEP]`), pads sequences, and prepares the final input for the model.     | Before: `[312, 1456, 908]`<br>After: `[101, 312, 1456, 908, 102]` |

---

## Why it Matters

- **Tokenization affects:** Token count, context usage, computational cost, and output quality.
- **Key:** Understanding this process is foundational for working with LLMs and optimizing/debugging their behavior.