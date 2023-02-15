# toyota-used-cars-machine-learning-predicting-prices

A Toyota used cars dealer in England has been decreasing their sales in the last months.  Also, the dealer has been contracting junior salesman.  The manager thinks that the reason for decreasing sales is the lack of knowledge in used cars prices by the junior salesman.  The manager wants to have a   fast and reliable system to predict prices correctly for the Junior Salesman that can help them give the clients the correct price of the used cars. The manager has delivered data from the business with sales of Toyota used cars with year of fabrication,  different models, mileage, fuel type, transmission, engine size, tax and price.  He asks, with this data can you predict prices correctly to give the junior salesmen a reliable reference?
Here we are going to show a machine learning model for this business  that solves in a great percentaje the problem.
For that, there is a **data validation(1 below)**, and **exploratory analysis of the data(2 below)*.  Then, there is an analysis of the **best(6 below)** of **four machine learning models(3,4,5,6 below)** to use to predict the best reliable and correct price of used cars.  Finally,  **the conclusion(7 below)** is that the reliable predictive price for used cars is possible. This  will help junior salespeople predict prices correctly,  building  their confidence to not lose clients   and  generate more sales in the future.

**1. DATA VALIDATION**

This data set has 6738 rows, 9 columns. I have validated all variables and I have not made any changes after validation. All the columns are just as described in the data dictionary:

- model: 18 models without missing values, same as the description. No cleaning is needed.

- year: 23 unique values without missing values, from 1998 to 2020, same as the description. No cleaning is needed.

- price: numeric values without missing values, same as the description. No cleaning is needed.

- transmission: 4 categories without missing values, same as the description. No cleaning is needed.

- mileage: numeric values, same as the description. No cleaning is needed.

- fuelType: 4 categories without missing values, same as the description. No cleaning is needed.

- tax: numeric values, same as the description, no cleaning is needed.

- mpg: numeric values without missing values, same as the description. No cleaning is needed.

- engineSize: 16 possible values without missing values, same as the description. No cleaning is needed.

The code for DATA VALIDATION is [here](data-validation)


**2. EXPLORATORY ANALYSIS**

TARGET VARIABLE: PRICE... We analyze price and change to log scale. The mean price for a car is 12522 pounds, and the price converted to a log number is 9.32. We will be using the log price for the machine learning models.

![download](https://user-images.githubusercontent.com/53232113/219167241-e3c7bb2f-064a-4340-b01a-6e7884cc2674.png)

![download](https://user-images.githubusercontent.com/53232113/219168418-164b5aeb-e057-4c77-9916-066ec727f88f.png)

We see that there is a negative correlation with mileage(-0.39), and positive correlation with year(0.55). There is no correlation with mpg. , 
![download](https://user-images.githubusercontent.com/53232113/219169324-27ab7071-0de7-4225-b51f-ba08237f4e95.png)

![download](https://user-images.githubusercontent.com/53232113/219169364-3531a9b4-391e-4271-8c52-f8f4dd66db4a.png)

In relation to year of manufacturing, most cars in the set have been manufactured in 2017 and above and most cars are 1.0 engineSize. 
![download](https://user-images.githubusercontent.com/53232113/219169405-dd5934b4-68de-4f1e-a1ad-31facc9529b9.png)

With category data, most cars in the data are model Yaris or Aygo with manual transmission, with Petro fuel 
![download](https://user-images.githubusercontent.com/53232113/219169451-c2be0cd0-8194-44ef-94c3-da313b72380a.png)

analyzed by boxplot graphs, there is a wider distribution on model GT86, RAV4 and Avensis, and a narrow distribution on Corollas, CH_r and Prius. On, transmision types, there is a wider distribution on Automatic and narrow on Manual, On fuel type, there is a narrow distribution on Petrol fuel.
![download](https://user-images.githubusercontent.com/53232113/219169489-1a1d1eca-0d55-42f8-976b-bbd90bd99779.png)

The code for EXPLORATORY ANALYSIS is [here](exploratory)

**3. LINEAR REGRESSION MODEL**

First: import all libraries used for linear regression such as pandas. numpy, matplotlib, Linear Regression, etc.

Second: there is a conversion of all category data to numeric for three features: transmission, fuel type and model, with the pandas replace method. For example the fuel type "Petrol" is converted to number "1".

Third: there is a scatter plot with two features, price and mileage. Millage is the feature with strongest correlation to price, and over the same plot there is a predicted line with the regression model, and predicts that the price of cars goes down to half of the inicial in aproximatelly 100000 miles.



![download](https://user-images.githubusercontent.com/53232113/219202279-d9d6e92e-c9f4-4ca8-aaea-674e885a0dbf.png)

Forth: we change price to a log price and numeric data such as mileage, year and engine size to scalar data. We have to have scalar and log data before using our machine learning model.

Fifth: we check the score using train test split with the linear regression model of train data and score with test data, get a 88% score, use the **r2_score between the y test data and the y predict, get and 88%, and use the square root of the mean_squared_error between the y test and the y predict and get a 16.4%**.

Sixth: on feature importance,the most important predictor for our target price is engine size, followed by year of manufacturing, transmission and mileage.

![download](https://user-images.githubusercontent.com/53232113/219202349-8cada64d-df24-4c5b-a054-9919e82299cf.png)

The code for **LINEAR REGRESSION** is [here](linear-regression)

**4. RIDGE AND GRIDSEARCHCV MODELS**

In this analysis we prepare the data converting the category data to numbers, preprocess the numeric data by scaling with min-max scaling, log the price data, and model with Ridge, get a score of 88%, r2 score of 88% and a root mean square error of 16%, go to GripSearchCV model, find the best parameter for Ridge, which is alpha equals to 0.0, and get a score of 88%.

The code for **RIDGE AND GRIDSEARCHCV REGRESSION MODELS** is [here](ridge)

**5. DECISION TREE REGRESSION MODEL**

With decision tree regression modeling, we change the category data to numeric, use feature columns: year','transmission','fuelType','engineSize','model','mileage, and use the target as a log price, then split the data into train and test data, and execute the decision  regression tree modeling, with a max  depth parameter equals to ten.  We fit and predict and get an r2 score of 94.4 % with a root mean squared error of 11.1%.  Then, we plot the r2 score of train and test data with different values and check that the best max depth for test data is ten.           
         
![download](https://user-images.githubusercontent.com/53232113/219208025-bff89f6f-71ad-4a57-83e8-0aeecf192cfd.png)

Now, we find that  the most important features for the model are: 'engine size', 'year', 'model' and 'mileage'.

![download](https://user-images.githubusercontent.com/53232113/219208053-80964ece-1528-4913-92c1-bd35b9f5ef0a.png)

Now, we use all features to model with tree regression modeling. The features are:
['model','year','transmission','mileage','fuelType','tax','mpg','engineSize'], split train and test data, fit it with train data, predict and get an r2 score of 94.76 % with a root mean squared error of 10.87%.
Finally we create a dataframe X_new with the following steps:

First: get data X_new with three cars to predict prices:  model: yaris, years: 2022,2020,2012, transmision:     all  manual, mileage: 0,20000,200000,  fueltype all petrol, tax all 100, mpg: 60,50,40 and enginesize:         1.6,1.6 and 1.0. 

Second: predict prices out of the decision tree regression model above.
 
 Third: transform the predicted log prices to real prices with np.exp.
 
 Result:   The predicted price for first car( Yaris year 2022, with 0 mileage, enginesize 1.6) is 11114 pounds.
 
          The predicted price for second car(Yaris year 2020, with 20000 miles,enginesize 1.6) is 10322 pounds.
          
         The predicted price for third car(Yaris year 2012 with 200000 miles, enginesize 1.0) is 4741 pounds.
