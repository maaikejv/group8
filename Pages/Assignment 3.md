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



---
Go to Assignment 1: [Water]({{site.baseurl}}/assignment-1)  
Go to Assignment 2: [Energy]({{site.baseurl}}/assignment-2)  
Go to Assignment 4: [Transport]({{site.baseurl}}/assignment-4)

