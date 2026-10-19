# Lab 9: Named Entity Recognition (NER)

This lab covers **Named Entity Recognition**: finding the names of people, organizations, places, dates, amounts of money, and other entities in a text and classifying them into categories. It uses **spaCy** both with its pre-trained model and with a custom model trained on our own annotations.

## Topics covered

### What NER is
- A two-step process: **detecting** the entities in the text, then **classifying** them into categories.
- Used in information retrieval, question answering, and sentiment analysis.
- Common spaCy entity labels: `PERSON`, `ORG`, `GPE`, `LOC`, `DATE`, `TIME`, `MONEY`, `PERCENT`, `PRODUCT`, `EVENT`, `LAW`, `LANGUAGE`, `NORP`.

### NER with spaCy
- Reading the entities from `doc.ents` and printing each entity's text, label, start/end token position, and `spacy.explain(label)`.

### Custom NER model
- Writing entity annotations as `(start_char, end_char, label)` offsets.
- Checking that the annotations line up with the tokens using `offsets_to_biluo_tags` (BILUO = Begin, Inside, Last, Unit, Outside).
- Training the NER component with `Example.from_dict()` and `nlp.update()`, saving the model with `to_disk()`, and loading it again with `spacy.load()`.
- Visualizing entities with **displaCy** (`style="ent"`).

### Tasks
- **Task 1:** Ask the user for a sentence, find its named entities, and print the details of each one.
- **Task 2:** For a contract paragraph, add the entity the model missed, count the `PERSON` and `ORG` entities, and visualize them.
- **Task 3:** Train a custom NER model on *"Microsoft was founded by Bill Gates and Paul Allen in Albuquerque, New Mexico. It is known for its Windows operating system and Office software products."* for 20 iterations, save it in `custom_ner_model`, and use the saved model to find entities.

## Results

**Task 1:** with the sample input *"Elon Musk visited Riyadh on Monday to meet Saudi Aramco officials about a $2 billion deal."* the model finds `Elon Musk` (PERSON), `Riyadh` (GPE), `Monday` (DATE), `Saudi Aramco` (NORP), and `$2 billion` (MONEY). Labeling Saudi Aramco as `NORP` instead of `ORG` shows the pre-trained model can still make mistakes.

**Task 2:** the pre-trained model labeled `Bcd LLC` as `WORK_OF_ART`. Since "LLC" marks a company, it was changed to `ORG` by replacing the span in `doc.ents`. After the fix:

| Label | Count | Entities |
|-------|-------|----------|
| PERSON | 1 | Samuel P. Jackson |
| ORG | 2 | Abc & Co., Bcd LLC |

**Task 3:** before training, the pre-trained model labeled `Windows` as `ORG` and missed `Office`. After 20 training iterations (the loss drops from about 1.73 to 0), the saved model finds all seven entities:

| Entity | Label |
|--------|-------|
| Microsoft | ORG |
| Bill Gates | PERSON |
| Paul Allen | PERSON |
| Albuquerque | GPE |
| New Mexico | GPE |
| Windows | PRODUCT |
| Office | PRODUCT |

On the new sentence *"Bill Gates said that Microsoft will release a new version of Windows next year."* the custom model now labels `Windows` as `PRODUCT`.

## Files

- [LAB9.ipynb](LAB9.ipynb)

Running the notebook creates a `custom_ner_model/` folder with the trained model. It is about 15 MB, so it is not tracked in Git (see [.gitignore](.gitignore)).

## Requirements

```bash
pip install spacy
python -m spacy download en_core_web_sm
```
