# Detection and Analysis of Hate Speech in Social Media against Women and Immigrants



---

## 📝 Overview

This project focuses on detecting and analyzing hate speech targeting **women** and **immigrants** on social media (Twitter), in **English** and **Spanish**. The system integrates **BERT** embeddings with **LSTM** and **MLP** architectures to capture both deep contextual and sequential aspects of hate speech.

It addresses key challenges such as:
- Sarcasm, double entendre, and subtle hate
- Multilingual content (English and Spanish)
- Informal and creative social media language

Our models outperform traditional methods in both accuracy and F1-score.

---

## 🎯 Objectives

- Develop a hybrid deep learning architecture using **BERT + BiLSTM / MLP**
- Implement robust preprocessing for noisy social media text
- Handle multilingual data and code-switching
- Advance real-world hate speech detection for safer online environments

---

## 📚 Tasks

**Task A:** Binary classification  
→ Detect if a tweet is **hateful** or **not hateful**.

**Task B:** Multi-label classification  
→ For hateful tweets:
- Classify as **aggressive** or **non-aggressive**.
- Identify whether the target is an **individual** or a **group**.

---

## 🏗️ Model Architectures

- **BERT + BiLSTM:** Captures deep contextual understanding + sequence modeling.
- **BERT + MLP:** Leverages BERT embeddings + simple feedforward classifier.

---

## 📂 Dataset

- **Source:** SemEval-2019 Task 5
- **Languages:** English and Spanish
- **English:** 9000 train, 1000 dev, 2000 test tweets  
- **Spanish:** 4469 train, 500 dev, 415 test tweets  
- Annotations:
  - `HS` (Hate Speech): 1/0
  - `TR` (Target Range): Individual or Group
  - `AG` (Aggressiveness): Aggressive or Non-aggressive

---

## 🛠️ Preprocessing

- Tokenization using `BertTokenizer`
- Cleaning non-standard text
- Handling of emojis/emoticons
- Normalization & case folding
- Hashtag splitting & extended character normalization

---

## ⚙️ Experimental Setup

- **Framework:** PyTorch + HuggingFace Transformers
- **Hardware:** NVIDIA Tesla K80 GPU
- **Hyperparameters:**
  - Batch Size: `32`
  - Epochs: `15`
  - Optimizer: `Adam`
  - Loss: `Cross-Entropy Loss`

---

## 📊 Results (Selected)

| Task                     | F1-score (EN BERT+BiLSTM) | F1-score (ES BERT+BiLSTM) |
|--------------------------|--------------------------|--------------------------|
| Hate / Not Hate          | 96.2                     | 75.2                     |
| Individual / Group       | 96.6                     | 80.6                     |
| Aggressive / Non-aggressive | 93.5                  | 75.5                     |

Our **BERT+BiLSTM** consistently outperforms **BERT+MLP** and baseline methods.

---

## 💡 Contributions

- Introduced a hybrid **BERT + BiLSTM** architecture for nuanced hate speech detection.
- Designed a preprocessing pipeline specific to social media text.
- Demonstrated superior performance in multilingual and subtle hate speech detection.
- Contributed to safer digital spaces through improved moderation tools.

---

## 🚀 Future Work

- Develop **cross-lingual models**.
- Improve handling of **sarcasm**, **pragmatics**, and **emerging slang**.
- Enable **real-time detection** and feedback loops.
- Collaborate with **social scientists** for broader insights.

---

## 📚 References

1. Valerio Basile et al., *SemEval-2019 Task 5*
2. Marzieh Mozafari et al., *BERT-Based Transfer Learning for Hate Speech Detection*
3. María Antonia Paz et al., *Hate Speech: A Systematized Review*
4. Alison Ribeiro et al., *CNNs for Hate Speech Detection Against Women and Immigrants*

---
