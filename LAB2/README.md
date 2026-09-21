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

### Tasks
- **Task 1** — Applied example on the Apple Twitter Sentiment dataset: lower-case the tweet text, extract hashtags with regex, and count/display the top 10 most used hashtags with a bar chart.
- **Task 2** — Use `re.compile()` to build a reusable digit-matching pattern and substitute a value in a string.
- **Task 3** — Use `re.split()` to split a string on runs of digits.
- **Task 4** — Tokenize a sentence with spaCy (`en_core_web_sm`) and compare the result against NLTK's `word_tokenize`.

## Files

- [LAB2.ipynb](LAB2.ipynb)
- [apple_twitter_sentiment_texts.csv](apple_twitter_sentiment_texts.csv) — dataset of tweets about Apple, labeled with sentiment (-1 negative, 0 neutral, 1 positive)

## Requirements

```bash
pip install nltk spacy pandas matplotlib
python -m spacy download en_core_web_sm
```

The notebook also downloads NLTK data (`punkt`, `punkt_tab`, `wordnet`, `omw-1.4`, `stopwords`) on first run.
