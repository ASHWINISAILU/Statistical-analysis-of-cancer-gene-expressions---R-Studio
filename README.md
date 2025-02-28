**Statistical analysis of cancer gene variants (invasive/non-invasive)**

**Introduction**

Gene expression analysis plays a crucial role in understanding the biological mechanisms underlying various diseases, including cancer. This report explores statistical analyses and machine learning techniques 
applied to gene expression data to identify patterns, relationships, and predictive models for distinguishing between invasive and noninvasive cancer types. By leveraging methods such as Principal Component Analysis (PCA), Multivariate Analysis of Variance (MANOVA), and classification algorithms like Linear Discriminant Analysis (LDA) and Quadratic Discriminant Analysis (QDA), we aim to uncover meaningful insights from the dataset.



**Dataset Description**

The dataset consists of gene expression levels from 78 samples across 10 randomly selected genes. Each gene represents a numerical expression level, which is used to evaluate variability, correlation, and 
predictive modeling. Additionally, a class variable is included, indicating whether a sample corresponds to invasive (label 1) or noninvasive (label 2) cancer. 
The dataset provides a foundation for performing statistical and machine learning analyses to distinguish between these cancer types.

**1.Statistical Analysis of Gene Variability

1.(a) Variance, Covariance, and Correlation Matrix

Variance Matrix**

The variance matrix provides insights into the variability of each gene. A variance value close to zero indicates minimal variability, whereas higher values show increased fluctuations.

**Covariance Matrix**

The covariance matrix identifies co-variability between genes. Positive values indicate a direct relationship, whereas negative values suggest an inverse relationship.

**Correlation Matrix**

The correlation matrix measures the strength of linear relationships between genes. Values near +1 or -1 indicate strong positive or negative correlations, respectively, while values close to 0 suggest weak or no correlation.

![image](https://github.com/user-attachments/assets/4dd5fded-223f-469b-b87d-56058a52bf68)
![image](https://github.com/user-attachments/assets/64aef142-cd80-4ae5-86a5-cb3ca93f1a50)



![image](https://github.com/user-attachments/assets/956663ad-64d4-4f37-b776-29ceb4c5ee5a)
![image](https://github.com/user-attachments/assets/78fae05d-44a6-421c-b79d-47e9c10c1901)


![image](https://github.com/user-attachments/assets/363ff98b-cda5-42d6-9513-5e679c90c17b)
![image](https://github.com/user-attachments/assets/d88d5aab-c4fa-4885-8a34-f644aa09b7ca)


**1.(b) Distance Matrix Calculation**

A distance matrix was generated using R to quantify the dissimilarity between genes. Larger values indicate greater differences in gene expression patterns.




Graphical Representation:

Clustering dendrogram to visualize gene similarities.

1.(c) Univariate Q-Q Plots and Generalized Distance Q-Q Plot

Univariate Q-Q plots compare gene expression distributions to a theoretical normal distribution.

Key Observations:

Some genes align closely with the normal distribution, indicating normality.

A few genes show deviations, suggesting outliers or non-normal distributions.

Mahalanobis distance-based Q-Q plot confirms multivariate normality for most genes.

Graphical Representation:

Individual Q-Q plots for each gene.

Generalized distance Q-Q plot using Mahalanobis distance.






