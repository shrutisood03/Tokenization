## Case Study 2 - Multilingual Models (XLM-R / mBERT)
**Scenario:** Tokenizing English, Hindi, and Arabic with a shared subword vocabulary.

**Example Input:**
```
English: Hello  
Hindi: नमस्ते  
Arabic: مرحبا

```
**Tokenization (XLM-R):**

| Language | Tokens |
|----------|--------|
| English  | `['Hello']` |
| Hindi    | `['न', '##म', '##स्', '##ते']` |
| Arabic   | `['مر', '##حب', '##ا']` |



**Python Hugging Face Example:**
```python
from transformers import XLMRobertaTokenizer

tokenizer = XLMRobertaTokenizer.from_pretrained("xlm-roberta-base")
text = ["Hello", "नमस्ते", "مرحبا"]
tokens = [tokenizer.tokenize(t) for t in text]
print(tokens)
```

```
Text (multi-language) → Shared Subword Tokenizer → Tokens → Embeddings
Hello, नमस्ते, مرحبا → ['Hello'], ['न','##म','##स्','##ते'], ['مر','##حب','##ا'] → IDs
```