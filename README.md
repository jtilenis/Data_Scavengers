# Data_Scavengers


# Pulling and cleaning census data
1. Run Census_Data_v2 to create Census data
1. Run JT Clean Census Data to clean/update the Census data

# Pulling and cleaning hospital data
1. Run Hospital_api to pull + clean hospital data
1. Run map_cities to update certain city values to align with census

# Graphs
1. Run HospitalCorrelationAnalysis to generate heatmaps, scatter plots
1. Run bar_charts to generate the bar charts
1. Run Box_Plot to generate the box plot





#Summary
We leveraged data to pinpoint which areas in Georgia are being medically under-served and have a disproportionate amount of obstacles to healthcare access. 

Using Wikipedia API and Google Places API, we were able to pull a list of all hospitals in Georgia, their address + coordinates, and number of acute care beds they have (which was our main measure of hospital capacity). 


We utilized the Census API to ultimately pull the median income and population by city/county in Georgia. We had to use Census estimates from 2018 since the real census hadn’t been pulled in a few years.While doing the analysis over the Census data, it’s been identified that the ZIP code does not exactly correspond to the location in a lot of cities. That said, we had to identify another source where the ZIP code presented on Census data can be derived exactly to the locale, so we could then use it to join with hospital information.


We merged the hospital data and census data together on city. We had to solve for discrepancies in terms of city names (ex: “Johns Creek” was rolled up under “Alpharetta” in the census data). 

Once all the data was cleaned, we began conducting our analyses


#Which cities are the furthest away from a hospital?
We generated a heatmap of Georgia where the markers were hospitals and the weight was a variable we calculated: miles from nearest hospital. Based on that variable, we were able to get the top 10 cities that were furthest away from a hospital. 


#Which counties in Georgia have the highest and lowest number of hospital beds available per 1000 people? 
After grouping data together at the county level, we divided the number of acute care beds that county has by the counties population and multiplied by 1000 to create the variable ‘# of beds per 1000 people’. From there, we could both plot this data on a heatmap, create a bar chart, and strip out the cities with both the highest and lowest number of hospital beds. We leaned on this metric to factor in population size and see if any areas were disproportionately covered


#Is there a correlation between median income and number of hospital beds?
Using a scatter plot and regression line, we concluded that there was no correlation between median income and number of hospital beds in that area. We were looking to see if more impoverished areas (wrongfully) had less hospitals/lower capacity of beds.
