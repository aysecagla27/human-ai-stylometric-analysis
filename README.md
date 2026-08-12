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

## Key Results

The final DistilBERT model was evaluated on a held-out test set
across the 52-class authorship classification setting.

| Metric | Validation | Test |
|---|---:|---:|
| Accuracy | 76.38% | **74.67%** |
| Macro F1 | 0.7155 | **0.6740** |
| Weighted F1 | 0.7496 | **0.7360** |
| Loss | 1.2013 | **1.2541** |

The relatively small gap between validation and test performance suggests
that the final evaluation is consistent with the behavior observed during
model development.

Macro F1 is reported alongside accuracy because the task contains many
author classes and overall accuracy alone may obscure differences in
per-class performance.

## Human vs. ChatGPT Confidence Analysis

To further examine model behavior for the Human and ChatGPT classes,
the predicted probability assigned to the correct class was extracted
for samples belonging to each group.

| Group | Mean Confidence |
|---|---:|
| ChatGPT | **62.32%** |
| Human | **52.73%** |

A Welch independent-samples t-test was used to compare the two
confidence distributions:

- **t-statistic:** 5.0013
- **p-value:** 0.00000215

The difference in mean model confidence was statistically significant
at α = 0.05.

This result indicates that the model's confidence behavior differs
between Human and ChatGPT samples. It should not, however, be interpreted
as evidence that a specific stylometric characteristic causes this
difference.

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
