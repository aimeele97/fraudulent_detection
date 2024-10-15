# Credit Card Fraud Detection Project

## Overview

This project focuses on the detection of fraudulent transactions in credit card data using Python. A synthetic dataset is generated to simulate various credit card transactions, including details such as transaction ID, customer ID, transaction date, amount, type, merchant category, location, and whether the transaction is fraudulent.

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

```python
plot_fraud_data(fraud_type, 'Transaction Type', 'Count', 'Total_Amount', 'Transaction Count and Total Amount by Type')
```

## Mapping Fraudulent Transactions

Utilizing Folium, a map is generated to visualize the locations of fraudulent transactions across different cities. This provides an intuitive representation of where fraud is occurring.

<img width="540" alt="image" src="https://github.com/user-attachments/assets/b447035b-5128-4b99-9c47-b3e931cae5fe">

## Database Integration

The dataset is saved to an SQLite database, allowing for SQL queries to be run on the transaction data:

```python
# Connect to the SQLite database
conn = sqlite3.connect('credit_card_data.db')
```

## Installation

Ensure you have the required libraries installed. You can install them using pip:

```bash
pip install pandas numpy matplotlib folium
```

## Usage

Run the notebook to generate the dataset, perform exploratory data analysis, and visualize the results. Modify parameters as needed to explore different scenarios.

## Conclusion

This project demonstrates the steps involved in detecting fraudulent transactions using synthetic data, including data generation, exploration, analysis, visualization, and storage in a database.

## License 

MIT license

Copyright (c) [2024] [Aimee Le]
