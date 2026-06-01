DI501_EdaOnay_2739415

My updated repository contains the materials for the DI 501 term project based on the SpotGenTrack dataset, both the interim work and final work included in my GitHub.

My Research Questions

1. How much does the inclusion of lyric-complexity features on top of Spotify high-level audio features improve decade-classification accuracy and macro-F1 over a majority-class baseline, and does the choice of model family (Logistic Regression vs. Random Forest) change the answer?
2. Is there a statistically significant difference between older (≤1980) and modern (≥2010) songs in terms of their mean acousticness and energy values?

My Repository Structure

- `articles/`: academic papers reviewed in the introduction and related-work section.
- `data/`: raw dataset files used in the project. Note: `low_level_audio_features.csv` (208 MFCC / Chroma / MEL / spectral columns) is present in the folder but is intentionally excluded from the analysis, I explained in my code (interpretability vs. tractability reasonings).
- `notebooks/`:
  - `DI501_Project_InterimReport_EdaOnay_2739415.ipynb`: original interim-phase notebook (single cell, preserved as the phase-1 artefact).
  - `DI501_Project_FinalReport_EdaOnay_2739415.ipynb`: final notebook, restructured into labelled markdown + code cells (loading -> cleaning -> merging -> EDA -> feature selection -> naïve baseline -> model ablation → hypothesis test → hyperparameter tuning → McNemar's test → permutation importance).
- `reports/`:
  - `DI501_EdaOnay_InterimReport_2739415.pdf`: interim report (also with .docx).
  - `DI501_EdaOnay_FinalReport_2739415.pdf`: final report in IEEE format (also with .docx).
  - `figures/`: generated figures used in the reports.
  - `generated csv files/`: generated summary tables and processed outputs used in reporting (separate files for the interim and the final phase, suffixed accordingly).
- `requirements.txt`: required Python packages and versions.
- `README.md`: this file.

Final Notebook Workflow

The final notebook is broken into labelled markdown + code cells, organised as follows:

1. Imports and project paths.
2. Data loading (the four CSVs from `data/`).
3. Cleaning (drop unnamed columns, rename `id -> track_id`, aggregate the artist table to track level, recode `-1` placeholders in the lyric features as `NaN`).
4. Merging into a single track-level frame.
5. Derived time features (`release_year`, `decade`, `era_group`), data-quality checks, descriptive statistics and the three EDA figures (decade distribution + acousticness / energy boxplots by era group).
6. Feature selection rationale (which audio, artist-context and lyric features are used, and why the 208 low-level audio features are excluded).
7. ML-dataset preparation (complete-case filter, `log1p` transform on heavy-tailed counts, rare-decade filter) and the naïve majority-class baseline.
8. RQ1 ablation: Logistic Regression vs. Random Forest, each on (audio + artist context) vs. (audio + artist + lyric) feature sets, with `class_weight="balanced"`.
9. RQ2 hypothesis test (two-sided Mann-Whitney U and Welch's t-test on `acousticness` and `energy`, with a Bonferroni correction for the two parallel comparisons).
10. Hyperparameter tuning of the best Random Forest configuration via `RandomizedSearchCV` scored by macro-F1.
11. Statistical comparison of the tuned model against the naïve baseline using McNemar's test on paired test-set predictions.
12. Interpretability: permutation importance for the tuned Random Forest, plus the corresponding figure.

All numerical artefacts used by the report are written to `reports/generated csv files/` and all figures to `reports/figures/`.

How to Run

1. Keep the folder structure unchanged.
2. Install the required packages listed in `requirements.txt`.
3. Open the final notebook (`notebooks/DI501_Project_FinalReport_EdaOnay_2739415.ipynb`).
4. Run the cells in order. End-to-end execution regenerates every CSV and figure referenced in the final report.

The interim work can still be executed independently for the first phase.

Notes: The notebook uses relative paths so that the project can be executed within this folder structure across different operating systems (I made the project with MacOS so I tried my best to make it operate smoothly on other OS too). Some large raw data files may be excluded from Git tracking for repository compatibility, while still remaining part of the local project folder. Also, since two of the .csv files were too big to commit to GitHub, I uploaded them to my Google Drive: https://drive.google.com/drive/folders/1lNY-2mdFPFDKf252v8fxymt_NndDWzsv?usp=sharing
