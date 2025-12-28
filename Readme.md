Titanic Survival Prediction - Kaggle Competition



This repository contains my solution for the \[Kaggle Titanic: Machine Learning from Disaster](https://www.kaggle.com/competitions/titanic/overview) competition. The project involves predicting which passengers survived the shipwreck using machine learning techniques in Python.



\## 🏆 Final Performance



Best Kaggle Score: `0.78708`

Model:Random Forest Classifier (`sklearn`)



\## 📈 Experimentation Log



During the development process, I tested multiple approaches to understand how model selection and hyperparameter tuning affect the final accuracy.



| Model | Transformation | Kaggle Score | Note |

| --- | --- | --- | --- |

| \*\*RandomForestRegressor\*\* | Threshold 0.5 | 0.75598 | Strong baseline for a regressor. |

| \*\*RandomForestClassifier\*\* | Default Settings | 0.73205 | Score dropped due to overfitting. |

| \*\*RandomForestClassifier\*\* | \*\*Tuned \& Optimized\*\* | \*\*0.78708\*\* | \*\*Current Best Version.\*\* |



---



\## 🛠️ Methodology



\### 1. Data Preprocessing



I developed a cleaning pipeline to prepare the raw Titanic data for the Random Forest model:



\* \*\*Feature Selection:\*\* Dropped high-cardinality features that didn't provide generalizable patterns (`Name`, `Ticket`, and `Cabin`).

\* \*\*Categorical Encoding:\*\* Converted `Sex` and `Embarked` into numerical category codes to allow the model to process string data.

\* \*\*Feature Consistency:\*\* Ensured both training and testing sets underwent the exact same transformations to avoid data leakage.



\### 2. The Model



The final submission uses the \*\*Random Forest Classifier\*\*. Key aspects of the implementation include:



\* \*\*Ensemble Learning:\*\* Leveraging multiple decision trees to reduce variance and improve stability.

\* \*\*Overfitting Control:\*\* By tuning parameters such as tree depth and leaf samples, I improved the score from 0.73 to 0.78, ensuring the model generalizes well to unseen data.



```python

from sklearn.ensemble import RandomForestClassifier



\# Optimized Model Configuration

model = RandomForestClassifier(

&nbsp;   n\_estimators=100,

&nbsp;   max\_depth=5,

&nbsp;   random\_state=42

)



\# Training

model.fit(X\_train, y\_train)



\# Prediction

predictions = model.predict(X\_test)



```



\## 📂 Project Structure



\* `train.csv` / `test.csv`: Original competition datasets.

\* `submission.csv`: The final output file generated for Kaggle.

\* `Titanic\_prediction\_kaggle.ipynb`: Main script containing the preprocessing function and model training.



\## 🚀 Next Steps



To break the 0.80 barrier, future iterations will focus on:



1\. \*\*Feature Engineering:\*\* Extracting "Titles" (Mr., Mrs., Master.) from the Name column.

2\. \*\*Family Mapping:\*\* Calculating family size by combining `SibSp` and `Parch`.

3.Missing Value Imputation:\*\* Using more advanced techniques for filling missing `Age` values based on Pclass or Title.


