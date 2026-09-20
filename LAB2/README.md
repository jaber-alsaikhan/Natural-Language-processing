# Lab 2: Text Pre-processing and Regular Expressions

This lab covers how to clean and prepare text data, and how to use regular expressions to find and manipulate patterns in text.

## Topics covered

### Regular expressions
- Basic regex symbols (`^`, `$`, `.`, quantifiers, character classes, sets)
- Using the `re` module in Python
- Main regex functions: `search`, `match`, `findall`, `sub`, `compile`, `split`

### Text pre-processing steps
- Tokenization (sentence and word level, with both NLTK and spaCy)
- Lower casing
- Stemming (Porter and Snowball stemmers, with a comparison)
- Lemmatization
- Stop word removal (with spaCy and NLTK stop word lists)

### Applied example
A small project that uses regular expressions and text pre-processing on the Apple Twitter Sentiment dataset to:
1. Lower-case the tweet text
2. Extract hashtags from each tweet using regex
3. Count and display the top 10 most used hashtags with a bar chart

## Files

- [LAB2.ipynb](LAB2.ipynb)
- [apple_twitter_sentiment_texts.csv](apple_twitter_sentiment_texts.csv) — dataset of tweets about Apple, labeled with sentiment (-1 negative, 0 neutral, 1 positive)

## Requirements

```bash
pip install nltk spacy pandas matplotlib
python -m spacy download en_core_web_sm
```

The notebook also downloads NLTK data (`punkt`, `punkt_tab`, `wordnet`, `omw-1.4`, `stopwords`) on first run.
