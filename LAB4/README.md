# Lab 4: Classification and Evaluation

This lab covers text classification, where a model assigns a predefined category (e.g. positive/negative/neutral) to a piece of text, and how to evaluate the resulting model.

## Case Study: Disneyland Reviews

- Dataset: [Disneyland Reviews](https://www.kaggle.com/datasets/arushchillar/disneyland-reviews) — 42,000 reviews of the Paris, California, and Hong Kong branches
- Maps 1-5 star ratings to `positive` / `negative` / `neutral` sentiment labels
- Pre-processes review text (lower casing, removing punctuation and special characters, tokenizing)
- Splits the data into train/test sets and vectorizes the text with TF-IDF (1000 features)
- Trains a linear Support Vector Machine (SVM) classifier
- Evaluates the model with accuracy and a classification report

## Use Case: Amazon Unlocked Phone Reviews

- Dataset: [Amazon Reviews - Unlocked Mobile Phones](https://www.kaggle.com/datasets/PromptCloudHQ/amazon-reviews-unlocked-mobile-phones) — 413,000+ reviews of unlocked phones
- **Task 1:** Loads the data and applies 5 pre-processing steps (drop missing rows, lower casing, remove URLs, remove punctuation/digits, remove stop words)
- **Task 2:** Splits the data into train (80%) and test (20%) sets
- **Task 3:** Extracts features with TF-IDF (1000 features)
- **Task 4:** Trains a Multinomial Naive Bayes classifier
- **Task 5:** Evaluates the model on the test set (accuracy, classification report)
- **Task 6:** Prints and plots the confusion matrix

## File

- [LAB4.ipynb](LAB4.ipynb)

## Datasets

The notebook expects the following CSV files (paths use the `/content/` convention for running in Google Colab — update the path if running locally):

- `DisneylandReviews.csv` — [Disneyland Reviews](https://www.kaggle.com/datasets/arushchillar/disneyland-reviews)
- `Amazon_Unlocked_Mobile.csv` — [Amazon Reviews - Unlocked Mobile Phones](https://www.kaggle.com/datasets/PromptCloudHQ/amazon-reviews-unlocked-mobile-phones)

Neither dataset is committed to this repo (both are 100+ MB); download them from Kaggle and place them next to the notebook, or upload them to `/content/` if running in Colab.

## Requirements

```bash
pip install pandas nltk scikit-learn matplotlib
```
