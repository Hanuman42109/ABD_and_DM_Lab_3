# Lab 3: Clustering Analysis Using K-Means and K-Medoids Algorithms

## Purpose

This lab explores unsupervised clustering techniques applied to the **Wine Dataset** from `sklearn`. It compares two algorithms — **K-Means** and **K-Medoids** - using performance metrics (Silhouette Score, Adjusted Rand Index) and 2-D PCA visualisations to understand the strengths and trade-offs of each method.

---

## Key Results

| Metric                    | K-Means | K-Medoids |
|---------------------------|---------|-----------|
| Silhouette Score          | 0.2849  | 0.2676    |
| Adjusted Rand Index (ARI) | 0.8975  | 0.7411    |

**K-Means performed better on both metrics.** Its ARI of ~0.90 indicates near-perfect recovery of the three true wine classes, while K-Medoids reached ~0.74.

---

## Key Insights

1. **K-Means wins on well-behaved continuous data.** The Wine dataset features are all numeric, roughly continuous, and not heavily skewed - ideal conditions for K-Means, which optimises within-cluster variance using virtual centroids.

2. **K-Medoids is more robust to outliers.** Because medoids must be real observations, extreme values cannot pull cluster centres out of the data distribution. For datasets with outliers or a meaningful "representative sample" requirement, K-Medoids is preferable.

3. **Silhouette Scores are modest for both (~0.27–0.28).** This reflects genuine cluster overlap in the 13-dimensional feature space; the structure is real (ARI > 0.74 for both) but not perfectly separable.

4. **Algorithm selection depends on data characteristics:**
   - Large, Euclidean, low-noise datasets → K-Means (faster, more accurate)
   - Outlier-prone or non-Euclidean datasets → K-Medoids (robust, flexible distance metric)

---

## Challenges and Decisions

- **K-Medoids not in sklearn core** – `scikit-learn-extra` was unavailable in the lab environment, so K-Medoids was implemented from scratch using a PAM (Partitioning Around Medoids) approach with a precomputed distance matrix.
- **2-D visualisation via PCA** – PCA captures only 55.4 % of total variance, so some cluster overlap in the plots is expected; the true 13-D structure is better captured by the ARI metric.
- **Random seed fixed** (`random_state=42`) for reproducibility across both algorithms.

---

## How to Run

1.**Clone the repository**

```bash
   git clone https://github.com/Hanuman42109/ABD_and_DM_Lab_3
   cd ABD_and_DM_Lab_3
```

2.**Create and activate a virtual environment**

```bash
   python -m venv venv
   venv\Scripts\activate        # Windows
   source venv/bin/activate     # Mac/Linux
```

3.**Install dependencies**

```bash
   pip install pandas numpy matplotlib seaborn scikit-learn ipykernel
```

4.**Open in VS Code**

- Open the project folder in VS Code
- Press `Ctrl+Shift+P` → **Python: Select Interpreter** → choose `venv`
- Open `ABD_and_DM_Lab_3.ipynb`
- Click **Run All**
