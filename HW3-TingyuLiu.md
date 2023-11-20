## 1. Create a drive network model for the city of Atlanta. (5 pts)

Plot a map of the network you built spatially overlaid on top of the neighborhoods.

I used ArcGIS to create a drive network dataset for the city of Atlanta. **The color of each edge represents the driving time.**

![pic1](plot/1-3.png)

## 2. Generate accessibility zones using 5 discrete travel time thresholds for health facilities and fire stations. (3 pts)

I used ArcGIS to create service areas for fire stations and hospital respectively. I used the same 5 time thresholds for health facilities and fire stations, which are 0,5,10,15,20 minutes. 

**Reasons for choosing this thresholds:**

>The range for travel times is determined based on realistic travel times in urban areas and previous studies. A study on the accessibility of urban fire stations in Nanjing, China [(Yu,2022)](https://link.springer.com/article/10.1007/s10109-022-00381-x#Sec9) used a range of 0 minutes to 12 minutes, with threshold values of 0, 4, 8, and 12. Taking into account the [real driving speed in Atlanta](https://www.tomtom.com/traffic-index/atlanta-traffic/) in Atlanta (source), I have chosen a range of 0 to 20 minutes, with equal intervals of 5.

Plot an accessibility map to health stations
![pic2](plot/2-med-2.png)

Plot an accessibility map to health stations
![pic3](plot/2-fire2-2.png)

I used the same 5 time thresholds for health facilities and fire stations, which are 0,5,10,15,20 minutes.

## 3. Find out the best and worst neighborhoods to live in. (7 pts)
Detail: Add a weight field to the attribute tables representing an ordinal ranked distance away from the facilities and combine the weights together. Overlay neighborhood polygons, calculate the combined/composite weight for each neighborhood, and find out the best and worst neighborhoods to live in based on accessibility to health facilities and fire stations. (7 pts)

I have found that the **best** neighborhood to live in is the **Old Fourth Ward neighborhood** (weighted score 4), while the **worst** is M**idwest Cascade** (weighted score 2.5). 

![pic4](plot/3.png)


Here is a screenshot of the attribute table, Descending order:
![5](plot/desc.png)

Ascending order:
![6](plot/desc.png)

### As shown in the data flow chart, my steps are as follows

![pic5](plot/process.png)

and below are screenshots for each steps mentioned in data flow chart:

step 1: Map range to score with field calculator
![1](plot/step3-detail4.png)

step 2: Join score attributes by location to neighborhood area, and add $area attribute.
![2](plot/step3-detail12.png)
![2-2](plot/step3-detail3.png)


step 3: Group by OBJECTID to calculate score in each complete neighborhood，with statistics by categories.

![3](plot/step3-detail6.png)
![3-2](plot/step3-detail7.png)

step 4: Calculate fire station accessibility score in each neighborhoods, weighted by area, with field calculator.
![4](plot/step3-detail10.png)

step 5: Iterate step 1-4 for hospital accessibility score, weighted by area.

step 6: Calculate the composite weighted score of the fire station and hospital(50% weight to each), with field calculator.
![6](plot/step3-detail11.png)





