# -Earthquake-Damage-Classification-in-Nepal-Using-Machine-Learning
#-📌 Project Overview
Earthquakes can cause extensive structural devastation and disrupt vulnerable communities. This project implements a machine learning decision-support framework to predict whether a building is likely to experience severe earthquake damage (damage grades 4–5) versus not severe damage (grades 1–3) using pre-earthquake characteristics.   
MLIS_IA_Karya.pdf

The primary objective is to build a screening tool that disaster-management teams can use to identify high-risk building profiles and optimize inspection and preparedness planning. Note: This system is intended strictly as a decision-support tool and does not replace professional structural engineering assessments.   
MLIS_IA_Karya.pdf
+ 1

#-📊 Dataset & Preprocessing
Source: Nepal earthquake building-damage dataset (sourced from Kaggle / NepalEarhquakeDamage2015.csv, containing over 760,000 records).   
MLIS_IA_Karya.pdf
+ 1

Target Variable: Binary classification target (severe_damage) derived from damage_grade (Grades 4–5 = 1, Grades 1–3 = 0).   
MLIS_IA_Karya.pdf

Data Hygiene & Leakage Prevention:

Removed unique identifiers (building_id).   
MLIS_IA_Karya.pdf

Strictly excluded all post-earthquake attributes (count_floors_post_eq, height_ft_post_eq, condition_post_eq) to eliminate target leakage and simulate real-world pre-event screening.   
MLIS_IA_Karya.pdf

Pipeline Design: Built automated scikit-learn preprocessing pipelines handling numeric imputation (median), categorical imputation (most frequent), one-hot encoding for categorical attributes, and feature scaling (StandardScaler) for linear models.   
MLIS_IA_Karya.pdf
+ 3

#-🛠️ Methodology & Workflow
Exploratory Data Analysis (EDA): Visualized class imbalances, feature distributions, building heights, and severe-damage rates segmented by foundation types.   
MLIS_IA_Karya.pdf
+ 3

Data Splitting: Applied a stratified 70% training, 15% validation, and 15% test split to preserve class distributions and prevent data leakage during hyperparameter tuning.   
MLIS_IA_Karya.pdf
+ 1

#-Model Development & Tuning:

Logistic Regression: Tuned regularization parameter 
𝐶
∈
{
0.01
,
0.1
,
1
,
10
}
C∈{0.01,0.1,1,10}.   
MLIS_IA_Karya.pdf

Decision Tree Classifier: Tuned maximum depth parameters (max_depth) using validation macro F1-scores.   
MLIS_IA_Karya.pdf
+ 1

Model Selection: Evaluated models primarily on Validation Macro F1-score to give balanced weight to both severe and non-severe classes. The Decision Tree was selected based on superior validation performance.   
MLIS_IA_Karya.pdf
+ 2

Final Test Evaluation: Assessed the generalized models on an untouched test partition using Accuracy, Macro Precision, Macro Recall, Macro F1, and ROC-AUC.   
MLIS_IA_Karya.pdf
+ 1

#-📈 Key Results & Performance
Both models were evaluated on the held-out test set (
𝑁
=
114
,
315
N=114,315):   
MLIS_IA_Karya.pdf
+ 1

Model	Accuracy	Precision (Macro)	Recall (Macro)	F1 (Macro)	ROC-AUC
Logistic Regression	
0.716 
MLIS_IA_Karya.pdf

0.713 
MLIS_IA_Karya.pdf

0.678 
MLIS_IA_Karya.pdf

0.683 
MLIS_IA_Karya.pdf

0.732 
MLIS_IA_Karya.pdf

Decision Tree (Selected)	
0.758 
MLIS_IA_Karya.pdf

0.749 
MLIS_IA_Karya.pdf

0.754 
MLIS_IA_Karya.pdf

0.751 
MLIS_IA_Karya.pdf

0.838 
MLIS_IA_Karya.pdf

Decision Tree Performance: Achieved an strong ROC-AUC of 0.84 and a high severe-class recall, ensuring that a minimal number of high-risk structures are missed by the screening model.   
MLIS_IA_Karya.pdf

#-🔍 Model Interpretation
Decision Tree Feature Importances (Gini): Regional metrics (district_id) and core structural integrity features—specifically foundation_type (notably structures built with Mud mortar-Stone/Brick)—dominated the decision tree's splitting rules.   
MLIS_IA_Karya.pdf

Logistic Regression Coefficients: Highlighted protective building characteristics associated with lower odds of severe damage (e.g., Reinforced Concrete (RC) foundations and ground floors) versus vulnerability indicators like Mud mortar-Stone/Brick foundations and tall, multi-floor configurations.   
MLIS_IA_Karya.pdf
+ 1

#-🚀 Tech Stack
Language: Python   
MLIS_IA_Karya.pdf

Libraries: pandas, numpy, scikit-learn, matplotlib, seaborn   
MLIS_IA_Karya.pdf
