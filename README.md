# EXPERIMENT 9 : IMPLEMENTATION OF DECISION TREE REGRESSOR MODEL FOR PREDICTING THE SALARY OF THE EMPLOYEE
## NAME : RUSHMITHA  R
## REGISTRATION NUMBER : 212224040281

## AIM:
To write a program to implement the Decision Tree Regressor Model for Predicting the Salary of the Employee.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. **Import necessary libraries** (pandas, sklearn, metrics, etc.).  
2. **Load the dataset** from CSV file into a pandas DataFrame.  
3. **Explore the data** using head(), info(), isnull().sum().  
4. **Encode categorical features** (e.g., Position) using LabelEncoder.  
5. **Select features (X)** → Position, Level.  
6. **Select target (y)** → Salary.  
7. **Split dataset** into training and testing sets (80%–20%).  
8. **Initialize the DecisionTreeRegressor** model.  
9. **Train the model** using training data (fit).  
10. **Predict salaries** for test data.  
11. **Evaluate performance** using R² score.  
12. **Optionally visualize the tree or print feature importances.**
"""))
## Program:
```
/*
Program to implement the Decision Tree Regressor Model for Predicting the Salary of the Employee.
Developed by: RUSHMITHA  R
RegisterNumber:  212224040281

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.preprocessing import LabelEncoder
from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeRegressor, plot_tree
from sklearn import metrics
import warnings
warnings.filterwarnings("ignore")

# 1) Load dataset
csv_path = "Salary.csv"    # <-- Change path if needed
try:
    data = pd.read_csv(csv_path)
except FileNotFoundError:
    raise FileNotFoundError(f"File not found at: {csv_path}. Update the path.")

print("Dataset Loaded Successfully!\n")

# 2) Data exploration
print("Shape:", data.shape)
display(data.head())
print("\nInfo:")
display(data.info())
print("\nMissing Values:\n", data.isnull().sum())

# 3) Encode categorical column 'Position'
if "Position" in data.columns:
    le = LabelEncoder()
    data["Position"] = le.fit_transform(data["Position"])
    print("\nLabel Encoding Mapping (Position):")
    mapping = dict(zip(le.classes_, le.transform(le.classes_)))
    print(mapping)

# 4) Select features and target
X = data[["Position", "Level"]]
y = data["Salary"]

print("\nFeature Sample:")
display(X.head())
print("\nTarget Sample:")
display(y.head())

# 5) Train-test split
X_train, X_test, Y_train, Y_test = train_test_split(
    X, y, test_size=0.2, random_state=2
)
print(f"\nTrain Size: {X_train.shape}, Test Size: {X_test.shape}")

# 6) Initialize and train Decision Tree Regressor
dt = DecisionTreeRegressor(random_state=10)
dt.fit(X_train, Y_train)
print("\nModel Training Completed!")

# 7) Predict on test data
y_pred = dt.predict(X_test)
print("\nPredicted Salaries:", y_pred)

# 8) Evaluate model using R² Score
r2 = metrics.r2_score(Y_test, y_pred)
print(f"\nR² Score: {r2:.4f}")

# 9) Visualize Decision Tree
plt.figure(figsize=(12,8))
plot_tree(dt, feature_names=["Position", "Level"], filled=True)
plt.title("Decision Tree Regressor for Salary Prediction")
plt.show()

# 10) Feature Importances
importances = pd.Series(dt.feature_importances_, index=["Position", "Level"])
print("\nFeature Importances:")
display(importances)


*/
```

## Output:

<img width="584" height="648" alt="image" src="https://github.com/user-attachments/assets/13477084-c9e8-4edb-a674-30d1f75b999e" />

<img width="444" height="418" alt="image" src="https://github.com/user-attachments/assets/07ef5028-8d77-4ed1-b14e-aac8ddb3dec0" />

<img width="464" height="61" alt="image" src="https://github.com/user-attachments/assets/60080ec9-5494-4152-bcc9-baba1bbbae15" />

<img width="488" height="57" alt="image" src="https://github.com/user-attachments/assets/3d026946-a390-4b90-bc11-50b62ce9a927" />

<img width="1026" height="731" alt="image" src="https://github.com/user-attachments/assets/9b41f212-5bb6-4fb7-ae11-7892b69ec922" />

<img width="833" height="124" alt="image" src="https://github.com/user-attachments/assets/9d1ddb8b-6d29-4d63-9fe6-4ec9105f085d" />


## Result:
Thus the program to implement the Decision Tree Regressor Model for Predicting the Salary of the Employee is written and verified using python programming.
