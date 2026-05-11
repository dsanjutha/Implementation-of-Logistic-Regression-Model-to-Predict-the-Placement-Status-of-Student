# Implementation-of-Logistic-Regression-Model-to-Predict-the-Placement-Status-of-Student

## AIM:
To write a program to implement the the Logistic Regression Model to Predict the Placement Status of Student.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
```
1.Start
2.Import required libraries: pandas, numpy, sklearn (for preprocessing, splitting, model, and evaluation).
3.Load dataset: Read Placement_Data.csv using pandas.read_csv().
4.Data preprocessing:
a.Drop irrelevant columns: sl_no (serial number), salary (since placement is predicted before salary). b.Encode categorical variables (gender, ssc_b, hsc_b, hsc_s, degree_t, workex, specialisation, status) into numerical values using LabelEncoder.

5.Define features and target:
a.Features X = all columns except status. b.Target y = status column (0 = Not Placed, 1 = Placed).

6.Split dataset: Divide into training and testing sets using train_test_split with 80% training and 20% testing.
7.Standardize features: Apply StandardScaler to scale the numeric values for better model convergence.
8.Build Logistic Regression model:
a.Initialize Logistic Regression with max_iter=200. b.Train (fit) the model using training data (X_train, y_train).

9.Predict placement status: Use the trained model to predict on X_test.
10.Evaluate performance:
a.Compute accuracy using accuracy_score. b.Generate confusion matrix using confusion_matrix. c.Generate classification report using classification_report. d.Convert confusion matrix and report into better tabular format with pandas.DataFrame.

11.End

``` 

## Program:
```python
/*
Program to implement the the Logistic Regression Model to Predict the Placement Status of Student.
Developed by:sanjutha D 
RegisterNumber:212225240136

import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler, LabelEncoder
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score, confusion_matrix, classification_report
# Step 1: Load dataset
df = pd.read_csv(r"C:\Users\sanju\Downloads\Placement_Data.csv")
# Display first 5 rows
print("First 5 rows:\n")
print(df.head())
# Step 2: Drop unnecessary columns
if "sl_no" in df.columns:
    df = df.drop("sl_no", axis=1)
if "salary" in df.columns:
    df = df.drop("salary", axis=1)
# Step 3: Encode categorical columns
le = LabelEncoder()
for col in df.columns:
    if df[col].dtype == "object":
        df[col] = le.fit_transform(df[col])
# Step 4: Separate features and target
X = df.drop("status", axis=1)
y = df["status"]
# Step 5: Train-Test Split
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)
# Step 6: Feature Scaling
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)
# Step 7: Logistic Regression Model
model = LogisticRegression(
    solver='liblinear',
    random_state=42
)
# Train model
model.fit(X_train, y_train)
# Step 8: Prediction
y_pred = model.predict(X_test)
# Step 9: Accuracy
print("\n✅ Accuracy:", accuracy_score(y_test, y_pred))
# Step 10: Confusion Matrix
cm = confusion_matrix(y_test, y_pred)
cm_df = pd.DataFrame(
    cm,
    index=["Actual:Not Placed", "Actual:Placed"],
    columns=["Pred:Not Placed", "Pred:Placed"]
)
print("\nConfusion Matrix (better format):")
print(cm_df)
# Step 11: Classification Report
report = classification_report(
    y_test,
    y_pred,
    output_dict=True
)
report_df = pd.DataFrame(report).transpose()
print("\nClassification Report (better format):")
print(report_df.round(2))

*/ 

```

## Output:

<img width="901" height="362" alt="image" src="https://github.com/user-attachments/assets/d2f5df6c-7b65-4c2a-b3f2-e6996cae8559" />

<img width="472" height="162" alt="image" src="https://github.com/user-attachments/assets/91d42e56-5cb6-4273-ae38-06fe1b6d4d62" />

<img width="530" height="355" alt="image" src="https://github.com/user-attachments/assets/eb1e6ae9-db97-4b14-8346-4b061119a93f" />


## Result:
Thus the program to implement the the Logistic Regression Model to Predict the Placement Status of Student is written and verified using python programming.
