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

This data set contains store_id, date and time, genre, location and holiday whcih are categorical data. There are 517 unique dates, 4947 unique stores, 44 different genre and 186 different area name. Regarding large number of categorical features, the categorical data were converted to the numerical data by grouping visitors over hour,day,day of te week, month, ear, store, genre and the location. This method also generates extar information. These information can help to find the best feature for our model. The code can be found here: https://github.com/leilanorouzi/SpringBoard/blob/master/Capstone_project1/Codes/Restaurant_forcats_data_processing.ipynb

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
Using data of the day of the week, weekly distribution of the visits is shown in ![Day of week](https://github.com/leilanorouzi/SpringBoard/blob/master/Capstone_project1/Files/Outputs/Graphes/Data_visual/Weekday_hist.png)
This histogram indicates that most of visits were made of Friday and Saturday. This shows people like to go resturant if the day after of dining is weekend. 
### Hour of the visits
This graph presents that when people like to eat in restaurants. 
![Hour of visit](https://github.com/leilanorouzi/SpringBoard/blob/master/Capstone_project1/Files/Outputs/Graphes/Data_visual/Visiting_hour.png) 
This plot implys that people are eating out rather in the evenings not in at noons. 
### Time difference histogram
This graph shows the distribution of time difference between the time of reservation and the time that the reservation is made for, ie the visit time. 
![Time difference](https://github.com/leilanorouzi/SpringBoard/blob/master/Capstone_project1/Files/Outputs/Graphes/Data_visual/Time_difference_hist.png)
There is a frequent variation in the distribution. 
## Prediction model

### [Porphet model](https://github.com/leilanorouzi/SpringBoard/blob/master/Capstone_project1/Codes/Restaurant_forcats_forcast_prophet_model.ipynb)
Prophet model is a model for timeseries and can be apply to study the trend and variation of features over the time. A breif documentation can be found in https://facebook.github.io/prophet/docs/quick_start.html. 

Appying datetime data of visits into the model shows the trend , weekly and yearly variation of the average visits as foloowing:

![prophet model](https://github.com/leilanorouzi/SpringBoard/tree/master/Capstone_project1/Files/Outputs/Graphes/prophet_model/Mean_daily_customer_components.png)

The trend shows a slight increase in 2017. The weekly and yearly variations are similar what havef found in previus data visulaziation. 


### Calssification model
- link to the code: 
- Random forest model
- why random forest
## Results
### Error and accuracy
## Recommendations
### Weather data
### generating data
