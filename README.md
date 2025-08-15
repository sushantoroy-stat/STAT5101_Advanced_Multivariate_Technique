## 📑 Table of Contents
- [Introduction](#introduction)
- [Tools Used Here](#tools-used-here)
- [L1 Principal Component Analysis](#l1-principal-component-analysis)
- [L2 Canonical Correlation Analysis (CCA)](#l2-canonical-correlation-analysis-cca)
- [L3 Covariance Matrix](#l3-covariance-matrix)
- [L4 Factor Analysis](#l4-factor-analysis)
- [L5 Clustering with Iris Data](#l5-clustering-with-iris-data)
- [L7 DBSCAN Clustering](#l7-dbscan-clustering)
- [L8 Multidimensional Scaling (MDS)](#l8-multidimensional-scaling-mds)
- [L9 Correspondence Analysis (CA)](#l9-correspondence-analysis-ca)

---
- ## Introduction
This repository showcases my academic projects focused on statistical analysis and data science. It includes in-depth implementations of techniques such as **Factor Analysis, Principal Component Analysis (PCA), Clustering algorithms (including DBSCAN), Multidimensional Scaling (MDS)** and other advanced analytical methods. All projects are developed and demonstrated using **Jupyter Notebook (Python)** with an emphasis on both theoretical understanding and practical application through real-world or sample academic datasets.

- ## Tools Used Here
- **Jupyter Notebook** – Interactive environment for writing and running Python code.
- **NumPy** – Numerical computing and array operations.
- **pandas** – Data manipulation and analysis.
- **scikit-learn** – Machine learning and statistical modeling, including:
- `PCA` for Principal Component Analysis
- `FactorAnalysis` for Factor Analysis
- `KMeans` for K-Means Clustering
- `DBSCAN` for Density-Based Spatial Clustering
- `matplotlib` – Data visualization.
- `seaborn` – Statistical data visualization with enhanced aesthetics.



# 📊 Lecture 1: Project Interpretation – Principal Component Analysis (PCA)
- ## L1 Principal Component Analysis
Principal Component Analysis (PCA) is a statistical technique used for dimensionality reduction — that means it reduces the number of variables (features) in a dataset while keeping as much important information (variance) as possible.

⚙ How PCA Works (Steps)
1. Standardize the data (so all features are on the same scale).
2. Compute the covariance matrix of the features.
3. Find the eigenvalues and eigenvectors of the covariance matrix.
4. Sort eigenvalues in descending order — higher eigenvalue → more variance explained.
5. Select top k eigenvectors to form new feature space (k < original number of features).
6. Transform original data into this reduced feature space.
---

This project demonstrates the application of **Principal Component Analysis (PCA)** for dimensionality reduction and classification using a small dataset containing **Height, Weight, Age, and Gender**.  


## Data Overview
- Dataset: **10 records** with no missing values.  
- No outliers detected in **Height**, **Weight**, or **Age**, confirmed using both a **boxplot** and the **IQR method**.  


## Data Preprocessing
- Features were **standardized** to ensure equal scaling before applying PCA.  
- PCA reduced **3 original features** to **2 principal components**, retaining most of the variance.  

---

## Model Building & Evaluation
- **Logistic Regression** was trained on the PCA-transformed dataset.  
- Achieved **100% accuracy** on the test set:
  - ✅ 2 Female instances (True Positives)  
  - ✅ 1 Male instance (True Negative)  
- **Confusion Matrix:** No false positives or false negatives → perfect **precision**, **recall**, and **accuracy**.  
> ⚠️ Note: High accuracy is due to the small dataset size and may not generalize to larger datasets.  

---

## Visualization Insights
- **Before PCA:** Original standardized features showed strong correlations → redundancy in information.  
- **After PCA:** Data rotated into uncorrelated principal components → simplified structure while retaining essential patterns.  

---

## Key Takeaways
- PCA successfully reduced redundancy and captured key variance patterns.  
- Standardization was crucial to avoid bias toward large-scale variables.  
- Logistic Regression performed flawlessly on the reduced dataset, but validation on larger data is recommended.  

---

# 📊 Lecture 2:  Canonical Correlation Analysis (CCA) – Psychological & Academic Variables
- ## L2 Canonical Correlation Analysis (CCA)


This project applies **Canonical Correlation Analysis (CCA)** to explore the relationships between two sets of variables — **psychological factors** and **academic performance indicators** — for the same group of subjects.

## Dataset Overview
- **Source file:** `mmreg.dta`  
- **Observations:** 600  
- **Variables:**
  - *Psychological*: `locus_of_control`, `self_concept`, `motivation`  
  - *Academic*: `read`, `write`, `math`, `science`  
  - Additional: `id`, `female`  

The dataset had **no missing values**. Descriptive statistics were calculated to understand the variable distributions.

## Data Preprocessing
1. **Outlier Detection**  
   - Method: **Interquartile Range (IQR)**  
   - Outliers found in `locus_of_control` and `self_concept`.
2. **Outlier Removal**  
   - Removed **14 records**, resulting in **586 cleaned observations**.
3. **Exploratory Analysis**  
   - Used **boxplots** and **correlation heatmaps** to visualize distributions and relationships.

## Canonical Correlation Analysis
- **Groups Defined:**
  - **Psychological Variables (X):** `locus_of_control`, `self_concept`, `motivation`
  - **Academic Variables (Y):** `read`, `write`, `math`, `science`
- **Method:** `sklearn.cross_decomposition.CCA` with 1 component.
- **Results:**
  - **Canonical Correlation:** `0.4588` → *moderate positive relationship*
  - **Variable Loadings:**
    - **Psychological:**
      - Locus of control: **0.8775** (strongest positive)
      - Motivation: **0.4378** (moderate positive)
      - Self-concept: **–0.1957** (slight negative)
    - **Academic:**
      - Writing: **0.7631** (strongest positive)
      - Reading: **0.5929** (positive)
      - Math: **0.2486** (weak positive)
      - Science: **–0.0656** (negligible negative)

## Interpretation
Higher **locus of control** and **motivation** are moderately associated with better performance in **writing** and **reading**, while **self-concept** and **science scores** have minimal influence in the canonical relationship.




# 📊 Lecture 3: Project Interpretation – Covariance Matrix of the Iris Dataset  
## L3 Covariance Matrix

This project demonstrates how to compute and visualize the **covariance matrix** for the numeric features of the **Iris dataset**, providing insights into the relationships between measurements of sepal and petal dimensions.  

---

## Data Overview
- Dataset: **150 rows × 5 columns** (4 numeric features and 1 categorical species label).  
- Numeric features: **Sepal Length**, **Sepal Width**, **Petal Length**, **Petal Width**.  

---

## Covariance Matrix Analysis

### 🔹 Diagonal Elements (Variance)
- **Petal Length** → highest variance (**3.1163 cm²**), indicating it varies the most.  
- **Sepal Width** → smallest variance (**0.18998 cm²**), showing more consistent measurements.  

### 🔹 Positive Covariance
- **Petal Length & Petal Width** → **1.2956**  
  - Longer petals tend to be accompanied by wider petals.  
- **Sepal Length & Petal Length** → **1.2743**  
  - Longer sepals are generally associated with longer petals.  

### 🔹 Negative Covariance
- **Sepal Width & Petal Length** → **-0.3297**  
  - Wider sepals tend to have slightly shorter petals.  

---

## Visualization Insights
- The **heatmap** shows strong positive covariance in petal measurements and negative association between sepal width and petal size.  
- **Warm colors** = positive covariance.  
- **Cool colors** = negative covariance.  

---

## Key Takeaways
- Petal measurements are **strongly correlated** and vary more than sepal measurements.  
- Sepal width has an **inverse relationship** with petal size, useful in classification.  
- Covariance matrix is a foundation for methods like **PCA**, where understanding variance and relationships between features is essential.  

---


# 📊 Lecture 4: Factor Analysis of Wine Quality Dataset
- ## L4 Factor Analysis


This project applies **Factor Analysis** to the **Wine Dataset** (from the UCI Machine Learning Repository) to identify latent factors that explain the relationships among various chemical properties of wine. The goal is to reduce dimensionality and interpret the underlying components influencing wine quality.

## Dataset Overview
- **Source:** UCI Wine Dataset (`load_wine` from `sklearn.datasets`)
- **Observations:** 178
- **Features:** 13 chemical measurements (e.g., alcohol, flavanoids, color intensity, proline, etc.)
- **Missing Values:** None

## Pre-analysis Testing
- **Bartlett’s Test of Sphericity**  
  - χ² = 1317.181, p-value = 0.000 → Data is suitable for factor analysis.
- **Kaiser-Meyer-Olkin (KMO) Test**  
  - KMO = 0.779 → Sampling adequacy is acceptable.

## Factor Analysis
- **Method:** `FactorAnalyzer` with **Varimax rotation**
- **Number of Factors:** 3 (chosen based on eigenvalues > 1 and scree plot)

### Factor Loadings Interpretation
1. **Factor 1 – Phenolic Compounds Factor**
   - **High loadings:** Flavanoids (0.921), OD280/OD315 (0.862), Total Phenols (0.798), Proanthocyanins (0.592), Hue (0.678)
   - Represents polyphenol and flavonoid content, influencing taste, bitterness, and aging potential.

2. **Factor 2 – Alcohol & Color Intensity Factor**
   - **High loadings:** Alcohol (0.798), Proline (0.728), Color Intensity (0.712)
   - Captures attributes related to alcohol strength, color richness, and associated compounds.

3. **Factor 3 – Acidity & Minerals Factor**
   - **High loadings:** Alcalinity of Ash (0.752), Ash (0.727), moderate Malic Acid (0.228)
   - Reflects acidity and mineral content, influencing freshness and tartness.

## Variance Explained
- **Factor 1:** 30.75%
- **Factor 2:** 17.84%
- **Factor 3:** 9.77%
- **Cumulative Variance:** 58.37%

## Conclusion
The analysis reduces the original 13 chemical measurements into **three interpretable latent factors**, providing meaningful insights into the main chemical dimensions affecting wine characteristics:
- **Phenolic Profile**
- **Alcohol & Color Intensity**
- **Acidity & Mineral Content**

# 📊 Lecture 5: Project Interpretation – K-Means Clustering on the Iris Dataset  
## L5 Clustering with Iris Data

This project applies **K-Means clustering** to the Iris dataset, explores the optimal number of clusters using the **Elbow Method**, and evaluates the results against the known species labels. **Hierarchical clustering** is also performed for comparison.  

---

## Data Overview
- **Dataset:** 150 samples × 4 numeric features — *Sepal Length*, *Sepal Width*, *Petal Length*, *Petal Width*.  
- **Target:** 3 species — *Setosa*, *Versicolor*, *Virginica*.  

---

## Determining Optimal Clusters (Elbow Method)
- The **Inertia vs. k** plot shows a clear “elbow” at **k ≈ 3**, aligning with the known 3 species.  
- Both **k = 2** and **k = 3** looked plausible, but **k = 3** was chosen for final clustering.  

---

## K-Means Clustering Results
- **Optimal k:** 3 clusters.  
- **Evaluation Metrics:**
  - Adjusted Rand Index (ARI): **0.6201** → moderate alignment with true species.  
  - Adjusted Mutual Information (AMI): **0.6552** → moderate agreement.  
- **Cluster Composition:**
  - Cluster 0 → Versicolor (39), Virginica (14)  
  - Cluster 1 → Setosa (50)  
  - Cluster 2 → Versicolor (11), Virginica (36)  
- **Observation:** *Setosa* was perfectly separated, while *Versicolor* and *Virginica* overlapped.  

---

## Hierarchical (Agglomerative) Clustering
- **Method:** Ward’s linkage on scaled data, cut into 3 clusters.  
- **Metrics:**
  - ARI: **0.6153**  
  - AMI: **0.6713**  
- **Cluster Composition:**
  - Cluster 0 → Versicolor (23), Virginica (48)  
  - Cluster 1 → Setosa (49)  
  - Cluster 2 → Setosa (1), Versicolor (27), Virginica (2)  
- **Observation:** Similar to K-Means — *Setosa* mostly separated, but *Versicolor* and *Virginica* showed overlap.  

---

##  Visualization Insights
- **PCA Projection:** Both clustering methods showed clear separation of *Setosa*.  
- *Versicolor* and *Virginica* overlapped in PC space.  
- K-Means produced slightly better separation than Agglomerative for these two species.  

---

## Key Takeaways
- The **Elbow Method** effectively identified **k = 3** clusters, matching the actual number of species.  
- *Setosa* is distinct and easy to cluster.  
- *Versicolor* and *Virginica* are similar, leading to some misclassification.  
- **K-Means** and **Agglomerative** performed similarly, with K-Means showing marginally better results.  

---
# 📊 Lecture 7: DBSCAN Clustering – Two Moons Dataset
## L7 DBSCAN Clustering


This project demonstrates the **DBSCAN** (Density-Based Spatial Clustering of Applications with Noise) algorithm on a synthetic **two-moon** dataset.  
DBSCAN groups together points that are closely packed and marks points in low-density regions as **noise**.

### ⚙️ Parameters Used
- `eps = 0.3` → Maximum distance between points to be considered neighbors.  
- `min_samples = 5` → Minimum number of points required to form a dense region.

### 🔍 Key Observations
- **Cluster Detection**  
  - DBSCAN successfully identified the two curved moon-shaped clusters without requiring the number of clusters in advance.  
  - Outliers were correctly labeled as noise (cluster label = `-1`).  

- **Geometric Intuition**  
  - **Core Points (green)**: Have at least `min_samples` neighbors within `eps`.  
  - **Border Points (orange)**: Within reach of a core point but do not have enough neighbors to be core points themselves.  
  - **Noise Points (red)**: Not part of any cluster.

- **Strengths of DBSCAN**  
  - Detects clusters of **arbitrary shapes**.  
  - Handles **noise/outliers** effectively.  
  - Does not require the number of clusters (`k`) to be specified.

---

✅ **Conclusion:** DBSCAN is well-suited for datasets with non-linear cluster boundaries and noise. In this example, it perfectly mapped the two moon-shaped patterns while filtering out outliers.


# 📊 Lecture 8: Multidimensional Scaling (MDS) – US City Distances
## L8 Multidimensional Scaling (MDS)



This project uses **Multidimensional Scaling (MDS)** to visualize pairwise distances between 10 major US cities in a 2-dimensional space.  
MDS takes the real-world distance matrix and places cities as points so that the distances on the plot approximate the original geographic distances.

### 🔍 Key Insights from the Output

- **Geographic Clustering**  
  - *New York* and *Washington D.C.* appear close together in the top-right, reflecting their short real-world distance.  
  - *Seattle*, *San Francisco*, and *Los Angeles* form a cluster in the lower-left, representing West Coast cities.  
  - *Atlanta* and *Miami* are close in the Southeast region.  

- **Coast-to-Coast Separation**  
  - East Coast cities (*New York*, *Washington D.C.*) and West Coast cities (*Los Angeles*, *San Francisco*) are placed far apart, mirroring their large geographic separation.  

- **Central Positioning**  
  - *Chicago* and *Denver* lie near the center, indicating intermediate distances to both coasts.  

- **Dimension Meaning**  
  - **Dimension 1** loosely separates East (positive values) from West (negative values).  
  - **Dimension 2** roughly captures a North–South relationship, though MDS dimensions are abstract and optimized for distance preservation rather than exact geographic coordinates.  

---

✅ This visualization confirms that **MDS effectively preserves relative distances** and reveals natural groupings based on geography, even without using latitude and longitude directly.

# 📊 Lecture 9: Correspondence Analysis (CA) – US Crime Data
## L9 Correspondence Analysis (CA)



This project applies **Correspondence Analysis (CA)** to explore the relationships between U.S. states and four crime statistics: **Murder**, **Assault**, **UrbanPop** (percentage of urban population), and **Rape**.  
CA reduces the dimensionality of the contingency table, projecting both **rows** (states) and **columns** (crime variables) into the same 2D space for easier interpretation.

### 🔍 Key Insights

- **Explained Variation**  
  - **Dimension 1**: 83.5%  
  - **Dimension 2**: 11.3%  
  - Together, they capture **94.8%** of the data’s variation — meaning the biplot preserves most of the information.

- **Points in the Plot**  
  - **Blue points** → U.S. states.  
  - **Orange triangles** → Crime variables.  
  - Distance between points reflects similarity:  
    - Closer = stronger association.  
    - Farther apart = weaker association.

- **Variable–State Relationships**  
  - **UrbanPop** (bottom-right): Hawaii, Wisconsin, Iowa, New Hampshire, North Dakota → higher urban population percentages.  
  - **Rape** (top-right): Vermont, Indiana, Ohio, Utah → slightly higher rape rates compared to other crimes.  
  - **Murder** (upper-left): Alaska → relatively higher murder rates.  
  - **Assault** (bottom-left): Mississippi, South Carolina → higher assault rates.

- **Neutral/Central States**  
  - Texas, Missouri, Georgia → average or balanced crime statistics with no strong association to a single crime type.

- **Quadrant Summary**  
  - **Top-right** → Higher rape rates.  
  - **Bottom-right** → Higher urban population.  
  - **Top-left** → Higher murder rates.  
  - **Bottom-left** → Higher assault rates.

---

✅ **Conclusion:** CA provides a clear visual separation of states based on their crime profiles, making it easy to identify which states are most strongly associated with specific crime variables.
