# Lab 3: N-Grams

This lab covers n-grams, which are groups of N words taken in order from a text, and how they are used to model and generate language.

## Part 1: N-Grams

- Types and use cases of n-grams
- Unigram model: counting words and calculating word probabilities
- Bigram model: two ways of building it
- Trigram model: two ways of building it
- Padding in NLP (adding start/end markers to sentences)
- Training a Maximum Likelihood Estimation (MLE) n-gram model with NLTK
- Counting unigrams and bigrams from the trained model
- Evaluating n-gram models using perplexity
- Task: generating tweets using n-grams (loads `tweets.csv`, a dataset of tweets from Pakistan; falls back to a small demo sample if the file is not found)

## Part 2: Text Analysis and N-gram Generation

**Task 1: Text Analysis and NLP**
- Loads a dataset of IMDB movie reviews (`IMDB Dataset.csv`, falls back to a demo sample if missing)
- Pre-processes the text (lower casing, removing punctuation, removing stop words)
- Calculates basic statistics on the text
- Plots a word frequency histogram of the most common words
- Prints a summary of the results

**Task 2: N-gram Generation from Poem Data**
- Loads a dataset of poems (`poem_classification.csv`, falls back to a demo sample if missing)
- Pre-processes the text
- Generates bi-grams (2-grams) from the text
- Calculates the frequency of each unique bi-gram
- Displays the top 10 most common bi-grams

## File

- [LAB3.ipynb](LAB3.ipynb)

## Datasets

The notebook expects the following CSV files in the same folder (each part will run with a small built-in demo sample if the file is missing):

- `tweets.csv` — [Large Random Tweets from Pakistan](https://www.kaggle.com/datasets/adizafar/large-random-tweets-from-pakistan)
- `IMDB Dataset.csv` — IMDB movie reviews
- `poem_classification.csv` — poem dataset

## Requirements

```bash
pip install nltk pandas matplotlib
```
