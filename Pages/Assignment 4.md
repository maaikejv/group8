---
layout: page
title: Assignment 4 Transport
permalink: /assignment-4
nav_order: 5
---

<img src="stijn-4fQAMZNaGUo-unsplash.jpg" alt="Public transport Amsterdam">

## Transport and the Amsterdam Paralympics  
On this page, we propose a suitable start point, finish point and route for the canal smimming event in Amsterdam. The route will be 5km and also a suitable, central location for the Event Headquarters will be determined. Available and suitable tram and bus connections for the visitors are mapped. Finally, it is found that there are 313 cafes and restaurants nearby for visitors. Below you will find all findings mapped out.

### Data used
With the following link, you can download the file we used for this assignment  
<a href="files/TRAMMETRO_PUNTEN_2022.csv" download="TRAMMETRO_PUNTEN_2022.csv">Download CSV Trams and Metro's Amsterdam</a>

### The route decision making  
With the planning of the swimming event, several crucial factors shaped our choice of route. We delved into several datasets, of which the following decided the route for the biggest part: 
* The waterways must be on, or cross the smallest number of canals which are used for commercial purposes (dataset 9, assignment 1). 
* There must be limitated parking spots and loading and unloading of goods and passenger boats along the route (dataset 6, assignment 1). 
* The assessment of water quality in the surface water adjacent to canals, relying on proven measurements from our datasets (dataset 5, assignment 1).

Drawing inspiration from the Amsterdam City Swim, we chose a course that mirrored its feasibility, regarding extra space before the starting line and after the finish, to ensure a seamless experience. It is assumed that the municipality of Amsterdam is keen to organise this event. Therefore, the commercial canal boats can be restricted from certain areas at certain times of the day: mitigating disruptions while respecting their operations. 

In harmonizing these elements, we envisage an event that not only thrills the swimmers but also integrates seamlessly with the vibrant pulse of Amsterdam's waterways. 

**Plotting of the swimming route**  
The following steps are taken to plot the swimming route in Phyton
1. The route is mapped out and downloaded as a GPX, to use with Python. (visualised with the use of gpxplotter)
2. Then a DataFrame is made out of the GPX file, with longitude, latitude, elevation and time in the columns.
3. Out of the longitude and latitude coordinates of the nodes, the average is calculated giving us the centre.

The following code is used to plot this map:

```
from gpxplotter import read_gpx_file, create_folium_map, add_segment_to_map

the_map = create_folium_map(zoom_start=15,
               zoom_control=False,
               scrollWheelZoom=False,
               dragging=False)
for track in read_gpx_file("C:/Users/maaik/Downloads/COURSE_234358203.gpx"):
    for i, segment in enumerate(track['segments']):
        add_segment_to_map(the_map, segment)

# Display map
the_map

the_map.save("map.html")
```
<img src="Map1.png" alt="Map1">

*Graph 1: The swimming course plotted*

### Finding the centre of the nodes of the swimming route
To determine the centre of the nodes of the swimming course, the following steps are taken: 
1. Extract the nodes out of the GPX file (for this, code on the site https://towardsdatascience.com/parsing-fitness-tracker-data-with-python-a59e7dc17418  is used) 
2. The centre of the nodes is calculated using the coordinates of the nodes 
3. The centre node is visualised 

```
from typing import Dict, Union
from datetime import datetime

import gpxpy
import pandas as pd

# The XML namespaces used by the GPX file for extensions, used when parsing the extensions
NAMESPACES = {'garmin_tpe': 'http://www.garmin.com/xmlschemas/TrackPointExtension/v1'}

# The names of the columns we will use in our DataFrame
COLUMN_NAMES = ['latitude', 'longitude', 'elevation', 'time']

def get_gpx_point_data(point: gpxpy.gpx.GPXTrackPoint) -> Dict[str, Union[float, datetime, int]]:
        """Return a tuple containing some key data about `point`."""
        
        data = {
            'latitude': point.latitude,
            'longitude': point.longitude,
            'elevation': point.elevation,
            'time': point.time
        }

        return data

def get_dataframe_from_gpx(f: str) -> pd.DataFrame:
    """Takes the path to a GPX file (as a string) and returns a Pandas
    DataFrame.
    """
    with open("C:/Users/maaik/Downloads/COURSE_234358203.gpx") as f:
        gpx = gpxpy.parse(f)
    segment = gpx.tracks[0].segments[0]  # Assuming we know that there is only one track and one segment
    data = [get_gpx_point_data(point) for point in segment.points]
    return pd.DataFrame(data, columns=COLUMN_NAMES)

if __name__ == '__main__':
    
    from sys import argv
    fname = argv[1]  # Path to GPX file to be given as first argument to script
    df = get_dataframe_from_gpx(fname)
    print(df)
  ```
latitude  longitude  elevation                             time
0   52.373425   4.913464       8.05        2023-10-16 12:51:04+00:00
1   52.371618   4.913335      -0.36 2023-10-16 12:51:04.060000+00:00
2   52.366643   4.906176       3.14 2023-10-16 12:51:04.342000+00:00
3   52.365648   4.901114       3.07 2023-10-16 12:51:04.732000+00:00
4   52.364756   4.895881       4.22 2023-10-16 12:51:05.233000+00:00
5   52.365463   4.890519      10.67 2023-10-16 12:51:05.846000+00:00
6   52.367663   4.886701       5.12 2023-10-16 12:51:06.567000+00:00
7   52.373843   4.887215       6.50 2023-10-16 12:51:07.494000+00:00
8   52.374741   4.887919       8.97 2023-10-16 12:51:08.454000+00:00
9   52.375379   4.885903       8.64 2023-10-16 12:51:09.461000+00:00
10  52.374347   4.885069       8.27 2023-10-16 12:51:10.506000+00:00
11  52.367165   4.884598       6.58 2023-10-16 12:51:11.791000+00:00
12  52.364201   4.889747       7.30 2023-10-16 12:51:13.221000+00:00
13  52.363389   4.895366       8.13 2023-10-16 12:51:14.769000+00:00

<img src="Map2.png" alt="Map2">

*Graph 2: The centre node of the swimming course plotted*

### Finding a suitable spot for the Event Headquarters
The center point gives us a street next to the canals in the middle of the city center and next to the University of Amsterdam. Because this is not a public space and the point is not adjacent to the swimming course, we would recommend going closer to the course and finding a spot. 

A headquarters on the water seems like a logical place, at the Blauwbrug for instance. Here it is also easy to move to other points along the course, since you are already on the same road. 

<img src="Map3.png" alt="Map3">

*Graph 3: Location for the Event Headquarters*

### Closest tram and bus stops at the start and finish and capacity
**Note**: only data about the metro and tram stops in Amsterdam was found, therefore only the closest tram stop is coded. 
1. For this, we first find the start and finish coordinates
2. The coordinates of the bus and tram stops are imported and processed. https://maps.amsterdam.nl/open_geodata/
3. Openstreetmaps is imported and used to find the distance between each bus stop point and the start and finish coordinates
4. The shortest stop is filtered out and found

**Starting point**  
Tram  
At the starting point, the closest tram stop is Muziekgebouw Bimhuis, where there is one line passing 8 times an hour. The trams have 90 standing places at maximum capacity (GVB, n.d.-a). This means that when running at maximum capacity (which is reasonable to think when there is a major event happening), 8*90=720 people can go from and to the starting point within an hour by tram. 

Bus  
Since there were no data sets online about the bus stops, the closest stop was found in Google Maps. It is clear that the closest stop is at Kattenburgerstraat. The buses have 105 standing places at maximum capacity (GVB, n.d.-a). There will be 4 buses per hour, which will transport 4*105=420 people to and from the starting point within one hour. 

**Finish point**  
Tram  
At the finish point, the closest tram stop is at Keizersgracht, where one line comes by every 15 minutes. The trams have 90 standing places at maximum capacity (GVB, n.d.-a). This means that when running at maximum capacity, 4*90=360 people can go from and to the starting point within an hour by tram. 

Bus  
The closest stop to the finish line is Beukenplein. The buses have 105 standing places at maximum capacity (GVB, n.d.-a). There will be 6 busses per hour, which will transport 6*105=630 people to and from the starting point within one hour. 

### Corresponding bus and tram lines and their route

**Starting pont**  
At the starting point the closest tram stop is at Muziekgebouw Bimhuis, where line 26 runs. In the previous exercise this can be found when looking up the whole row from the coordinates from the closest tram line. 

Since there were no data sets online about the bus stops, the closest stop was found in Google Maps. It is clear that the closest stop is at Kattenburgerstraat. 

<img src="OV1.png" alt="OV1">

*Graph 4: Tram line 26, closest tram line near the starting point (marked in green)(GVB, 2023)*

<img src="OV2.png" alt="OV2">

*Graph 5: Bus line 43, closest bus line near the starting point (marked in green)(GVB, 2023)*

**Finish point**  
For the finish point the closest tram stop is at Keizersgracht, where line 4 runs. This can be found in the previous exercise as well when looking up the whole row from the coordinates from the closest tram line. 

The closest bus stop and its line is again found in Google Maps. The closest bus stop to finish line is at Beukenplein, where line 37 runs. This is quite far away, because there are no busses in the city center during the day, since there are tram lines everywhere. 

<img src="OV3.png" alt="OV3">

*Graph 6: Tram line 4, tram line near the finish point (marked in red)(GVB, 2023)*

<img src="OV4.png" alt="OV4">

*Graph 7: Bus line 37, closest bus line near the finish point (marked in red)(GVB, 2023)*

### Centrality  
Using NetworkX and OSM 
To decide on the best centrality to use, we defined the need for the exercise.  

For the start and finish nodes of the route, people need to be able to reach them and exit them quickly, which means that we are looking for a node in the network that can reach other nodes quickly. The best to use in this case is closeness centrality. Closeness centrality measures how quickly a node can reach all other nodes in the network, taking into account the shortest paths between them. A node with high closeness centrality is one that is located in such a way that it can efficiently reach other nodes in the network with fewer steps, so in our case individuals would be able to reach other exit routes and paths quickly. 

To calculate closeness centrality for a node, we need to find the inverse of the sum of the shortest path distances from that node to all other nodes in the network. Nodes with higher closeness centrality values are closer to other nodes in terms of network distance. 

For the central node, the organization team needs to be able to reach all the nodes on the route from the headquarters. For this we can use either closeness centrality or eccentricity centrality. Eccentricity centrality is related to the eccentricity of a node, which is the maximum distance from that node to any other node in the network. We chose to calculate closeness centrality, since a node with high closeness centrality is one that is close to all other nodes in terms of network distance, meaning it can reach them more quickly than other nodes. We will follow the following steps to calculate centrality:
* First, we will calculate the nodes based on the coordinates of the Amsterdam center map.  
* Calculate the closeness centrality of the starting, center and ending point.  
* Calculate nodes which are closest to swimming routes.  

```
import networkx as nx
import osmnx as ox

# Find coordinates of (start point)
location_start = (52.373425, 4.913464)
location_center = (52.369163, 4.894500)
location_end = (52.363389, 4.895366)

# This gets all the canal data from Amsterdam
place_name = "Amsterdam, Netherlands"
graph = ox.graph_from_place(place_name, network_type="all", simplify=True)

# Find the nearest nodes
nodes_start = ox.distance.nearest_nodes(graph, location_start[1], location_start[0], return_dist=True)
nodes_end = ox.distance.nearest_nodes(graph, location_end[1], location_end[0], return_dist=True)

# Convert the coordinates of the start and end points to nodes within the network
nodes_start_walk = ox.distance.nearest_nodes(graph, location_start[1], location_start[0], return_dist=True)
nodes_end_walk = ox.distance.nearest_nodes(graph, location_end[1], location_end[0], return_dist=True)
nodes_center_walk = ox.distance.nearest_nodes(graph, location_center[1], location_center[0], return_dist=True)

# Use networkx to calculate the centrality
start_centrality = nx.closeness_centrality(graph, u=nodes_start_walk[0])
center_centrality = nx.closeness_centrality(graph, u=nodes_center_walk[0])
end_centrality = nx.closeness_centrality(graph, u=nodes_end_walk[0])

# Then print the centrality values
print('The centrality of the start point is', start_centrality)
print('The centrality of the center point is', center_centrality)
print('The centrality of the end point is', end_centrality)
```

The centrality of the start point is 0.013736946454284894
The centrality of the center point is 0.01431024781365906
The centrality of the end point is 0.015308178014500335


### Cafes and restaurants near the finish line
We make the assumption that 750m can be covered in a 10min walk.  
We define the coordinates and the walking radius and we use the Overpy to find the amenities we  are  looking for, namely Cafes or restaurants close to the finish point.  

```
import overpy

#define coordinates and walking radius for 10 minutes walk which we estimated at 750m
lat, lon = 52.363389, 4.895366
walk_area = 750  

#create query to find cafes and restaurants
query = f"""
[out:json];
(
    node["amenity"="cafe"](around:{walk_area},{lat},{lon});
    node["amenity"="restaurant"](around:{walk_area},{lat},{lon});
);
out center;
"""
#run api
api = overpy.Overpass()
result = api.query(query)

#print cafes or restaurants list
for node in result.nodes:
    name = node.tags.get("name", "Unknown")
    location = (float(node.lat), float(node.lon))
    print(f'Restaurant or Cafe: {name}, Location: ({location[0]}, {location[1]})')

#print a message if no cafes or restaurants are found
if not result.nodes:
    print("No cafes or restaurants around the finish point.")
```

The following cafes ad restaurants are found:

Restaurant or Cafe: El Torado Grill, Location: (52.3666908, 4.8947159)   
Restaurant or Cafe: Rain, Location: (52.3657475, 4.8972735)   
Restaurant or Cafe: De Jaren, Location: (52.3680203, 4.8953278)   
Restaurant or Cafe: Water en Brood, Location: (52.3641405, 4.9058121)   
Restaurant or Cafe: La Margarita, Location: (52.3692724, 4.8930721)   
Restaurant or Cafe: La Place, Location: (52.3676426, 4.8924135)   
Restaurant or Cafe: Blue Amsterdam, Location: (52.3673568, 4.8915534)   
Restaurant or Cafe: Screaming Beans, Location: (52.3632827, 4.8986443)   
Restaurant or Cafe: Soenda Kelapa, Location: (52.3630054, 4.8987669)   
Restaurant or Cafe: Kramer, Location: (52.3654467, 4.8926577)   
Restaurant or Cafe: Bollywood Indian Restaurant, Location: (52.3639694, 4.8844033)   
Restaurant or Cafe: Puri Mas Indonesisch Restaurant, Location: (52.3641036, 4.8845382)     
And many, many more ...

In total 313 restairants and cafes are found. 

### References
GVB. (n.d.-a). Onze bussen. Over GVB. Retrieved 16 October 2023, from https://over.gvb.nl/ov-in-amsterdam/voer-en-vaartuigen/bus-in-cijfers/  

GVB. (n.d.-b). Onze trams. Over GVB. Retrieved 16 October 2023, from https://over.gvb.nl/ov-in-amsterdam/voer-en-vaartuigen/tram-in-cijfers/  

GVB. (2023). Haltes | GVB. https://reisinfo.gvb.nl/nl/haltes 

OpenStreetMap. (2023). OpenStreetMap. OpenStreetMap. Retrieved 16 October 2023, from https://www.openstreetmap.org/  

Gboeing. (2023, October). Gallery of OSMnx tutorials, usage examples, and feature demonstations. GitHub. Retrieved October 20, 2023, from https://github.com/gboeing/osmnx-examples 

Hoffman, M. (2021, October). Centrality. Bookdown. Retrieved October 20, 2023, from https://bookdown.org/markhoff/social_network_analysis/centrality.html#closeness-centrality 

NetworkX. (2023). Centrality. Retrieved October 20, 2023, from https://networkx.org/documentation/stable/reference/algorithms/centrality.html 

OSMnx. (2023). User Reference. Retrieved October 20, 2023, from https://osmnx.readthedocs.io/en/stable/user-reference.html# 

Python overpass API. (2023). Examples. Python Overpass API. Retrieved October 20, 2023, from https://python-overpy.readthedocs.io/en/latest/example.html 

Stack Overflow. (2018, September). How to get a {{geocodeArea: xxx }} query to work in python using overpy? Retrieved October 20, 2023, from https://stackoverflow.com/questions/52236655/how-to-get-a-geocodearea-xxx-query-to-work-in-python-using-overpy 

Stack Overflow. (2023, May). Overpass API: query for counting amenity of specified type around set of lat lons. Retrieved October 20, 2023, from https://stackoverflow.com/questions/72192572/overpass-api-query-for-counting-amenity-of-specified-type-around-set-of-lat-lon 

---
Go to Assignment 1: [Water]({{site.baseurl}}/assignment-1)  
Go to Assignment 2: [Energy]({{site.baseurl}}/assignment-2)  
Go to Assignment 3: [Housing]({{site.baseurl}}/assignment-3)
