# Natural-Language-Processing

This repository is a collection of lab work built for the ARTI 452: Natural Language Processing course. Each lab covers one part of the NLP pipeline, going from basic text handling to language models built from text data. More labs will be added as the course goes on.

## What is covered

- **Text pre-processing:** Tokenization, lower casing, stemming, lemmatization, and stop word removal.
- **Pattern matching:** Using regular expressions to search, extract, and clean text data.
- **Language modeling:** Building n-gram models, computing word probabilities, and generating text.
- **Applied text analysis:** Working with real datasets (tweets, movie reviews, poems) to extract hashtags, word statistics, and common phrases.

## Labs

| Lab | Topic |
|-----|-------|
| [LAB1](LAB1/README.md) | Introduction to NLP |
| [LAB2](LAB2/README.md) | Text Pre-processing and Regular Expressions |
| [LAB3](LAB3/README.md) | N-Grams |

## Tools Used

- **Language:** Python
- **Libraries:** NLTK, spaCy, pandas, matplotlib
- **Environment:** Jupyter Notebook
- **Version Control:** Git & GitHub

## Setup

```bash
pip install nltk spacy pandas matplotlib
python -m spacy download en_core_web_sm
```

Open a lab's `.ipynb` file in Jupyter or VS Code to run it. Some notebooks download extra NLTK data the first time they run.
