# Chicago-Ride-share-Trips-Analysis
Chicago ride-share trip analysis

I just have written a recent R code to analyze "rideshare trips" data from the Chicago data portal. Data contains individuals’ trips from origin coordinates to destination coordinates along with travel time and cost of the trip and some other information. The goal of using this data is for travel demand modeling. In travel demand modeling, we need to know zone-to-zone interaction. I am going to count how many trips has been made within the zones. However, there are some issues with the data set:

(1) Almost for each trip, census trac information is given. But in order to have a complete data set, missing census tracts are needed to be found. So we need to download the Chicago census tracts polygon data to find missing tracts for trips. Luckily, this Census tract data is also available in the Chicago data portal. As a result, we need to do a spatial match between Census tracts and missing data points in the trips data set.

(2) Downloaded data is about 19GB which has around 73M rows. My computer's memory is 16GB. If I want to analyze this data either I have to rent an AWS or Google Cloud resources or split the data to the chunks and analyze individually. I could also use big data frameworks for this analysis, but it is not that big to rent Hadoop resources as well. I have to use my computer. I developed the following R code to handle this big data and analysis on the fly.

Source for the trip data: [link](https://data.cityofchicago.org/Transportation/Transportation-Network-Providers-Trips/m6dm-c72p)

Source for the census tracts data: [link](https://data.cityofchicago.org/Facilities-Geographic-Boundaries/Boundaries-Census-Tracts-2010/5jrd-6zik)

I had experience with all of the data handling libraries. For big data sets, I can suggest "data.table" library. For my spatial analysis, I used to analyze with PostgreSQL and PostGIS but there is a recent great library by Edzer Pebesma et. al (2019) for R which is "sf". It is fast and easy to use. I don't have to write spatial SQL code anymore.
