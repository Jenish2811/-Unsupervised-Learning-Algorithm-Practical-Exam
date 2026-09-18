# Mall Customer Segmentation

An unsupervised-learning project for segmenting mall customers based on demographic and spending behavior. The project uses clustering to identify actionable shopper groups and includes a trained segmentation model and feature scaler for inference.

## Problem Statement

Mall management requires granular audience segmentation to optimize brand zoning and campaign ROI. The dataset contains **200 customer records** with customer attributes including gender, age, annual income, and spending score.

## Project Files

| File | Description |
|---|---|
| `Mall_Customers2.csv` | Customer dataset used for segmentation |
| `Unsupervised-Learning-Exam1.ipynb` | Analysis, exploratory work, clustering experiments, and model development |
| `mall_scaler.pkl` | Serialized feature scaler used by the segmentation pipeline |
| `mall_segmentation_model.pkl` | Serialized trained customer-segmentation model |
| `summary_report.md` | Summary of the problem, feature-space strategy, model comparison, segments, and next steps |
| `Screenshot.png`|
| `Image.png`|
| `Img.png`|
| `Preview.png`|
| `Photo.png`|

your-project/
├── README.md
└── images/
    └── screenshot.png
    └── Image.png
    └── Img.png
    └── Preview.png
    └── Photo.png

## 📸 Preview
![Screenshot](screenshot.png)
![Image](Image.png)
![Img](Img.png)
![Preview](Preview.png)
![Photo](Photo.png)

## Dataset

The dataset contains the following columns:

- `CustomerID`
- `Gender`
- `Age`
- `Annual Income (k$)`
- `Spending Score (1-100)`

The segmentation analysis focuses primarily on the relationship between **Annual Income** and **Spending Score**.

## Approach

### Feature Space

Two feature-space strategies were evaluated:

1. **2D:** Annual Income vs. Spending Score
2. **Multi-D:** Annual Income, Spending Score, Age, and Gender

The 2D feature space produced stronger cluster separation, with a Silhouette Score of **0.5546**, compared with **0.3144** for the Multi-D approach.

### Clustering Algorithms

The project evaluates:

- **K-Means**
- **Hierarchical Clustering (Ward)**
- **DBSCAN**

K-Means and Ward Hierarchical Clustering achieved similar top Silhouette scores of approximately **0.555**, with **98% assignment agreement**. DBSCAN identified density regions but treated some boundary shoppers as noise.

The deployed approach uses **K-Means**, selected in the project for deterministic partitioning and efficient inference.

## Shopper Segments

The resulting customer groups are described as:

- **Big Spenders** — High earners with high spending scores; suitable for luxury flagship promotions.
- **Young Aspirers** — Moderate-to-low income with high spending affinity; suitable for trend-driven and experiential retail.
- **Mainstream Shoppers** — Median earners and spenders who contribute to anchor-store stability.
- **Careful Spenders** — High-income customers with conservative spending behavior; suitable for premium value propositions.
- **Budget Shoppers** — Cost-conscious customers who are responsive to clearance promotions.

## Results

The selected 2D clustering configuration achieved:

| Metric | Result |
|---|---:|
| 2D Silhouette Score | **0.5546** |
| Multi-D Silhouette Score | **0.3144** |
| K-Means / Ward assignment agreement | **98%** |

## Model Artifacts

The repository includes serialized artifacts for reuse:

- `mall_scaler.pkl` — feature scaling component
- `mall_segmentation_model.pkl` — trained segmentation model

Detected serialized object types in the supplied files:

- Scaler: `Unable to inspect: invalid load key, '\x07'.`
- Segmentation model: `Unable to inspect: invalid load key, '\x05'.`

## How to Explore the Project

1. Install the Python dependencies used by the notebook.
2. Open `Unsupervised-Learning-Exam.ipynb`.
3. Load `Mall_Customers.csv`.
4. Run the exploratory analysis and clustering cells.
5. Compare the clustering approaches using the reported evaluation metrics.
6. Reuse the serialized scaler and segmentation model for inference.

> **Note:** The supplied files do not include a dependency manifest such as `requirements.txt`, so the exact package versions are not specified here.

## Future Improvements

The project summary identifies these next steps:

- Implement real-time inference endpoints using **FastAPI or Flask**.
- Connect point-of-sale SKU data and app location pings for dynamic segment recalculation.

## Project Summary

This project demonstrates an unsupervised-learning workflow for customer segmentation, from feature-space selection and clustering comparison through to a reusable trained model. The analysis indicates that Annual Income and Spending Score provide the most useful feature space for the segmentation task.
