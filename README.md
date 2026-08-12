# Linguistic Boundaries Between Human and Machine Writing

A stylometric and transformer-based analysis of human authorship and ChatGPT-generated text using the Reuters C50 and HC3 datasets.

## Overview

This project investigates whether human authors and ChatGPT exhibit distinguishable linguistic patterns.
The study combines traditional stylometric features with a fine-tuned DistilBERT classifier to analyze:

- 50 individual Reuters journalists
- Generic human-written responses from HC3
- ChatGPT-generated responses from HC3

The final task is formulated as a **52-class authorship classification problem**.

## Research Question

> To what extent can human linguistic signatures and LLM-generated writing be distinguished using stylometric analysis and transformer-based classification?

## Datasets

### Reuters C50
Authorship attribution dataset containing texts written by 50 professional journalists.

### HC3
Human–ChatGPT comparison dataset containing human-written and ChatGPT-generated responses from multiple domains.

## Methodology

The project follows the pipeline below:

1. Reuters C50 and HC3 data loading
2. Dataset cleaning and balancing
3. Stylometric feature extraction
4. PCA-based style visualization
5. DistilBERT fine-tuning
6. Class-weighted training
7. Model evaluation
8. Statistical significance testing
9. Manual inference experiments

## Stylometric Features

The analysis includes:

- Word count
- Average sentence length
- Average word length
- Type-Token Ratio (TTR)
- Lexical diversity
- Repetition rate
- Stopword ratio
- Punctuation ratio

## Model

The classification model is based on:

`distilbert-base-uncased`

A custom class-weighted training strategy is used to reduce the effect of class imbalance between Reuters authors and the larger Human/ChatGPT groups.

## Results

| Metric | Result |
|---|---:|
| Test Accuracy | 74.0% |
| Macro F1 | 0.68 |
| Number of Classes | 52 |

The model showed substantial overlap between Human and ChatGPT writing while still identifying statistically significant differences in model confidence.

## Statistical Analysis

An independent-samples t-test was applied to the model confidence scores for Human and ChatGPT samples.

- ChatGPT mean confidence: **65.61%**
- Human mean confidence: **59.22%**
- p-value: **0.00607**

## Technologies

Python · PyTorch · Hugging Face Transformers · DistilBERT · spaCy · scikit-learn · pandas · NumPy · Matplotlib

## Future Work

- Evaluation on additional LLMs
- Cross-domain robustness analysis
- Explainable AI-generated text detection
- Human–LLM collaborative writing
- Hybrid stylometric + transformer models

## Author

**Ayşe Çağla Can**  
Master's Student in Computer Engineering  
Ankara University
