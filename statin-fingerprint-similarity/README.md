# Statin Fingerprint Similarity Search

A retrospective test of whether molecular fingerprint similarity could have guided drug discovery. Nine statins are hidden among 5,448 approved and experimental drugs, and a similarity search starting from lovastatin shows where the others appear.

## What the notebook does

- **Part A: The statin family.** Computes pairwise Tanimoto similarity between the nine statins, shows it as a heatmap, and draws all nine structures.
- **Part B: Similarity search.** Ranks the whole library by similarity to lovastatin, finds where each other statin appears, and examines the top non-statin hits.
- **Part C: Limits of similarity.** Compares ezetimibe (a cholesterol drug with a different mechanism) to the statins and discusses what fingerprint similarity can and cannot find.

All fingerprints are Morgan, radius 2, 2,048 bits. The query is excluded from its own ranking.

## Key findings

- Type I (fungal) statins are clearly related to each other (Tanimoto 0.56-0.85).
- Type I vs type II (synthetic) statins are only 0.19-0.24 similar, close to random drug pairs.
- Atorvastatin ranks 9th of 5,447 (similarity 0.24) from lovastatin, but this is a low value that is near the top only because the rest of the library is very dissimilar.
- Ezetimibe ranks 1,414th (similarity 0.11), so it would have been missed.
- Fingerprint similarity finds close analogues of a known scaffold. It cannot find new scaffolds with the same mechanism, or drugs with the same effect by a different mechanism.

## Files

| File | Description |
|------|-------------|
| `statin_similarity_search.ipynb` | Analysis with code, outputs and written interpretation |
| `drug_library.csv` | 5,448 drugs (`drugbank_id`, `name`, `smiles`) |


## Tools

Python, RDKit, pandas, NumPy, matplotlib, seaborn.