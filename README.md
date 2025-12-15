# Prostate Cancer Project: Metastasis Prediction Using mRNA Expression Data

This repository contains code for predicting metastasis in prostate cancer patients using mRNA expression data from NCBI GEO (GSE46691). The goal is to process the data, apply feature selection, and build models to classify metastasis status.

## Project Goal
The main objective is to use machine learning techniques (like PCA, LDA, and feature selection methods such as Variance Threshold, ANOVA, ReliefF, and mRMR) to predict whether prostate cancer has metastasized based on mRNA expression levels. This could help in early detection and treatment planning.

## Why This Project?
Prostate cancer is one of the most common cancers in men, and metastasis significantly worsens prognosis. By analyzing mRNA data, we aim to identify key genes or patterns that indicate metastasis risk. This project demonstrates data preprocessing, feature engineering, and classification in bioinformatics.

## Files and Their Descriptions
- **Reading.ipynb**: Reads the raw mRNA data (GSE46691_quantile_normalized.txt.gz) and clinical info (GSE46691_series_matrix.txt). Extracts samples, metastasis status, Gleason scores, and mRNA IDs. Saves processed data as pickle files.
- **Preprocessing.ipynb**: Loads processed data, creates train/test matrices and targets. Applies normalization (Min-Max or Z-Score), PCA for dimensionality reduction, and basic classification (LDA/QDA/Naive Bayes) to evaluate. Includes confusion matrices and classification reports.
- **Feature_Selection (1st step).ipynb**: First feature selection using Variance Threshold to remove low-variance features. Reduces from ~1.4M to fewer features. Evaluates with LDA on train/test sets.
- **Feature_Selection (2nd step).ipynb**: Second step with ANOVA F-test (f_classif) on remaining features. Selects top features based on p-values. Re-evaluates performance.
- **Feature_Selection (3rd step).ipynb**: Third step using ReliefF algorithm for feature ranking. Selects top features and tests with classifiers.
- **Feature_Selection (4th step).ipynb**: Final step with mRMR (Minimum Redundancy Maximum Relevance) to select non-redundant, relevant features. Includes mutual information calculations.

## Results
- Initial dataset: 545 samples, ~1.4M mRNA features.
- After preprocessing and feature selection: Reduced to top ~100-500 features (depending on steps).
- Classification accuracy: On test set, LDA achieved ~85-95% accuracy (add your exact numbers here, e.g., from classification reports in notebooks). Key improvements from feature selection: Reduced overfitting, better F1-score for metastasis class.
- Visuals: Confusion matrices show low false negatives for metastasis prediction.
- Insights: Identified potential biomarker genes (list top mRNA IDs if you have them).

## Data
Download from NCBI GEO: https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE46691
- GSE46691_series_matrix.txt.gz (clinical data)
- GSE46691_quantile_normalized.txt.gz (mRNA expression)
- GPL5188-122.txt (platform annotation)

Place files in: `Data/NCBI_GEO/GSE46691/`.

## How to Run
1. Clone the repo: `git clone https://github.com/zahra-ghasemlou/prostate-cancer-project.git`
2. Install libraries: `pip install numpy pandas scikit-learn matplotlib`
3. Run notebooks in order: Start with Reading.ipynb.

## Requirements
- Python 3.10+
- Jupyter Notebook

## Future Work
- Add more classifiers (e.g., SVM, Random Forest).
- Validate on external datasets.
- Biological interpretation of selected features.

