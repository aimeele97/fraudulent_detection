# Credit Card Fraud Detection Project

## Overview

This project focuses on the detection of fraudulent transactions in credit card data using Python. A synthetic dataset is generated to simulate various credit card transactions, including details such as transaction ID, customer ID, transaction date, amount, type, merchant category, location, and whether the transaction is fraudulent.
The goal is to identify patterns and relationships in the data and build a predictive model that can accurately classify transactions as fraudulent or non-fraudulent.

## Dataset Generation

The dataset is created with the following attributes:

- **Transaction ID**: Unique identifier for each transaction (e.g., TID000001).
- **Customer ID**: Unique identifier for each customer (e.g., CUST01).
- **Transaction Date**: Date and time of the transaction.
- **Transaction Amount**: The monetary amount of the transaction.
- **Transaction Type**: Type of transaction (e.g., purchase, withdrawal, refund).
- **Merchant Category**: Category of the merchant (e.g., groceries, electronics).
- **Location**: The city where the transaction occurred.
- **Fraudulent**: Binary indicator of whether the transaction is fraudulent (1) or not (0).

The dataset contains 1,000 records, with 5% classified as fraudulent transactions.

## Exploring the Dataset

After generating the dataset, it is explored through various methods, including:

- **Head**: Displaying the first few rows of the dataset.
- **Descriptive Statistics**: Summarizing the main characteristics of the dataset, including counts and unique values.
- **Missing Values**: Checking for any null values in the dataset.
- **Duplicated Records**: Ensuring there are no duplicate entries.

### Sample Output

```python
credit_card_data.head()
```

| Transaction ID | Customer ID | Transaction Date          | Transaction Amount | Transaction Type | Merchant Category | Location    | Fraudulent |
|----------------|-------------|---------------------------|--------------------|------------------|-------------------|-------------|------------|
| TID000000      | CUST82     | 2024-07-16 00:56:54.162904 | 375.17             | refund           | dining            | Chicago     | 0          |
| TID000001      | CUST15     | 2024-05-14 00:56:54.162904 | 950.76             | withdrawal       | entertainment      | Houston     | 0          |
| ...            | ...        | ...                       | ...                | ...              | ...               | ...         | ...        |

## Data Analysis

The project includes detailed analysis of the dataset to identify patterns and insights related to fraudulent transactions:

- **Grouping**: Data is grouped by fraudulent status, transaction type, merchant category, and location to summarize the total amounts and counts.
- **Visualizations**: Using Matplotlib to plot transaction counts and total amounts across different categories.

### Sample Visualization

<img width="370" alt="image" src="https://github.com/user-attachments/assets/ecb38387-dbd0-45f9-b474-4605455b3ee7">
<img width="367" alt="image" src="https://github.com/user-attachments/assets/9e638501-2813-42c3-bf4f-55acf888f1d9">

## Mapping Fraudulent Transactions

Utilizing Folium, a map is generated to visualize the locations of fraudulent transactions across different cities. This provides an intuitive representation of where fraud is occurring.

<img width="540" alt="image" src="https://github.com/user-attachments/assets/b447035b-5128-4b99-9c47-b3e931cae5fe">

## Database Integration

The dataset is saved to an SQLite database, allowing for SQL queries to be run on the transaction data:

```python
# Connect to the SQLite database
conn = sqlite3.connect('credit_card_data.db')
```
Write a query 
```python
query = '''
    SELECT 
        `Customer ID`, 
        `Fraudulent`, 
        COUNT(*) AS Fraud_Count, 
        SUM(`Transaction Amount`) AS Total_Transaction_Amount 
    FROM 
        CreditCardTransactions 
    GROUP BY 
        `Customer ID`, `Fraudulent`
    HAVING `Fraudulent` = 1
    ORDER BY `Fraudulent` desc, `Fraud_Count` desc, `Total_Transaction_Amount` desc, `Customer ID`;
'''
```
Then transform and visualize the output using matplotlib

<img width="540" alt="image" src="https://github.com/user-attachments/assets/850968fe-7dfa-43ef-8e63-aa2fc049c625">

## Machine Learning Models
For this project, three different models were trained to classify fraudulent transactions: Logistic Regression, Random Forest, and Gradient Boosting. The models were evaluated using accuracy, and all achieved a high accuracy of 95%.

| Model               | Accuracy |
|---------------------|----------|
| Logistic Regression | 95%      |
| Random Forest       | 95%      |
| Gradient Boosting   | 95%      |

## Installation

Ensure you have the required libraries installed. You can install them using pip:

```bash
pip install pandas numpy matplotlib folium
```

## Usage

Run the notebook to generate the dataset, perform exploratory data analysis, and visualize the results. Modify parameters as needed to explore different scenarios.

## Conclusion

This project demonstrates the steps involved in detecting fraudulent transactions using synthetic data, including data generation, exploration, analysis, visualization, and storage in a database.

Logistic Regression, Random Forest, and Gradient Boosting models were trained and achieved similar high accuracy of 95%.Feature importance analysis provided actionable insights, which can be used to improve future models and support business decision-making.

### Next Steps

1. Experiment with larger datasets or datasets from different sources to test the model’s robustness.
2. Explore ensemble methods or hyperparameter tuning to improve the performance.
3. Deploy the model and test it on real-time data to evaluate how it handles real-world fraud detection scenarios.

## License 

MIT license

Copyright (c) [2024] [Aimee Le]
