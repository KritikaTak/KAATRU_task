# KAATRU_task:[Significant variables for demand sharing of bikes]
## OBJECTIVE
### To develop a model to find the variables that are significant in the demand for shared bikes with the available independent variables and report appropriate metrics of your model evaluation.
## Data Cleaning
Data was found cleaned on checking missing variables and dtypes for the variables as well.
For the variables found categorical in values, was changed as same using one hot encoding.
## Data Visualisation
### Visualisaing relation between different features using Pair-Plot outcomes:
From the above pairplot, it is cleared that, features temp, atemp are in linear relationshio with dependent feature cnt respectively.
temp and atemp are in relationship with each other.
### Checking correlation through heatmap:
Heat map showing correlation and multicorrelation between different variables.
Considering cnt we can see this is high correlated with: yr,temp,atemp,season3,weathersit_3 (taken nearly to -1,1)
### Checking outliers through boxplot:
It can be seen there are no outliers considerably in the features(temp,atemp,cnt) which are correlated(analysed through above visualisations).
### Checking relation between categorical variables and dependent variable using boxplot:
yr & cnt: it can be seen that demand of bike sharing is increased from 2018 with median(approx 3900) to 2019 with median(app 6000).
season & snt: it can be seen that demand for bike sharing is more in season3 followed by season2, season4, season1. It can predict cnt well.
mnth & cnt: higher bike demand can be seen in mnth7 and(then mnth: 9,6,8 respectively). This can also predict cnt well.
holiday and cnt: Almost more than 50% of bike demand is seen when no holiday.
workingday & cnt: Equivalently bike demands are there on workingday or not workingday.
weathersit & cnt: higher bike demands can be seen in weathersit 1 then weathersit 2 and 3. It can also predict cnt well.
weekday & cnt: Almost equivalent bike demands are seen on different week days.
### Checking for normality using distplot:
All the features(numerical) plotted show normality(normal distribution).
### Scaling the features
## Applying RFE(Recursive Feature Selection)
Given an external estimator that assigns weights to features (e.g., the coefficients of a linear model), the goal of recursive feature elimination (RFE) is to select features by recursively considering smaller and smaller sets of features. First, the estimator is trained on the initial set of features and the importance of each feature is obtained either through any specific attribute or callable. Then, the least important features are pruned from current set of features. That procedure is recursively repeated on the pruned set until the desired number of features to select is eventually reached.RFE can be done for classification as well as regression.

Here we will use RFE for Linear Regression Model.
## VIF check and OLS modelling

#### VIF
VIF determines the strength of the correlation between the independent variables. It is predicted by taking a variable and regressing it against every other variable.VIF score of an independent variable represents how well the variable is explained by other independent variables.

R^2 value is determined to find out how well an independent variable is described by the other independent variables. A high value of R^2 means that the variable is highly correlated with the other variables. This is captured by the VIF:
VIF formula= 1/(1-R^2)

So, the closer the R^2 value to 1, the higher the value of VIF and the higher the multicollinearity with the particular independent variable. VIF=[1,)


#### OLS
A linear regression model establishes the relation between a dependent variable(y) and at least one independent variable(x) as : 
\hat{y}=b_1x+b_0  
In OLS method, we have to choose the values of b_1  and b_0  such that, the total sum of squares of the difference between the calculated and observed values of y, is minimised. 

### On applying OLS model fit, in final model the significant features came out to be:
yr              
temp            
windspeed      
season_2        
season_4       
mnth_3         
mnth_9         
weekday_2      
weathersit_2  
weathersit_3  

## Predicting on test data using final model=ols_6
On predicting for the cnt on test data using final model. The evaluation metrics show following scores:
###Model Evaluation Metrics
Mean_Absolute_error   	Mean_Squared_error	    Root_mean_squared_error	    R_squared value	    Adjusted_R_squared_value
0	0.074583	            0.009494	              0.097435	                  0.802741	          0.793303

## Result
From the above analysis: It can be clearly concluded that the feature variables that can be significant in the demand for shared bikes are

1. Temperature(temp) : As according to its coeff=0.5754, it can be seen as a unit increase in temp can increase the demand by 0.5745.
2. Weather(weathersit_3): As according to its coeff= -0.3094, it can be seen as a unit increase in weathersit_3 can deccrease the demand by 0.3094, as coeff is negetive.
3. Year(yr): As according to its coeff=0.2299, it can be seen as a unit increase in temp can increase the demand by 0.2299.
