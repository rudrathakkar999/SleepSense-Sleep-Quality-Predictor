# SleepSense: Sleep Quality Predictor

A Machine Learning project for predicting sleep quality using lifestyle and health-related data.

## About the Project

SleepSense is a machine learning-based project that predicts an individual's sleep quality using various lifestyle and health-related factors.

The project explores how factors such as sleep duration, stress level, physical activity, BMI category, heart rate and daily habits relate to sleep quality.

The main objective is to understand the dataset, perform data preprocessing, train suitable regression models and evaluate their performance.

## Objectives

* Understand and explore the Sleep Health and Lifestyle dataset.
* Perform data cleaning and preprocessing.
* Identify relevant features for predicting sleep quality.
* Build and train machine learning regression models.
* Evaluate and compare model performance.
* Analyse the importance of different input features.

## Dataset

**Dataset:** Sleep Health and Lifestyle Dataset

* Total records: 374
* Total original columns: 13
* Target variable: `Quality of Sleep`
* Prediction type: Regression

The dataset contains information about individuals, including:

* Age
* Gender
* Occupation
* Sleep Duration
* Physical Activity Level
* Stress Level
* BMI Category
* Blood Pressure
* Heart Rate
* Daily Steps
* Sleep Quality

## Data Preprocessing

The following preprocessing operations were performed:

1. **Dataset Exploration:** Examined the dataset structure, column types, descriptive statistics and missing values.
2. **BMI Standardisation:** Combined the `Normal Weight` category with `Normal`.
3. **Blood Pressure Transformation:** Split the Blood Pressure column into separate Systolic BP and Diastolic BP features.
4. **Feature Selection:** Excluded Person ID, Quality of Sleep (target) and Sleep Disorder from the input features.
5. **Missing Values:** Retained all records and excluded Sleep Disorder from model inputs because it contained missing values.
6. **Train-Test Split:** Divided the dataset into 80% training data and 20% testing data.
7. **Feature Transformation:** Applied StandardScaler to numerical features and OneHotEncoder to categorical features.

The preprocessing operations were implemented using Scikit-learn pipelines and ColumnTransformer.

## Machine Learning Models

Two regression models were implemented:

### 1. Linear Regression

Used as a baseline regression model to understand the relationship between input features and sleep quality.

### 2. Random Forest Regression

Used to capture more complex relationships between lifestyle factors and sleep quality through an ensemble of decision trees.

## Model Evaluation

The models were evaluated using the following metrics:

* **Mean Absolute Error (MAE):** Measures the average absolute difference between actual and predicted values.
* **Root Mean Squared Error (RMSE):** Measures prediction error while giving greater weight to larger errors.
* **R-squared (R²):** Measures how much of the variation in the target variable is explained by the model.

### Random Forest Results

**Single 80/20 Holdout Test:**

| Metric   | Result |
| -------- | -----: |
| MAE      |  0.039 |
| RMSE     |  0.129 |
| R² Score |  0.989 |

### Group K-Fold Cross-Validation

To evaluate generalisation more carefully, Group K-Fold cross-validation was performed using groups of identical input feature combinations.

| Metric        | Random Forest | Linear Regression |
| ------------- | ------------: | ----------------: |
| Mean R² Score |         0.958 |             0.927 |
| Mean MAE      |         0.076 |             0.179 |

Random Forest achieved better average performance across the Group K-Fold validation.

## Feature Importance Analysis

Random Forest feature importance analysis identified the following leading features:

| Feature        | Importance |
| -------------- | ---------: |
| Sleep Duration |     79.05% |
| Stress Level   |     10.61% |

Together, these two features account for approximately 89.66% of the model's reported feature importance.

These values describe the model's predictive behaviour and do not establish causation.

## Feature Ablation Analysis

An additional experiment was performed by removing Sleep Duration and Stress Level from the input features.

The Random Forest model achieved a mean Group K-Fold R² score of approximately **0.798** without these two features, compared with **0.958** when they were included.

This experiment helped understand their contribution to the model's predictive performance.

## Technologies Used

* Python
* Google Colab
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Jupyter Notebook

## Project Notebook

The complete implementation, including data exploration, preprocessing, model training, evaluation, visualisations and validation experiments, is available in the Jupyter Notebook:

**SleepSense_ML_Project_Final.ipynb** (available in this repository).

## Limitations

* The dataset contains only 374 records.
* Repeated input feature combinations are present in the dataset.
* Model performance on this dataset may not represent performance on unseen real-world populations.
* Feature importance does not imply a causal relationship.
* The project has not been clinically validated.

## Future Scope

* Evaluate the models using additional and larger datasets.
* Explore other regression algorithms.
* Improve model generalisation.
* Develop an interactive interface for user predictions.
* Investigate additional lifestyle features that may contribute to sleep quality prediction.

## Disclaimer

SleepSense is an educational machine learning project developed for learning and experimentation.

It is not a medical tool and should not be used for medical diagnosis, treatment decisions or clinical assessment.

---

**Project:** SleepSense – Sleep Quality Predictor
**Domain:** Machine Learning
**Task:** Regression
