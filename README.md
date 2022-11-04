# Supervised_Regression_Model
Sales Prediction and Model for Predicting sales of a major store chain Rossmann

Rossmann operates over 3,000 drug stores in 7 European countries. Currently, Rossmann store managers are tasked with predicting their daily sales for up to six weeks in advance. Store sales are influenced by many factors, including promotions, competition, school and state holidays, seasonality, and locality. With thousands of individual managers predicting sales based on their unique circumstances, the accuracy of results can be quite varied.

//PROBLEM DEFINITION:
The Rossmann store dataset consists of data about stores with respect to their features. We need to explore and analyze the data to discover key factors responsible for sales and come up with a supervised model that can predict the data for the next six weeks.
Data:
You are provided with historical sales data for 1,115 Rossmann stores. The task is to forecast the "Sales" column for the test set. Note that some stores in the dataset were temporarily closed for refurbishment.
Rossmann Stores Data.csv - historical data including Sales
store.csv - supplemental information about the stores!

Features:
Store - a unique Id for each store
Sales - the turnover for any given day (this is what you are predicting)
Customers - the number of customers on a given day
Open - an indicator for whether the store was open: 0 = closed, 1 = open
StateHoliday - indicates a state holiday. Normally all stores, with few exceptions, are closed on state holidays. Note that all schools are closed on public holidays and weekends. a = public holiday, b = Easter holiday, c = Christmas, 0 = None
SchoolHoliday - indicates if the (Store, Date) was affected by the closure of public schools
StoreType - differentiates between 4 different store models: a, b, c, d
Assortment - describes an assortment level: a = basic, b = extra, c = extended
CompetitionDistance - distance in meters to the nearest competitor store
CompetitionOpenSince[Month/Year] - gives the approximate year and month of the time the nearest competitor was opened
Promo - indicates whether a store is running a promo on that day
Promo2 - Promo2 is a continuing and consecutive promotion for some stores: 0 = store is not participating, 1 = store is participating
Promo2Since[Year/Week] - describes the year and calendar week when the store started participating in Promo2
PromoInterval - describes the consecutive intervals Promo2 is started, naming the months the promotion is started anew. E.g. "Feb,May,Aug,Nov" means each round starts in February, May, August, November of any given year for that store

Basic information of dataset on analysing:
There are two data sets rossmann stores data and store data.
In rossmann stores data : There are 7 numerical data and 2 object data
In store data: There are 7 numerical data and 3 object data
To make sense we concatinate/merged the data with respect to store features in both the dataset 
now we have 13 numerical data and 5 object data

wrangling of data : from the data we can see the null values in six features such as CompetitionDistance, CompetitionOpenSinceMonth, CompetitionOpenSinceYear, Promo2SinceWeek,  Promo2SinceYear, and PromoInterval
we added data to CompetitionDistance, CompetitionOpenSinceMonth, CompetitionOpenSinceYear based on median&mode since this kind of data never changes and the rest empty data filled with null value 

From the data set we can observe that date was in the yyyy-mm-dd format , we need to split the data with respect to day, month, quarter and year separate 
And from above dataset we replace few features with respect to numerical and converted object type to numerical type

\\basic EDA:\\
 Total no of days = 1017209 
 Number of shops/days OPEN = 844392 
 Number of shops/days CLOSED = 17281
 sales with respect to day of week: Day 5 145845, Day 4 145845, Day 3 145665, Day 2 145664, Day 1 144730, Day 7 144730, Day 6 144730
 distinct number of stores: 1115 
 maximum sales of stores: 1115 
 average sales of stores: 558.4297268309659 
 minimum sales of stores: 1 
 total sales of stores: 568039744
 
 Exploratory data analysis:
 From the dataset above, we can describe a few relationships between Rossmann sales of stores with different perspectives and scenarios.
 The sales at Rossmann are directly proportional to the distance between the other stores.
 Rossmann's sales are not directly proportional to promo or promo2, but they still provide us with a 10–30% increase in sales.



SUPERVISED MODEL

Steps to create a model
select dependent and independent features for model
check for linear distribution
check for multicollinearty
split the dataset into training data and test data with respect to (80:20)
Transform the data within range of 0-1 so that we can increase the model bit effiency, for this model we use min max scalar for transforming the dataset


Linear regression is an algorithm used to predict, or visualize, a relationship between two different features/variables
importing the linear regression from sklearn.metrics and 
executing model with respect to training and test data and calculating MSE(mean square error) for performance and R Square for model efficiency
Train performance: 1406.9155109794283 
Test performance: 1406.9155109794283 
R-square for predicted train: 0.8666563612894873 
R-square for test: 0.8672303384554428
![image](https://user-images.githubusercontent.com/104783155/200027709-644967c6-b8b8-4646-8096-8c6c4377f627.png)


Random Forest is a Supervised learning algorithm that is based on the ensemble learning method and many Decision Trees. Random Forest is a Bagging technique, so all calculations are run in parallel and there is no interaction between the Decision Trees when building them
importing the RandomForestRegressor from sklearn.metrics and 
executing model with respect to training and test data and calculating MSE(mean square error) for performance and R Square for model efficiency
Train performance: 172.47376478810307 
Test performance: 172.47376478810307 
R-square for predicted train: 0.9979960708932786 
R-square for test: 0.9857699037693892
![image](https://user-images.githubusercontent.com/104783155/200027747-3c869c39-fcb0-455d-8d8b-2c8b52035110.png)


From both the models, we can see that the linear model predicts 86%, whereas the random forest regressor predicts 98.5%. From this, we can conclude that the random forest has a higher efficiency than the linear model.
