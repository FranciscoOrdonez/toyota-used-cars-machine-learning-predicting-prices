# toyota-used-cars-machine-learning-predicting-prices

A Toyota used cars dealer in England has been decreasing their sales in the last months.  Also, the dealer has been contracting junior salesman.  The manager thinks that the reason for decreasing sales is the lack of knowledge in used cars prices by the junior salesman.  The manager wants to have a   fast and reliable system to predict prices correctly for the Junior Salesman that can help them give the clients the correct price of the used cars. The manager has delivered data from the business with sales of Toyota used cars with year of fabrication,  different models, mileage, fuel type, transmission, engine size, tax and price.  He asks, with this data can you predict prices correctly to give the junior salesmen a reliable reference?
Here we are going to show a machine learning model for this business  that solves in a great percentaje the problem.
For that, there is a data validation, and exploratory analysis of the data.  Then, there is an analysis of the best of four machine learning models to use to predict the best reliable and correct price of used cars.  Finally,  the conclusion is that the reliable predictive price for used cars is possible. This  will help junior salespeople predict prices correctly,  building  their confidence to not lose clients   and  generate more sales in the future.

DATA VALIDATION

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


EXPLORATORY ANALYSIS

TARGET VARIABLE: PRICE... We analyze price and change to log scale. The mean price for a car is 12522 pounds, and the price converted to a log number is 9.32. We will be using the log price for the machine learning models.

![download](https://user-images.githubusercontent.com/53232113/219167241-e3c7bb2f-064a-4340-b01a-6e7884cc2674.png)

![download](https://user-images.githubusercontent.com/53232113/219168418-164b5aeb-e057-4c77-9916-066ec727f88f.png)

We see that there is a negative correlation with mileage(-0.39), and positive correlation with year(0.55). There is no correlation with mpg. , analyzed by boxplot graphs, there is a wider distribution on model GT86, RAV4 and Avensis, and a narrow distribution on Corollas, CH_r and Prius. On, transmision types, there is a wider distribution on Automatic and narrow on Manual, On fuel type, there is a narrow distribution on Petrol fuel.
![download](https://user-images.githubusercontent.com/53232113/219169324-27ab7071-0de7-4225-b51f-ba08237f4e95.png)

In relation to year of manufacturing, most cars in the set have been manufactured in 2017 and above. With category data, most cars in the data are model Yaris or Aygo with manual transmission, with Petro fuel and 1.0 engine size. In data distribution by models
![download](https://user-images.githubusercontent.com/53232113/219169364-3531a9b4-391e-4271-8c52-f8f4dd66db4a.png)
![download](https://user-images.githubusercontent.com/53232113/219169405-dd5934b4-68de-4f1e-a1ad-31facc9529b9.png)
![download](https://user-images.githubusercontent.com/53232113/219169451-c2be0cd0-8194-44ef-94c3-da313b72380a.png)
![download](https://user-images.githubusercontent.com/53232113/219169489-1a1d1eca-0d55-42f8-976b-bbd90bd99779.png)
