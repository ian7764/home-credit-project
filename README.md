# home-credit-project
My IS 6850 Home Credit Project
This repository will contain my IS 6850 Home Credit Project work.


## Data Preparation Script (02/08/2026):
This project includes a data preparation script called `data_preparation.qmd`.
The purpose of this script is to clean and preprocess the Home Credit Default Risk dataset and create engineered features that can be used for modeling. It applies consistent transformations to both the training and test datasets to ensure they have the same structure.
To run the script, open `data_preparation.qmd` in RStudio and click **Render**.
The output will be a cleaned dataset that can be used for model development and evaluation.


## Modeling Notebook (02/22/2026):
This project also includes a modeling notebook called modeling.qmd. In this notebook, I started by building a majority-class baseline and quickly saw why accuracy alone is misleading for this dataset. Even though the baseline had about 91.9% accuracy, the ROC AUC was only 0.50 since it was basically predicting non-default for everyone in a highly imbalanced dataset (~8% defaults). From there, I compared several models using a 50,000-row stratified sample with 3-fold cross-validation and ROC AUC as the main metric. I tested logistic regression (with and without class weighting), random forest, and HistGradientBoosting. HistGradientBoosting performed the best (around 0.736 CV AUC), so I decided to focus on that model. I also experimented with imbalance strategies like oversampling, undersampling, and SMOTE, but none of them improved performance over the regular model. After that, I ran a RandomizedSearchCV on a smaller 5,000-row stratified sample to tune hyperparameters, and when I evaluated the tuned model again on the full 50k sample, the AUC improved to about 0.740. I then used this tuned HistGradientBoosting model to generate predictions for Kaggle, which resulted in a Public AUC of 0.73288 and a Private AUC of 0.72729.

Kaggle Scores:
- Public AUC: 0.73288  
- Private AUC: 0.72729
