# Hunger meets Golden Time 🧁😋
## Project Overview   
This project analyzes food delivery data to understand customer ordering behavior, 
identify golden time periods, and explore key factors affecting delivery time. 
And then applies **Machine learning models** to predict which factors truly impact delivery duration.
The insights are used to suggest promotion strategies that can help delivery platforms improve efficiency and support business growth.

## Dataset
- **Source:** [Zomato Delivery Operations Analytics Dataset (Kaggle)](https://www.kaggle.com/datasets/saurabhbadole/zomato-delivery-operations-analytics-dataset)
- **Rows:** 45,584
- **Columns:** 20

## Tools & Tech
- JupyterLab
- Python
- Pandas, NumPy
- Matplotlib, Seaborn
- Scikit-learn

## Knowledge & Skills
- Perform **EDA** to understand patterns, trends, and anomalies in real-world delivery data
- Clean and preprocess raw datasets for analysis and modeling
- Build and compare **ML model** (Linear Regression, Random Forest) for delivery time prediction
- Evaluate model performance using Mean Absolute Error (MAE)
- Interpret model outputs and feature importance to understand key factors affecting delivery time
- Translate data insights into **actionable business strategies** for promotion planning and operations

## Project Structure
```
.
├── data/
│ ├── raw
│ │   ├── zomato_dataset.csv
│ │   └── cleaned_zomato.csv
│ └── zomato_cleaned_features.csv
│
├── notebooks/
│ ├── 01_data_cleaning.ipynb
│ ├── 02_time_analysis.ipynb --> Time-based analysis to identify peak & off-peak hours
│ ├── 03_food_type_analysis.ipynb --> Food type analysis and Golden Time × Food insights
│ ├── 04_delivery_time_model.ipynb --> Predictive modeling (Linear Regression, Random Forest)
│ └── 05_promotion_strategy.ipynb --> BU recommendations based on insights & ML results
│
├── .gitignore
└── README.md
```

## What I’m Most Proud Of in This Project
- **Problem**  
The `Time_Ordered` column contained approximately **1,731 missing values**.  
I think it's not a good idea tp filling them with `00:00` 
or a global median could introduce significant bias into time-based analysis.

- **Solution**   
  Instead of filling missing values with an median or default value, I took advantage of the fact that `Time_Order_picked` has no missing values.
  1. Calculated the time difference between `Time_Ordered` and `Time_Order_picked` for rows where both values were available  
  2. Computed the **median time difference grouped by `Type_of_order` and `Type_of_vehicle`**, which are complete and relevant features  
  3. Imputed missing `Time_Ordered` values by subtracting the group-level median time difference from `Time_Order_picked`  
  4. Merged the imputed values **only for missing rows**, ensuring existing data remained unchanged

- **Result**  
  - I was able to reduce data loss from **1,731 rows to just 68 rows.**
  - Keeps the ordering patterns close to real-world behavior, without forcing artificial values
  - Enabled more reliable time-based and predictive analysis
