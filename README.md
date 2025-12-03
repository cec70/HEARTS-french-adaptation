# French Stereotype Detection with CamemBERT  
### An Adaptation of the HEARTS Framework for the AI for Sustainable Development Coursework

This project adapts the HEARTS framework (*A Holistic Framework for Explainable, Sustainable and Robust Text Stereotype Detection*) to the **French language**, using the **FairTranslate** dataset to detect occupational gender stereotypes in translated sentences.  
The goal is to evaluate whether a French transformer model (CamemBERT) can identify stereotyped content, compare it to a simple baseline and analyse potential bias and sustainability impacts.

---

## Motivation

Gender stereotypes embedded in French translations are often reinforced by grammatical gender and occupational morphology.  
Following the HEARTS methodology, this work investigates how machine learning models handle these biases and how performance varies across different stereotype categories.

---

## Dataset: FairTranslate

FairTranslate contains **2,418 English–French sentence pairs**, each annotated with:
- **Gender variant** (male, female, inclusive)  
- **Ambiguity level** (ambiguous, unambiguous, long unambiguous)  
- **Stereotype category** (male-stereotyped, female-stereotyped, neutral)  
- **French occupational forms**, often gender-marked

We fine-tune CamemBERT on **French text only**, since French morphology carries the gender information relevant to stereotype detection.

---

## Models

### **Baseline**
- TF-IDF + Logistic Regression  
- Trained on French text  
- Provides a simple baseline for comparison  

### **CamemBERT**
- `camembert-base` fine-tuned for binary classification  
- Deterministic training setup for reproducible results  
- Evaluated using macro-F1, per-class metrics, and subgroup analysis  

---

## Evaluation

The project includes:
- Confusion matrices  
- Performance comparison baseline vs CamemBERT
- Macro-F1 across training epochs  
- Statistical significance testing (McNemar’s test)  
- Bootstrap confidence intervals for F1  
- CodeCarbon emissions tracking  

Explainability tools (SHAP/LIME) were not used due to instability with BPE tokenization in French transformers.

---

## Running the Notebook

**Install dependencies:**

```bash
pip install -r requirements.txt
```

**Launch**

This project is designed to run directly in **Google Colab**.
1. Open the notebook in Colab using this badge: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://github.com/cec70/HEARTS-French-Adaptation/blob/main/HEARTS_FairTranslate_CamemBERT.ipynb)

2. Once opened, run all cells from top to bottom (`Runtime -> Run all`).

---

## References
1. King, T., et al. (2024). "HEARTS: A Holistic Framework for Explainable, Sustainable and Robust Text Stereotype Detection".
2. Jourdan, F., Chevalier, Y. & Favre, C. (2025) ‘FairTranslate: An English-French Dataset for Gender Bias Evaluation in Machine Translation by Overcoming Gender Binarity’, in 8th annual ACM FAccT conference (FAccT 2025), Athens, Greece, June. ACM.
