# Big Mart Sales Prediction using Python AI/ML

This project aims to predict sales data for Big Mart stores using machine learning algorithms. The **XGBoost Regressor** model is used to predict the sales (`Item_Outlet_Sales`) based on various features such as item weight, visibility, price, and outlet characteristics.

The dataset for this project can be found at [Kaggle - Big Mart Sales Data](https://www.kaggle.com/datasets/brijbhushannanda1979/bigmart-sales-data?select=Train.csv).

## Table of Contents
- [Overview](#overview)
- [Dependencies](#dependencies)
- [Dataset Information](#dataset-information)
- [Data Collection and Processing](#data-collection-and-processing)
- [Data Analysis](#data-analysis)
- [Data Pre-Processing](#data-pre-processing)
- [Model Training](#model-training)
- [Model Evaluation](#model-evaluation)
- [How to Run the Code](#how-to-run-the-code)

## Overview

This project uses **XGBoost**, a gradient boosting algorithm, to predict the **Item_Outlet_Sales** for Big Mart based on multiple features such as product type, visibility, price, and outlet information.

### The project includes the following steps:
1. Data Collection
2. Data Processing and Handling Missing Values
3. Data Analysis and Visualization
4. Data Pre-Processing (label encoding categorical variables)
5. Model Training using **XGBoost Regressor**
6. Model Evaluation using R-squared values
7. Predictive System for new data

---

## Dependencies

Ensure you have the following dependencies installed to run the code:

- **Python 3.x**
- **NumPy**: For numerical computing
- **Pandas**: For data manipulation
- **Matplotlib**: For data visualization
- **Seaborn**: For statistical data visualization
- **Scikit-learn**: For machine learning and evaluation
- **XGBoost**: For gradient boosting model implementation

To install these dependencies, you can run:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn xgboost
```

---

## Dataset Information

The dataset consists of the following columns:

1. **Item_Identifier**: Unique identifier for each item.
2. **Item_Weight**: Weight of the item.
3. **Item_Fat_Content**: Whether the item is low fat or regular fat.
4. **Item_Visibility**: Visibility of the item in the store.
5. **Item_Type**: The category of the item.
6. **Item_MRP**: Maximum Retail Price of the item.
7. **Outlet_Identifier**: Unique identifier for the outlet.
8. **Outlet_Establishment_Year**: The year the outlet was established.
9. **Outlet_Size**: Size of the outlet.
10. **Outlet_Location_Type**: Location type of the outlet.
11. **Outlet_Type**: Type of the outlet.
12. **Item_Outlet_Sales**: The target variable, representing the sales of the item in the outlet.

---

## Data Collection and Processing

The data is loaded from a **CSV file** into a **Pandas DataFrame**. The initial exploration includes checking for missing values, data types, and basic statistics.

### Handling Missing Values:
- **Item_Weight**: Missing values are filled with the mean of the `Item_Weight` column.
- **Outlet_Size**: Missing values are filled using the mode of the respective outlet type.

---

## Data Analysis

We perform an exploratory data analysis (EDA) to understand the distribution of numerical features such as:
- **Item_Weight**
- **Item_Visibility**
- **Item_MRP**
- **Item_Outlet_Sales**

We also analyze categorical features, such as:
- **Item_Fat_Content**
- **Item_Type**
- **Outlet_Size**
- **Outlet_Location_Type**

### Visualizations include:
- Distribution plots for continuous variables.
- Count plots for categorical variables.

---

## Data Pre-Processing

### Label Encoding:
Categorical features are encoded into numerical values using **LabelEncoder** to make them suitable for machine learning algorithms.

The columns encoded are:
- **Item_Identifier**
- **Item_Fat_Content**
- **Item_Type**
- **Outlet_Identifier**
- **Outlet_Size**
- **Outlet_Location_Type**
- **Outlet_Type**

This step converts the categorical columns into numeric values, allowing us to train the model.

---

## Model Training

We use **XGBoost Regressor** for training the model to predict the **Item_Outlet_Sales**.

1. **Splitting the dataset**: The data is split into training (80%) and testing (20%) datasets using `train_test_split`.
2. **Model Training**: The XGBoost model is trained on the training data.

```python
regressor = XGBRegressor()
regressor.fit(X_train, Y_train)
```

---

## Model Evaluation

Once the model is trained, we evaluate its performance using the **R-squared (R²)** value:
- **Training R²**: The R² score for the training data indicates how well the model fits the training data.
- **Testing R²**: The R² score for the test data evaluates how well the model generalizes to unseen data.

```python
# R squared value for training data
r2_train = metrics.r2_score(Y_train, training_data_prediction)
print('R Squared value = ', r2_train)

# R squared value for test data
r2_test = metrics.r2_score(Y_test, test_data_prediction)
print('R Squared value = ', r2_test)
```

---

## How to Run the Code

1. **Download the dataset** from [Kaggle - Big Mart Sales Data](https://www.kaggle.com/datasets/brijbhushannanda1979/bigmart-sales-data?select=Train.csv).
2. **Load the dataset** into a Pandas DataFrame.
3. **Handle missing values** and perform necessary preprocessing steps.
4. **Encode categorical variables** using **LabelEncoder**.
5. **Split the dataset** into features (X) and target (Y), then further split into training and testing sets.
6. **Train the XGBoost Regressor model**.
7. **Evaluate the model's performance** using R² values on training and testing data.
8. **Predict sales** for new data.

---

## Conclusion

This project demonstrates how machine learning can be applied to predict retail sales for Big Mart. The **XGBoost Regressor** model effectively predicts the sales of an item in an outlet, providing valuable insights for inventory management and sales forecasting. By training on multiple features, the model is able to make accurate predictions and generalize well to unseen data.

Feel free to enhance the model, experiment with different algorithms, or add additional features to further improve the predictions.S