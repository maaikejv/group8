---
layout: page
title: Assignment 1 Water
permalink: /assignment-1
nav_order: 2
---

<img src="ethan-hu-gP2PNn1fCiU-unsplash.jpg" alt="Amsterdam canals">

## Water and the Amsterdam Paralympics
Many requirements are important to include in the Amsterdam Paralympics' organization. Among other things, the event cannot have an impact on commercial water transport and a minimum impact on canal boats’ routes. In addition, it is crucial to get an idea of the pollution level of the canals. On this page, we will research whether there is sufficient data available to ensure the feasibility of the Amsterdam Paralympics from an environmental and safety perspective.  

### Conclusions
Based on our research, not all canals are consistently monitored, so data available is limited. According to the Water Framework Directive (Rijksoverheid, 2023) report on monitoring surface water from 2020, the water quality is either inadequate or poor in a significant number of the canals, in 2019 [dataset 5: (Gemeente Amsterdam, 2021)]. Further information is required to understand whether safe routes of 5km can be planned for an open swim event which should have no impact on commercial shipping and little impact on the canal traffic overall. A limited set of data also shows that swimming in the canals increases the risk of acute gastrointestinal illness [dataset 2: (Hintaran et al., 2018)].  

Water quality measurements should be taken 48 hours prior to the event, to make sure adequate advice can be given on the health risks taken by the participants. Next to that, the water temperature should be measured in the middle of the course two hours prior to the event to make sure it is sufficient for the event to take place.  

### Useful data
We decided that the following information will be useful to draw-up an advice for the municipality of Amsterdam on the feasibility of the Paralympics from the perspective of the safety of the partaking athletes from an environmental perspective: 
* Water quality and ecological conditions - pollution levels  
* Medical data sets - to identify any specific health concerns 
* Commercial routes (for all water transport types) 
* Weather and Climate Data- historical weather data for Amsterdam in May to assess the climate conditions and potential risks, such as extreme temperatures or storms. 
* Sewage system overflow data 
* Previous Event Reports- reports and lessons learned from previous open water swimming events in Amsterdam.  

According to the Open water swimming guid of Fina (2022), there are a number of factors that need to be considered and documented before an area of open water is used for an event. These factors depend on whether a sea, lake or river swim is being considered.  
* Access, condition, sufficient space and proximity of start and finish points  
* Likely water temperature (set event minimum and maximum temperature)  
* Currents or eddies  
* Water quality  
* Hidden, overhanging or underwater hazards  
* Other water users  
* Minimum depth of not less than 1.40 m. at any point, including start and finish  
* Conditions underfoot at start and exit  
* Sites for medical evacuation along the course

### Functional datasets 
The following datasets provide the data needed to draw up the advice:  

**1. Historical weather data for Amsterdam, Netherlands (Visual Crossing Corporation, 2023)**  
To understand the weather patterns in Amsterdam in the month of May and assess if they are suitable for the event, we looked at the Visual Crossing weather query builder and retrieved minimum and maximum temperature, feels like temperature, precipitation, dew, humidity data for Amsterdam over the last 10 years from May 01-May 31. 

**2. Infection risks of city canal swimming events in the Netherlands in 2016 / Dataset of Utrecht SingelSwim and Amsterdam City Swim (Hintaran et al., 2018)**  
Looking for information and the health risks associated to swimming in the canals in Amsterdam, we learned that the Public Health Service (PHS) investigated two city canal swimming events in 2015 and another report from 2016 tried to determine the risks of infection during two urban swimming events, the Utrecht Singel Swim 2016 (USS) and the Amsterdam City Swim 2016 (ACS). This last report contains useful information related to 1579 participants in ACS, from age, weight, food and drinks consumption during the event, health symptoms, swimming patterns and so on. The report concluded based on this data that participants of events in urban canals in the Netherlands could be at a higher risk for acute gastrointestinal illness than those not participating.  

**3. Grachtenmonitor 2022 (Gemeente Amsterdam, 2022a)**  
The Grachtenmonitor 2022 report provides useful data about sailing movements on the canals of Amsterdam, broken down into pleasure and recreational shipping, passenger shipping and water transport. The report contains information about which times and which days it is busy in which places. This is useful when determining a date, time and place for the swimming competition, because it allows you to plan a moment and route that will interfere with the fewest boats. The data is mostly provided in tables and figures. To make the data workable, it should be put into excel files so that it can be used with pandas in python.  

**4. Water in kaart: Water clarity, oxygen concentration, salinity (Waterschap AGV, 2023)**  
Waternet offers information about clean water in Amsterdam, in the form of a thematic map which shows the water clarity, salinity and oxygen concentration levels. This information can be used to analyze whether swimming in certain areas is advisable or not. 

**5. Amsterdam measurement results surface water quality research, 2019 (Gemeente Amsterdam, 2021)**  
The report covers only Amsterdam surface waters and canals are not measured. The results of the surface water quality survey measurement from 2019 do offer useful information about levels of oxygen, phosphorus, nitrogen, chloride, temperature, transparency, saturation, which can be used to map possible safe swimming routes for the event. Although it does not directly measure the canals, some of the water surfaces are connected so they do influence the canal water quality. 

**6. Maps commercial and private boat routes (Gemeente Amsterdan, n.d.)**  
This dataset shows geospatial data where the docks for passenger vessels (large/medium/small/unmanned/pedal boats) as well as the boarding and disembarking locations for commercial shipping are shown. These can be used to design a swimming route on the canals which has no impact on commercial shipping and limited impact on private boats.  

**7. Intensity of boat traffic on a certain point in the Amsterdam canals (Mobycon, 2022)**  
Another dataset with geospatial data where the actual Amsterdam canals water traffic takes place, including moving direction on the water and number of vessels. Combined with the previous dataset, this can be used to better understand where the swimming should take place to have the least impact on the ongoing canal traffic.  

**8. Sewage system of Waternet, with f.e. depth underneath ground, building year (Gemeente Amsterdam, 2022b)**  
This dataset with geospatial data shows where the sewage system of Waternet is situated in Amsterdam. By clicking on a line in a GIS programme the information of the sewage system segment will be visible. In a GIS programme (f.i. QGIS) it is possible to select a few segments of the sewage system and export the data to a CSV. With this data it is possible to see where the sewage system is close to the canals and where it is close to the surface and thus most likely to overflow in case of heavy rainfall. Unfortunately, we were not able to find data containing at what points the sewage system has overflown in the past years. 

**9. Waterway Network Data Service - Navigability (Rijkswaterstaat, 2023)**  
This WMS file shows the navigability of the waterway network in the Netherlands. In Amsterdam it shows which canals cannot be used by large boats, therefore the swimming event would have less impact on ongoing traffic in these canals. It does not include commercial canal boats, which need to be taken into account as well. 

### Specification of the data 
The table below provides more information about the type of data the aforementioned datasets contain. 

| # | Data format | Is it human readable? (Y/N) | Is it numerical? | Which python data library could read it? | Is it geodata? (Y/N) | Is it temporal? (interval) |
| :--------: | :--------: | :--------: | :--------: | :--------: | :--------: | :--------: 
| 1 | JSON, CSV, XLS | Y | Y | Pandas | N | 01.05-31.05 2013-2023 |
| 2 | XLS | Y | Partly | Pandas | N | N |
| 3 | Report | Y | Partly | Pandas (after putting in excel | N | Oct 2021 - Oct 2022 |
| 4 | Spatial data / thematic map | Y | Partly | GeoPandas or GDAL/OGR* | Y: points | N |
| 5 | XLS | Y | Partly | Pandas | N | N |
| 6 | Spatial data / thematic map | N | Partly | GeoPandas or GDAL/OGR* | Y: points | N |
| 7 | Geodata | N | N | GeoPandas or GDAL/OGR* | Y: points | N |
| 8 | WFS, GEOJSON & CSV (XML/RDF) | N | N | GeoPandas or GDAL/OGR* | Y: points and lines | N |
| 9 | WMS | Y | N | GeoPandas or GDAL/OGR* | Y: lines | N|

*The GIS-data is readable with the use of for instance QGIS. Within this program the points in the researched area can be selected and extracted into a CSV file. This CSV file can then be read like other CSV files above. 

### Datasets/references
Fina. (2022). Open Water Swimming Guide - 2022 edition. In World Aquatics. Fédération Internationale de Natation. Retrieved September 27, 2023, from https://resources.fina.org/fina/document/2022/03/14/357ae477-02a3-44ad-bdf6-0668c3fc7d39/OWS-Guide_2022_Final.pdf 

Gemeente Amsterdam. (n.d.). Data en informatie. Data.Amsterdam. Retrieved October 4, 2023, from https://data.amsterdam.nl/data/?center=52.3731295%2C4.8933141&legenda=true&modus=kaart  

Gemeente Amsterdam. (2021, November 9). Water in Amsterdam: Meetresultaten kwaliteitsonderzoek oppervlaktewater, 2019. Data.Amsterdam. Retrieved October 4, 2023, from https://data.amsterdam.nl/datasets/lAqjIsj-_a7psg/water-in-amsterdam/ 

Gemeente Amsterdam. (2022a, October 1). Grachtenmonitor 2022. Openresearch.Amsterdam. Retrieved September 27, 2023, from https://openresearch.amsterdam/nl/page/92981/grachtenmonitor-2022 

Gemeente Amsterdam. (2022b, November 25). Rioolnetwerk Waternet. overheid.nl. Retrieved September 27, 2023, from https://data.overheid.nl/dataset/xnhveaeyheww2w 

Hintaran, A. D., Kliffen, S. J., Lodder, W. J., Pijnacker, R., Brandwagt, D., Van Der Bij, A. K., Siedenburg, E., Sonder, G. J., Fanoy, E., & Joosten, R. (2018). Infection risks of city canal swimming events in the Netherlands in 2016. PLOS ONE, 13(7), e0200616. https://doi.org/10.1371/journal.pone.0200616 

Mobycon. (2022, September 2). Herhalingsonderzoek gebruik Amsterdams binnenwater aug 2022. Openresearch.Amsterdam. Retrieved September 27, 2023, from https://openresearch.amsterdam/nl/page/92983/herhalingsonderzoek-gebruik-amsterdams-binnenwater-aug-2022 

Rijksoverheid. (2023). Kaderrichtlijn Water. Rijksoverheid. Retrieved October 4, 2023, from https://www.helpdeskwater.nl/onderwerpen/wetgeving-beleid/kaderrichtlijn-water/  

Rijkswaterstaat. (2023, March 1). Dataset: Vaarweg Netwerk Data Service - bevaarbaarheid. Pdok. Retrieved October 4, 2023, from https://www.pdok.nl/ogc-webservices/-/article/vaarweg-informatie-nederland-vin- 

Visual Crossing Corporation. (2023, October 4). Historical weather data for Amsterdam, Netherlands. Visual Crossing. Retrieved October 4, 2023, from https://www.visualcrossing.com/weather-history/Amsterdam,Netherlands/met%20ric/monthtodate 

Waterschap AGV. (2023, September 27). Water in kaart. Waterschap Amstel, Gooi En Vecht. Retrieved September 27, 2023, from https://www.agv.nl/onze-taken/schoon-water/waterkwaliteit/ 

---
Go to Assignment 2: [Energy]({{site.baseurl}}/assignment-2)  
Go to Assignment 3: [Housing]({{site.baseurl}}/assignment-3)  
Go to Assignment 4: [Transport]({{site.baseurl}}/assignment-4)


