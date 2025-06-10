# How Does a Multilingual LM Handle Multiple Languages?



## Abstract

In this study, we explore the multilingual capabilities of the pre-trained **BLOOM-1.7B** model through a series of tasks: **similarity between word embeddings across languages**, **probing for language understanding**, and **cross-lingual transferability**. The results show that BLOOM-1.7B effectively encodes semantic relationships across languages and demonstrates cross-lingual transferability, with performance depending on **language similarity** and **resource availability**. Our analysis offers insights into BLOOM’s potential for **zero-shot learning** in low-resource languages.

---

## 1 Introduction

### 1.1 Background

Transformer-based LLMs have shown great progress in multilingual NLP. Understanding what linguistic information these models capture—syntax, semantics, morphology—is critical. Probing techniques allow us to analyze model representations and cross-lingual capabilities.

This project investigates the multilingual abilities of **BLOOM-1.7B**, focusing on:
- Word embedding similarity across languages
- Probing for syntactic and semantic understanding
- Cross-lingual transferability to low-resource languages

---

## 2 Related Work

- Models: **BERT**, **XLM-R**, **mBART**, **mBERT**, **GPT-based**
- Probing studies show higher transformer layers capture semantics; lower layers syntax
- Cross-lingual transfer critical for **low-resource languages**
- Embedding alignment (e.g. **MUSE**) remains a key challenge

BLOOM-1.7B leverages **shared subword tokenization** and **cross-lingual pretraining**, providing a promising architecture for multilingual tasks.

---

## 3 Methodology

### Task 1: Similarity between Word Embeddings

- 992 words translated into **English, French, Spanish, Chinese, Hindi**
- Embeddings extracted, normalized, compared using **cosine similarity**
- Results show consistent semantic alignment across languages

### Task 2: Probing to Understand Model Behavior

- **XNLI** dataset used for multilingual **textual entailment**
- Probing classifier (Transformer block + MLP head) trained on top of frozen BLOOM layers
- Layer-wise analysis reveals **middle layers** capture most generalizable multilingual features

### Task 3: Cross-Lingual Transferability

- Fine-tuned BLOOM on English **XNLI**
- Tested zero-shot on 13 languages (Swahili, Arabic, Urdu, etc.)
- Insights on how BLOOM transfers knowledge to low-resource languages

---

## 4 Dataset

- **Word Similarity:** Custom dataset with translations (Google Translate)
- **XNLI:** Cross-lingual NLI dataset (15 languages)
  - Premise-Hypothesis pairs with entailment labels

---

## 5 Experimental Setup

- **Model:** BLOOM-1.7B (Frozen backbone)
- **Classifier:** Transformer block + 2-layer MLP head
- **Training:** 60 epochs
- **Batch Size:** 16
- **Evaluation:** Layer-wise accuracy on validation set

---

## 6 Results

### Task 1: Word Similarity

- Strong alignment for **English, French, Spanish**
- Lower alignment for typologically distant languages (**Chinese**, **Hindi**)
- Performance correlates with **training data representation** and **script similarity**

### Task 2: Probing

| Layer  | Avg Accuracy (%) |
|--------|------------------|
| Layer 16 | 57.78 |
| Layer 13 | 57.54 |
| Layer 14 | 57.22 |
| ...    | ...  |
| Layer 24 | 43.18 |

- **Middle layers** (Layer 13–16) most effective for multilingual understanding
- Final layers more task-specific and less generalizable

### Task 3: Cross-Lingual Transferability

| Language | Accuracy |
|----------|----------|
| English  | 59.4%    |
| French   | 47.4%    |
| Spanish  | 42.0%    |
| Hindi    | 40.0%    |
| Swahili  | 31.2%    |
| Arabic   | 29.4%    |
| Urdu     | 29.4%    |

- **High-resource languages** perform better
- **Low-resource languages** need further targeted fine-tuning
- **Script differences** impact transferability

---

## 7 Conclusion

Our study demonstrates that **BLOOM-1.7B** effectively encodes semantic relationships across multiple languages and supports **cross-lingual transfer**. Performance varies with **language similarity**, **training data availability**, and **script alignment**. The model shows promise for **zero-shot learning** in low-resource languages, but further work is needed to close the performance gap.

---

## 8 Contribution

- **2023AIB2072**: Task 1, Task 3, Report  
- **2023AIB2079**: Task 2, Report  

---

## References

- OpenAI, GPT-4 Technical Report
- Alexis Conneau et al., XNLI: Cross-lingual Natural Language Inference
- Devlin et al., BERT
- Pires et al., How Multilingual is Multilingual BERT?
- Teven Le Scao et al., BLOOM: Open Multilingual Language Model

---

