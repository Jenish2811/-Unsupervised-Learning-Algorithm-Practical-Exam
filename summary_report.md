# Customer Segmentation Summary Report

### 1. Problem Statement & Dataset
Mall management requires granular audience segmentation to optimize brand zoning and campaign ROI. The dataset contains 200 customer records detailing Gender, Age, Annual Income, and Spending Score.

### 2. Feature Space Strategy: 2D vs Multi-D
Clustering on the 2D feature subspace (`AnnualIncome` vs `SpendingScore`) produced well-defined density boundaries (Silhouette: 0.5546). Including `Age` and `Gender` (Multi-D) diluted cluster separation (Silhouette: 0.3144) because spending behavior in this dataset is dominated by the orthogonal relationship between income and retail spend.

### 3. Algorithmic Ranking & Metrics
K-Means and Hierarchical Clustering (Ward) tied with top Silhouette scores (~0.555) and 98% assignment agreement. DBSCAN found the density regions but classified boundary shoppers as noise points. K-Means is selected for deployment due to deterministic partitioning, $O(n)$ inference efficiency, and zero centroid drift across random initializations.

### 4. Shopper Segments
- **Big Spenders:** High earners with high spending scores; prioritize luxury flagship promotions.
- **Young Aspirers:** Moderate-to-low income with peak spending affinity; targeted by trend-driven, experiential retail.
- **Mainstream Shoppers:** Median earners and spenders; drive anchor store stability.
- **Careful Spenders:** High income with conservative spend; require premium value propositions.
- **Budget Shoppers:** Cost-conscious visitors driven by clearance promotions.

### 5. Next Steps
- Implement real-time inference endpoints via FastAPI or Flask.
- Connect point-of-sale SKU data and app location pings for dynamic segment recalculation.