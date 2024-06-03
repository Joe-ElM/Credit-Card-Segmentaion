# Credit Card Segmentaion utilizing Unsupervised Learning

Focusing on clustering. the process entails categorizing data points into distinct groups. Unlike supervised learning, where the groups are predetermined, clustering operates on an **unsupervised learning**. The objective of this project is to segment credit card customers into various groups and derive recommendations tailored to each group.

- Usage of the k-Means algorithm to split data into clusters
- Utilizing the silhouette method to assess the effectiveness of the clusters

## Data Set

[HR Analytics Dataset](https://www.kaggle.com/datasets/arjunbhasin2013/ccdata)\
**Structured:** Yes\
**Format:** single .csv file\
**Size:** 8949 observations \
**Number of Features:** 11\
_data dictionary_

| Column number | Column name        | Type                | Description                                     |
| ------------- | ------------------ | ------------------- | ----------------------------------------------- |
| 0             | `CUST_ID`          | categorical (`int`) | identification number of the credit card holder |
| 1             | `BALANCE`          | numeric (`float`)   | balance on the account                          |
| 2             | `PURCHASES`        | numeric (`float`)   | number of purchases from the account            |
| 3             | `PURCHASES_TRX`    | numeric (`int`)     | number of purchase transactions made            |
| 4             | `ONEOFF_PURCHASES` | numeric (`float`)   | Maximum purchase amount with one purchase       |
| 5             | `CASH_ADVANCE`     | numeric (`float`)   | prepayment by user                              |
| 6             | `CASH_ADVANCE_TRX` | numeric (`int`)     | number of transactions with prepayment          |
| 7             | `CREDIT_LIMIT`     | numeric (`float`)   | credit limit of the card                        |
| 8             | `PAYMENTS`         | numeric (`float`)   | Payments made by user                           |
| 9             | `PRC_FULL_PAYMENT` | numeric (`float`)   | percentage of fully paid-up payments            |
| 10            | `TENURE`           | numeric (`int`)     | Duration of possession of the credit card       |

## Scenario:

A bank wants to refine the credit card terms and conditions for its customers. The bank aims to gain a deeper understanding of its credit card clients to offer tailored conditions. While data on its credit card holders is available, the specific customer segments remain undiscovered. The task at hand is to explore whether distinct customer groups exist within the credit card base and, if so, recommend which groups should receive improved terms. By identifying these segments, targeted terms and conditions can be proposed that cater to the diverse needs of "good" credit card customers, enhancing their satisfaction and the bank's competitive edge

## Process

### 1. Project's Conventions

Conventions are discussed and agreed on: coding convention (programming style), variable names, random parameters (`random_state` for data splits and models), internal JupyterLab notebooks' structure, Git's repository folder structure.\
Early establishment of project's conventions is crucial, since:

- allows for unbiased models performance's metrics comparison
- increases code / JupyterLab's notebooks readability
- in the later project's phases: prevents time overhead required for cleanups (code, repository)

### 3. Models

## Model Interpretation

### Summary of Cluster Names:

Cluster 0: " High Spenders" -->
Description: High balances with frequent and substantial purchases. Significant one-off purchases, high credit limits, and high payment amounts. Moderate likelihood of full payments.

Cluster 1: "Premium Customers" -->
Description: Extremely high balances and spending. Make numerous high-value purchases, both regular and one-off. Highest credit limits and payments, with a high percentage of fully paid balances.

Cluster 2: "Moderate Spenders" -->
Description: Moderate balances and spending. Regular purchase activities with occasional cash advances. Moderate credit limits and a balanced approach to payments and full payments.

Cluster 3: "Cash Advance Dependent" -->
Description: High balances with significant reliance on cash advances. Moderate one-off purchases and high credit limits, but low percentage of full payments.

Cluster 4: "Occasional Spenders" -->
Description: Low activity across the board. Low balances, purchases, and credit limits. They make some cash advances and have a high tendency to fully pay off their balances.

### Retention Strategies

Should address the observations listed in the Feature Importance point, prioritizing from top to bottom.\
Obviously we cannot have a direct influence on some of the employee's attributes, like for instance: **`marital status`**, **`years they are professionally active`**.

Couple of suggestions:

- **`Overtime`**: lower whenever possible, if not: be transparent regarding the reasons of overtime, delegate some of the ownership to the employees. Potentially the problem could also be planning-related and have its source in the Production Dept. It would be worth to assess the situation further and potentially train the Production Dept. in order to increase their planning precission.
- **`Marital Status`**: it's difficult to be addressed because it's not work-related
- **`Job Involvement`** and **`Level of Job Satisfaction`**: keywords here would be: motivate and delegate ownership (appointing chapions of specific production cycles or features)
- **`Business Travel`**: investigate and limit whenever possible, but inspect further if it's not correlated with employee's **`marital status`**
- **`Role within the organization`**:
<p align="center">
<img src="/Images/attrition_JobRole.png" />
</p>

As per above chart we can observe that we have higher than average `Attrition` in the roles: **Human Resources**, **Laboratory Technician**, **Sale Representative**. We would recommend further assessment of those departments and coming up with specific retention strategies per roles / dept.

## Project highlights

- shared files for functions and global settings allowing for streamlined editing of global parameters (i.e. `random_state`), as well as uniform / consistent visualization's style throught Jupyter Notebooks
- main pipeline with external model-definitions .py file allowing for streamlined model switching and comparison
- advanced confussion matrix with meaningful color-coding with custom color maps additionally accompanying for color-blindness
- bulk-generation of data visualizations streamlining the process of EDA

## Repository description

- how to install
- files description

## Disclaimer

This project was done in the period of 2 weeks as a follow-up to the [StackFuel GmbH](https://stackfuel.com/en/) courses: Data Analytics Certification and Data Science Certification.

### Data Set: HR Analytics Dataset

Obtained from: [kaggle.com](https://www.kaggle.com/datasets/arjunbhasin2013/ccdata)\
License: [CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/)
