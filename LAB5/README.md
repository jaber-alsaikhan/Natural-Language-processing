# Lab 5: Text Representation

This lab covers how to turn text into numerical vectors that machine learning models can work with, using TF-IDF and Word2Vec embeddings.

## Topics covered

### TF-IDF
- What TF-IDF is and why it discounts common words (term frequency, inverse document frequency)
- Building a TF-IDF matrix with `TfidfVectorizer`
- Cosine similarity between documents represented as TF-IDF vectors

### Word2Vec
- What word embeddings are and why they capture inter-word semantics
- CBOW vs. Skip-Gram architectures
- Training a Skip-Gram `Word2Vec` model with `gensim`
- Querying a trained model: `similarity`, `most_similar`, `doesnt_match`

### Tasks
- **Task 1** — Cosine similarity between 4 sentences ("This is the first document.", etc.) using TF-IDF vectors.
- **Task 2** — TF-IDF on 3 data-science sentences, printing the highest-scoring (most important) word per document.
- **Task 3** — Load the Simpsons script lines dataset, clean the `spoken_words` column, and train a Skip-Gram `Word2Vec` model on it.
- **Task 4** — Use `wv.most_similar()` to find words similar to "homer", "marge", and "bart".
- **Task 5** — Use `wv.doesnt_match()` to find the odd one out among `['jimbo', 'milhouse', 'kearney']`, `['nelson', 'bart', 'milhouse']`, and `['homer', 'patty', 'selma']`.

The notebook also keeps the instructor's original Skip-Gram demo (trained on a fake/real news dataset). It expects a `True.csv` file next to the notebook; if that file isn't found, a small demo sample is used instead so the notebook still runs end-to-end.

## Files

- [LAB5.ipynb](LAB5.ipynb)
- [simpsons_script_lines.csv](simpsons_script_lines.csv) — Simpsons script lines dataset (`raw_character_text`, `spoken_words` columns), used in Tasks 3-5

## Requirements

```bash
pip install nltk pandas scikit-learn gensim
```

The notebook uses NLTK's `word_tokenize`, which needs the `punkt`/`punkt_tab` tokenizer data on first run:

```python
import nltk
nltk.download('punkt')
nltk.download('punkt_tab')
```
