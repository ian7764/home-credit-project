# home-credit-project
My IS 6850 Home Credit Project
This repository will contain my IS 6850 Home Credit Project work.


## Data Preparation Script (02/08/2026):
This project includes a data preparation script called `data_preparation.qmd`.
The purpose of this script is to clean and preprocess the Home Credit Default Risk dataset and create engineered features that can be used for modeling. It applies consistent transformations to both the training and test datasets to ensure they have the same structure.
To run the script, open `data_preparation.qmd` in RStudio and click **Render**.
The output will be a cleaned dataset that can be used for model development and evaluation.


## Modeling Notebook (02/22/2026):
This project also includes a modeling notebook called `modeling.qmd`. In this notebook, I establish a baseline benchmark, compare several candidate models using 3-fold cross-validation, and evaluate performance using ROC AUC due to class imbalance. The final selected model was a tuned HistGradientBoosting model.

Kaggle Scores:
- Public AUC: 0.73288  
- Private AUC: 0.72729
