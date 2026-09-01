# Arabic Medical Dataset Preprocessing

> **A large-scale Arabic NLP preprocessing workflow for cleaning, normalizing, restructuring, and preparing medical question-answer data for machine learning applications.**

## Overview

This project focuses on the preprocessing and preparation of a large Arabic medical question-answer dataset for downstream Natural Language Processing (NLP) and machine learning tasks.

The dataset contains **800K+ Arabic question-answer records across 90 medical categories**. The preprocessing workflow addresses common challenges in Arabic text data, including inconsistent writing conventions, textual noise, category fragmentation, class imbalance, duplicate records, and variable text length.

The resulting data is structured into smaller, more manageable subsets suitable for experimentation with machine learning and NLP models.

---

## Project Highlights

| Component              | Description                           |
| ---------------------- | ------------------------------------- |
| Dataset                | Arabic medical question-answer corpus |
| Original size          | 800K+ records                         |
| Original categories    | 90                                    |
| Final major categories | 20                                    |
| Language               | Arabic                                |
| Task                   | Dataset preprocessing and preparation |
| Sampling               | Category-aware sampling               |
| Text processing        | Arabic normalization and cleaning     |
| Tokenization           | NLTK                                  |
| Output                 | Processed CSV subsets                 |

---

## Objective

The primary objective was to transform a large and inconsistently formatted Arabic medical Q&A dataset into a cleaner and more structured corpus suitable for downstream machine learning experiments.

The workflow includes:

* Arabic text normalization
* Removal of diacritics and tatweel
* URL and unwanted-character removal
* Category consolidation
* Rare-category filtering
* Category-aware sampling
* Tokenization
* Duplicate removal
* Text-length handling
* Stopword removal
* Export of processed subsets

---

## Dataset

The project uses the **Arabic Healthcare Dataset (AHD)**, a large Arabic medical Q&A dataset containing more than **808K questions and answers distributed across 90 categories**.

The original dataset contains substantial variation in category sizes, with some categories containing hundreds of thousands of records while others contain only a small number of examples.

This imbalance creates challenges for downstream classification experiments and motivates the category consolidation and filtering steps implemented in the preprocessing workflow.

### Original Dataset Characteristics

* **800K+** question-answer records
* **90** medical categories
* Arabic text
* Question-answer format
* Highly imbalanced category distribution
* Raw text requiring preprocessing

> The original dataset is not included in this repository.

---

## Preprocessing Workflow

The notebook implements the following preprocessing stages:

```text
Raw Arabic Medical Dataset
            │
            ▼
     Text Cleaning
            │
            ├── Remove leading/trailing whitespace
            ├── Remove tatweel
            ├── Remove diacritics
            ├── Remove URLs
            └── Remove unwanted characters
            │
            ▼
     Arabic Normalization
            │
            ▼
    Category Consolidation
            │
            ▼
     Rare Category Removal
            │
            ▼
    Category-Aware Sampling
            │
            ▼
       Tokenization
            │
            ▼
      Deduplication
            │
            ▼
     Length Processing
            │
            ▼
      Stopword Removal
            │
            ▼
       CSV Subsets
```

---

## Arabic Text Preprocessing

The preprocessing workflow applies several transformations designed to reduce unnecessary variation and noise in the Arabic text.

### Text normalization

The workflow handles:

* Arabic diacritics
* Tatweel characters
* Different forms of Alef
* Selected Arabic character variations
* Leading and trailing whitespace

### Noise removal

The workflow removes:

* URLs
* Unwanted characters
* Selected punctuation
* Other non-Arabic characters according to the preprocessing rules

### Tokenization

Processed questions and answers are tokenized using **NLTK's word tokenizer** before subsequent processing steps.

---

## Category Consolidation

The original dataset contains 90 categories with significant fragmentation and imbalance.

Related categories are consolidated into broader specialist-oriented categories to produce a more manageable classification structure.

Examples include:

| Original categories   | Consolidated category |
| --------------------- | --------------------- |
| أمراض نسائية          | طبيب نساء وتوليد      |
| الحمل والولادة        | طبيب نساء وتوليد      |
| جراحة نسائية          | طبيب نساء وتوليد      |
| صحة المرأة            | طبيب نساء وتوليد      |
| أمراض الغدد الصماء    | طبيب غدد صماء         |
| مرض السكري            | طبيب غدد صماء         |
| هرمونات               | طبيب غدد صماء         |
| أمراض القلب والشرايين | طبيب قلب              |
| ارتفاع ضغط الدم       | طبيب قلب              |
| جراحة القلب والشرايين | طبيب قلب              |

This reduces category fragmentation and produces a smaller set of specialist-oriented classes for downstream experimentation.

---

## Class Imbalance

The original dataset is highly imbalanced.

For example, the largest categories contain tens or hundreds of thousands of records, while several categories contain fewer than 100 examples.

After category consolidation and filtering, the workflow retains **20 major categories** with substantially larger sample sizes.

The resulting category distribution includes:

* طبيب نساء وتوليد
* طبيب مسالك بولية
* طبيب باطني
* طبيب عظام
* طبيب جلدية
* طبيب جهاز هضمي
* طبيب أطفال
* طبيب نفسي
* طبيب أسنان
* طبيب قلب
* طبيب عيون
* طبيب أنف وأذن وحنجرة
* طبيب جراح
* طبيب غدد صماء
* أخصائي تغذية
* طبيب أورام
* طبيب أعصاب
* طبيب صدرية
* طبيب أمراض دم
* طبيب تجميل

---

## Sampling Strategy

Because processing and training on the entire corpus can be computationally expensive, the workflow creates multiple sampled subsets.

The sampling strategy:

* samples independently within each category
* uses a fixed sampling fraction
* maintains representation from smaller retained categories
* uses different random seeds for different subsets
* produces five processed subsets for experimentation

This provides multiple manageable datasets while retaining representation across the selected categories.

---

## Data Cleaning Operations

The workflow includes:

```text
Whitespace cleaning
       ↓
Tatweel removal
       ↓
Diacritic removal
       ↓
URL removal
       ↓
Arabic text normalization
       ↓
Category consolidation
       ↓
Rare-category filtering
       ↓
Category-aware sampling
       ↓
Tokenization
       ↓
Duplicate removal
       ↓
Length handling
       ↓
Stopword removal
```

---

## Output

The processed data is exported as separate CSV files:

```text
subset_1.csv
subset_2.csv
subset_3.csv
subset_4.csv
subset_5.csv
```

Each subset contains processed question-answer data together with the associated category and intermediate/final preprocessing representations generated by the notebook.

The generated datasets are intentionally **not committed to this repository** because of their size.

---


## Technologies

* **Python**
* **Pandas**
* **NumPy**
* **NLTK**
* **PyArabic**
* **Transformers**
* **Matplotlib**
* **Pillow**
* **Tabulate**
* **Jupyter Notebook**

---


## Project Report

A detailed project report is available in the [`docs/`](docs/) directory.

The report contains broader documentation of the graduation project. This repository specifically focuses on the **Arabic medical dataset preprocessing component**.

---

## My Contribution

This repository represents my contribution to a larger AI-based medical assistant graduation project.

My primary responsibilities included:

* Designing the Arabic text preprocessing workflow
* Cleaning and normalizing the raw dataset
* Handling category inconsistencies
* Addressing severe class imbalance
* Creating sampled datasets for experimentation
* Tokenizing and structuring the text
* Removing duplicate records
* Preparing machine-learning-ready CSV outputs

---

## Applications

The processed corpus can serve as a foundation for experiments involving:

* Arabic text classification
* Medical question classification
* Specialist/department routing
* Arabic NLP
* Medical conversational AI
* Text preprocessing research
* Supervised machine learning

---

## Limitations

This repository focuses on **data preprocessing and preparation** rather than medical model development.

The preprocessing pipeline does not establish the clinical correctness of the original medical answers and should not be interpreted as a medical advice system.

The original dataset is not redistributed through this repository.

---


