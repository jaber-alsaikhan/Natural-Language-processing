# Lab 8: Part-of-Speech (POS) Tagging

This lab covers **part-of-speech tagging**: labeling each word in a text with its grammatical category (noun, verb, adjective, ...) based on the word itself and its context. It uses both **NLTK** and **spaCy**.

## Topics covered

### Why POS tagging is useful
- Focusing on certain word types, for example nouns for information retrieval and adjectives for sentiment analysis.
- Supporting Named Entity Recognition (NER) and extracting relations between words.
- Grammar correction, spelling correction, and question answering.

### POS tagging with NLTK
- The Penn Treebank tag set used by NLTK (`NN`, `VBD`, `JJ`, `PRP`, ...).
- Tagging tokens with `nltk.pos_tag` after `word_tokenize`.

### POS tagging with spaCy
- **Coarse-grained tags** (`token.pos_`): general categories such as `NOUN`, `VERB`, `ADJ`.
- **Fine-grained tags** (`token.tag_`): detailed tags such as `VBD` (past tense) or `NNS` (plural noun).
- `spacy.explain(tag)` to get a description of any tag.
- How context changes the tag: *"I read books"* → `VBP` (present), *"I read a book"* → `VBD` (past).
- Visualizing the tags and dependency parse with **displaCy**.

### Example
- Extracting the adjectives (`JJ`) from a product review sentence by sentence, which is a simple first step toward sentiment analysis.

### Tasks
- **Task 1:** For *"I like watching football matches. I do not know how to play it though"*, print the coarse tag, fine tag, and explanation for "play", then for every word in the sentence.
- **Task 2:** Compare the tags of "google" and "table" across four sentences.
- **Task 3:** Visualize the parts of speech of *"I like to play football. I hated it in my childhood though"* with displaCy.

## Results

**Task 1:** "play" is tagged `VERB` (coarse) and `VB` (fine), which spaCy explains as "verb, base form".

**Task 2:** the same word gets a different tag depending on its context:

| Sentence | Word | Coarse | Fine | Meaning |
|----------|------|--------|------|---------|
| Did you search on Google? | Google | PROPN | NNP | noun, proper singular |
| Let us google it. | google | VERB | VB | verb, base form |
| The has placed the food on the table | table | NOUN | NN | noun, singular or mass |
| She plans to table a motion for debate in Parliament | table | VERB | VB | verb, base form |

**Task 3:** displaCy renders the sentence with the POS tag under each word and arcs for the dependency relations.

## Files

- [LAB8.ipynb](LAB8.ipynb)

## Requirements

```bash
pip install nltk spacy
python -m spacy download en_core_web_sm
```

The notebook downloads the NLTK `averaged_perceptron_tagger_eng` and `punkt_tab` data the first time it runs.
