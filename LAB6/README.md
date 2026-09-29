# Lab 6: Deep Learning for NLP

This lab builds feed-forward neural networks in PyTorch to classify Yelp restaurant reviews as **positive (1)** or **negative (0)**, and compares TF-IDF features with Word2Vec embeddings as the network's input.

## Topics covered

### Neural network pipeline
- Loading the Yelp reviews dataset (1,000 reviews, 500 positive / 500 negative)
- Text cleaning with regular expressions (lowercase, remove punctuation and extra spaces)
- Stratified 80/20 train/test split
- TF-IDF features (`max_features=1000`) converted to PyTorch tensors
- A network with two hidden layers (1000 → 64 → 32 → 1) and ReLU activations
- `BCEWithLogitsLoss` + Adam optimizer, a training loop (forward pass, loss, backpropagation, weight update)
- Evaluation with sigmoid + 0.5 threshold, accuracy, classification report and confusion matrix

### Tasks
- **Task 1:** Represent the reviews with Word2Vec: tokenize the reviews, train a Skip-Gram `Word2Vec` model on the training reviews (`vector_size=200`, `window=5`, `min_count=1`, `sg=1`), average the word vectors to get one vector per review, and convert the result to PyTorch tensors.
- **Task 2:** Build a new network on the Word2Vec vectors with three hidden layers (200 → 128 → 64 → 32 → 1, ReLU), train it with `BCEWithLogitsLoss`, Adam (`lr=0.001`) for 15 epochs (mini-batches of 32), and compute the test accuracy.

## Results

| Features | Network | Test accuracy |
|----------|---------|---------------|
| TF-IDF (1000-dim) | 64 → 32 → 1 | 0.755 |
| Word2Vec average (200-dim) | 128 → 64 → 32 → 1 | 0.635 |

TF-IDF does better here because the Word2Vec model is trained on only 800 short reviews, and averaging word vectors loses word order and dilutes strong sentiment words. Word2Vec usually does better with a much larger training corpus or pre-trained embeddings.

## Fixes to the provided code
- The preprocessing lines `df["review"] = df["review"].apply(preprocess_text)` were indented inside the function after `return`, so they never ran. They are now at the top level.
- Added `stratify=y` to `train_test_split` (the notes describe a stratified split).
- Added `optimizer.zero_grad()` to the training loop so gradients don't build up across epochs.
- Added `torch.manual_seed(42)` so results can be reproduced.

## Files

- [LAB6.ipynb](LAB6.ipynb)
- [07-yelp-dataset.txt](07-yelp-dataset.txt): tab-separated Yelp reviews (`review`, `label`)

## Requirements

```bash
pip install pandas scikit-learn gensim torch
```
