# IsiZulu POS Tagging using Linear Chain Conditional Random Field (LC-CRF)

This project trains and evaluates a **Linear Chain Conditional Random Field (CRF)** model to perform **Part-of-Speech (POS)** tagging on an isiZulu corpus. It includes data cleaning, morphological feature extraction, UNK word handling, and model evaluation.

---

## 📁 Dataset Format

The dataset is a tab-separated file with the following structure:

## TOKEN MORPH ANALYSIS UPOS

- **TOKEN**: the original word as it appears in the sentence.
- **MORPH ANALYSIS**: morphological segmentation using hyphens (`-`).
- **UPOS**: Universal POS tag.

**Sample lines from the dataset:**
Ukwengeza u-kw-engez-a V
kulokhu ku-lokhu CDEM
imibandela i-mi-bandela N
iyenziwa i-ye-enz-iw-a V
...

- Sentences are separated by **blank lines**.
- Invalid or malformed lines are skipped during preprocessing.

---

## 🔄 Data Preprocessing

### ✅ Steps:

1. **Mounting Dataset**
   - Uses Google Drive to access the corpus.

2. **Sentence Grouping**
   - Sentences are grouped by blank lines.
   - Each sentence becomes a list of `(token, morph, tag)` tuples.

3. **Train/Test Split**
   - The dataset is split into 75% training and 25% testing using `sklearn`.

---

## 🧠 Feature Engineering

### ✨ Highlights:

- Rare words (based on frequency) are replaced with a placeholder using a dynamic threshold.
- Extracts:
  - Word casing, affixes, and digit checks
  - Morphological prefix/suffix
  - Contextual features from neighboring tokens
  - isiZulu-specific affix patterns for prefix/suffix matching

---

## 🏋️‍♂️ Model Training

- Model: `sklearn_crfsuite.CRF`
- Optimization: L-BFGS
- Regularization: L1 (`c1`) and L2 (`c2`)
- Max iterations: 100
- All possible transitions enabled

---

## ✅ Evaluation

- **Accuracy Score** using `sklearn.metrics.accuracy_score`
- Also prints predicted vs actual tags for sample sentences

---

## 💻 Requirements

- Python 3.x
- `sklearn`
- `sklearn-crfsuite`
- Google Colab (recommended)

## bash
pip install sklearn-crfsuite 

👩‍💻 Author
Akhona Nzimande
Honours Student | NLP & AI Enthusiast
