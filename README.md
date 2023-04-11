<p align="center">
  <img src="images/H22.png" />
</p>

## _Introduction_

Over the past few years, the pandemic has reshaped our lives in many ways. Inflation has taken its toll on us. Our cost of living has increased dramatically. Being a resident in Queens County, I began to wonder how the housing market has been affected. This project investigates the relationship between the occurrence of crime and the housing price in different areas of Queens. Generally, a safe neighborhood with lower crime rate would have higher property value. The dataset includes larceny, burglary, assault and sexual harassment crime rate for each zip code in Queens. We will explore which kind of crime has a greater effect on the sale price of a house. We will also use neighborhood information to make choropleth graphs to illustrate the sale price in Queens County as a whole.

H1: Bigger houses will sell at a higher price per square foot.

H2: Burglary crimes reduce a house’s price more severely than do larceny crimes.

---

## _Data Collection_

I use data collected from NYC Department of Finance on property sales in Queens County from January to December 2022. Also, I use NYC OpenData for valid felony and misdemeanor complaints reported to the New York City Police in December 2022. Moreover, I added population data for each zip code in Queens from New York Demographics. After cleaning the data files, I calculate the crime rates for each zip code in Queens and add these variables to the home sale data file.
To investigate how different type of crimes affect housing price, the linear regression model appears below:

sale per sqft = β0 + β1*total units + β2*gross square feet + β3*property age + β4*larceny_rate + β5*assault_rate + β6*harassment_rate + β7*burglary_rate + β8*population

- total units: the total number of units at the listed property
- gross square feet: the total area of all the floors of a building, including the land area
- property age: age of the property sold
- larceny_rate: number of larceny complaints in a zip code area divided by total complaints in Queens
- assault_rate: number of assault complaints in a zip code area divided by total complaints in Queens
- harassment_rate: number of harassment complaints in a zip code area divided by total complaints in Queens
- burglary_rate: number of burglary complaints in a zip code area divided by total complaints in Queens
- population: population in a zip code area

<p align="center">
  <img src="images/H19.png" />
</p>

> Descriptive Statistics

<p align="center">
  <img src="images/H20.png" />
</p>

> Histograms for crime rates

---

## _Choropleth Graphs_

I used plotly to make choropleth graphs on the housing data. The neighborhood information is used to match the id numbers in Queens geojson file. The first graph shows the sale price per square foot in Queens County. In general, most property was sold between 500 and 1000 per square foot. The second graph shows the age of the properties at the time of sales. Well, it seems that a lot of properties sold are between 80 and 120 years old. In the middle of the map, the properties sold are relatively new.

<p align="center">
  <img src="images/H11.png" />
</p>

> Sale price in Queens

<p align="center">
  <img src="images/H12.png" />
</p>

> Age of Property Sold

---

## _Correlation Heatmap_

I use seaborn to draw a heatmap for the correlation among home sale variables. The blue color means they are highly correlated. The lighter the color means they are not correlated with one another. It appears that the sale price per square foot does not have a strong correlation with any other variables. Burglary crime has the greatest positive coefficient on sale price. Assault and harassment both have negative coefficients. It can be argued that wealthy suburbs attract more burglaries. High burglary rate indicates that the area is wealthy. Larceny, assault and harassment are highly correlated with one another.

<p align="center">
  <img src="images/H21.png" />
</p>

> Correlation Table

---

## _Ridge and Lasso Model_

For testing my model, I use train test split on my data for cross validation. To avoid model bias, I apply polynomial features to my linear regression and use root mean square error as a cost function. Then I use ridge regularization and lasso regularization to reduce variance in my models. Overall, my model does not predict the sales per square foot well. The coefficient of determination r-squared is as low as 0.18. With ridge regularization, the r-squared did improve a little and the ridge model is a better model to use for prediction. The red line in ridge model is more spread out and captures more variance than that in the lasso model.

<img src = "images/H17.png" width ="470" /> <img src = "images/H18.png" width ="470" />

> Lasso Model & Ridge Model

---

## _Conclusion_

Housing prices can be as unpredictable as stock prices. In my study, gross square feet has a negative coefficient. Properties with larger gross square feet do not sell at a higher price per square foot. Instead, the larger the property area, the less the price per square foot. Perhaps buyers tend to bargain when the total sell price is high. Besides, buyers are already getting Covid discount. Furthermore, burglary crime does not reduce the sale price per square foot. Instead, it increases the property price as the coefficient on burglary crime is positive. The pandemic has changed our lives in so many ways. Burglary crimes have become more common and that does not drag down the property value. Apart from this, other crimes do have small negative effects on the property price. Overall, no crime reduces the housing price significantly.

My model does not predict housing price per square foot well. The r-squared shows that the model only explains roughly 19% of the variance in the housing price. After all, the housing market in Queens has become a buyers’ market. Generally, property prices are lower than they were before the pandemic and homes stay on the market longer. None of my explanatory variables has a strong correlation with the housing price. It appears that the property value is not dependent on the property age, population or gross square feet. In short, it is a good time to buy a house in Queens. If a place has a relatively high burglary rate, that area has some nice houses.

---

## _Postmortem_

Due to data availability, some variables are not included in my model such as house insurance cost and property tax. I had to search high and low for other factors relevant to my prediction model but I had no much luck bring the data together. Cleaning the crime data takes a lot of time. I first converted the latitudes and longitudes into addresses. The zip code was extracted and used to keep track of the number of crime occurrences. Then I joined the crime data file with the home data file based on the zip code. Creating the choropleth graph was a challenge. I needed to create a dictionary that includes key value pairs for the neighborhoods in Queens. If a neighborhood is found in geojson file, an id number is assigned to that observation. The choropleth graphs were colored based on the id numbers. Finally, plotting the Ridge and Lasso models requires adjusting the ranges of x and y values and the size of the display windows. In short, colleting, analyzing and presenting data takes a lot of patience and dedication.
