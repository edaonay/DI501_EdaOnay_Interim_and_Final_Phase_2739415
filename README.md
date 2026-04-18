DI501_EdaOnay_InterimPhase_2739415

My repository contains the interim phase materials for the DI 501 term project based on the SpotGenTrack dataset.

My Research Questions
1. To what extent can a song’s release decade be predicted using Spotify audio features and Genius lyric-complexity features in a multi-class classification setting?
2. Is there a statistically significant difference between older and modern songs in terms of their mean acousticness and energy values?

My Repository Structure
- `articles/`: academic papers reviewed in the introduction and related work section.
- `data/`: raw dataset files used in the project.
- `notebooks/`: Jupyter notebook used for preprocessing, profiling, descriptive statistics, and naive baseline analysis.
- `reports/`: interim report files in Word and PDF format.
- `figures/`: generated figures used in the report.
- `generated csv files/`: generated summary tables and processed outputs used in reporting.
- `requirements.txt`: required Python packages and versions.
- `README.md`: explanation of the project structure and execution steps.

Notebook Workflow
The notebook is organized into the following main stages:

1. Data Loading
   The track-level, album-level, artist-level, and lyric-feature tables are loaded from the `data/` folder.

2. Data Cleaning
   Unnecessary index-like columns are removed, key columns are standardized, and invalid placeholder values such as `-1` in lyric features are converted to missing values.

3. Merge Operations
   The tables are merged by `track_id` to construct a unified song-level dataset.

4. Feature Preparation  
   Variables required by the research questions are selected. The `release_year`, `decade`, and `era_group` variables are derived for the machine learning and hypothesis-testing tasks.

5. Data Profiling and Descriptive Statistics  
   Missing values, duplicate structures, release year distribution, and selected descriptive statistics are examined and exported.

6. Exploratory Visualization 
   Figures used in the report, such as the release decade distribution chart, are generated and saved to the `figures/` folder.

7. Naive Baseline Evaluation 
   A majority-class baseline is defined for the release decade classification task and evaluated using accuracy, macro-F1, and balanced accuracy.

How to Run
1. Keep the folder structure unchanged.
2. Install the required packages listed in `requirements.txt`.
3. Open the notebook in the `notebooks/` folder.
4. Run the notebook cells in order.

Notes:
The notebook uses relative paths so that the project can be executed within this folder structure across different operating systems (I made the project with MacOS so I tried my best to make it operate smoothly on other OS too). Some large raw data files may be excluded from Git tracking for repository compatibility, while still remaining part of the local project folder. Also, since two of the .csv files were too big to commit to GitHub, I uploaded them to my Google Drive: https://drive.google.com/drive/folders/1lNY-2mdFPFDKf252v8fxymt_NndDWzsv?usp=sharing
