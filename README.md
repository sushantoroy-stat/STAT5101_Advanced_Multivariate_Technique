## 📑 Table of Contents
- [Introduction](#introduction)
- [Tools Used Here](#tools-used-here)
- [L1 Principal Component Analysis](#l1-principal-component-analysis)
- [L2 Canonical Correlation Analysis](#l2-canonical-correlation-analysis)
- [L4 Factorial Analysis](#l4-factorial-analysis)

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

- ## L1 Principal Component Analysis
Principal Component Analysis (PCA) is a statistical technique used for dimensionality reduction — that means it reduces the number of variables (features) in a dataset while keeping as much important information (variance) as possible.

⚙ How PCA Works (Steps)
1. Standardize the data (so all features are on the same scale).
2. Compute the covariance matrix of the features.
3. Find the eigenvalues and eigenvectors of the covariance matrix.
4. Sort eigenvalues in descending order — higher eigenvalue → more variance explained.
5. Select top k eigenvectors to form new feature space (k < original number of features).
6. Transform original data into this reduced feature space.

- ## L2 Canonical Correlation Analysis
# Canonical Correlation Analysis (CCA) – Psychological & Academic Variables

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



- ## L4 Factorial Analysis
# Factor Analysis of Wine Quality Dataset

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

