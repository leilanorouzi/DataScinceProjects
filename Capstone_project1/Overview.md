# Project predict customer of resturant 
This project is about predicting the number of customer in Japan in each restaurant every day. This project can help businesses to forcat how many visitors they are going to have in future. There for they can manage the resources like how many people they may need to run their restaurant and serve the customers and how much material they need. 


Data are collected from reservation websites and include date and time of reservation and the number of people. Also, there are some information about the restaurant such as location and the type of the restaurant. 
Other information like the capacity of the restaurant, the rate of restaurant,  other non-online reservation, like over the phone reservation or total number of customer in each day is not provided.


This project is based on [RRVF](https://www.kaggle.com/c/recruit-restaurant-visitor-forecasting) kaggle competition. 
- Content of the project on github:
  - [Code folder](https://github.com/leilanorouzi/SpringBoard/tree/master/Capstone_project1/Codes): contains codes of data processing, data visulaziation and forcasting models.
  - [Files folder](https://github.com/leilanorouzi/SpringBoard/tree/master/Capstone_project1/Files): This folder contains [input files](https://github.com/leilanorouzi/SpringBoard/tree/master/Capstone_project1/Files/Inputs) and  [output files](https://github.com/leilanorouzi/SpringBoard/tree/master/Capstone_project1/Files/Outputs). This folder includes graphes, pictures and histograms of two models.
## Data
Recruit Holdings has unique access to key datasets that could make automated future customer prediction possible. Specifically, Recruit Holdings owns Hot Pepper Gourmet (a restaurant review service), AirREGI (a restaurant point of sales service), and Restaurant Board (reservation log management software).
Data are avaible on https://www.kaggle.com/c/recruit-restaurant-visitor-forecasting/data. There are some informatin about the data files following:

|       File name       | Size of file |            Description           | Size of data (Row × Col) |
|:---------------------:|:------------:|:--------------------------------:|:-----------------------------:|
| air_reserve.csv       | 5.8 MB       | Reservation data in Air system   |  92378 × 4               |
| air_store_info.csv    | 74 KB        | Air restaurants information      | 829 × 5                  |
| air_visit_data.csv    | 8.8 MB       | Visit information in air ayatem  | 252108 × 3               |
| hpg_reserve.csv       | 126.2 MB     | Reservation data in hpg system   | 2000320 × 4              |
| hpg_store_info.csv    | 479 KB       | Hpg restaurants information      | 4690 × 5                 |
| store_id_relation.csv | 6 KB         | Visit information in  hpg system | 150 × 2                  |
| date_info.csv         | 11 KB        | Information about the date       | 517 × 3                  |

More information about those data files is presentes  in [readme.md](https://github.com/leilanorouzi/SpringBoard/blob/master/Capstone_project1/Files/Inputs/Readme.md) file.

## Data wrangling and visualization
Two data set of store information, reservation data and visit data from each air and hpg data sytems were merge together to provide a whole data sets for each system. The missing values were deleted . Then both data system were combined using relation information of retaurants to generate our main data set. However, there were not the relation information for some of the entries. 

This data set contains store_id, date and time, genre, location and holiday whcih are categorical data. There are 517 unique dates, 4947 unique stores, 44 different genre and 186 different area name. There were no missing data. However, this project confronting few problems. One of them is the is no ranking or rating information for resturant. Another issue is high number of categorical varibles. Also, there is not equal number of entries, or observations, for every restaurant. There is only one entry for some resturants whereas there are lots of entries for others. This could happend if some resturants are taking reservation more by phone rather than via websites, or they are more likely to be fast-food type of stores. 


The data include datatime type for reservarton and visiting. The year, month, day, day of the week, time and time difference between reservation and visit calculated. 
Then regarding large number of categorical features, the categorical data were converted to the numerical data by grouping visitors over hour,day,day of te week, month, year, store, genre and the location. This method also generates extar information.  The code can be found here: https://github.com/leilanorouzi/SpringBoard/blob/master/Capstone_project1/Codes/Restaurant_forcats_data_processing.ipynb
These information can help to find the best feature for our model and finding a solution to identify how favorable there retaurants are for public, please see "Extracting new data" section.


There are an extensive data visulazation in output directory, https://github.com/leilanorouzi/SpringBoard/tree/master/Capstone_project1/Files/Outputs/Graphes.  The [visulazation code](https://github.com/leilanorouzi/SpringBoard/blob/master/Capstone_project1/Codes/Restaurant_forcats_features_visual.ipynb) can be found inthe code directory. 

Some of the results are given following:

### Location
The location of the restaurants were plotted using google map in html format. Here is the location of restaurants in Tokyo.
![Tokyo Restaurant](https://github.com/leilanorouzi/SpringBoard/blob/master/Capstone_project1/Files/Outputs/Graphes/Data_visual/Tokyo_restaurants.png)

Other data were plotted too. 
### People in reservation
The distribution of the number of people in every reservation has been plotted. 
![People in reservation](https://github.com/leilanorouzi/SpringBoard/blob/master/Capstone_project1/Files/Outputs/Graphes/Data_visual/Visitor_hist.png)
This graph shows most of reservation was made for couples as 342459 reservation was for two people. 
### Day of month
Another graph shows people go to restaurant in which day. The distribution of the day  of visit is shown in 
![Day of week](https://github.com/leilanorouzi/SpringBoard/blob/master/Capstone_project1/Files/Outputs/Graphes/Data_visual/Visit_day_hist.png)
The plot shows no prefence in days of month. 
### The monthly distribution
To investigate the which month people are intent to resrve a table, the distribution of monthly reservation is shown in here:
![Montly distribution](https://github.com/leilanorouzi/SpringBoard/blob/master/Capstone_project1/Files/Outputs/Graphes/Data_visual/Visit_month_hist.png)
The result shows people love to dine out in pre-new-year time in December and in spring festivals in March. However people are going to go to restaurant less in summer and fall seasons.
### Day of the week
Using data of the day of the week, weekly distribution of the visits is shown in ![Day of week](https://github.com/leilanorouzi/SpringBoard/blob/master/Capstone_project1/Files/Outputs/Graphes/Data_visual/Weekday_hist_.png)
This histogram indicates that most of visits were made of Friday and Saturday. This shows people like to go resturant if the day after of dining is weekend. 
### Hour of the visits
This graph presents that when people like to eat in restaurants. 
![Hour of visit](https://github.com/leilanorouzi/SpringBoard/blob/master/Capstone_project1/Files/Outputs/Graphes/Data_visual/Visiting_hour.png) 
This plot implys that people are eating out rather in the evenings not in at noons. 
### Time difference histogram
This graph shows the distribution of time difference between the time of reservation and the time that the reservation is made for, ie the visit time. 
![Time difference](https://github.com/leilanorouzi/SpringBoard/blob/master/Capstone_project1/Files/Outputs/Graphes/Data_visual/Time_difference_hist.png)
There is a frequent variation in the distribution. 
### Data visualazation using [Porphet model](https://github.com/leilanorouzi/SpringBoard/blob/master/Capstone_project1/Codes/Restaurant_forcats_forcast_prophet_model.ipynb)
Prophet model is a model for timeseries and can be apply to study the trend and variation of features over the time. A breif documentation can be found in https://facebook.github.io/prophet/docs/quick_start.html. 

Appying datetime data of visits into the model shows the trend , weekly and yearly variation of the average visits as foloowing:
![prophet model](https://github.com/leilanorouzi/SpringBoard/tree/master/Capstone_project1/Files/Outputs/Graphes/prophet_model/Mean_daily_customer_components.png)

The trend shows a slight increase in 2017. The weekly and yearly variations are similar what havef found in previus data visulaziation. 

### Extracting new data
The project contains lots of categorical data.  In this case, I have the genre of the resturant, day of the week, the name of the restaurant location, holiday, date, and etc. One approach is encoding them. To do that, they can be converted to a big set of ones and zeros (hot-encoding). This method may be problematic since the number of the categorical features is high. The other solution can be the extraction of some information from those categorical data. 

Here, the rate of restaurants, or reviews one may say, or the rank of restaurants have not been given. Hence, I  attempted to see how much each variable is affecting the popularity of a restaurant. The intuition of generating these factors has come from the histogram of the number of reservation on the day of the week and in the month. 
As histogram of weekly distribution shows, for example on Friday and Saturday people intent to go restaurant more, rather than other days of the week. Or people like to dine out more before New Year or during Nature celebration in March. 
one the other hand, the restaurant itself something like the quality of the food and the service of the restaurant represent the quality and popularity of the restaurant too. In the same way,  the popularity of locations and neighborhoods can play the same role in the popularity of the restaurant.

To do so, I used histograms information on the distribution of visitors with respect to different variables. Then I have introduced new factors as the ration of each hight of the bar to the maximum height of bars as (hight_bar/Max(hight_bar).
These new variables of a restaurant may represent the quality and popularity of the restaurant.

Another variable I was thinking of was the capacity of the restaurant, which again it has not be given initially. 10 customers for a restaurant can be a fully booked reservation, while for some other, it is only a fraction of the total number of customers they can take in at any time. So, the best way to estimate this variable was to calculate the maximum number of people can be taken in an hour for every restaurant. I call them weighted factors. 

The code of this part can be found in ![predicting model code] https://github.com/leilanorouzi/SpringBoard/blob/master/Capstone_project1/Codes/MultiRegression_model_RRVF.ipynb.

### Data selection
Now, having all possible variables of the project, the most related variables should be selected to use for the model. The time appeared to be irrelevant for the model. I have tried two methods, correlation between variables and feature selection from random forest method.  The calculation showed that time difference between reservation and visit, the capacity of the restaurant, the date are most correlated independent variable to the number of visitors. 
In the end, these features have been selected as the input of predicting model: genre name, area name, day, month, year, day of the week, time difference, capacity, weighted factors of holiday, day, day of the week, year, store, genre, and finally area. 
### Input of the model
The categorical features, genre name, area name, day, month, year and day of the week, were encoded. 
These features along with other which mentioned above were taken as independent variables and the number of visitors at the time of visiting selected as the dependent variable. 
Then these data were split into train and test datasets.

## Prediction models
One of the problem in this project was the unequal number of observations for different restaurants. That makes it harder to have an accurate prediction. Moreover, forecasting the number of visitors to a restaurant is highly depends on the popularity of the store. This suggests that we need some sort of clustering method to find similarity between restaurants and entries. 
On the other hand, the number of visitors can be considered a function of those weighted factors and categorical features. Therefore, we need a regression model to predict the number of visitors. 
All things considered, acombined model was developed using ![StackingRegressor]
https://rasbt.github.io/mlxtend/user_guide/regressor/StackingRegressor/. In this approach a random forest regression, regression based on k-nearest neighbors (KNeighborsRegressor) and Extreme Gradient Boosting (XGBRegressor) models were put together. 

## Results and Error and accuracy

Each model result very poor r2 coeffient individually:

  - Random forest regression: r2=0.242
  - XGBoost: r2=0.1965
  - KNeighborsRegressor: r2= 0.2816

The error has reduced by using the combined models. It results much better r2 of 0.7814 and a root mean logarithmic error of 0.43907 which is less than scores in Kaggle competition. Please check at the bottom of the page.

## Recommendations
To improve the prediction, we may need more information from the restaurant such as restaurant rating, The population of the area, the capacity of the store and more observation. Some people have added the weather information to their model. However, it can be a very short time forecast due to only a 10-day accurate weather forecast can be provided by the meteorological institutes. 
