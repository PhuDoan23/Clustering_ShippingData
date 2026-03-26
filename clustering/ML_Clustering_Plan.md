# Machine Learning Final Project: Comparative Clustering Analysis

## 🎯 Project Objective
To apply, optimize, and compare multiple clustering algorithms on a dataset (e.g., our modernized `data/Ship_Performance_Dataset_Modernized.csv`) to identify inherent groupings, and evaluate their performance using internal validation metrics.

---

## 📅 Project Roadmap

### Phase 1: Data Understanding & Preprocessing
*Clustering is highly sensitive to the scale and shape of the data.*
- [ ] **Exploratory Data Analysis (EDA):** Analyze distributions, check for skewness, and visualize correlations between features.
- [ ] **Handling Missing Data:** Impute or remove missing values.
- [ ] **Encoding:** Convert categorical variables (like `Fuel_Type`, `Route_Type`) using One-Hot Encoding via `model.matrix()` or `caret::dummyVars`.
- [ ] **Feature Scaling (Crucial):** Apply the base `scale()` function so distance-based algorithms (like K-Means and DBSCAN) work correctly.

### Phase 2: Dimensionality Reduction (For Visualization)
*High-dimensional data is hard to visualize. We reduce it to 2D or 3D.*
- [ ] **PCA (Principal Component Analysis):** Find the most important linear components explaining the variance.
- [ ] **t-SNE / UMAP:** Use non-linear reduction specifically to visualize cluster separation in a 2D plot.

### Phase 3: Implementing Clustering Algorithms
*Implement algorithms from different mathematical families to compare their approaches.*
- [ ] **1. K-Means (Centroid-based):** 
  - *Setup:* Use the Elbow Method and Silhouette Analysis to find the optimal number of clusters ($k$).
- [ ] **2. Hierarchical Clustering (Connectivity-based):** 
  - *Agglomerative (AGNES):* Bottom-up approach using `stats::hclust()` or `cluster::agnes()`.
  - *Divisive (DIANA):* Top-down approach using `cluster::diana()`.
  - *Setup:* Experiment with different linkage methods (Ward's method, Complete, Average, Single).
  - *Visualization:* Plot and cut a Dendrogram using `factoextra::fviz_dend()` or base R `plot()` to decide the number of clusters and cut-off distance. 
- [ ] **3. DBSCAN (Density-based):** 
  - *Setup:* Find the optimal `eps` and `min_samples` using a k-distance graph. Excellent for finding irregularly shaped clusters and anomalies (noise).
- [ ] **4. Gaussian Mixture Models / GMM (Distribution-based):**
  - *Setup:* Use AIC/BIC scores to find the optimal number of components. Good for clusters that overlap or have elliptical shapes.

### Phase 4: Evaluation & Comparison
*Since there are usually no "true labels" in clustering, we compare algorithms using internal mathematical metrics.*
- [ ] **Silhouette Score:** Measures how similar an object is to its own cluster compared to other clusters (Values from -1 to 1; higher is better).
- [ ] **Davies-Bouldin Index:** Measures average 'similarity' between clusters (Lower score is better).
- [ ] **Calinski-Harabasz Index (Variance Ratio Criterion):** Ratio of between-cluster dispersion to within-cluster dispersion (Higher score is better).
- [ ] **Comparison Table:** Create an R `data.frame` or `tibble` comparing the 4 algorithms across these 3 metrics and execution time.

### Phase 4.5: Data Quality Optimization (To improve low Silhouette scores)
*If your Silhouette score is low (e.g., < 0.15), the data is likely a continuous spectrum rather than distinct blobs. Apply these techniques:*
- [ ] **Domain Feature Engineering**: Create ratio-based features (like `Profit_Margin`, `Cost_per_nm`, or `Power_per_Cargo_ton`). These often cluster much better than absolute values like pure `Distance` or `Operational_Cost`.
- [ ] **Outlier Winsorization**: Cap extreme values at the 1st and 99th percentiles before scaling. K-Means centroids are easily dragged by outliers, destroying cluster cohesion.
- [ ] **Feature Subsetting**: Instead of clustering on all PCA components, try clustering on specific domain subsets (e.g., *only* efficiency metrics, or *only* financial metrics).
- [ ] **Adjust K**: Check if K=2 or K=3 yields a mathematically stronger silhouette, even if K=4 was suggested by the Elbow method.

### Phase 5: Cluster Interpretation (Profiling)
*What do the clusters actually mean in the real world?*
- [ ] Calculate the mean and median of original features for each cluster.
- [ ] Create radar charts or boxplots showing the defining characteristics of Cluster 0 vs Cluster 1 vs Cluster 2.
- [ ] *Example (if using Shipping Data):* "Cluster 1 represents small, highly efficient coastal vessels, while Cluster 2 represents massive, high-emission oceanic freighters."

### Phase 6: Final Report & Presentation
- [ ] Document the methodology.
- [ ] Export all comparative visuals (t-SNE plots, dendrograms).
- [ ] Write the conclusion on which algorithm performed best for this specific dataset and why.

---

## 🛠️ Tech Stack Recommendation
* **R Packages:** 
  - **Data Wrangling:** `dplyr`, `tidyr`, `tibble`
  - **Clustering:** `stats` (for `kmeans`, `hclust`), `dbscan`, `mclust` (for GMM)
  - **Evaluation & Visualization:** `factoextra` (great for elbows, silhouettes, biplots), `cluster` (for silhouette scores), `fpc` (for clustering evaluation metrics).
  - **Plotting:** `ggplot2`
  - **Dimensionality Reduction:** `stats` (for `prcomp`), `Rtsne`, `umap`
