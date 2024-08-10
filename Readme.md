# Food Delivery Time Prediction Model

This capstone project, developed for the Digica Academy Data Science Bootcamp, simulates the workflow of a data scientist. The project involves building a model to predict food delivery times using a Jupyter Notebook (.ipynb) and communicating the model's insights effectively through a PowerPoint presentation (.pptx). Additionally, a cost assumption analysis is included in an Excel file to provide further context.

## Project Objective

1. Develop a predictive model for accurate delivery times.
2. Enhance customer satisfaction by aligning expectations with actual delivery times.
3. Reduce customer support costs by decreasing the number of delivery time-related complaints.
4. Improve profitability through cost reduction and customer base growth.

## Libraries Used

**Data Manipulation and Analysis**

- **pandas**: For data manipulation and analysis with DataFrames and Series.
- **numpy**: For numerical operations and array manipulation.
- **janitor**: For data cleaning and tidying operations.
- **statsmodels**: For statistical modeling, including calculating Variance Inflation Factor (VIF).
- **geopy**: For geographical calculations, specifically calculating distances using coordinates.

**Machine Learning**

- **sklearn**: For machine learning algorithms (Linear Regression, Ridge, Lasso, Random Forest), model selection (train_test_split, GridSearchCV, RandomizedSearchCV), and evaluation metrics (mean_absolute_error, root_mean_squared_error, r2_score).

**Data Visualization**

- **matplotlib**: For creating static, animated, and interactive visualizations.
- **seaborn**: For high-level data visualization based on matplotlib, providing attractive statistical graphics.

## Data Overview

The dataset provided by Digica Academy, in CSV format (Food_Delivery_Time_Dataset.csv), contains 45,593 entries with 20 columns:

| Column Name                  | Data Type |
|------------------------------|-----------|
| Delivery_person_ID            | object    |
| Delivery_person_Age           | object    |
| Delivery_person_Ratings       | object    |
| Restaurant_latitude           | float64   |
| Restaurant_longitude          | float64   |
| Delivery_location_latitude    | float64   |
| Delivery_location_longitude   | float64   |
| Order_Date                    | object    |
| Time_Orderd                   | object    |
| Time_Order_picked             | object    |
| Weatherconditions             | object    |
| Road_traffic_density          | object    |
| Vehicle_condition             | int64     |
| Type_of_order                 | object    |
| Type_of_vehicle               | object    |
| multiple_deliveries           | object    |
| Festival                      | object    |
| City                          | object    |
| Time_taken(min)               | object    |

## Methodology

### Data Preparation

Data cleaning was performed to ensure:
- No null values or duplicate rows.
- Standardized column names to comply with snake_case naming conventions.
- Appropriate data type conversions.
- Removal of outliers using the Interquartile Range (IQR) method.
- Removal of abnormal values, e.g., coordinates (0,0).

### Feature Engineering

Engineered features include:
- Calculating delivery distance using coordinates and the `geopy` library.
- Generating day names and labeling weekdays vs. weekends.
- Calculating pickup period as the difference between the order time and the pickup time.
- Grouping order times into breakfast, lunch, dinner, and late-night categories.

### Model Preparation

Preparation included:
- One-hot encoding for categorical columns.
- Feature selection based on a correlation threshold of 0.1 with the target variable (`Time_taken(min)`).
- Ensuring no multicollinearity issues among the selected features.
- Splitting the dataset into an 80:20 ratio for training and testing, with and without stratified sampling.

### Model Algorithms

Eight models were built using the following algorithms (two models for each):
- Linear Regression
- Ridge Regression
- Lasso Regression
- Random Forest Regression

### Model Evaluation

The models were evaluated using Mean Absolute Error (MAE), Root Mean Square Error (RMSE), and R-Squared ($R^2$).

The Random Forest Regression model without stratification emerged as the best model, with:
- **MAE:** 3.813071 (approx. 4). If the model predicts a delivery time of 10 minutes, the actual time could range from 6 to 14 minutes.
- **RMSE:** Lowest among all models, indicating the best performance in minimizing prediction errors.
- **$R^2$:** 0.712220, meaning the model explains approximately 71.22% of the variance in the target variable.

## Shortcomings

This project is far from perfect, with several areas for improvement:
- The project primarily focused on building a machine learning model, with limited Exploratory Data Analysis (EDA).
- The data was provided in a CSV file format, while real-world scenarios may require pulling data directly into Jupyter Notebook or other tools.
- The business impact calculation currently only considers the cost of handling customer complaints via phone calls, but it should also account for the additional cost of vouchers given to customers as an apology for delivery delays.

## Conclusion

This project demonstrates the end-to-end workflow of a data scientist, from data preparation and feature engineering to model evaluation and communication of results. While the Random Forest model without stratification proved most effective, further improvements and real-world adaptations could enhance the model's performance and applicability.
