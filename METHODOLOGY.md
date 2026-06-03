# Methodology

This project detects fake news by following a simple text classification pipeline.

## 1. Data preparation
- Load `True.csv` and `Fake.csv`.
- Label the real news examples as `0` and fake news examples as `1`.
- Combine both datasets and shuffle the rows.

## 2. Text cleaning
- Convert text to lowercase.
- Remove punctuation, numbers, and symbols.
- Keep only letters and spaces.

## 3. Feature extraction
- Use BERT (`bert-base-uncased`) to convert each news text into a numerical embedding.
- The notebook creates embeddings from the BERT model output for each article.

## 4. Model training
- Split the data into training and test sets using 80% training and 20% test.
- Train an XGBoost classifier on the BERT embeddings.
- The notebook uses a smaller model size for faster training.

## 5. Evaluation
- Calculate accuracy, precision, recall, and F1-score.
- Display a confusion matrix for real vs fake predictions.
- Plot performance metrics for easy comparison.

## 6. Example prediction
- The notebook shows how to use the trained model to classify new text input.
- It also includes a LIME explanation section to provide interpretability.

## Project goal
- Build a simple proof-of-concept system for fake news detection.
- Use real and fake news datasets to train and evaluate a text classification model.
