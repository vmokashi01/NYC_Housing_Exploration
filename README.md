# NYC_Housing_Exploration
An exploration of the NYC Property Sales dataset from Kaggle. 

I used the Kaggle dataset on NYC property sales in order to conduct data analysis - this included the creation of Tableau dashboards to accompany the various regression models within the notebook. 

# Introduction

The project is centered around exploring what factors and trends exist within the NYC housing markets. I centered my exploration on a guiding question: what factors most prominently affect the selling price of properties in NYC?

Various other questions continued to sprout throughout the exploration process - I will highlight my stream of questions and analysis below.

# Data Cleaning

I initiated the project by removing empty or indexing columns as well as replacing empty fields with the none type. Within the sales price field, I replaced empty rows with a 0 (I later dropped all rows with a sales price below $1000 in order to remove property transfer entries that were represented in the dataset as sales). Next, I cleaned the data types of the columns in order to match the nature of the data that was being represented.

# Data Exploration
## Initial Overview

I began by creating a heatmap of the features and their correlation to the sales price. I made scatterplots of the top three features with relation to sales price while colouring them by the borough. 

## Sale Price

I used a boxplot to visualize the distribution of the data with respect to the sale price. Using the boxplot, I removed outliers and points used to represent a transfer of property as opposed to a sale (i.e. those that had an extremely low sale price). 

I created a histogram to better understand the distribution of the sale price; from here, it was evident that the sale price data was heavily skewed right.

## Numerical Features
### Gross & Land Square Feet

Boxplots were created to visualize the distribution and outliers were then removed. Scatterplots (against sale price) were then created for each, with the borough being used as the colour. 

Questions for further analysis arose at this point - it appeared that both gross and land square feet formed distinct clusters based on the borough, with distinct regions. For example, Brooklyn seemed to have lower square footage but higher sale prices relative to Staten Island, which had similar gross square footage but higher land square feet at a lower sale price, while Queens fell between the two. 

What distinct housing patterns based on the Borough could be leveraged to further understand the sale price?

### Residential, Commercial, & Total Units

I began with a scatterplot of the total units against sale price with the borough as the colour. I removed an outlier at 2000+ units and any entries where the total units was 0. I then created boxplots of the three features against the sale price. 

All three seemed to have a relatively steady trend of increasing median sale price as the number of units increased, however, the range of the sale price at each number of units was fairly large. 

## Categorical Variables
### Borough & Neighborhood

I used a pivot table to examine the mean sale price of each neighborhood and borough. I then used a barplot to chart both neighborhood and borough against sale price, which highlighted the difference in property price - Manhattan was by far the most expensive, followed by Brooklyn, Queens, and Staten Island. The Bronx had the lowest mean property price. 

A number of questions arose:

How do the number of units within each neighborhood/borough differ? Are more expensive boroughs filled with fewer, but more pricey properties? Are less expensive boroughs concentrated with smaller sized units or are they priced lower due to other factors?

### Building Class Category

I followed a similar process (created pivot tables and barplots) to examine the building class categories, the class at present, and the class at the time of sale. With regards to categories, rental apartments, homes, and lofts were the most expensive respectively.

The highest mean prices for the building class at present and at the time of sale were for Libraries (P8), Hospitals (I4), and Elevator Apartments (D#).

Questions that arose:

Are the concentration of the building class categories different by the borough (i.e. are cheaper building categories more heavily concentrated in specific boroughs)? Does a recategorization of the building class affect the sale price?

### Tax Class 

Once again, I created a series of pivot tables and barplots to explore the mean sale price for each category within the tax class at present and at the time of sale. There are several more categories of tax classes within the tax class at present field which prompted an exploration as to why such a drastic difference exists - has there recently been an update into the NY property tax class system?

### Sale Date

A lineplot was used to visualize sales throughout the one-year period. It appears that sales stayed relatively constant throughout the year, with a few exceptions which are likely explained by a high value property purchase.

# Modelling

I dropped the address, apartment number, and sale date features due to the apparent lack of correlation.  I log-transformed numerical data with a skew 0.75 over prior to any modelling. The numerical data was then scaled using the Standard Scaler to prepare for modelling. The categorical features were one-hot encoded in order to represent them numerically prior to the modelling. 

I used five regression models (Linear, Ridge, Lasso, Elastic Net, and Random Forest) to test which would work the best. Models were assessed using root mean squared error. Of the models, the Random Forest Regressor worked the best, with an RMSE of 0.71 and an R-squared of 0.5. 

Note: the regular linear regression model had astronomically abysmal scores which rose a flag for exploring the methodology used to pre-process the data. 

# Next Steps

In the future, I am going to explore how properties with changes in the building class and tax class have affected sale price as well as whether the sales date had any influence on the sale price.

# Resources
The notebook is based heavily off the following resource: https://www.kaggle.com/sahilrider/learn-regression-nyc/notebook
