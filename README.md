# home-credit-project
### Ian Christiansen

My IS 6850 Home Credit Project
This project focuses on predicting loan default risk using the Home Credit dataset, with an emphasis on turning data analysis into meaningful business insights. The data itself highlights key patterns behind default behavior, including the strong class imbalance (only about 8% of applicants default), as well as how factors like income, credit history, loan size, and past payment behavior contribute to risk differences across borrowers. By building and comparing several models and refining a gradient boosting approach, the final solution achieved a ROC AUC of around 0.73, showing a solid ability to distinguish between higher- and lower-risk borrowers despite the challenging dataset. Beyond performance, I focused on how these results would actually be used in a real lending environment by exploring decision thresholds, model explainability, and fairness considerations. Overall, this project demonstrates how data-driven insights can uncover the drivers of default risk, improve borrower segmentation, reduce potential credit losses, and support more informed and responsible lending decisions at scale.


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


## Model Card (03/05/2026):
This repository’s model_card.qmd is a business‑friendly write‑up of the Kaggle Home Credit Default Risk work, turning the modeling results into an executive summary plus sections on Model Details, Intended Use, Performance Metrics, Threshold Analysis, Explainability, Adverse Action Mapping, Fairness, and Limitations. It explains the chosen threshold, the expected financial impact, and the key caveats in plain language, while linking to the underlying modeling notebook for traceability. The document is designed for non-technical readers, with code folded and outputs visible in the HTML render and with governance notes (ECOA and fair lending) and a plan for monitoring, retraining, and deployment readiness.


## Summary of Business Problem and Project Objective:
Home Credit is trying to expand access to credit while managing the risk of borrower default. The core challenge is identifying which applicants are likely to default so the company can make better lending decisions without being overly restrictive. The objective of this project was to use historical applicant and loan data to predict default risk and support more informed, data-driven lending strategies.


## My Solution to the Business Problem:
To address this problem, I cleaned and transformed the dataset, created meaningful features, and tested multiple modeling approaches to find the most effective way to distinguish between high- and low-risk borrowers. I ultimately focused on a gradient boosting approach that performed best based on ROC AUC and refined it through tuning. I also went beyond prediction by analyzing decision thresholds and model outputs in a way that aligns with real business use.


## The Business Value of the Solution:
This solution provides a way to better segment borrowers by risk, allowing lenders to approve more qualified applicants while avoiding high-risk loans. By improving the ability to identify likely defaults, the model can help reduce credit losses and improve overall portfolio performance. It also supports more consistent and explainable decision-making, which is important for both internal stakeholders and regulatory requirements.


## Difficulties Encountered:
One of the biggest challenges was dealing with the highly imbalanced dataset, where only a small percentage of applicants default. This made traditional metrics like accuracy misleading and required a shift toward more appropriate evaluation methods like ROC AUC. Additionally, managing the large dataset, experimenting with different techniques, and ensuring consistent preprocessing between training and test data added complexity throughout the project.


## What I Learned:
Through this project, I learned how important it is to connect technical results back to real business decisions rather than focusing only on model performance. I gained experience working with imbalanced data, selecting appropriate evaluation metrics, and understanding how small improvements in prediction can translate into meaningful financial impact. I also developed a better understanding of how to communicate analytical results clearly to both technical and non-technical audiences.



