# 🧬 Lab Project: Machine learning models of CFTR genetic diversity predict on-target effects of gene editing as a therapeutic strategy in Cystic Fibrosis

This repository contains 4 jupyter notebooks which are modular and sequentially build upon the previous one. These jupyter notebooks were collectively used to generate all the results for the paper. 

# Notebook Order of Execution: 

1."pwCF Unsupervised Machine Learning.ipynb"
↓
2."pwCF Supervised Machine Learning and Associations.ipynb"
↓
3."CF Carriers Association Validation (part i).ipynb"
↓
4."CF Carriers Association Validation (part ii).ipynb"

# Notebook Overview

1.**"pwCF Unsupervised Machine Learning.ipynb"**
- Retrieves clinical, demographic, and genomic data for the people with CF (pwCF) cohort.
- Defines intronic regions and organizes variants by intron across all individual.
- Filters individuals with CF based on genetic relatedness.
- Loads a curated list of CFTR exonic variants with pathogenicity and genomic coordinates to annotate each individual.
- Performs variant-level quality control across introns.
- Converts genotype calls to numerical format and uploads the processed data to a secure Google Cloud Workbucket.
- Performs unsupervised machine learning (PCA) to reduce dimensionality and annotate patterns based on demographic or genomic factors.
- Used to generate Figures 1, 2, S2, S3, S4, and Table 1 in the manuscript.

2.**"pwCF Supervised Machine Learning and Associations.ipynb"**
- Calculates phase-agnostic linkage disequilibrium among variants within each intron.
- Trains XGBoost models using pre-optimized hyperparameters (via GridSearchCV). Note: First-time users must perform and save the hyperparameter tuning.
- Visualizes feature importance of intronic variants for predicting exonic genotypes (F508del, V470M, Combined) using bar and dot plots.
- Summarizes variant contributions per intron for each prediction task.
- Evaluates model performance using confusion matrices and precision-recall curves.
- Computes class-specific average precision scores from the precision-recall curves. 
- Conducts one-tailed Fisher’s exact tests (greater) to validate model-identified associations, exporting results for downstream use.
- Used to generate Figures 3–7, S1, S5, and Tables S2, S3.

3.**"CF Carriers Association Validation (part i).ipynb"**
- Defines and organizes variants by intronic region for individuals in the CF carrier cohort.
- Filters individuals who are CF carriers based on relatedness.
- Performs quality control on intronic variants.
- Converts genotype calls to numerical format and uploads to the secure cloud Workbucket.
- Harmonizes variant locus naming across pwCF and CF carrier cohorts to ensure comparability (due to cohort size differences, variant filtering thresholds may differ resulting in different locus names LocusA (1) vs. LocusA (B) between cohorts).

4.**"CF Carriers Association Validation (part ii).ipynb"**
- Performs one-tailed Fisher’s exact tests in CF carriers to validate pwCF model-predicted associations.
- Merges statistical results from both cohorts into a unified dataset.
- Annotates variants based on eQTL status, identifying unique eQTLs per model.
- Exports final statistical results for each variant for further formatting and presentation.
- Used to generate Figures 8, 9 and Tables S4, S5, S6.

# 💻 Package/Software Versions used for this analysis
python version: 3.10.12
pandas version: 2.0.3
os version: posix
numpy version: 1.23.5
hail version: 0.2.130.post1-c69cd67afb8b
openpyxl version: 3.1.5
matplotlib version: 3.7.2
json version: 2.0.9
plotly version: 5.23.0
scipy version: 1.13.0
seaborn version: 0.12.2
graphviz version: 0.20.3
mpl_axes_aligner version: 1.3
sklearn version: 1.3.0
XGBoost version: 3.0.0
SHAP version: 0.47.2
