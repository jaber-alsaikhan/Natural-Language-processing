# Natural-Language-Processing

This repository is a collection of lab work built for the ARTI 452: Natural Language Processing course. Each lab covers one part of the NLP pipeline, going from basic text handling to language models built from text data. More labs will be added as the course goes on.

## What is covered

- **Text pre-processing:** Tokenization, lower casing, stemming, lemmatization, and stop word removal.
- **Pattern matching:** Using regular expressions to search, extract, and clean text data.
- **Language modeling:** Building n-gram models, computing word probabilities, and generating text.
- **Applied text analysis:** Working with real datasets (tweets, movie reviews, poems) to extract hashtags, word statistics, and common phrases.
- **Text representation:** Turning text into numerical vectors with TF-IDF and Word2Vec embeddings, and comparing documents/words with cosine similarity.
- **Deep learning:** Training feed-forward neural networks in PyTorch for sentiment classification on TF-IDF and Word2Vec features.
- **Large language models:** Using pre-trained Hugging Face transformers (encoder-only, encoder–decoder, decoder-only) for sentiment analysis, translation, summarization, and text generation.
- **Part-of-speech tagging:** Labeling words with their grammatical category using NLTK and spaCy, and visualizing tags with displaCy.
- **Named entity recognition:** Finding and classifying people, organizations, places, dates, and money in text with spaCy, correcting missed entities, and training a custom NER model.

## Labs

| Lab | Topic |
|-----|-------|
| [LAB1](LAB1/README.md) | Introduction to NLP |
| [LAB2](LAB2/README.md) | Text Pre-processing and Regular Expressions |
| [LAB3](LAB3/README.md) | N-Grams |
| [LAB4](LAB4/README.md) | Classification and Evaluation |
| [LAB5](LAB5/README.md) | Text Representation (TF-IDF and Word2Vec) |
| [LAB6](LAB6/README.md) | Deep Learning for NLP (PyTorch Neural Networks) |
| [LAB7](LAB7/README.md) | Large Language Models (Hugging Face Transformers) |
| [LAB8](LAB8/README.md) | Part-of-Speech (POS) Tagging |
| [LAB9](LAB9/README.md) | Named Entity Recognition (NER) |

## Tools Used

- **Language:** Python
- **Libraries:** NLTK, spaCy, pandas, matplotlib, scikit-learn, gensim, PyTorch, Hugging Face Transformers
- **Environment:** Jupyter Notebook
- **Version Control:** Git & GitHub

## Setup

```bash
pip install nltk spacy pandas matplotlib scikit-learn gensim torch transformers sentencepiece
python -m spacy download en_core_web_sm
```

Open a lab's `.ipynb` file in Jupyter or VS Code to run it. Some notebooks download extra NLTK data the first time they run.
