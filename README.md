# Food Deserts in Three Texas Cities

## Team Members
Lynn Leifker and Kellye Rennell

## Project Description
A food desert is an area that lacks access to affordable and fresh fruits, vegetables, whole grains, and dairy items. We chose to study their occurrence in three urban areas: Austin, Dallas, and Laredo, Texas. We further restricted our study to low-income areas where residents are less likely to have access to transportation and therefore are more negatively affected by supermarket distance than residents of wealthier areas. 

## Research Questions
1) If you live in a neighborhood with a Title 1 school, how likely are you also to live in a food desert?
2) Is there a difference among the three cities in the proportion of food deserts?
3) Does the likelihood of living in a food desert increase as poverty increases?
4) What is the average distance a person in any given neighborhood must drive to get to the nearest grocery store?
5) Does driving distance correlate to the level of poverty in a neighborhood?
## Data Gathering
The demographic data we found mostly tended to be aggregated by zip code, which vary in size, making it difficult to get accurate information about the presence of food deserts at a neighborhood level. To study food deserts in smaller areas, we needed to find points to represent the centers of neighborhoods. We decided to use Title 1 elementary schools, which qualify for federal funding for low-income families. Not only do elementary schools tend to be in the center of neighborhoods, the federal government provides annual reports on the poverty level within Title 1 schools, which gave us the ability draw conclusions about the relationship between poverty level and food desert status. We pulled the 2018 list of Title 1 schools from the U.S. Department of Education to begin our study.

Using the Google Geocode API we found each school’s coordinates. We then searched for the closest grocery stores selling fresh food using Google’s nearby search API. This turned out to be surprisingly complicated. For example, the API excluded H-E-B and Randalls in Austin while including Whole Foods and Walmart Supercenter. We ended up running additional API pulls explicitly calling for H-E-B and Randalls to get them into our dataset. 

Once gathered from the Google API, the data still required significant cleaning because it included stores like Family Dollar that don’t meet the fresh fruit and vegetable qualification. To find replacement stores, we compared results of the API pulls to what we found when we looked on Google Maps. Many times we would see a discrepancy between what the closest store on a map turned out to be and what the API returned. After repeated back-and-forth for cleanup it became apparent that it would be faster to look stores up one-by-one on the map and not use the nearby search API.

Once we had a list of schools and nearest grocery stores, we needed the distance between them. Reasoning that driving distance is a more realistic metric of distance than geographic distance is, we used the Google Distance Matrix API to find this.


![Schools PDF](https://github.com/LBBL96/Food-Deserts/blob/master/Datasets/Title%20I%20Schools.pdf)

![Combined Cities.csv](https://github.com/LBBL96/Food-Deserts/blob/master/Datasets/Combined_Cities.csv)

## Findings
1) If you live in a neighborhood with a Title 1 school, how likely are you also to live in a food desert?
2) Is there a difference among the three cities in the proportion of food deserts?
![low income](https://github.com/LBBL96/Food-Deserts/blob/master/Images/Percent_Low_Income_Pov_Deserts.png)
We found that the likelihood that a neighborhood is located in a food desert varies significantly based on which city is being studied. In Austin, 65% of Title 1 schools are in food deserts, and 35% are not. Dallas has a slightly lower rate — 59% of Title 1 schools are in food deserts, while 41% are not. Laredo proves to be surprising outlier in this group. Although its Title 1 schools have the greatest poverty rate of the three cities, it has the lowest occurrence of food deserts: only 30% of Title 1 schools are in a food desert. The overall likelihood that any given neighborhood across the three cities is in a food desert is 58%.

The heat maps below give an illustration of how dispersed grocery stores are within neighborhoods with Title 1 schools. The heat map shows where Title 1 schools are located, and darker red corresponds to greater poverty within a school. The blue squares represent locations of grocery stores.

![Austin Heatmap](https://github.com/LBBL96/Food-Deserts/blob/master/Images/Austin_Heatmap.png)

![Dallas Heatmap](https://github.com/LBBL96/Food-Deserts/blob/master/Images/Dallas_Heatmap.png)

![Laredo Heatmap](https://github.com/LBBL96/Food-Deserts/blob/master/Images/Laredo_Heatmap.png)

![As poverty increases](https://github.com/LBBL96/Food-Deserts/blob/master/Images/Food_Desert_As_Poverty_Increases.png)

![Crosstab](https://github.com/LBBL96/Food-Deserts/blob/master/Images/Pov_Group_Crosstab.png)

![Mean vs Median Drive](https://github.com/LBBL96/Food-Deserts/blob/master/Images/Mean_vs_Median_Driving_Distance.png)

![Median drive distance](https://github.com/LBBL96/Food-Deserts/blob/master/Images/Median_driving_distance.png)



## Surprises

![Boxplot](https://github.com/LBBL96/Food-Deserts/blob/master/Images/Boxplot_Title_1_Poverty.png)



![Six Zips](https://github.com/LBBL96/Food-Deserts/blob/master/Images/Six_Zips.png)

## Conclusions

## Suggestions for Further Study

Are there correlations between the racial and ethnic makeup of a given neighborhood and its food desert status?

What are the relative health outcomes
