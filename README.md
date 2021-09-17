# Glycosylated-hemoglobin-prediction (Diabetes-Type-2)
> In this research we explore the extent of Machine learning algorithms used to diagnose a diabetes in the early stages. 
This research work proposes an **Optimized Weighted Ensemble Model** that can predict the risk of Type 2 Diabetes Mellitus.

## About the Dataset
Here we used the Dataset of 403 patients from the Department of Medicine at the University of Virginia given by Dr John Schorling.

## About the Approach
Here we evaluated individual machine learning models which are **Ridge Regressor, LASSO, Feedforward
Artificial Neural Networks, Linear Regression** on their prediction performance. Then we used the same model to create our average Ensemble Model.
To further improve the results of our Ensemble model we create a function to optimize weights on the basis of Low mean sqaure error (MSE) which results in increase of 18% in R2 Score.

### Weights Optimization for Ensemble
#### Function :
~~~~py

from scipy.optimize import minimize
rmse_optimize =[]
def rmse_loss_func(weights):
    ''' scipy minimize will pass the weights as a numpy array '''
    final_prediction = 0
    for weight, prediction in zip(weights, predictions):
            final_prediction += weight*prediction

    print(np.sqrt(mean_squared_error(y_test,final_prediction)),weights)
    rmse_optimize.append(np.sqrt(mean_squared_error(y_test,final_prediction)))
    return np.sqrt(mean_squared_error(y_test,final_prediction))
    
~~~~

#### How to use : 
~~~~py
# add every model's prediction into list
predictions = []
predictions.append(y_Ridge_GS_pred)
predictions.append(y_rf)
predictions.append(y_lasso_GS_pred)
predictions.append(y_XGBReg_pred)
#starting Value
starting_values = [0.5]*len(predictions)
#cons = ({'type':'eq','fun':lambda w: 1-sum(w)})
#our weights are bound between 0 and 1
bounds = [(0,1)]*len(predictions)
res = minimize(rmse_loss_func, starting_values, method='Powell')
~~~~

#### Weights Optimization Plot 
![Image](https://github.com/atharvjairath/Glycosylated-hemoglobin-prediction/blob/main/Scipy_miminize.png)

## Results :
The results showed that the proposed optimized weighted ensemble
model outperformed individual models, achieving the highest **0.81(R2 score)** and **lowest 0.98(MSE)**.
