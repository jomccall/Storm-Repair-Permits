# **Storm Repair Permits in the City of Nashville**

## *Table of Contents*
+ Overview   
+ Data Prep  
+ Technologies and Packages
+ Geographic Visualization
    + *
+ Regression Model

## Overview
Nashville can be subject to extreme weather events rather frequently, particularly dangerously high winds and tornadoes. This project uses building permit data from the last three years about storm repairs to visualize where the majority of property damage is being done, to investigate what kind of property is being damaged and the cost of this damage, and then uses regression methods to see if there are any informative trends or seasonality when this data is parsed as a time series. It is common knowledge that there is a regular storm season, however Madison - a Nashville neighborhood and township - recently saw damage from a December tornado. It is also an attempt to see how long it takes for permits to be issued following established storm events.

## Data Prep

The Socrata API is used to call both building permit data and geographic outlines of the 35 city council districts. The point data from the building permits has to be pulled out of a dictionary containing latitude, longitude, and the human address. One data cleaning challenge that pops up is that many of the addresses are merely human addresses. Using a `lambda function`, this can be resolved by making a list of these instances and dropping them from the dataset. When the geographic boundary data is brought in, the multipolygon boundary has to be made into a geometry using the `.apply(shape)` function from `shapely.geometry`. In order to create a set of visualizations, grouped totals of permits are calculated from the points dataframe and joined to the polygons. This way both can be visualized on an interactive map via choropleth and clustered points.
