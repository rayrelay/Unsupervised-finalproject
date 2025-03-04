# Customer Personality Analysis Project Report

## 1. Problem and Data Overview

In today's highly competitive market, understanding customer consumption behavior is crucial. The goal of this project is to analyze customer spending patterns through clustering analysis, enabling businesses to formulate more targeted marketing strategies. For this purpose, we use the "Customer Personality Analysis" dataset from Kaggle.

The dataset contains 2,240 records and 29 features, covering customers' basic information (such as age, education level, marital status, and income) as well as their consumption behavior (such as purchase frequency, total spending, and recent purchase time).

## 2. Exploratory Data Analysis (EDA)

### Data Inspection and Visualization
1. **Age Distribution**: Customer ages are mainly concentrated between 30-70 years old.
2. **Education Distribution**: Primarily consists of "Graduation," "Master's," and "PhD" categories.
3. **Marital Status Distribution**: Mainly includes "Married," "Single," and "Together."
4. **Income Distribution**: The data contains outliers that need to be cleaned.

### Data Cleaning
- Handling missing values by filling in appropriate data.
- Removing outliers in income and age to ensure reliable analysis results.
- Calculating the correlation of each feature with the target variable, ultimately selecting the 11 most relevant features for model training:
  - `Education`, `Marital_Status`, `Income`, `Kids`, `CustomerDays`, `Recency`, `TotalAmount`, `TotalNumPurchases`, `TotalAcceptedCmp`, `Complain`, `Response`

## 3. Model Architecture

This project uses three clustering methods for customer segmentation:

1. **K-Means Clustering**
   - Suitable for large-scale datasets with efficient computation.
   - Requires pre-specifying the number of clusters.

2. **DBSCAN Clustering**
   - Can identify noise points and automatically determine the number of clusters.
   - Works well for unevenly distributed data but performs poorly on high-dimensional data.

3. **Optimized K-Means Clustering**
   - Used PCA for dimensionality reduction, selecting "TotalAmount," "Income," and "TotalNumPurchases" as key features.
   - Tuned hyperparameters to improve clustering performance.

### Hyperparameter Tuning
- **K-Means**: Adjusting the `k` value to optimize the silhouette coefficient.
- **DBSCAN**: Adjusting `eps` and `min_samples` to enhance clustering results.
- **PCA**: Selecting the most representative features to improve computational efficiency.

## 4. Results and Analysis

| Model | Silhouette Coefficient |
|------|--------------------|
| K-Means | 0.310 |
| DBSCAN | 0.361 |
| Optimized K-Means | 0.445 |

The optimized K-Means achieved the best clustering performance, primarily because PCA improved the separation of clusters and an appropriate `k` value optimized cluster division.

### Identified Customer Segments:
1. **Moderate Income, Moderate Spending**
   - Customers in this segment have balanced income and spending behavior.
   - This is the largest group, representing typical spending patterns.

2. **Low Income, Low Spending**
   - These customers have lower income and spend less.
   - Likely to be more financially conservative due to limited financial resources.

3. **High Income, Low Spending**
   - These customers have high income but low spending.
   - They may prioritize saving over spending or adopt a conservative approach to expenses.

## 5. Conclusion

### Key Takeaways
- EDA helped uncover major customer spending patterns.
- Comparison of different clustering methods showed that the optimized K-Means performed best in this project.
- PCA improved computational efficiency and clustering quality.

### Future Improvements
- Explore more advanced clustering algorithms such as Gaussian Mixture Model (GMM) or hierarchical clustering.
- Enhance feature engineering to discover more variables influencing consumption behavior.
- Combine with supervised learning methods to further refine customer profiling.

The findings of this project provide valuable insights for marketing strategies, helping businesses better target their customers.

