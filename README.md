# PA11_1 - Project Assignment for module 11

### Project description
###### The provided dataset contains information on 426K cars to ensure speed of processing. The goal is to understand what factors make a car more or less expensive. As a result of the analysis, I will provide clear recommendations to my client (a used car dealership) as to what consumers value in a used car.

#### Translation of the business problem statement into data problem statement:
------------------------------------------------------------------
I need to create and compare different regression models that will predict acurately the price of a car and identify the most important features and their impact in the overall price. I need to comunicate to the clients the following: 
1. The accuracy of the price estimation/forecast
2. The features and their relative weights in the final price estimation
__________________________________________________________________

#### Solution approach and key steps:
------------------------------------------------------------------
1. Cleanup the data set and create a clean dataframe. 
2. Analyze data, understand its business meaning, numerical and categorical features
3. Conduct a Principal Component Analysis (PCA) to extract important features and reduce the size of the dataset
4. Prepare data for model training and testing (Transform, normalize, scale, etc.)
5. Select the most accurate model and record its features, weights and it's accuracy
6. Create the clients report
------------------------------------------------------------------
#
###### Project jupyter notebook file: [PA11.1 Jupyter notebook file](https://github.com/IULIAN-COSTEA/PA11_1/blob/main/Assignment_11.1_final.ipynb)
#
#### TECHNICAL ASSESSMENT AND CONCLUSIONS:
I have evaluated four regression models ( Linear, Ridge, Polynomial and Lasso ) using three experiments that allowed me to evaluate and select the best model for the price prediction and for the key recommendation for the dealer:
- Experiment A - I've run all four models on numerical features - the best model was  Polynomial Regression (3rd degree). On numerical features it seems that the best performance we can get with the current models is close to R2=0.47. Linear Regression was not able to predict anything.
- Experiment B - I've run three models (Linear, Ridge and Polynomial) on numerical and a subset of categorical features(the ones with the most significant variance) using PCA. In this case Polynomial regression (2nd degree + 40 parameters) delivered the best result(R2=0.723). Linear Regression was not able to predict anything. Note: Lasso regression was excluded from this experiment because has its own PCA.
- Experiment C - I've run Lasso regression on all features. The performace was modest R2=0.607 when compared with polynomial regression. Bestmodel with (alpha=0.390 + 79 parameters)

Here is a look at the overall models performance ranking:

![Regression models performance chart](/images/models_performance.png)

#### CONCLUSION AND RECOMMENDATIONS FOR THE CAR DEALER:
I have valuable information for the car dealer. I will inform the car dealer the following:
The price prediction model I've created has a relatively good prediction result. It is able to predict with more than 70% accuracy the correct market price for a car based on car specifications/fearures. With a bit more work the accuracy can be improved. eg. using more advanced models. However, based on this model some usefull recommendations can be made.
My key recommendations for a car features that will ensure that the car will sell well are listed below (with the type of feature listed in order of preference): 
1. Car age (Newer car command a better price that older cars)
2. Car Odometer/Mileage (cars with less mileage command a better price)
3. Car manufacturer (1-Chevrolet, 2-Ford, 3-Toyota)
4. Car that are using gas are in higher demand
5. Car Type (1-SUV, 2-Sedan and 3-Pickup)
6. Car wheel drive (1-fwd, 2-4wd, 3-rwd)
7. Car Title_status(1-lien, 2-clean, 3-rebuilt)
8. Car condition (1-like new, 2-excellent, 3-good)

######   *Note: The values inside each features were extracted by analysing Principal components. The details were not provided becuase of the big table and 

Here is a look at the overall car features importance:

![Car features importance chart](/images/features_importance.png)
