# Mall Customer Segmentation Analysis

## 1. Project Overview

This is an unsupervised machine learning project that uses the K-Means clustering algorithm to analyze mall customer data. The goal is to move beyond simple demographics and identify distinct, actionable "customer personas" based on their spending habits, age, and income.

This type of customer segmentation is a core business strategy, allowing a company to create targeted marketing campaigns, optimize store layouts, and improve customer engagement.

## 2. Dataset

The data is the "Mall Customer Segmentation Data" from Kaggle:
[https://www.kaggle.com/datasets/vjchoudhary7/customer-analytics](https://www.kaggle.com/datasets/vjchoudhary7/customer-analytics)

The analysis focuses on three key features:
* `Age`
* `Annual Income (k$)`
* `Spending Score (1-100)`

## 3. Methodology

1.  **Exploratory Data Analysis (EDA):** I first loaded and inspected the data. A pairplot was used to visualize the relationships between all features, which showed potential groupings.
2.  **Data Preprocessing:** K-Means is a distance-based algorithm, so it's critical that all features are on the same scale. I applied `StandardScaler` to the three features (`Age`, `Income`, `Spending Score`) to normalize them.
3.  **Finding the Optimal 'k' (Number of Clusters):**
    * **Elbow Method (Inertia):** I plotted the Within-Cluster Sum of Squares (WCSS) for k=1 to 10. This showed a soft "elbow" around 5 or 6.
    * **Silhouette Score:** To get a more definitive answer, I plotted the average Silhouette Score for k=2 to 10. This metric is more robust as it measures both cluster cohesion (tightness) and separation (distance).
    * **Conclusion:** The Silhouette Score peaked clearly at **k=6**, indicating that 6 is the optimal number of distinct clusters for this 3D data.
4.  **Final Modeling & Analysis:**
    * I trained the final K-Means model on the scaled data with `n_clusters=6`.
    * I then performed an `inverse_transform()` on the resulting cluster centers to get their true, human-readable values.
    * Finally, I analyzed these 6 centers to create the data-driven "customer personas" seen below.

## 4. Key Findings: The 6 Customer Personas

The analysis successfully identified 6 distinct customer segments based on their `Age`, `Income`, and `Spending Score`.

| Cluster | Persona (My Analysis) | Characteristics |
| :--- | :--- | :--- |
| **0** | **Careful & Mature** | Average income, average spending, mature age. |
| **1** | **Careful & Young** | Average income, average spending, young age. |
| **2** | **Economic (Target 2)** | High income, but low spending. A key group for marketing. |
| **3** | **VIP (Target 1)** | **High income and high spending.** The mall's most valuable customers. |
| **4** | **Spendful** | Low income, but high spending. Likely students or young professionals. |
| **5** | **Sensible** | Low income and low spending. Cautious shoppers. |

## 5. How to Run

1.  Clone the repository.
2.  Install the required libraries:
    `pip install -r requirements.txt`
3.  Run the `Mall_Customer_Segmentation_Data.ipynb` Jupyter Notebook.
