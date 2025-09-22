##  README for `archnewtask3.pdf` — Customer Segmentation

**Title**: Customer Segmentation using RFM Analysis and K-Means Clustering

###  Objective
To segment customers into distinct groups based on their purchasing behavior using **RFM (Recency, Frequency, Monetary)** metrics. This enables targeted marketing strategies and improved customer relationship management.

###  Dataset
- **Source**: UCI Machine Learning Repository — Online Retail Dataset
- **URL**: `https://archive.ics.uci.edu/ml/machine-learning-databases/00352/Online%20Retail.xlsx`
- **Initial Shape**: 541,909 rows × 8 columns
- **After Cleaning**: 4,338 unique customers

###  Data Preprocessing
1. Removed rows with missing `CustomerID`.
2. Filtered out negative/zero `Quantity` (cancellations/returns).
3. Calculated `TotalPrice = Quantity * UnitPrice`.
4. Computed RFM metrics:
   - **Recency**: Days since last purchase (relative to latest date + 1 day).
   - **Frequency**: Total number of invoices.
   - **Monetary**: Total spend (`TotalPrice` sum).
5. Removed customers with zero monetary value.
6. Standardized RFM features using `StandardScaler` for K-Means.

###  Modeling
- **Algorithm**: K-Means Clustering (`sklearn.cluster.KMeans`)
- **Optimal Clusters**: Determined via Elbow Method → Selected **k=4**
- **Cluster Interpretation**:
  - **Cluster 0 (“Fans”)**: Low recency, high frequency & spend — loyal core customers.
  - **Cluster 1 (“Lost Customers”)**: High recency, medium-low spend — at risk of churn.
  - **Cluster 2 (“Potential Loyalists”)**: Very low recency, extremely high frequency & spend — VIPs.
  - **Cluster 3 (“Active Spenders”)**: Very high recency, low-medium frequency — occasional big spenders.

###  Visualization & Output
- Scatter plot of Recency vs. Monetary, colored by cluster.
- Summary table showing mean RFM values and customer count per segment.
- Each customer assigned a human-readable segment label.

###  Tools Used
- Python, pandas, numpy
- matplotlib, seaborn
- scikit-learn: `StandardScaler`, `KMeans`
---

These READMEs concisely summarize the purpose, methodology, data, results, and tools for each task — perfect for documentation, GitHub repos, or project submissions.
