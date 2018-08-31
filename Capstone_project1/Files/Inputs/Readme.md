# Summary of data description
The original data contain:
- Hot Pepper Gourmet (hpg): similar to Yelp, here users can search restaurants and also make a reservation online
- AirREGI / Restaurant Board (air): similar to Square, a reservation control and cash register system. 
Some of these files were biger than 25 M. So it was not possible to upload. 
Each file is prefaced with the source (either air_ or hpg_) to indicate its origin. Each restaurant has a unique air_store_id and hpg_store_id. These data files include 17 different features, explained following:

### air_reserve.csv
This file contains reservations made in the air system. Note that the reserve_datetime indicates the time when the reservation was created, whereas the visit_datetime is the time in the future where the visit will occur.

- air_store_id - the restaurant's id in the air system
- visit_datetime - the time of the reservation
- reserve_datetime - the time the reservation was made
 -reserve_visitors - the number of visitors for that reservation


### hpg_reserve.csv
This file contains reservations made in the hpg system.

- hpg_store_id - the restaurant's id in the hpg system
- visit_datetime - the time of the reservation
- reserve_datetime - the time the reservation was made
- reserve_visitors - the number of visitors for that reservation


### air_store_info.csv
This file contains information about select air restaurants. Column names and contents are self-explanatory.

- air_store_id
- air_genre_name
- air_area_name
- latitude
- longitude
Note: latitude and longitude are the latitude and longitude of the area to which the store belongs

### hpg_store_info.csv
This file contains information about select hpg restaurants. Column names and contents are self-explanatory.

- hpg_store_id
- hpg_genre_name
- hpg_area_name
- latitude
- longitude
Note: latitude and longitude are the latitude and longitude of the area to which the store belongs

### store_id_relation.csv
This file allows you to join select restaurants that have both the air and hpg system.

- hpg_store_id
- air_store_id
- air_visit_data.csv
This file contains historical visit data for the air restaurants.

### air_store_id
- visit_date - the date
- visitors - the number of visitors to the restaurant on the date

### date_info.csv
This file gives basic information about the calendar dates in the dataset.

- calendar_date
- day_of_week
- holiday_flg - is the day a holiday in Japan
