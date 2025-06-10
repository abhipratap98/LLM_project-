How Does a Multilingual LM Handle Multiple Languages?



Overview

This project explores the multilingual capabilities of the BLOOM-1.7B language model through a series of tasks:

Measuring word embedding similarity across languages
Probing the model for multilingual language understanding
Evaluating cross-lingual transferability in a zero-shot setting
Our findings reveal that BLOOM-1.7B effectively encodes semantic relationships across languages and demonstrates strong cross-lingual transfer, with performance influenced by language similarity and resource availability.

Objectives

Analyze how BLOOM-1.7B encodes cross-lingual semantic similarity.
Probe layer-wise multilingual understanding using XNLI.
Assess the model's ability to perform zero-shot transfer across high and low-resource languages.
Understand challenges in multilingual representation learning.
Tasks

Task 1: Word Embedding Similarity
→ Evaluate cosine similarity of word embeddings across multiple languages.

Task 2: Probing
→ Perform a multilingual NLI task (XNLI) using a layer-wise probing classifier.

Task 3: Cross-Lingual Transferability
→ Fine-tune on English NLI, test on 13 other languages in a zero-shot setup.

Model Architecture

Base Model: BLOOM-1.7B (frozen parameters)
Probing Classifier: Transformer block + MLP classification head
Training Strategy: Lightweight classification head trained on top of BLOOM representations.
Dataset

Task 1: Parallel word dataset (992 words, 5 languages: EN, FR, ES, HI, ZH)
Task 2 & 3: XNLI dataset
15 languages
Premise-Hypothesis pairs
Entailment labels (Entailment, Neutral, Contradiction)
Preprocessing

Tokenization with BLOOM tokenizer.
Handling subword tokenization:
Word embedding = average of subword embeddings.
XNLI prompting: "Premise: <sentence1> <sep> Hypothesis: <sentence2>"
Experimental Setup

Framework: PyTorch + HuggingFace Transformers
Hardware: NVIDIA A100 GPU
Hyperparameters:
Batch Size: 16
Epochs: 60
Optimizer: Adam
Loss: Cross-Entropy Loss
Results (Selected)

Task	Observation
Word Embedding Similarity	High alignment for related languages; challenges for typologically distant languages.
Probing (XNLI)	Middle layers (Layers 13-16) encode the most generalizable multilingual representations.
Cross-Lingual Transferability (XNLI)	High-resource languages perform well; significant drop in low-resource languages.
Zero-Shot Accuracies:

English: 59.4%
French: 47.4%
Spanish: 42.0%
Hindi: 40.0%
Swahili, Arabic, Urdu: ~29-31%
Contributions

Introduced a systematic evaluation pipeline for BLOOM-1.7B’s multilingual understanding.
Conducted in-depth analysis of layer-wise encoding and cross-lingual transfer.
Highlighted strengths and limitations of BLOOM in multilingual NLP applications.
Provided actionable insights for improving multilingual LMs.
Future Work

Fine-tune BLOOM for low-resource languages.
Extend probing to more linguistic features (morphology, syntax).
Explore adapter-based fine-tuning for efficient multilingual adaptation.
Investigate alignment techniques to bridge distant language gaps.
References

T. Le Scao et al., BLOOM: A 176B-Parameter Open-Access Multilingual Language Model, 2022.
A. Conneau et al., XNLI: Evaluating Cross-Lingual Sentence Representations, 2018.
J. Devlin et al., BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding, 2019.
T. Pires et al., How Multilingual is Multilingual BERT?, 2019.
Achiam et al., GPT-4 Technical Report, 2023.
