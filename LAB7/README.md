# Lab 7: Large Language Models (LLMs)

This lab uses pre-trained transformer models from Hugging Face to compare the three main transformer families: **encoder-only**, **encoder–decoder**, and **decoder-only**.

## Topics covered

### The three transformer families

| Family | Example models | Main use |
|--------|----------------|----------|
| Encoder-only | BERT, RoBERTa | Classification, sentiment analysis, NER |
| Encoder–decoder | T5, BART | Translation, summarization, question answering |
| Decoder-only | GPT family | Text generation, conversation, completion |

### Demos
- **Part A (decoder-only):** text generation with **DistilGPT-2** through the `text-generation` pipeline (greedy decoding).
- **Part B (encoder–decoder):** English → French translation with **FLAN-T5-small** using `AutoTokenizer` and `AutoModelForSeq2SeqLM`.
- **Part C (encoder-only):** sentiment classification with **DistilBERT** fine-tuned on SST-2 (`sentiment-analysis` pipeline).

### Tasks
- **Task 1:** Pick the best model family for each task: sentiment classification and NER → encoder-only; machine translation and summarization → encoder–decoder; open-ended text generation → decoder-only.
- **Task 2:** Classify three sentences with the DistilBERT sentiment model and print the label and score for each.
- **Task 3:** Summarize a short paragraph about NLP with FLAN-T5.
- **Task 5:** Short reflection on why a decoder-only model suits a chatbot like ChatGPT. (The provided lab has no Task 4.)
- **Optional challenge:** Generate text with sampling (`do_sample=True`, `top_k=50`) several times with and without `set_seed(42)`, and explain why the outputs change.

## Results

**Task 2: sentiment classification**

| Sentence | Label | Score |
|----------|-------|-------|
| The movie was excellent. | POSITIVE | 0.9999 |
| The lecture was difficult to understand. | NEGATIVE | 0.9997 |
| I enjoyed learning about transformers. | POSITIVE | 0.9997 |

**Task 3: summarization**

> Using natural language processing, computers can learn the meaning of words from their context.

The prompt uses the lowercase `summarize:` prefix that T5 was trained with. With `Summarize:` (capital S) the small model got stuck repeating "Learn the language."

**Optional challenge:** without a seed, each sampling run gives a different continuation, because the next token is drawn at random from the probability distribution. Calling `set_seed(42)` before each run gives the same text every time.

## Notes
- The models are small (DistilGPT-2, FLAN-T5-small, DistilBERT), so they run on a CPU but their output quality is limited. For example, the French translation in Part B is not fully correct.
- The models are downloaded from Hugging Face the first time the notebook runs.

## Files

- [LAB7.ipynb](LAB7.ipynb)

## Requirements

```bash
pip install transformers sentencepiece torch
```
