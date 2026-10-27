# Lab 10: Introduction to Machine Translation

This lab covers **Machine Translation (MT)**: building systems that automatically translate text from one language to another. It focuses on **Neural Machine Translation (NMT)**, where a single neural network learns to map a source language (English) to a target language (French), and uses **TensorFlow/Keras** LSTMs to build it.

## Topics covered

### What machine translation is
- Challenges: **ambiguity** (*"I went to the bank"*), **idiomatic expressions** (*"It's raining cats and dogs"*), and **low-resource languages** with very little data.
- Applications: global business and e-commerce, cross-cultural communication, multilingual content, and language learning.

### Preparing the data
- Turning sentences into integer sequences with the Keras `Tokenizer` (`fit_on_texts`, `texts_to_sequences`, `word_index`).
- Making all sequences the same length with `pad_sequences` (index `0` is reserved for padding).

### LSTM translation model
- `Embedding` → encoder `LSTM` → `RepeatVector` → decoder `LSTM` → `TimeDistributed(Dense(softmax))`.
- Training with `sparse_categorical_crossentropy` and translating with `argmax` over the predicted word probabilities.

### Tasks
- **Task 1:** Explain in my own words what the Embedding layer, the encoder LSTM, the decoder LSTM, and the softmax output layer do.
- **Task 2:** For an e-commerce company that wants to reach French-speaking customers, build an English → French translator using the [Kaggle English–French dataset](https://www.kaggle.com/datasets/devicharith/language-translation-englishfrench) (175,621 sentence pairs).

## Task 2 approach

The example model in the lab only sees three sentences, so for Task 2 I built a full **encoder–decoder (seq2seq) LSTM**:

1. **Cleaning:** lower case, replace the French narrow no-break space (` `) used before `?` and `!`, and remove punctuation but keep apostrophes (`j'ai`, `I'm`).
2. **Filtering:** keep pairs with at most 6 English and 8 French words, then sample 40,000 pairs so it trains on a CPU.
3. **Tokenizing:** 5,000 English and 7,000 French words, with an `<unk>` token for the rest. French sentences get `sos` / `eos` (start / end) tokens, and padding goes at the end and is masked.
4. **Model:** a 256-unit encoder LSTM passes its hidden and cell states to a 256-unit decoder LSTM, trained with **teacher forcing**. It has about 5.9M parameters and trains for 20 epochs with early stopping.
5. **Inference:** separate encoder and decoder models do **greedy decoding**, adding one word at a time until the model outputs `eos`.
6. **Evaluation:** test-set word accuracy and **corpus BLEU** (using every reference translation the dataset gives for each English sentence).

## Results

| Metric | Value |
|--------|-------|
| Training accuracy | 0.84 |
| Validation accuracy | 0.60 |
| Test accuracy (per word) | 0.60 |
| Corpus BLEU (2,000 test sentences) | 0.29 |

Example translations:

| English | Model output |
|---------|--------------|
| i gave you fair warning | je t'ai bien assez averti |
| he employs a maid | il emploie une servante |
| why are you alone | pourquoi êtes vous seul |
| I love this shirt. | j'adore cette chemise |
| Thank you for your help. | merci pour ton aide |
| Where is my order? | où est mon métier |

Many short sentences come out correct or close in meaning even when they don't match the reference word for word. The gap between training and validation accuracy shows the model overfits the small dataset, and rare words often become `<unk>`. A production system would need more data, attention or a Transformer, and product-specific vocabulary.

## Files

- [LAB10.ipynb](LAB10.ipynb)

The notebook downloads the dataset with `kagglehub` the first time it runs (about 3.5 MB, saved in the kagglehub cache, not in this folder).

## Requirements

```bash
pip install tensorflow scikit-learn pandas matplotlib nltk kagglehub
```
