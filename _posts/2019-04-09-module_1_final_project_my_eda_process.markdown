---
layout: post
title:      "Module 1 Final Project: My EDA Process"
date:       2019-04-09 23:03:13 +0000
permalink:  module_1_final_project_my_eda_process
---


## The Question - What Factors Influence Price?
I begun my EDA process by making an educated guess at which three factors I thought were most likely to have the biggest influence on price by drawing from my own experiences with residential real estate. The factors I settled on were location and size.

## Size
For the size factor, I found no evidence that size had any effect on price. After running a correlation between the lot square footage column and price, there was a very weak correlation of 0.14. 

## Location - Zip Codes
For the location factor I began my exploration by analyzing the waterfront and zip code columns, the rationale being that "niceness of surroundings" could likely be a significant price determinant i.e. affluent neighbourhood, proximity to a beach. The data, however, showed a very weak relationship between the data in these columns and price. The joint plot for waterfront below displays an almost identitical distribution of prices between waterfront and non-waterfront properties. The zip code plot below shows that codes between 98000 and 98050 have a greater cluster of prices towards the high-end of the dataset, however more research is needed to determine this is not just merely a result of there being more houses that fall within those codes. 

## Location - Latitude/Longitude

### Heatmaps
The most meaningful analysis from the location data was generated from the latitude and longitude values. By plugging the values into Google's `gmaps` library, I created the heatmap visualizations shown below. The heatmaps give a visual representation of how densely populated each area is. The results from these heatmaps gave a very strong overview of how houses of different price ranges were clustered. The top 25% priced houses cluster mostly towards the central Seattle area, Queen Anne, Capitol Hill, Mercer Island  and Bellevue. Noticeably, from the south of Renton to Enumclaw, the concentration of houses is almost entirely that of that of the houses in the 50th percentile or below in price. 

A shortcoming of this visualization method is that it does not account for the bias of overall population density. Areas may be red in certain areas simply because of how densely populated those areas are which may be adding noise to the data. I attempted to account for this bias through a 'control' visualization of the entire dataset, as well as making judgements on density in a comparitive manner.


#### Houses in the 75th to 100th percentile in Price
![alt text](https://github.com/jsavory-94/dsc-1-final-project-online-ds-pt-021119/blob/master/visualizations/ultra-high-nw.png?raw=true)




#### Houses in the 50th to 75th percentile in Price
![alt text](https://github.com/jsavory-94/dsc-1-final-project-online-ds-pt-021119/blob/master/visualizations/high-nw.png?raw=true)




#### Houses in the 25th to 50th percentile in Price
![alt text](https://github.com/jsavory-94/dsc-1-final-project-online-ds-pt-021119/blob/master/visualizations/low-nw.png?raw=true)




#### Houses in the 0th to 25th percentile in Price
![alt text](https://github.com/jsavory-94/dsc-1-final-project-online-ds-pt-021119/blob/master/visualizations/low-nw.png?raw=true)

### Polygon Overlay
From the information I gathered from the heatmaps, I created a second type of visualization that used `gmaps` Polygon feature to give an illustration depicting which areas of Washington can be considered either 'wealthy', 'upper class', or 'poor'. An area was categorized as wealthy (highlighted in red) if its 75th to 100th percentile heatmap had significant red clusters where the 50th to 75th percentile heatmap did not. An area was categorized as upper middle class (highlighted in orange) if both its 75th to 100th percentile heatmap and its 50th to 75th percentile  heatmap had significant red clusters. An area was categorized as poor (highlighted in blue) if it had significant red clustering in either the 0th to 25th percentile heatmap or the 25th to 50th percentile one as well as none in the other two. 

The most challenging part of using Polygon was setting the coordinates to plot because of how many there typically are, and the strictness that `gmaps` requires with inputting them in order. To other data scientists wishing to experiment with the Polygon feature of `gmaps` I would recommend the following process to help manage this: first determine the area you would like to draw your polygon and plot a series of points on a printed map to establish your perimeter. Second obtain the coordinates of each point to input by going through each point one at a time, marking it on google maps in order to get its coordinates, then copy and paste the coordinates given to you into the the Polygon function's argument. 



![alt text](https://github.com/jsavory-94/dsc-1-final-project-online-ds-pt-021119/blob/master/visualizations/polygons.png?raw=true)

Steps I would take to improve this visualization would be to create more granular wealth categories for the areas, and spend more time populating the rest of the map.

## Conclusion/Retrospective
In a further iteration of this EDA I would have liked to figure out a way to create a more thorough representation of which areas are wealthy, extremely wealthy, poor, middle class etc. and find a way to use that information in order to integrate the latitude/longitude values into my model. 

A technique I'm interested in exploring further to do this would be through inserting the Polygon Overlay shapes created into Python's Shapely library. This would allow testing of individual points in the dataset to determine whether they fit into the defined areas, which could make for interesting function logic. 
