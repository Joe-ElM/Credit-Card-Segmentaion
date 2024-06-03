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

KMeans Clustering Model with 5 Clusters
Overview
The project utilizes the KMeans clustering algorithm to categorize credit card customers into distinct groups based on their spending behavior and payment patterns. This unsupervised learning technique is essential for identifying customer segments that can be targeted with tailored credit card conditions.

Methodology
Data Preparation
Standardization: The dataset is standardized to ensure that each feature contributes equally to the clustering process. This is done using the StandardScaler from scikit-learn.
KMeans Clustering
Number of Clusters: After evaluating different cluster counts using the silhouette method, a model with 5 clusters was selected.
Initialization: The KMeans algorithm is initialized with n_clusters=5 and n_init=50 to ensure robust clustering results.
Model Fitting: The model is trained on the standardized dataset to identify clusters of customers with similar behaviors.
Evaluation
Silhouette Scores: The silhouette scores for different numbers of clusters were examined. The structure of the silhouette values indicated that 5 clusters provided a good balance between cluster cohesion and separation.
Cluster Visualization: Although PCA was not used in the KMeans algorithm itself, it was applied for visualization purposes to project the high-dimensional data into a 2D space. The clusters were visualized using a scatter plot, with each cluster represented by a distinct color from a custom palette.
Results
Cluster Names: Each cluster was given a descriptive name based on the observed customer behaviors:

Cluster 0: High Spenders
Cluster 1: Premium Customers
Cluster 2: Moderate Spenders
Cluster 3: Cash Advance Dependent
Cluster 4: Occasional Spenders
Cluster Analysis: The characteristics of each cluster were analyzed to understand the spending and payment behaviors of customers. For instance, Premium Customers (Cluster 1) were identified as those who make a lot of purchases and pay their bills on time, while Cash Advance Dependent customers (Cluster 3) frequently rely on cash advances.

![Description](/Images/elbow.png)

### Choosing the Optimal Number of Clusters (k=5)

The decision to use 5 clusters for the KMeans model was based on an in-depth analysis of the silhouette scores and the distribution of data points among clusters.

Analysis of Silhouette Scores
Silhouette scores provide a metric for evaluating the quality of clusters by measuring how similar each point is to its own cluster compared to other clusters. Through this analysis, it was observed that:

Inter-cluster Proximity: There were two clusters with several values that were notably close to points in other clusters. This indicated that increasing the number of clusters might not significantly improve the separation between these clusters.
Large Positive Cluster: A distinct, large cluster of purely positive values was identified. This cluster remained consistent across different values of k, suggesting a natural grouping of these data points.
Consistency in Silhouette Values: The silhouette values showed minimal structural change when varying the number of clusters. This consistency implies that adding more clusters would not significantly enhance the overall cluster quality.
Given these observations, it was concluded that increasing the number of clusters beyond 5 would not yield better-defined groups. Therefore, the model was finalized with 5 clusters, which provided a balanced and interpretable segmentation of the credit card customers. This choice ensures that the clustering solution is both meaningful and practical for developing targeted credit card conditions.

![Description](/Images/silhoutte_scores_and_PCA_k_5.png)

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

![Description](/Images/Clusters.png)

## Project highlights

- shared files for functions and global settings allowing for streamlined editing of global parameters (i.e. `random_state`), as well as uniform / consistent visualization's style throught Jupyter Notebooks
- main pipeline with external model-definitions .py file allowing for streamlined model switching and comparison
- advanced confussion matrix with meaningful color-coding with custom color maps additionally accompanying for color-blindness
- bulk-generation of data visualizations streamlining the process of EDA

### Data Set: HR Analytics Dataset

Obtained from: [kaggle.com](https://www.kaggle.com/datasets/arjunbhasin2013/ccdata)\
License: [CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/)
