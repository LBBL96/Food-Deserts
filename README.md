# Food Deserts in Three Texas Cities

## Team Members

Lynn Leifker and Kellye Rennell


## Project Description:

A food desert is an area that lacks access to affordable and fresh fruits, vegetables, whole grains, and dairy items. We chose to study their occurrence in three urban areas: Austin, Dallas, and Laredo, Texas. We further restricted our study to low-income areas where residents are less likely to have access to transportation and therefore are more negatively affected by supermarket distance than residents of wealthier areas. 

## Research Questions: 

* If you live in a poor neighborhood, how likely are you to also live in a food desert?
* Is there a difference among the cities in the severity of this phenomenon?	
* Does likelihood of living in a food desert increase as poverty increases?
* What is the average distance a person in any given neighborhood has to drive to the nearest grocery store? 
* Does driving distance correlate to the level of poverty in a neighborhood?

## Data Gathering:

The demographic data we found tended to be estimated from the 2010 census and to be aggregated by zip code. Zip codes vary in total area, making it difficult to get accurate information about sub-populations. Pockets of poverty can be difficult to discern when wealthy neighborhoods in one section of a zip code skew the overall mean income. We needed to find points to represent the centers of neighborhoods within zip codes in order to get a more granular income level. We decided to use Title 1 elementary schools as a proxy for neighborhoods. Title 1 is a federal designation for schools that qualify for federal funding due to a low-income population. 

Choosing elementary schools as a proxy had two advantages: 1) they tend to be in the center of neighborhoods whose populations are more economically homogeneous than the population across a zip code, and 2) the federal government provides annual reports on the poverty level within Title 1 schools, giving us the most recent and accurate data on poverty level within those neighborhood populations. To begin our study, we pulled the 2018 list of Title 1 schools from the U.S. Department of Education's website. 

[Title 1 Schools](https://github.com/LBBL96/Food-Deserts/blob/master/Datasets/Title%20I%20Schools.pdf)

Using the Google Geocode API we found each school’s coordinates. We then used Google's Nearby Search API to find the closest grocery stores selling fresh food. This turned out to be surprisingly complicated. For example, the API results excluded H-E-B and Randalls in Austin while including Whole Foods and Walmart Supercenters. We had to make additional, explicit, API calls to get H-E-B and Randalls into our dataset. 

Once gathered from the Google API, the data still required significant cleaning because it included stores that didn’t meet the fresh fruit and vegetable qualification. To find replacement stores, we compared results of the API calls to what we found when we looked on Google Maps. Many times we would see a discrepancy between what the closest store on a map turned out to be and what the API returned. We suspect that a hidden algorithm accounts for which stores get the top rankings for location. After repeated back-and-forth comparisons between API results and the maps, it became apparent that it would be faster to look stores up on the map directly and not use the Nearby Search API.

Once we had a list of Title 1 schools and their nearest grocery stores, we needed to find the distance between them. Reasoning that driving distance is a more realistic metric of distance than geographic distance ("as the crow flies"), we used the Google Distance Matrix API to find driving distance.

[Combined Cities.csv](https://github.com/LBBL96/Food-Deserts/blob/master/Datasets/Combined_Cities.csv)

## Findings:

### If you live in a poor neighborhood, how likely are you to also live in a food desert? Is there a difference among the cities in the severity of this phenomenon?

![Percent Low Income](https://github.com/LBBL96/Food-Deserts/blob/master/Images/Percent_Low_Income_Pov_Deserts.png)

We found that the likelihood that a neighborhood is located in a food desert varies significantly based on which city is being studied. In Austin, 65% of Title 1 schools are in food deserts, and 35% are not. Dallas has a slightly lower rate — 59% of Title 1 schools are in food deserts, while 41% are not. Laredo proved to be the surprising outlier in this group. Although its Title 1 schools have the greatest poverty rate of the three cities, it has the lowest occurrence of food deserts: only 30% of its Title 1 schools are in a food desert. The overall likelihood that any given neighborhood across the three cities is in a food desert is 58%.

The heat maps below give an illustration of how dispersed grocery stores are within neighborhoods with Title 1 schools. The heat map shows where Title 1 schools are located, and darker red corresponds to greater poverty within a school. The blue squares represent locations of grocery stores.

![Austin Heatmap](https://github.com/LBBL96/Food-Deserts/blob/master/Austin.png)
![Dallas Heatmap](https://github.com/LBBL96/Food-Deserts/blob/master/Images/Dallas.png)
![Laredo Heatmap](https://github.com/LBBL96/Food-Deserts/blob/master/Images/Laredo_Heatmap.png)

### Does the likelihood of living in a food desert increase as poverty increases?
![Likelihood in food desert]( https://github.com/LBBL96/Food-Deserts/blob/master/Images/Food_Desert_As_Poverty_Increases.png)


The proportion of Title 1 schools within poverty groups that are in a food desert stays fairly steady across all groups. In the 50-59% poverty range, the proportion is about 50-50. The povety range where food deserts are proportionally highest is the 60-69% range—75% of these schools are in food deserts. Strangely, the second-to-lowest proportion of food deserts occurs in the 90-100% poverty range. Of those schools, 54% are in food deserts and 46% are not.

![Food Desert Crosstab](https://github.com/LBBL96/Food-Deserts/blob/master/Images/Pov_Group_Crosstab.png)
### What is the average distance a person in any given neighborhood has to drive to the nearest grocery store?

As seen below, the variance between mean and median driving distance can be extreme in the different cities. 

![Mean vs Median]( https://github.com/LBBL96/Food-Deserts/blob/master/Images/Mean_vs_Median_Driving_Distance.png)

Based on this, we chose median driving distance as the better metric for average drive.

![Median]( https://github.com/LBBL96/Food-Deserts/blob/master/Images/Median_driving_distance.png)

Residents of Austin’s and Dallas’ Title 1 school neighborhoods had comparable drives, at a median of 1.3 miles and 1.2 miles, respectively. Laredo’s median of 0.9 miles shows that on average, a Title 1 school in Laredo is not in a food desert.


### Does driving distance correlate to the level of poverty in a neighborhood?


The correlation coefficient between poverty level and driving distance is 0.003. This means there is no relationship whatsoever between an increase in poverty level and increase in driving distance.


## Surprises:

The poverty disparity in Title 1 schools among the cities was unexpected, as was its variance within cities. Looking at this boxplot, you can see that Austin has the greatest spread in IQR and the lowest median poverty level. Dallas’ lowest poverty level is 55%, but this and every other level up to 75% is an outlier. Laredo has no spread at all. Every one of its twenty Title 1 elementary schools has a poverty level of 100%!

![Boxplot](https://github.com/LBBL96/Food-Deserts/blob/master/Images/Boxplot_Title_1_Poverty.png)

Examining the zip codes containing the most Title 1 schools shows another surprising result: the proportion that are in a food desert can be radically different from zip code to zip code, even within the same city. In Dallas, the two zip codes containing the greatest number of Title 1 schools are completely opposite in food desert status: in 75217, 14 of 16 schools are in a food desert, while in 75211, only 2 of 14 are in a food desert.

![Six Zips](https://github.com/LBBL96/Food-Deserts/blob/master/Images/Six_Zips.png)


## Conclusion:

Urban neighborhoods in the two large cities we studied tended to be located in food deserts. Austin had the greatest likelihood, at 65%, and this may be a result of the rapid population growth of the city over the last decade. It may be that housing growth has outpaced commercial building, leading to a drop in available space for grocery stores as the number of people needing housing grows. 

In the smaller city of Laredo, the low likelihood of living in a food desert (30%) despite also living in the highest poverty of the three cities is difficult to explain. Perhaps its population is more densely clustered than in the bigger cities. If grocery chains build new stores based on total number of expected customers, then it would make sense for them to put more stores in areas where the population density is higher.  

## Suggestions for Further Study:

* Are there correlations between the racial and ethnic makeup of a given neighborhood and its food desert status? 

* What are the relative health outcomes for neighborhoods whose poverty level is similar but whose food desert status is radically different? 
