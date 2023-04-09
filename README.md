### INTRODUCTION

This project investigates the relationship between the occurrence of crime and the housing price in different areas of Queens. Generally, a safe neighborhood with lower crime rate would have higher property value. The dataset includes larceny, burgalry, assulault and sexual harrassment crime rate for each zipcode in Queens. We will explore which kind of crime has a greater effect on the sale price of a house. We will also use neighborhood information to make choropleth graphs to illustrate the sale price in Queens county as a whole.

---

### DATA COLLECTION

I use data originally collected from NYC Department of Finance on property sales in Queens County from January to December 2022. Also, I use NYC OpenData for valid felony, misdemeanor, and violation crimes reported to the New York City Police in December 2022. Further, I added population data for zipcodes in Queens from New York Demographics. After cleaning the data files, I calculate the crime rates for each zipcode in Queens and add them to the home sale file.
To investigate how different type of crimes affect housing price, the linear regressioin model appears below:
sale per sqft=β0 + β1*total units + β2*gross square feet + β3*property age + β4*larceny_rate + β5*assualt_rate + β6*harassment_rate + β7*burglary_rate + β8*population

- total units: The total number of units at the listed property.
- gross square feet: The total area of all the floors of a building, including the land area
- property age: age of the property sold
- larceny_rate: number of larceny complaints in a zipcode area divided by total complaints in Queens
- assualt_rate: number of assualt complaints in a zipcode area divided by total complaints in Queens
- harassment_rate: number of harassment complaints in a zipcode area divided by total complaints in Queens
- burglary_rate: number of burglary complaints in a zipcode area divided by total complaints in Queens
- population: population in a zipcode area

<p align="center">
  <img src="images/H19.png" />
</p>
> Descriptive Statistics

<p align="center">
  <img src="images/H20.png" />
</p>
> Histograms for crime rates
