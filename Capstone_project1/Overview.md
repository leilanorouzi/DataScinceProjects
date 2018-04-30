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

|       File name       |   Size   |            Description           |
|:---------------------:|:--------:|:--------------------------------:|
| air_reserve.csv       | 5.8 MB   | Reservation data in Air system   |
| air_store_info.csv    | 74 KB    | Air restaurants information      |
| air_visit_data.csv    | 8.8 MB   | Visit information in air ayatem  |
| hpg_reserve.csv       | 126.2 MB | Reservation data in hpg system   |
| hpg_store_info.csv    | 479 KB   | Hpg restaurants information      |
| store_id_relation.csv | 6 KB     | Visit information in  hpg system |
| date_info.csv         | 11 KB    | Information about the date       |
## Data wrangling
- size of files
- extracing data instead of dealing with categorical data
- generating more features
### Merging data
- air data and hpg data using air and hpg store_id_relation
### Extacting more data
- year
- month
- day
### missing data
- in hpg data
## Data processing
### Visulazation the data
- link to graphs : https://github.com/leilanorouzi/SpringBoard/tree/master/Capstone_project1/Files/Outputs/Graphes
### Categorical data
- changing categorical data to numerical data
- why numerical data
#### resturant locations on the map
- using google map
#### histograms
- daily
- weakly
- monthly
- holiday
- area
- genre
- stores
## Prediction model
- why we have two models
### Porphet model
- link to the code: 
- gives general tred of all reservation over the time in all resturant
- Seasonal, monthly, weekly, daily variation
### Calssification model
- link to the code: 
- Random forest model
- why random forest
## Results
### Error and accuracy
## Recommendations
### Weather data
### generating data
