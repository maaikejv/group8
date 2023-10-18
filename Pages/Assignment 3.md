---
layout: page
title: Assignment 3 Housing
permalink: /assignment-3
nav_order: 4
---
<img src="pexels-liene-ratniece-1329510.jpg" alt="Description of the image">

## Housing and the Amsterdam Paralympics
This assignment...

## Conclusions
Based on our research, not all canals are consistently monitored, so data available is limited. According to the Water Framework Directive (KRW) report on monitoring surface water from 2020, the water quality is either inadequate or poor in a significant number of the canals, in 2019 [dataset 5: (Gemeente Amsterdam, 2021)]. Further information is required to understand whether safe routes of 5km can be planned for an open swim event which should have no impact on commercial shipping and little impact on the canal traffic overall. A limited set of data also shows that swimming in the canals increases the risk of acute gastrointestinal illness [dataset 2: (Hintaran et al., 2018)].  

Water quality measurements should be taken 48 hours prior to the event, to make sure adequate advice can be given on the health risks taken by the participants. Next to that, the water temperature should be measured in the middle of the course two hours prior to the event to make sure it is sufficient for the event to take place. 

## Useful data


## question 1: 

    <pre><code class=”python”> 
import pandas as pd

with open ("C:/Users/maaik/Documents/UNI/MSc MADE/Metropolitan Data/Assignments/Housing data/listings.csv", 'r') as ams_csv: 
    bnb_df = pd.read_csv(ams_csv) 

rows = bnb_df['price'].size
total_price = bnb_df['price'].sum()
average = total_price / rows

mean = bnb_df['price'].mean()
median = bnb_df['price'].median()
print(mean, median)
    </code></pre>
---
Go to Assignment 1: [Water]({{site.baseurl}}/assignment-1)
Go to Assignment 2: [Energy]({{site.baseurl}}/assignment-2)
Go to Assignment 4: [Transport]({{site.baseurl}}/assignment-4)
