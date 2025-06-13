Cardiovascular Diseases Risk Prediction
=======================================

This project focuses on building predictive models to assess the risk of cardiovascular diseases (CVD) using machine learning. By leveraging both realistic and synthetic data, we aim to identify key health and lifestyle factors contributing to cardiovascular conditions—especially in the context of recent global health events like COVID-19 and vaccination drives.

---------------------------------------
Project Motivation
---------------------------------------

Cardiovascular diseases are a major cause of mortality worldwide. Traditional models often miss recent influences such as COVID-19 infection, vaccination type, and side effects like myocarditis. This project aims to:

1. Build machine learning models to predict CVD risk.
2. Incorporate synthetic data to model modern risk factors (vaccines, infections, etc.) that are not present in public datasets.

---------------------------------------
Dataset Overview
---------------------------------------

1. Realistic Dataset:
   - 308,854 rows and 20 features.
   - Includes data on sex, age category, height, weight, BMI, general health, exercise, heart disease, cancer, depression, diabetes, arthritis, smoking, alcohol use, and diet.
   - This dataset captures core lifestyle and health metrics affecting cardiovascular health.

2. Synthetic Dataset:
   Designed to simulate additional modern risk factors:
   - COVID-19 infection status and severity.
   - Vaccination status, vaccine type (Pfizer, Moderna, AstraZeneca), dose number, and days since vaccination.
   - Myocarditis diagnosis, onset, and recovery.
   - Long COVID symptoms.

   Myocarditis was modeled using logical rules:
   - Higher risk in males aged 16–30 with Moderna or Pfizer after 2nd dose within 28 days.
   - Lower risk for 3rd booster doses.
   - COVID infection increases myocarditis and CHD risk.

   CHD ("cardio") was simulated based on:
   - 40% risk if myocarditis diagnosed.
   - 30% risk if long COVID symptoms present.
   - 20% baseline risk otherwise.

---------------------------------------
Machine Learning Models Used
---------------------------------------

Both base and tuned versions of the following models were used:

- Logistic Regression
- K-Nearest Neighbors
- Linear SVM
- SVM (with hyperparameter tuning)
- Decision Tree
- Random Forest
- XGBoost
- Naive Bayes
- Neural Network
- Neural Network + Bayesian Hyperparameter Search

---------------------------------------
Model Evaluation Metrics
---------------------------------------

Models were evaluated using:

- Precision (Train and Test)
- Recall (Train and Test)
- Accuracy (Train and Test)
- F1 Macro Score (Train and Test)
- ROC-AUC Score (Train and Test)

---------------------------------------
Results Summary
---------------------------------------

Model                    | Train Acc | Test Acc
------------------------ | --------- | --------
Logistic Regression      | 0.6468    | 0.6525
Tuned Logistic Regression| 0.6468    | 0.6525
KNN                      | 0.8397    | 0.6249
Linear SVM               | 0.7314    | 0.7226
SVM Tuned                | 0.6461    | 0.6515
Decision Tree            | 0.7052    | 0.7174
Decision Tree Tuned      | 0.7426    | 0.7455
Random Forest            | 0.7707    | 0.7414
XGBoost                  | 0.8312    | 0.7505
XGBoost Tuned            | 0.8274    | 0.7507
Naive Bayes              | 0.6625    | 0.6792
Naive Bayes Tuned        | 0.6641    | 0.6902
Neural Network           | 0.7061    | 0.7073
NN + BayesSearch         | 0.7016    | 0.7233

Best Model:
- Tuned XGBoost with well-balanced test accuracy, ROC-AUC, and F1 score.

---------------------------------------
Model Interpretability with SHAP
---------------------------------------

SHAP (SHapley Additive Explanations) was used to interpret the best model (Tuned XGBoost).

Top contributing features included:
- BMI
- Smoking history
- Diabetes
- Myocarditis diagnosis
- COVID severity
- Age and sex

SHAP helped identify how individual features influenced CVD risk predictions.

---------------------------------------
Conclusion
---------------------------------------

- Combining real and synthetic data offers richer modeling capacity.
- Ensemble models like XGBoost and Random Forest perform best.
- Interpretability tools like SHAP are essential for model transparency.

---------------------------------------
Future Work
---------------------------------------

- Add time-series or longitudinal tracking of risk.
- Incorporate genetic or environmental variables.
- Validate synthetic assumptions with medical experts.
- Experiment with class imbalance handling.

---------------------------------------
How to Run This Project
---------------------------------------

1. Clone the repository:
   git clone https://github.com/yourusername/Cardiovascular-Diseases-Risk-Prediction.git

2. Install the required libraries:
   pip install -r requirements.txt

3. Train the models:
   python train_models.py

4. Run SHAP analysis:
   python shap_analysis.py

---------------------------------------
References for Synthetic Data Assumptions
---------------------------------------

The synthetic data logic used for myocarditis and cardiovascular risks post-COVID or vaccination is inspired by the following trusted public health resources:

1. CDC Clinical Considerations for COVID-19 Vaccines and Myocarditis:
   https://www.cdc.gov/vaccines/covid-19/clinical-considerations/myocarditis.html

2. British Heart Foundation - Myocarditis and COVID-19 Vaccines:
   https://www.bhf.org.uk/informationsupport/heart-matters-magazine/news/coronavirus-and-your-health/myocarditis-and-covid-19-vaccines-should-you-be-worried

3. Australian Department of Health - Clinical Guidance on Myocarditis and Pericarditis:
   https://www.health.gov.au/our-work/covid-19-vaccines/advice-for-providers/clinical-guidance/myocarditis-pericarditis

