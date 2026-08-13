# Diabetes Risk Prediction Analysis
A predictive modeling project that looks at which health, lifestyle, and socioeconomic factors are most closely linked to diabetes risk. The project uses CDC survey data from more than 250,000 U.S. adults and was completed as part of a B.S. in Data Analytics capstone. It demonstrates the full data analytics process, including cleaning the data, exploring patterns, building models, and explaining the results in a way that is easy for non technical audiences to understand.

## Research Question
Can predictive analytics be used to predict diabetes risk and inform early screening and decisions for preventive care? 
### Hypothesis
Elevated blood pressure, higher BMI, and advanced age are associated with an increased likelihood of diabetes.

### Data
#### **Source**: 
CDC Diabetes Health Indicators Dataset (Kaggle, via BRFSS 2015)
#### **Size**: 
253,680 survey responses, 22 variables (BMI, blood pressure, cholesterol, physical activity, general/mental/physical health, age, income, education, and more)
#### **Target**: 
Diabetes_binary — whether the respondent reported a diabetes diagnosis
- The dataset is naturally imbalanced (most respondents do not have diabetes); this imbalance was kept intentional rather than artificially rebalanced, since the goal was to model real-world prevalence rather than an idealized 50/50 split.

### Approach 
1. **Data cleaning:** Checked data types, identified missing values, and removed duplicate records
2. **Exploratory analysis:** Examined the number of people with and without diabetes and compared BMI and age between the two groups. Also looked at how BMI, age, and high blood pressure were related to diabetes.
3. **Data Preparation:** Standardized BMI and age using z-score scaling and split the data into 80% for training and 20% for testing.
4. **Modeling:** Built and compared two models:
 - **Logistic Regression:** Used as a simple and easy to understand baseline model.
 - **Random Forest:** Used 100 decision trees to identify more complex patterns and relationships in the data.
6. **Evaluation:** Compared the models using accuracy, recall, and AUC ROC. Confusion matrices and feature importance were also used to better understand the results.

### Results
| Model | Accuracy | Recall | AUC |
|---|---|---|---|
| Logistic Regression | 0.851 | 0.154 | 0.565 |
| Random Forest | 0.843 | 0.168 | 0.779 |

**Model selection:** Random Forest performed better overall. Both models had similar accuracy, but the Random Forest model had a much higher AUC (0.779 vs. 0.565). This means it was better at telling the difference between people with and without diabetes. Accuracy can be misleading here because most people in the dataset did not have diabetes.

**Top predictors:** BMI, age, and income were the most important factors in the Random Forest model. General health and physical health were also important. These results support the idea that BMI, age, and health conditions can be useful in assessing diabetes risk.

**Model limitation:** One thing to keep in mind is that both models had low recall, around 15% to 17%. This means the models were not very good at finding people who actually had diabetes. If the model were ever used for screening, this would need to be improved. Using a different cutoff or balancing the data could help the model catch more diabetes cases.

### Tools
- **Python Library:** Pandas, Numpy 
- **Visualization:** Matplotlib, Seaborn
-  **Modeling:** scikit-learn (Logistic Regression, Random Forest, train/test split, evaluation metrics)

 ### Cited Source
 Teboul, A. Diabetes Health Indicators Dataset, Kaggle, sourced from the CDC Behavioral Risk Factor Surveillance System (BRFSS) 2015. https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset
