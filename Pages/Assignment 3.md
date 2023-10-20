---
layout: page
title: Assignment 3 Housing
permalink: /assignment-3
nav_order: 4
---
<img src="pexels-liene-ratniece-1329510.jpg" alt="Description of the image">

## Housing and the Amsterdam Paralympics  
Amsterdam is expecting 30.000 tourists during the Amsterdam Paralympics. All these visitors need a place to sleep. In this assignment we will dive into the AirBnB data to provide the municipality of Amsterdam with a bit of insight in the number of tourists the city is possible to accommodate in AirBnB apartments during the Amsterdam Paralympics. 

### Conclusions and recommendations  
The following results are useful to gain a bit of insight into the number of tourists who will possibly make use of AirBnB during the event. 

* Amsterdam can earn between €2.672.143 and €3.152.784 out of tourism tax.  
* The number of AirBnbs varies a lot for different neighborhoods. Neighborhoods close to the city center like De Baarsjes – Oud-West, Centrum-West, De Pijp – Rivierenbuurt and Centrum-Oost have the most Airbnbs. Neighborhoods further away from the city center have the very least number of Airbnbs.  
* The street with the most Airbnbs is the Nassaukade with 16 apartments.  
* Additional data research is needed to determine which number of AirBnB apartments are not rented out all the time but are also used as normal housing.  
* Next to all the 8.386 Airbnb apartments in Amsterdam where 16.772 tourists can sleep, an additional number of 6.614 hotel rooms is needed to ensure the remaining visitors of a place to sleep.  
* 7288 different licenses are used for the AirBnBs in Amsterdam. 

### Information

**Potential earnings from tourist tax during the Amsterdam Paralympics**  
<img src = "Toeristenbelasting.png" alt = "Toeristenbelasting">

According to the municipality of Amsterdam the tourist tax in Amsterdam is a combination of a percentage of the price of the overnight stay plus a fixed price per night.

```
import pandas as pd

with open ("C:/Users/maaik/Documents/UNI/MSc MADE/Metropolitan Data/Assignments/Housing data/listings.csv", 'r') as ams_csv: 
    bnb_df = pd.read_csv(ams_csv) 

rows = bnb_df['price'].size
total_price = bnb_df['price'].sum()
average = total_price / rows

mean = bnb_df['price'].mean()
median = bnb_df['price'].median()
print(mean, median)
```
Out of the data of the AirBnBs in Amsterdam, the average price of a one night stay is calculated. This is €254,48. This does not include the hotels in the Amsterdam. For AirBnB the tax percentage is 10% (overig). For this category there is no fixed price added. 

Per room per night  
= 254,48 * 0,1  
= 25,45 

There are 30.000 visitors, and we assume that every AirBnB will be shared by two people 
= 25,45 * (30000 / 2)  
= 381.734,80 

The event lasts a week, so they will stay 7 nights 
= 381750 * 7  
= 2.672.143,57 

Tax per person per night is €25,45 
Tax for all 30.000 visitors per night is €381734,80 
Total amount of tourist tax Amsterdam will earn from the paralympics is €2672143,57 

Amsterdam will earn €2.672.143,57 out of the tourism tax if all the visitors stay in AirBnBs. 

However, we are also providing a different calculation of a flat tax rate. According to several sources including Reuters and LonelyPlanet, Amsterdam is planning to change the tourist tax for accommodation to a flat 12.5%. We took the Statista average price for one night of accommodation in Amsterdam in June 2023 to be €295.  

Per person per night  
= 295 * 0,125  
= 36,88 

For all 30.000 visitors   
= 36,88 * (30000 / 2)  
= 553.125 

The event lasts a week, so they will stay 7 nights  
= 553.125 * 7  
= 3.152.784 

According to this calculation, Amsterdam will earn €3.152.784 out of tourism tax.  


**Number of AirBnBs per neighbourhood in Amsterdam**  
<img src = "AirBnBs.png" alt = "AirBnBs">

The following code is used to create the graph above:
```
import pandas as pd 
import matplotlib.pyplot as plt 

with open ("C:/Users/maaik/Documents/UNI/MSc MADE/Metropolitan Data/Assignments/Housing data/listings.csv", 'r') as ams_csv: 
    ams_df = pd.read_csv(ams_csv) 

plt.ylabel('number of AirBnBs') 
plt.xlabel('neighbourhood') 
plt.title('number of AirBnBs per neighbourhood in Amsterdam') 

ams_df['neighbourhood'].value_counts().plot (kind='bar',color='r')
```

**The street with the most AirBnB apartments**

1. Convert latitude and longitude coordinates into streets with geolocator.  
2. Add the streets of each index to a new column at the end of the row  
3. Value_counts the column with streets in a histogram to see which one occurs the most 

For this exercise, the first 400 adresses (out of more than 8000 in the file) are looked at. 

```
import pandas as pd
from geopy.geocoders import Nominatim


geolocator = Nominatim(user_agent="geo_locator")
ams_df = ams_df.head(10)

# Function to get street address from latitude and longitude
def get_street_address(row):
    location = geolocator.reverse((row['latitude'], row['longitude']), language='en', exactly_one=True)
    if location:
        print(location.raw)
        return location.raw['address']['road']
    else:
        return "Unknown Street"

# Apply the function to the DataFrame and create a new column 'Street'
ams_df['street'] = ams_df.apply(get_street_address, axis=1)

# print(ams_df)

# Count the occurrences of each street to find the street with the most Airbnb apartments
most_common_street = ams_df['street'].mode().iloc[0]

# Count the number of apartments on the most common street
apartment_count = ams_df[ams_df['street'] == most_common_street].shape[0]

print(f"The street in Amsterdam with the most Airbnb apartments is '{most_common_street}' with {apartment_count} apartments.")
```
Go to Assignment 1: [Water]({{site.baseurl}}/assignment-1)  
Go to Assignment 2: [Energy]({{site.baseurl}}/assignment-2)  
Go to Assignment 4: [Transport]({{site.baseurl}}/assignment-4)

