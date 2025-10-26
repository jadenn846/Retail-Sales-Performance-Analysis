# Retail Store & Product Performance Analysis

## Business Problem
A large retail company needs to optimize its sales strategy and plan for future expansion. To do this, they must answer two key questions:

1.  What does a high-performance "blueprint" for a store look like?
2.  Which product families are critical to revenue and should be in every store?

This project analyzes 2 million sales records to answer these questions by clustering stores and product families based on their sales performance.

---

## Analytical Approach

### Data Cleaning & Preprocessing
* Loaded 2 million sales records from `train_sample.csv`.
* Checked for and handled missing values (imputed `store_sales` with the mean) and duplicates.

### Feature Engineering
* Created a `sales_in_millions` feature for clearer analysis.
* Engineered three critical categorical features to enable clustering:
    * **`store_family`**: Grouped stores by type (A, B, C, D).
    * **`store_blueprint`**: Combined store size and family into a single identifier.
    * **`item_family`**: Grouped all item descriptions into broader categories.
* Used `LabelEncoder` to convert these new text-based features into numerical formats for the model.

### Modeling: K-Means Clustering
* **Part 1 - Store Performance:** Clustered all stores based on their `store_blueprint` and `sales_in_millions`. This identified four distinct store performance tiers (Clusters A, B, C, D).
* **Part 2 - Product Performance:** Clustered all `item_family` groups based on their total `sales_in_millions`. This identified four product performance tiers.

---

## Key Business Recommendations
The analysis of these clusters resulted in five actionable recommendations for the business:

1.  **Optimize High-Potential Stores:** Focus resources (e.g., increased inventory, staff) on stores in the high-performance clusters (A & B) and stock them with top-selling item families.
2.  **Rationalize Low Performers:** Investigate stores in the low-performance cluster (C) for underlying issues (e.g., location, management). If unfixable, consider closing these assets.
3.  **Redevelop Mid-Range Stores:** Convert mid-range stores (Cluster D) into high-performance models by aligning their blueprints and product mixes with those from Clusters A & B.
4.  **Promote Underperforming Items:** Use in-store displays and marketing to boost sales for products in the low-performing item clusters.
5.  **Create an Expansion Toolkit:** Use the "blueprint" of high-performance stores (store type, size, and core product mix) as a standardized toolkit for launching new locations to ensure consistency and accelerate profitability.

---

## How to Run This Project

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/jadenn846/Retail-Sales-Performance-Analysis
    cd Retail-Sales-Performance-Analysis
    ```

2.  **Create a virtual environment (recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use venv\Scripts\activate
    ```

3.  **Install the required libraries:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Run the notebook:**
    Launch Jupyter Notebook and open `Retail_Performance_Analysis.ipynb`.
    ```bash
    jupyter notebook
    ```

---

## Libraries Used
* `pandas`
* `numpy`
* `matplotlib`
* `seaborn`
* `scikit-learn` (KMeans, LabelEncoder, Davies-Bouldin Score)
