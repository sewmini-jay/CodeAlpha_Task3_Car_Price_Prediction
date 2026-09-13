# Car Price Prediction with Machine Learning

## Introduction
This project is developed as part of the CodeAlpha Data Science Internship.

The objective is to build a regression model that predicts the selling price of a used car based on features like the car's age, present showroom price, kilometers driven, fuel type, seller type, transmission, and ownership history.

## Problem Statement
Used car pricing depends on multiple factors including depreciation, mileage, brand, and condition. This project builds a regression model to predict the `Selling_Price` of a car using its other attributes, helping buyers and sellers estimate a fair resale value.

## Dataset Description
The dataset contains 301 used car listings (model years 2003–2018) with the following columns:
- `Car_Name` — model name of the car
- `Year` — year of manufacture
- `Selling_Price` — price at which the car was sold (target variable, in Lakhs INR)
- `Present_Price` — current ex-showroom price (Lakhs INR)
- `Kms_Driven` — total kilometers driven
- `Fuel_Type` — Petrol / Diesel / CNG
- `Seller_Type` — Dealer / Individual
- `Transmission` — Manual / Automatic
- `Owner` — number of previous owners

## Feature Engineering
- Converted `Year` into `Car_Age` (2020 − Year) to better capture depreciation
- One-hot encoded categorical columns (`Fuel_Type`, `Seller_Type`, `Transmission`)
- Dropped `Car_Name` due to high cardinality (98 unique values across 301 rows)

## Model Comparison

| Model | MAE | RMSE | R² |
|---|---|---|---|
| Linear Regression | 1.216 | 1.865 | 0.849 |
| Lasso Regression | 1.471 | 2.154 | 0.799 |
| Decision Tree | 0.862 | 1.434 | 0.911 |
| **Random Forest** | **0.639** | **0.960** | **0.960** |

Random Forest was selected as the final model.

## Key Findings
- `Present_Price` is by far the most important feature (~88% of feature importance) — a car's original price strongly determines its resale value
- `Car_Age` and `Kms_Driven` contribute smaller but meaningful predictive power
- Categorical features (fuel type, seller type, transmission) had comparatively minor influence once price and age were accounted for
- The final model achieved an R² of 0.96, meaning it explains 96% of the variance in used car selling prices

## Tools & Libraries
- Python
- Pandas, NumPy
- Matplotlib, Seaborn
- Scikit-learn

## Conclusion
Random Forest Regression provided the most accurate and reliable predictions for used car prices in this dataset. The results confirm that a car's original price is the dominant driver of resale value, while age and mileage provide secondary adjustments. This model could be a practical tool for buyers and sellers to estimate fair used car prices in real-world scenarios.
