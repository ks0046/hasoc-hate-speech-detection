# Hindi-English Hate Speech Detection

## Overview
This project implements a hate speech detection system for Hindi and Hinglish (Hindi-English code-mixed) tweets. The system classifies tweets into two categories:
- **HOF (Hate Offensive)**: Posts containing hate speech, profane, or offensive content
- **NOT (Non-Hate-Offensive)**: Posts without hate speech, profane, or offensive content

## Table of Contents
- [Problem Definition](#problem-definition)
- [Dataset](#dataset)
- [Techniques Used](#techniques-used)
- [Methodology](#methodology)
- [Experimental Results](#experimental-results)
- [Key Insights](#key-insights)
- [How to Use](#how-to-use)
- [References](#references)

## Problem Definition
The task is a binary classification problem that classifies tweets into:
- **Hate and Offensive (HOF)**: Contains hate speech, profanity, or offensive content
- **Non-Hate Offensive (NOT)**: Does not contain hate speech, profanity, or offensive content

This task is derived from Subtask-A of HASOC 2021, and the dataset contains Twitter posts in Hindi and Hinglish, inspired by the OLID dataset.

## Dataset
The dataset used is from HASOC 2021 Subtask-A with the following characteristics:
- **Languages**: Hindi (Devanagari) and Hinglish
- **Source**: Twitter
- **Preprocessing Steps**:
  - URL, hashtag, mention, and number removal
  - Translation to English using Google Translate API
  - Username standardization
  - Case normalization and lemmatization
  - Stop word removal

## Techniques Used

### Feature Engineering
1. **Username Features**
   - Count of usernames in tweets
   - Indicator of targeted harassment

2. **Profanity Vector**
   - Vector indicating presence of profane words

3. **Sentiment Vector**
   - Extracted using VADER library
   - Components: positive, negative, neutral, compound

4. **Contextual Sentence Embeddings**
   - Generated using fine-tuned BERT-base model

### Machine Learning Models
- **Traditional ML**: 
  - Support Vector Machine (SVM)
  - Logistic Regression (LR)
  - Random Forest (RF)
  - Multinomial Naive Bayes

- **Deep Learning**:
  - CNN
  - Bi-LSTM with Attention
  - GRU

- **Transformers**:
  - Fine-tuned BERT
  - RoBERTa
  - DistilRoBERTa

## Experimental Results

### Model Performance (F1 Scores)

#### Hate-specific Neural Architectures
| Architecture | RFC | MLP | SVM |
|--------------|-----|-----|-----|
| distilroberta-hatespeech | 0.642 | 0.671 | 0.668 |
| uncased-hatexpain | 0.647 | 0.676 | 0.666 |
| facebook/roberta | 0.657 | 0.697 | 0.697 |

#### Best Performing Models
| Model | F1 Score |
|-------|-----------|
| Fine-Tuned BERT | 0.77 |
| CNN + Bi-LSTM (DL Ensemble) | 0.87 |
| Random Forest with TF-IDF | 0.76 |
| SVM with Contextual Embeddings | 0.77 |

## Key Insights
1. Contextual embeddings significantly outperformed non-contextual approaches
2. Deep Learning ensemble (CNN + Bi-LSTM) achieved highest F1 score of 0.87
3. Feature combination (embeddings + profanity + sentiment) improved performance
4. Fine-tuning pre-trained models showed significant gains
5. BatchAllTripletLoss proved effective for classification tasks


## References

[1] P. Burnap, M. L. Williams, "Us and them: identifying cyber hate on Twitter across multiple protected characteristics," in: EPJ Data Science vol. 5, Springer, 2016 (pp. 1-15).

[2] Sreelakshmi K, Premjith B, Soman KP, "Detection of HATE Speech text in Hindi-English code-mixed data," Procedia Comput Sci. [https://doi.org/10.1016/j.procs.2020.04.080](https://doi.org/10.1016/j.procs.2020.04.080)

[3] Jadhav, Ishali & Kanade, Aditi & Waghmare, Vishesh & Chaudhari, Deptii, "Hate and Offensive Speech Detection in Hindi Twitter Corpus," 2022. [https://ceur-ws.org/Vol-3159/T1-33.pdf](https://ceur-ws.org/Vol-3159/T1-33.pdf)

[4] Kamble, Satyajit & Joshi, Aditya, "Hate Speech Detection from Code-mixed Hindi-English Tweets Using Deep Learning Models," 2018. [https://doi.org/10.48550/arXiv.1811.05145](https://doi.org/10.48550/arXiv.1811.05145)

[5] Chopra, Shivang & Sawhney, Ramit & Mathur, Puneet & Shah, Rajiv, "Hindi-English Hate Speech Detection: Author Profiling, Debiasing, and Practical Perspectives," Proceedings of the AAAI Conference on Artificial Intelligence, 2020. [https://doi.org/10.1609/aaai.v34i01.5374](https://doi.org/10.1609/aaai.v34i01.5374)

[6] Jahan, Md Saroar & Oussalah, Mourad & Mim, Jhuma Kabir & Islam, Mominul, "Offensive Language Identification Using Hindi-English Code-Mixed Tweets, and Code-Mixed Data Augmentation," 2021. [https://ceur-ws.org/Vol-3159/T1-23.pdf](https://ceur-ws.org/Vol-3159/T1-23.pdf)

[7] Srivastava, Ananya & Hasan, Mohammed & Bhargva, Yagnik & Walambe, Rahee & Kotecha, Ketan, "Role of Artificial Intelligence in Detection of Hateful Speech for Hinglish Data on Social Media," 2021. [https://doi.org/10.48550/arXiv.2105.04913](https://doi.org/10.48550/arXiv.2105.04913)

[8] Rahul, V. Gupta, V. Sehra and Y. R. Vardhan, "Ensemble Based Hinglish Hate Speech Detection," 2021 5th International Conference on Intelligent Computing and Control Systems (ICICCS), 2021, pp. 1800-1806. [doi: 10.1109/ICICCS51141.2021.9432352](https://doi.org/10.1109/ICICCS51141.2021.9432352)

[9] Rahul, V. Gupta, V. Sehra and Y. R. Vardhan, "Hindi-English Code-Mixed Hate Speech Detection using Character Level Embeddings," 2021 5th International Conference on Computing Methodologies and Communication (ICCMC), 2021, pp. 1112-1118. [doi: 10.1109/ICCMC51019.2021.9418261](https://doi.org/10.1109/ICCMC51019.2021.9418261)
