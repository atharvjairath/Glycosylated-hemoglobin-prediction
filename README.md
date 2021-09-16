# Glycosylated-hemoglobin-prediction (Diabetes-Type-2)
> In this research we explore the extent of Machine learning algorithms used to diagnose a diabetes in the early stages. 
This research work proposes an **Optimized Weighted Ensemble Model** that can predict the risk of Type 2 Diabetes Mellitus.

## About the Dataset
Here we used the Dataset of 403 patients from the Department of Medicine at the University of Virginia given by Dr John Schorling.

## About the Approach
Here we evaluated individual machine learning models which are **Ridge Regressor, LASSO, Feedforward
Artificial Neural Networks, Linear Regression** on their prediction performance. Then we used the same model to create our average Ensemble Model.
To further improve the results of our Ensemble model we create a function to optimize weights on the basis of Low mean sqaure error (MSE) which results in increase of 18% in R2 Score.

## Results :
The results showed that the proposed optimized weighted ensemble
model outperformed individual models, achieving the highest **0.81(R2 score)** and **lowest 0.98(MSE)**.
