**Statistical analysis of cancer gene variants (invasive/non-invasive)**

**Introduction**

Gene expression analysis plays a crucial role in understanding the biological mechanisms underlying various diseases, including cancer. This report explores statistical analyses and machine learning techniques 
applied to gene expression data to identify patterns, relationships, and predictive models for distinguishing between invasive and noninvasive cancer types. By leveraging methods such as Principal Component Analysis (PCA), Multivariate Analysis of Variance (MANOVA), and classification algorithms like Linear Discriminant Analysis (LDA) and Quadratic Discriminant Analysis (QDA), we aim to uncover meaningful insights from the dataset.



**Dataset Description**

The dataset consists of gene expression levels from 78 samples across 10 randomly selected genes. Each gene represents a numerical expression level, which is used to evaluate variability, correlation, and 
predictive modeling. Additionally, a class variable is included, indicating whether a sample corresponds to invasive (label 1) or noninvasive (label 2) cancer. 
The dataset provides a foundation for performing statistical and machine learning analyses to distinguish between these cancer types.

**1.Statistical Analysis of Gene Variability**

**1.(a) Variance, Covariance, and Correlation Matrix**

**Variance Matrix**

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

![image](https://github.com/user-attachments/assets/494d7f7c-1f10-4e79-8732-aea7e3ddedc5)
![image](https://github.com/user-attachments/assets/0f319cf0-96ed-4a7c-8043-d4782f2bd95e)

**1.(c) Univariate Q-Q Plots and Generalized Distance Q-Q Plot**

Univariate Q-Q plots compare gene expression distributions to a theoretical normal distribution.

![image](https://github.com/user-attachments/assets/7e63258f-245d-420b-97e3-3465389d398f)

**Observations:**

Some genes align closely with the normal distribution, indicating normality.A few genes show deviations, suggesting outliers or non-normal distributions.

The univariate Q-Q plots are generated for a random subset of 10 genes. These plots depict the quantities of the observed data to the theoretical normal distribution. Each plot represent each gene of a random subset of 10 genes under the variable name my.gene.subset.
The blue points represent the observed quantities and the red line represents quantities of the normal distribution. When the blue points fall closely to the red line, inferring that the data nearly follows the normal distribution.While for some genes the blue points are deviated from the red line representing a high-tailed distribution.
This Q-Q plot graph helps to infer the normality assumptions and further statistical methods to apply to further research.


![image](https://github.com/user-attachments/assets/2749c6ad-8421-4b7d-97b0-2ce3d8e9fe38)




The pair plot graph shows the significant pairwise relationships between the randomly selected 10 genes. This gives us a clear picture to identify the patterns and outliers in the existing data structure.

The Mahalanobis distance is used to calculate the generalized distance here. The corresponding observations, mean values and covariance of the dataset are used. The Q-Q plot helps to assess the distribution using this Mahalanobis distance.

This plot compares the observed Mahalanobis distance to the chi-square distribution, which represents the degree of freedom as 9(10 random gene variable -1). The green line represents the reference line showing the exact match point of observed and expected quantiles. The observed Mahalanobis distance, mostly closely on the green line (reference line), depicted that they are chi-square distributed, further indicating a multivariate normality of the data set containing 10 random genes.

The few observations falling apart from the green line indicate that there are few outliers in the dataset. However, this doesn’t affect the data much. This helps to evaluate the multivariate assumptions of observations in the dataset and any potential data anomalies before proceeding observations with further analysis.


**2. Principal Component Analysis (PCA)**

PCA was performed to reduce data dimensionality and identify significant components explaining variance.
Principal Component Analysis is generally used to reduce the complex dimensions and identify the high dimensions of the dataset. The PCA is performed on the randomly selected 10 genes consisting of two main tasks in the analysis; importance of components and loading of each gene on the principal components.
The importance of the Components table shows the quantitative measure of standard deviation, Proportion of variance and the cumulative proportion of each component.


The standard deviation is calculated by the square root of eigenvalues of the covariance matrix.
The proportion of variance is the square of the standard deviation divided by the sum of squares of all standard deviations.
The cumulative proportion of variance is the cumulative sum of proportions of variance explained by each principal component.
Loadings refers to the contribution of each gene to principal component. High value depicts the high association between the gene and the respective principal component.

![image](https://github.com/user-attachments/assets/dc1daf57-537d-4c6e-a7f5-2c6b7662b5f6)
![image](https://github.com/user-attachments/assets/415135ff-ccfa-4e3d-8539-84341524bff0)

In principal component 1, there exists the highest value in standard deviation, Proportion of Variance and Cumulative Proportion showing the high variability in the data. And the trend is decreasing in further component proceedings, which clearly indicates less variability in the data. Each component gives valuable information for analyzing the overall structure of this data set.


While analyzing the loadings in component 1, genes Contig11075_RC, NM_004358, and L36069 contribute significant variations in Component 1. Similarly, in Component 2, Contig54232_RC, NM_004056, Contig11075_RC and NM_001218 genes have higher values. The loading table illustrates the relationship between the genes and the principal components. The high loading values of genes represents high correlation and negative values are negatively correlated.


This PCA model gives us the underlying structure of this gene expression data. The repeated pattern of loading of genes to the components and analyzing the importance of components give us the key pattern and relationship between the genes. The graph clearly shows the variance in the data that has decreased with increasing components.

**Results:**

Component 1 (PC1) explains the highest variance (~21%).

Component 2 (PC2) explains additional variance (~18%).

Variance decreases progressively across components.

Loadings indicate the contribution of each gene to principal components.


![image](https://github.com/user-attachments/assets/2df9114b-b2b2-44e1-ad7b-8797829527d3)


**3. Multivariate Analysis of Variance (MANOVA)**

The MANOVA fit model helps to investigate whether there is a significant difference in the expression levels of 10 random genes between invasive and non-invasive cancer.

In MANOVA, intercepts represent the estimated intercepts of the regression equation for each dependent variable. Similar to the intercepts in linear regression models, the position where the expected variable of each dependent variable when all other independent variables tend to zero, intercepts are formed.
F-Statistics are determined to test the overall significance of the model. In the overall MANOVA test, F-statistics are calculated by comparing the variability between groups to the variability within groups.

The degree of freedom is associated with the number of groups, the number of dependent variables and parameters estimated in the MANOVA model. A multivariate test statistic termed Pillai trace is used in MANOVA to evaluate the overall significance of the model or individual effects. Ranges from 0 to 1 with larger values depicting greater discrimination between the groups. The p-value indicates the probability of observing the data with test statistics. Here, the smaller the p-value depicts that there are significant differences between the groups or effect in the respective model. Pr’s value, otherwise known as the Probability Ratio, is another measure of significance. The ratio of the observed value of a test statistic to its expected value in the null hypothesis. If a Pr value close to 1 indicates a prediction of a null hypothesis is approved when the Pr values differ far from 1, the most likely null hypothesis is rejected.

The intercept of Pillai traces 0.54587, indicates a moderate-to-large effect size. The approximate F-statistic is 8.0534 and the degree of freedom is 10 and 67 for the numerator and denominator, respectively. The associated p-value (Pr(>F)) is highly significant (p < 0.001), showing that there is a significant overall effect when considering all variables.

The intercept of Pillai traces 0.17394 for variable class, which indicates smaller effect size when compared to the intercept.
The approximate F-statistic is 1.4108 and the degree of freedom is 10 and 67 for the numerator and denominator, respectively. The associated p-value (Pr(>F)) is 0.1948, which is not significant (p > 0.05). This suggests that there is no significant difference in gene expression levels of 10 random genes between invasive and noninvasive cancer after controlling for other variables.

The residual 76 shows the unexplained variances after counting on the intercepts.

To conclude, the MANOVA results show there is a significant impact while considering all variables, while specific variable-class (invasive vs. noninvasive cancer) does not significantly impact the differences in gene expression levels.
Therefore, the H0 null Hypothesis is not rejected, concluding that there is no significant difference in the expression levels of the random subset of 10 genes between invasive (label 1) and noninvasive (label 2) cancer.

**Results:**

Pillai’s Trace for intercept: p < 0.001, indicating significant variance.

Pillai’s Trace for cancer type: p = 0.1948, suggesting no significant difference.

![image](https://github.com/user-attachments/assets/b8d4f673-c40a-459e-8d64-9e8a307bd65d)


The above box plot shows the interquartile range of gene expression for each cancer type (invasive and noninvasive).
The Q1 and Q3 are the top and bottom edges of the box and the middle line(line inside the box) represents the median value of the gene expression. The data points scattered outside the box are termed as outliers. Label 1 represents noninvasive cancer and Label 2 represents invasive cancer.

From the MANOVA table:

For the intercept (overall gene expression levels), the Pillai’s trace statistic is 0.54587, indicating a significant difference between the two groups (p < 0.001).


For the factor my.gene.subset$class (cancer type), the Pillai’s trace statistic is 0.17394, indicating a non-significant difference between the two groups (p = 0.1948).


The box plot shows substantial overlap in label 1 and label 2 which clearly shows that there is o significant difference in the expression levels of the random subset of 10 genes between invasive (label 1) and noninvasive (label 2) cancer. Hence, H0 Null hypothesis is accepted.


**Using the first and second principal component to illustrate, if there is a difference between invasive and noninvasive cancer.**

In order to compare the first and second principal components, we are extracting the coefficients of the first principal component (PC1) and second principal component (PC2). These coefficients are the contributions of each variable to their respective principal component. The positive coefficient represents positive correlation and the negative coefficient represents negative correlation.



The plot graph of coefficients of PC1 and PC2 helps us to visualize the difference between the two groups of invasive and noninvasive cancer types. PCA is performed on the extracted PC1 and PC2, which is a subset of genes excluding the class variables, and of ggplots are used to give a clear visualization of differences between the two groups, invasive and noninvasive cancer types.



![image](https://github.com/user-attachments/assets/7ee1595f-63d0-4c31-b50a-ae5674c2580a)

The inferences from the above analysis is that the PCA coefficient showing the correlation between each gene and PC1 and PC2 and insights in the gene contribute more variation in PC1 and PC2. The graph of the coefficients of the first two principal components gives the relative contribution of each gene to overall variation in the dataset, which is more of a scattered plot without any overlaps.



However, through the PC1 and PC2 of gene expression in a reduced dimensional-space, we see there are significant clustered plot patterns providing insights into the potential discriminatory power of the selected subset (differentiated by red and blue points in the graph) of genes for distinguishing between invasive and noninvasive cancer types.



![image](https://github.com/user-attachments/assets/aee643ce-5271-4d41-9882-97915a842929)



**4. Classification Using LDA and QDA**

Linear Discriminant Analysis (LDA) and Quadratic Discriminant Analysis (QDA) were used to classify cancer types.


**LDA Results:**

![image](https://github.com/user-attachments/assets/24807bac-5c14-4c0a-a437-e0444e906db9)

Accuracy: 34.78%

Sensitivity: 20%

Specificity: 46.15%

Misclassification Error: 65.21%

Inference: Poor predictive performance.


The above output of the Linear Discriminant Analysis (LDA) helps to analyze the performance to classify the cancer types as invasive and noninvasive. LDA is applied to a subset of 10 random genes with class variables indicating invasive and noninvasive cancer types.
The data has been split into training represented as Data.1 (70 percentage of the data) and testing as Data.2(remaining 30 percentage of the data). LDA is applied to Data.1 training dataset with class variables as a response and predictors as gene expression features. The trained LDA model is used to predict the class labels of the testing set (data.2) of the data. In order to analyze the performance of the LDA model, a confusion matrix is computed.

The confusion matrix shows the numeric data of the performance of the LDA model as follows:
Accuracy is 34.78 percent, which is considerably low, referring to a low performance model. The 95 percent confidence interval for accuracy is between 16.38 percent to 57.27 percent, representing a poor model’s predictive capabilities. The kappa statistic is -0.3424, indicating poor agreement beyond the chance of current and actual class. This show’s model’s performance is not significant. The sensitivity (true positive rate) is 20 percent, which is a measure of the proportion of actual invasive cases identified by the model. The specificity is 46.15 percent, which is a measure of the proportion of actual noninvasive identified by the model. The misclassification error is miscalculated instances which computes to 65.21 percent.


To conclude, the above LDA model trained has poor performance with the testing data. Further classification accuracy has to be improved by exploring more alternative classification algorithms.

**Quadratic discriminant analysis (QDA) to random subset of 10 genes and the class variable (invasive (label 1) and noninvasive (label 2) cancer).**

![image](https://github.com/user-attachments/assets/823744e5-c209-490e-98cf-dc97d44fa30f)
![image](https://github.com/user-attachments/assets/8563e205-4d66-46c6-933b-98b341b03899)


**QDA Results:**

Accuracy: 82.05%

Sensitivity: 70.59%

Specificity: 90.91%

Misclassification Error: 17.95%

Inference: QDA outperformed LDA significantly.

The above Quadratic Discriminant Analysis (QDA) helps to develop a predictive model to classify the invasive and noninvasive cancer type based on the gene expression data. A subset of gene expression data is created and converted to the matrix ‘x’. The prior probabilities of the group and group means are calculated. The QDA fitting is performed with the predictor variables specified as gene expressions, and the response variable as ‘class’. The classes are predicted from the QDA fitted model.


A contingency table is created to compare the predicted classes with actual classes. A confusion matrix is generated to evaluate the performance of the QDA predictions. The classification is as follows:

24 invasive cancer cases as True Positives, 40 non-invasive cancer cases as True Negatives, 4 non-invasive cancer cases as False Positives, 10 invasive cancer cases as False Negatives.


The QDA model accuracy computes to 82.05 percent, which is significantly a high performance of the model. The 95 percent confidence interval for accuracy is between 71.72 percent to 89.73 percent, representing a decent model’s predictive capabilities. The kappa statistic is 0.6276, which shows agreement between predicted and actual classes beyond chance turns to be moderate. Sensitivity for this QDA model is 70.59 percent, which determines the true positives of invasive cancer cases. Specificity identified by this QDA model is 90.91 percent of noninvasive cancer cases, which determines the ability to avoid false alarm in noninvasive cases. The calculated misclassification error of the overall QDA model is 17.95 percent, which is the proportion of incorrectly classified cases.


In order to infer from this QDA model, there is a promising accurate classification of cancer types based on gene expression data. High performance, sensitivity and specificity values are remarkably high, depicting good performance in detecting invasive and noninvasive cancer cases.


**Difference between LDA and QDA using the results on your random subset of 10 genes and the class variable (invasive (label 1) and noninvasive (label 2) cancer).**



The LDA model is based on the assumption that the predictors have a multivariate normal distribution within each class and the covariance matrix across classes is equal. The QDA model proceeds with no assumption, allowing each class to have its own covariance matrix.


With respect to the accuracy of the overall model, the LDA model shows a low accuracy level of 34.78 percent comparatively on the other hand, the QDA model has a high accuracy of 82.05 percent. The kappa statistics for the LDA model is -0.3424 and the QDA model is 0.6276. The kappa statistic generally determines the agreement between the predicted and actual classes. In this case, the QDA model exhibits high agreement beyond the chance of the positive value 0.6276 to that of LDA model in negative value -0.3424.


The 95 percent confidence interval for accuracy range in the LDA model is low, between 16.38 percent to 57.27 percent, whereas the QDA model comes with a better accuracy range from 71.72 percent to 89.83 percent. It is evident that the LDA model has poor predictive capabilities when compared to the QDA model.


The Sensitivity(True Positive Rate), specificity(True Negative Rate) and misclassification error of the LDA model are 20 percent,46.15 percent and 65.21 percent. And the QDA model has 70.59 percent,90.91 percent and 17.94 percent respectively. Sensitivity and specificity are significantly higher in the QDA model compared to the LDA model. This is a true positive rate of invasive cancer cases and a true negative rate of noninvasive cancer cases in a random 10 gene subset. The misclassification error is comparatively lower in the QDA model than the LDA model, which determines that the QDA model possess more accurate classification of cancer types. The LDA model approaches with the assumption that classes are linear. However, the QDA model showcases more flexibility for complex decisions, which leads to better classification performance.


In order to conclude, the above LDA and QDA models. In this case, the difference in assumption of the predictors component makes the QDA model to be more flexible with respect to the covariance matrix. This further enhances the performance of the QDA model compared to the LDA model for this analysis. The LDA model seems to be more promising for simpler computation of a dataset where the assumptions of equal covariance matrices is satisfied. But the QDA model has become a more optimal model to use due to its flexibility in negotiating the assumption of covariance matrices.
This supports the QDA model to be more reliable for complex relationship modelling between predictors and classes.

**5. Fisher’s Exact Test for Class Prediction Using PC1 Median**

The median of PC1 was used to classify cancer types, followed by Fisher’s Exact Test to assess the significance of classification.

![image](https://github.com/user-attachments/assets/fe029aff-eff0-411d-a80e-3b9fd77e29d3)
![image](https://github.com/user-attachments/assets/e8cb7311-dff2-4eb8-9370-4e96746ddc99)


**Results:**

p-value: 0.8196 (insufficient evidence for association).

Youden’s Index: Not computable.

Inference: PC1 median is not a reliable predictor for cancer classification.


The main aim of this analysis is to predict the relationship between predicted classifications based on the first principal component of gene expression data and the actual class using Fischer’s exact test. Fischer’s exact test is used to determine the significant association between two categorical values when the sample size is small and chi-square assumptions (no random sampling, low count in contingency table) are violated. A significant tool for analysis when other methods are not appropriate.


Null Hypothesis(H0): There is no association between the predicted class based on the first principal component and the actual class from the dataset.
Alternative Hypothesis(H1): There is an association between the predicted class based on the first principal component and the actual class from the dataset.


A new data frame is created as Data.5 by excluding the last column from my.gene.subset data frame, an essential step to perform Principal Component Analysis on the gene expression data only. Principal Component Analysis is performed on new data frame Data.5. Further, the First Principal Component is extracted from the result and the respective median is computed. This median value is a threshold for classifying the data points into two groups based on their position relative to the median along the first principal component axis. The data points are further classified as 1 for points above the median, 0 for points below the median. The actual class labels are extracted from the original data frame and are converted to character type for analysis. A contingency table is created with predicted and actual classes to execute the Fisher’s exact test to check the association between the predicted and actual class labels.


The Confusion matrix shows the True negatives is 0, False Positives is 16, False Negatives is 0, True positives is 18. The Accuracy of classification of sample is 52.94 percent for this model. Kappa value is 0 which represents that there is no agreement beyond the chance between the predicted and actual class. Specificity marks 52.94 percent, representing the negative samples of the model. McNemar’s Test P-value is 0.0001768 which shows that the significant difference in error between the predicted and actual classes. Youden's Index is 0 as its cannot be calculated as sensitivity is not available.


The above Fisher’s Exact test has a p-value 0.8196, which shows insufficiency to reject the null hypothesis. This suggests a likelihood of no association between the predicted class on the first principal component and the actual class. The 95 percent confidence interval for the odds ratio ranges from 0.3010991 to 2.1825224. And the estimated odds ratio calculated as 0.8137785 depicts that the odds of the correct class based on the first component are slightly lower than the odds of the incorrect class. The difference is not significant.


To conclude, on the above Fisher’s Exact test, there is insufficient evidence to conclude the association. Alternative methods or larger datasets are required for further validation. Hence, it concludes that there is no association between the predicted class based on the first principal component and the actual class from the dataset.

**Conclusion**

This study provides statistical insights into gene expression variability, classification effectiveness, and the relationship between gene subsets and cancer types. PCA and QDA proved valuable for dimensionality reduction and classification. However, further refinement is necessary to improve predictive performance.
