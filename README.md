# Overview
This project aims to identify the customer characteristics that increase the likelihood of purchasing a health plan. Leveraging a survey dataset with 12,686 unique respondents, we explore demographic and socioeconomic factors to predict health plan adoption (binary target: 1 = Yes, 0 = No). Our approach involves building and testing predictive models—logistic regression, decision trees, and K-Nearest Neighbors (K-NN)—to uncover significant predictors and provide actionable marketing recommendations. The goal is to help health insurance providers target potential customers effectively by understanding key drivers like gender, income, marital status, and education, ultimately optimizing outreach strategies.

# Features
The analysis employs a multi-model framework in R to dissect customer behavior. We use logistic regression (glm with family = binomial) to identify statistically significant predictors, refining the model to focus on Male, Income, Marital_status, and Education. A decision tree model segments customers into likely buyers based on rules like income thresholds and education levels. The K-NN algorithm, optimized at k=10, offers a non-parametric prediction method, evaluated via accuracy, kappa, sensitivity, and specificity. Key outputs include coefficient estimates, odds ratios, confusion matrices, and performance metrics like Area Under the Curve (AUC = 0.6881), all designed to interpret variable impacts and predictive power.

# Dataset
The dataset comprises 12,686 rows, each representing an individual with a unique ID, and 24 variables, though we focus on a subset for modeling. The target variable, HealthPlan, is binary (1 = covered by a health plan in 2000, 0 = not covered). Key input variables include: Age (interval, as of 1979), Urban (binary, urban vs. non-urban residence at age 14), Mother_Edv (interval, mother’s education years), Income (interval, income in 2000), Siblings (interval, number of siblings in 1979), Black (binary, race), Christian (binary, religion in 1979), Height (interval, height in inches in 1981), Male (binary, gender), Marital_status (binary, married vs. single), and Education (interval, years of education). Missing data reduced the sample to 7,568 usable observations for regression.

# Analysis
Our process unfolds in three steps. First, we define the big picture by selecting HealthPlan as the target and testing 24 variables, narrowing to significant predictors via logistic regression (p < 0.05), resulting in a model with Male, Income, Marital_status, and Education. Cross-validation is implied through model refinement and performance checks. Second, we build and test alternative models: a decision tree to derive customer segments (e.g., females with income > $22,000) and K-NN, iterating k from 1 to 10, selecting k=10 for peak accuracy (85.6%). Third, we analyze results using odds ratios, confusion matrices, and performance charts (AUC, lift curves) to interpret predictor effects and model efficacy.

# Insights
Logistic regression reveals four significant predictors: Male (odds decrease by 52.43% for males vs. 47.57% for females, favoring females), Income (negligible 0.0037% increase per unit, suggesting minimal impact), Marital_status (odds increase 10.57% for married vs. 89.43% for single, favoring singles), and Education (22.54% odds increase per year, favoring educated individuals). The decision tree highlights specific segments: females with income > $22,000, unmarried males with >12 years of education, and males with income < $106 and age > 19. K-NN excels at identifying positives (high sensitivity) but struggles with negatives (low specificity), with an AUC of 0.6881 outperforming a baseline model. Notably, income’s weak effect challenges assumptions about financial drivers.

# Results
The logistic model (AIC = 5816.6, residual deviance = 5806.6) confirms Male, Income, Marital_status, and Education as key predictors, with females, singles, and educated individuals more likely to buy health plans. The decision tree refines this into actionable segments, while K-NN at k=10 achieves 85.6% accuracy, offering a reliable predictive tool (though the 97.59% accuracy claim in the document seems overstated relative to the table). We recommend targeting: (1) females with income > $22,000, (2) unmarried males with education beyond high school, and (3) males with income < $106 and age > 19. The K-NN model can guide marketing by predicting health plan uptake with nearest-neighbor logic, enhancing customer targeting precision.
