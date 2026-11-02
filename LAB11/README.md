# Lab 11: Attention with RNN

This lab covers the **attention mechanism**: a way for a neural network to focus more on the relevant parts of the input when making a prediction. It builds a small question-answering model in **PyTorch**, where an RNN reads a question, attention gives each word a weight, and the model picks one answer from the dataset.

## Topics covered

### What attention is
- In an encoder–decoder model, attention lets the decoder look back at **all** encoder hidden states instead of only the last one.
- Each hidden state gets a score, the scores go through a **softmax** to become weights that add up to 1, and the output is the **weighted sum** of the hidden states.

### Preparing the data
- The dataset ([Lab_11_QnA_Dataset.csv](Lab_11_QnA_Dataset.csv)) has **168 questions** split into **12 answer groups** (14 questions each), for example *"How old are you?"* → *"Age doesn't really apply to me."*
- Questions are lower cased, turned into integer sequences with the Keras `Tokenizer` (226 words), and padded with zeros to 11 tokens with `pad_sequences`.

### RNN with attention
- `Embedding(16)` → `RNN(32)` → `Linear(32 → 1)` attention score per word → softmax → weighted sum → `Linear(32 → 12)` answer.
- Trained with `cross_entropy` and Adam (`lr=0.01`) for 50 epochs. The attention weights are plotted as a bar chart for each word.

### Tasks
- **Task 1:** Plot the attention weights for three questions and check whether the highest-weighted word is important for the question.
- **Task 2:** Compare the attention for two questions with the same meaning but different wording.

## Fixes to the starter code

While running the lab I found three problems in the given code and fixed them in the notebook:

1. **`nn.RNN` without `batch_first=True`.** PyTorch's RNN expects `(sequence, batch, features)` by default, but `X` is `(batch, sequence)`. So the RNN was reading the 168 *questions* as one long sequence instead of reading the words of each question in order.
2. **No `optimizer.zero_grad()`.** Without it, the gradients of every epoch are added together instead of being reset.
3. **Padding got attention.** The zeros added by padding were included in the softmax. They are now masked with `-inf`, so only real words get weight.

The plotting also uses the tokenizer's words instead of `question.split()`, so each bar matches the token the model saw (no `?` attached). The Colab-only `google.colab` import was removed and the CSV is read from this folder.

## Results

The model reaches **98.8% training accuracy** (final loss 0.069). It is trained and checked on the same 168 questions, as in the lab, so this shows how well it fits the data, not how well it handles new questions.

### Task 1: three questions

| Question | Highest attention | Predicted answer |
|----------|-------------------|------------------|
| can you cry? | **you** (0.94) | I don't have a body. ✔ |
| do you ever eat beef? | **eat** (0.55), beef 0.41 | I don't need to eat. ✔ |
| do you have a name? | **name** (0.98) | I don't have a name. ✔ |

Most of the time the attention lands on the content words that decide the answer (*name*, *eat*, *beef*) and ignores filler words (*do, you, have*). The exception is *"can you cry?"*, where the top word is **you**. The weight is on the RNN hidden state, which at *you* has already read *"can you"*, and 6 of the 7 *"can you …?"* questions in the dataset are in the *"I don't have a body."* group. So the model learned *"can you"* as a shortcut.

### Task 2: similar questions

| Question | Highest attention | Predicted answer |
|----------|-------------------|------------------|
| do you have a name? | **name** (0.98) | I don't have a name. ✔ |
| so what is your name? | **so** (0.94) | I don't have a name. ✔ |
| how old are you? | **old** (0.69) | Age doesn't really apply to me. ✔ |
| what's your age? | **your** (0.53), age 0.37 | Age doesn't really apply to me. ✔ |

Questions with the same meaning reach the same answer but often through **different** words. *"so what is your name?"* puts almost all its weight on **so**, because all five questions in the dataset that start with *"so"* belong to the name group. This shows that attention is learned from the data: it picks whatever words best separate the answers (including shortcuts), and since the weights are on RNN hidden states, a weight on a small word can still carry the meaning of the words before it. Attention is a useful but partial explanation of what the model is doing.

## Files

- [LAB11.ipynb](LAB11.ipynb)
- [Lab_11_QnA_Dataset.csv](Lab_11_QnA_Dataset.csv)

## Requirements

```bash
pip install torch tensorflow pandas matplotlib
```

TensorFlow is only used for the Keras `Tokenizer` and `pad_sequences`.
