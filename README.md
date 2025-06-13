Cardiovascular Diseases Risk Prediction post COVID-19 Vaccine and Myocarditis Risk Analysis
============================================================================================

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


Model Performance Summary:
--------------------------
Model                        | Prec. Train | Prec. Test | Recall Train | Recall Test | Acc. Train | Acc. Test | ROC-AUC Train | ROC-AUC Test | F1 Train | F1 Test
----------------------------|-------------|------------|--------------|-------------|------------|-----------|----------------|---------------|----------|---------
Logistic Regression         | 0.6483      | 0.6664     | 0.6468       | 0.6525      | 0.6468     | 0.6525    | 0.6468         | 0.6355        | 0.6458   | 0.6575
Tuned Logistic Regression   | 0.6483      | 0.6664     | 0.6468       | 0.6525      | 0.6468     | 0.6525    | 0.6468         | 0.6355        | 0.6458   | 0.6575
KNN                         | 0.8468      | 0.6490     | 0.8397       | 0.6249      | 0.8397     | 0.6249    | 0.8397         | 0.6161        | 0.8388   | 0.6324
Linear SVM                  | 0.7239      | 0.7132     | 0.7314       | 0.7226      | 0.7314     | 0.7226    | 0.6637         | 0.6527        | 0.7135   | 0.7036
Tuned SVM                   | 0.6476      | 0.6656     | 0.6461       | 0.6515      | 0.6461     | 0.6515    | 0.6461         | 0.6346        | 0.6452   | 0.6566
Regular Decision Tree       | 0.7195      | 0.7089     | 0.7052       | 0.7174      | 0.7052     | 0.7174    | 0.7052         | 0.6694        | 0.7004   | 0.7106
Tuned Decision Tree         | 0.7803      | 0.7443     | 0.7426       | 0.7455      | 0.7426     | 0.7455    | 0.7426         | 0.6687        | 0.7336   | 0.7231
Regular Random Forest       | 0.7952      | 0.7356     | 0.7707       | 0.7414      | 0.7707     | 0.7414    | 0.7707         | 0.6711        | 0.7658   | 0.7231
XGBoost                     | 0.8596      | 0.7693     | 0.8312       | 0.7505      | 0.8312     | 0.7505    | 0.8312         | 0.6587        | 0.8278   | 0.7172
Tuned XGBoost               | 0.8561      | 0.7683     | 0.8274       | 0.7507      | 0.8274     | 0.7507    | 0.8274         | 0.6596        | 0.8239   | 0.7180
Naive Bayes                 | 0.6682      | 0.6807     | 0.6625       | 0.6792      | 0.6625     | 0.6792    | 0.6625         | 0.6489        | 0.6596   | 0.6799
Tuned Naive Bayes           | 0.6747      | 0.6855     | 0.6641       | 0.6902      | 0.6641     | 0.6902    | 0.6641         | 0.6506        | 0.6590   | 0.6874
Neural Network              | 0.7174      | 0.7014     | 0.7061       | 0.7073      | 0.7061     | 0.7073    | 0.7061         | 0.6661        | 0.7023   | 0.7035
BayesSearch NN              | 0.7240      | 0.7136     | 0.7016       | 0.7233      | 0.7016     | 0.7233    | 0.7016         | 0.6688        | 0.6940   | 0.7135
Tuned Neural Network        | 0.7240      | 0.7136     | 0.7016       | 0.7233      | 0.7016     | 0.7233    | 0.7016         | 0.6688        | 0.6940   | 0.7135

Best Model:
-----------
Tuned XGBoost
- Accuracy (Test): 0.7507
- F1 Score (Test): 0.7180
- ROC-AUC (Test): 0.6596


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

1. **Clone the repository**:
   ```bash
   git clone [https://github.com/yourusername/Cardiovascular-Diseases-Risk-Prediction.git]
   cd energy-_forecasting-using-linear-models
2. ** Set Up a Virtual Environment**
   ```bash
   🔹 On Windows
    python -m venv p1env
    env\Scripts\activate

3. Install Required Libraries
   ```bash
   Make sure your virtual environment is activated, then install all required packages using:
   pip install -r requirements.txt
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

