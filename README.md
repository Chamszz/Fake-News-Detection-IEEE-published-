# Fake News Detection using BERT and XGBoost

> Hybrid deep learning model combining BERT embeddings with XGBoost classifier for accurate fake news detection
> IEEE Research Project | Python 3.9+

---

## Overview

This project implements a hybrid fake news detection system that combines:
- **BERT** (Bidirectional Encoder Representations from Transformers) for semantic understanding
- **XGBoost** (Extreme Gradient Boosting) for efficient classification

The model achieves 96.5% accuracy on a balanced dataset of real and fake news articles by leveraging BERT's contextual embeddings with XGBoost's robust decision-making capabilities.

---

## Key Features

- Bidirectional transformer-based language understanding
- Hybrid architecture combining deep learning and gradient boosting
- 96.5% accuracy on balanced fake news dataset
- Supports multiple news sources (Kaggle, ISOT, PolitiFact, Snopes)
- Complete NLP preprocessing pipeline
- Cross-validation and hyperparameter tuning
- Detailed performance metrics (accuracy, precision, recall, F1-score)

---

## Model Architecture

```
Input Article (Title + Body)
        |
        v
NLP Preprocessing (Cleaning, Tokenization, Normalization)
        |
        v
BERT Embeddings (768-dimensional contextual vectors)
        |
        v
Feature Extraction (CLS token representation)
        |
        v
XGBoost Classifier (Binary Classification)
        |
        v
Output (Fake: 0 / Real: 1)
```

---

## Dataset

- **Size**: Approximately 40,000 labeled news articles
- **Balance**: Equal distribution of real and fake news
- **Sources**: Kaggle, ISOT, PolitiFact, Snopes
- **Languages**: English only
- **Categories**: Politics, Health, Economics, International Affairs
- **Split**: 80% training, 20% testing

---

## Performance Metrics

| Metric | Score |
|--------|-------|
| Accuracy | 96.5% |
| Precision | 95.3% |
| Recall | 96.9% |
| F1-Score | 95.5% |
| ROC-AUC | 0.98 |

---

## Requirements

- Python 3.9+
- torch
- transformers (Hugging Face)
- xgboost
- scikit-learn
- pandas
- numpy
- matplotlib
- seaborn

---

## Installation

```bash
# Clone repository
git clone https://github.com/hemanthreddy2806/Fake-News-Detection.git
cd Fake-News-Detection

# Install dependencies
pip install -r requirements.txt
```

---

## Usage

### 1. Data Preparation

```python
from src.data_loader import load_dataset

# Load dataset from multiple sources
train_data, test_data = load_dataset(
    sources=['kaggle', 'isot', 'politifact'],
    train_split=0.8
)
```

### 2. Preprocessing

```python
from src.preprocessor import NLPPreprocessor

preprocessor = NLPPreprocessor()
cleaned_text = preprocessor.preprocess(raw_text)
# Operations: lowercasing, cleaning, stopword removal, tokenization
```

### 3. Feature Extraction with BERT

```python
from src.bert_embedder import BERTEmbedder

embedder = BERTEmbedder(model_name='bert-base-uncased')
embeddings = embedder.get_embeddings(cleaned_text)
# Returns 768-dimensional vectors
```

### 4. Classification with XGBoost

```python
from src.xgboost_classifier import FakeNewsClassifier

classifier = FakeNewsClassifier()
classifier.train(embeddings, labels)
predictions = classifier.predict(test_embeddings)
```

### 5. Evaluation

```python
from src.evaluator import ModelEvaluator

evaluator = ModelEvaluator()
results = evaluator.evaluate(predictions, true_labels)
print(f"Accuracy: {results['accuracy']:.4f}")
print(f"F1-Score: {results['f1_score']:.4f}")
```

---

## Project Structure

```
Fake-News-Detection/
├── data/
│   ├── raw/              # Original datasets
│   ├── processed/        # Cleaned and prepared data
│   └── config.yaml       # Data source configurations
│
├── src/
│   ├── __init__.py
│   ├── preprocessor.py   # NLP preprocessing pipeline
│   ├── bert_embedder.py  # BERT feature extraction
│   ├── xgboost_classifier.py  # XGBoost model
│   ├── data_loader.py    # Dataset loading utilities
│   ├── evaluator.py      # Evaluation metrics
│   └── utils.py          # Helper functions
│
├── notebooks/
│   ├── 01_EDA.ipynb      # Exploratory data analysis
│   ├── 02_Preprocessing.ipynb
│   ├── 03_BERT_Features.ipynb
│   ├── 04_Model_Training.ipynb
│   └── 05_Results_Analysis.ipynb
│
├── models/               # Saved BERT and XGBoost models
├── results/              # Evaluation results and plots
├── requirements.txt
├── README.md
└── LICENSE
```

---

## Methodology Highlights

### NLP Preprocessing
- Lowercasing and character cleaning
- Punctuation and special character removal
- Stopword removal (common words like 'the', 'is', 'and')
- Tokenization using BERT tokenizer
- Text normalization (handling different word forms)

### BERT Integration
- Uses bert-base-uncased model (110M parameters)
- Generates 768-dimensional contextual embeddings
- Captures bidirectional context from surrounding tokens
- Extracts [CLS] token representation for classification

### XGBoost Configuration
- n_estimators: 50
- max_depth: 3
- learning_rate: 0.2
- objective: binary:logistic
- Regularization (lambda, gamma) for overfitting prevention

---

## Model Comparison

| Model | Accuracy | Precision | Recall | F1-Score |
|-------|----------|-----------|--------|----------|
| Naive Bayes | 82.4% | 80.0% | 79.1% | 79.9% |
| Logistic Regression | 85.5% | 83.9% | 84.6% | 83.1% |
| Random Forest | 89.2% | 88.8% | 88.7% | 88.2% |
| SVM | 88.7% | 86.3% | 87.5% | 86.2% |
| LSTM | 91.1% | 90.0% | 91.2% | 90.0% |
| BERT | 94.5% | 93.5% | 94.8% | 93.2% |
| **BERT + XGBoost** | **96.5%** | **95.3%** | **96.9%** | **95.5%** |

---

## Research References

This project is based on the IEEE research paper:
- Title: "Detecting Fake News using a Hybrid BERT-XGBoost Model"
- Authors: Jonnabhatla Kashyap, Dr. Beebi Naseeba, Chatala Dave Neel, Gudibandi Hemanth Reddy
- Institution: VIT-AP University, Amaravati, India

---

## Contributing

Contributions are welcome. Please feel free to submit pull requests or open issues for bugs and feature requests.

---

## License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## Author

**Hemantha Reddy** - hemanthreddy2806@gmail.com

GitHub: [github.com/hemanthreddy2806](https://github.com/hemanthreddy2806)
