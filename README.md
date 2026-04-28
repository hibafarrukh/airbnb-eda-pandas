# 🏡 Airbnb Data Cleaning & Exploratory Data Analysis (EDA)

## 📌 Project Overview

This project focuses on cleaning and analyzing an Airbnb dataset using **Python (Pandas, NumPy, Matplotlib, Seaborn)**.

The goal was to:

* Clean and preprocess raw Airbnb data
* Handle missing values and inconsistent formats
* Explore relationships between features
* Extract insights using visualizations

---

## 📂 Dataset

The dataset contains Airbnb listings with features such as:

* Price
* Room type
* Neighbourhood group
* Availability
* Reviews
* Host-related information

---

## 🧹 Data Cleaning Process

The dataset required multiple preprocessing steps before analysis:

### 1. Initial cleaning and manipulation

* Checked dataset structure using `.info()` and `.describe()`
* Identified missing values and data types.
* Ensuring no duplicates and handling missing values, like reviews per month where number of reviews was 0 and filling the last_review* *date with a placeholder value and making a boolean called has_last_review 
* Inspected column relevance; removed columns that were not useful for analysis and focused. on features relevant to pricing and availability
* Converted columns to appropriate data types, like  Converted price values to numeric format  
* Ensured numerical columns were usable for analysis, eg  Removed symbols like `$` and commas
* Checking if numeric values are skewed.

 

### **2. Checking correlation and multicollinearity.** 

  

* Using .corr() revealed direct correlation of the features against price was very low. Heatmap showed no strong correlation with features either.
* variance_*inflation_*factor showed that multicollinearity is extremely high for latitute and longitude, so dropped those columns as they do not represent distance in a linear way. Instead, created a single feature: distance to Times Square, which captures location effect more meaningfully.

  

 

  

---

## 📊 Exploratory Data Analysis (EDA)

After cleaning, the dataset was analyzed using visualizations and comparisons.

### 1. Univariate Analysis

* Identified price outliers using boxplot.
*  Applied log1p transformation to numeric columns to correct skew, and visualized the difference using histplots.

---

### 2. Bivariate Analysis

###     a. Room Type vs Price: which types of rooms are most expensive?

* Entire home/apartment listings have the highest average price
* Private rooms are moderately priced
* Shared rooms are the cheapest
* Entire homes also show a wider price range, indicating variability in property quality and location.
* Visualization used: boxplot and barplot.

###   b. Neighborhood Group vs Price: how does price vary with different neighborhood groups, and does room type play a role?

* Manhattan consistently has the highest prices across all room types
* Brooklyn follows as the second most expensive
* Queens, Bronx, and Staten Island have relatively similar and lower pricing
* This suggests that **location plays a major role in pricing.**
* Visualization used: barplot

###    c. Price Distribution vs Number of Reviews: is there any correlation between price and number of reviews?

* Airbnbs that cost < 200 have the greatest number of reviews, indicating that higher reviewed listings are generally more affordable. 
* As price increases, number of reviews decreases, suggesting either fewer bookings or a niche market.
* Visualization used: scatterplot

###   d. Geographical location and room types: which locations are more popular for specific room types?

* Entire homes are dominant across all areas. Similarly, private rooms are also widespread and common.
* Shared rooms are the least common across all areas.
* Visualization used: scatterplot

### 3. Hypothesis Testing

* Hypothesis:  Entire home/apt listings have significantly higher average prices than private or shared rooms. 

       Null hypothesis: Mean price of entire apt = Mean price of private rooms.                     Alternate: Mean price of entire apt > Mean price of private rooms

Used a two-sample t-test and converted to one tailed test. Since p value obtained was less than 0.05,  there is overwhelming statistical evidence that entire home listings on Airbnb are more expensive than private rooms.

  

  

---

## 🔍 Key Insights

*  Entire homes/apartments dominate the higher price range
*  Location significantly impacts price, with Manhattan being the most expensive
*  Price variation is high, especially for entire homes
*  Shared rooms remain the most affordable option across all areas
*  Pricing is influenced by multiple factors, not a single variable
