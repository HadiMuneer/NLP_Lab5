# Lab 5 — Text Representation

**Name:** Hadi Muneer Abu Allairat
**Student ID:** 2230005761

## Tasks

1. **Cosine similarity** between four short sentences.
2. **TF-IDF** on three data-science sentences, to find the important words.
3. **Word2Vec** (skip-gram) on the Simpsons script, using the `spoken_words` column.
4. **`most_similar`** for `homer`, `marge` and `bart`.
5. **`doesnt_match`** on three lists of characters.

## Contents

| File | |
| --- | --- |
| `Lab5_Text_Representation.ipynb` | The lab notebook, executed with all outputs saved |
| `dataset/simpsons_script_lines.csv` | The dataset, unchanged from the original lab repository |

## Results

- Documents 1 and 4 score **exactly 1.000** — identical to TF-IDF despite one being a question,
  because bag-of-words discards word order.
- `data` is pushed to the IDF floor of 1.0 for appearing in every sentence, yet still ranks **top in
  the shortest sentence**: a high enough term frequency beats the minimum IDF.
- Skip-gram trained on **126,951 lines / 1.2M tokens**, vocabulary 40,748. It groups character names
  together, and groups terms of address (`honey`, `sweetie`) with them.
- `doesnt_match` answered all three questions correctly, but the margins differ sharply: **0.22** for
  Homer / Patty / Selma versus **0.037** and **0.065** for the lists of schoolboys.
- Word2Vec is nondeterministic under gensim's default thread count. `seed=42` alone is not enough —
  `workers=1` is also required, and without it none of the numbers above are stable.

## Running it

```bash
pip install pandas numpy scikit-learn gensim notebook
jupyter notebook Lab5_Text_Representation.ipynb
```

The dataset is committed alongside the notebook, so it runs as-is with no download step.
