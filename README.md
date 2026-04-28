# 🏡 Airbnb Data Cleaning & Exploratory Data Analysis (EDA)

## 📌 Project Overview

This project focuses on cleaning and analyzing an Airbnb dataset using **Python (Pandas, NumPy, Matplotlib, Seaborn)**.

The goals of this project were to:

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

### 1. Initial Cleaning and Manipulation

* Checked dataset structure using `.info()` and `.describe()`
* Identified missing values and data types
* Removed duplicate records
* Handled missing values:

  * For `reviews_per_month`, missing values where `number_of_reviews = 0` were treated accordingly
  * Filled `last_review` with a placeholder value
  * Created a boolean feature `has_last_review`
* Inspected column relevance and removed unnecessary columns
* Focused on features relevant to pricing and availability
* Converted columns to appropriate data types:

  * Cleaned `price` by removing `$` and commas
  * Converted price to numeric format
* Checked for skewness in numerical features

---

### 2. Correlation and Multicollinearity Analysis

* Used `.corr()` to evaluate relationships between features

* Observed very low direct correlation between most features and price

* Heatmap confirmed lack of strong linear relationships

* Applied **Variance Inflation Factor (VIF)**:

  * Found extremely high multicollinearity between `latitude` and `longitude`
  * Dropped both features

* Engineered a new feature:

  * `distance_to_times_square`
  * This captures location influence more meaningfully than raw coordinates

---

## 📊 Exploratory Data Analysis (EDA)

After cleaning, the dataset was analyzed using multiple visualizations.

### 1. Univariate Analysis

* Identified price outliers using boxplots
* Applied `log1p` transformation to reduce skewness
* Compared distributions before and after transformation using histograms

---

### 2. Bivariate Analysis

#### a. Room Type vs Price

**Question:** Which types of rooms are most expensive?

* Entire home/apartment listings have the highest average price
* Private rooms are moderately priced
* Shared rooms are the cheapest
* Entire homes show a wider price range, indicating higher variability

**Visualizations used:** Boxplot, Barplot

---

#### b. Neighbourhood Group vs Price

**Question:** How does price vary across neighbourhoods?

* Manhattan has the highest prices across all room types

* Brooklyn is the second most expensive

* Queens, Bronx, and Staten Island show similar and lower pricing

* This suggests that **location is a major driver of price**

**Visualization used:** Barplot

---

#### c. Price vs Number of Reviews

**Question:** Is there a relationship between price and demand?

* Listings priced below 200 have the highest number of reviews
* As price increases, the number of reviews decreases
* This suggests:

  * More affordable listings receive more bookings
  * Expensive listings may cater to a niche market

**Visualization used:** Scatterplot

---

#### d. Location vs Room Type Distribution

**Question:** Which room types are common across locations?

* Entire homes dominate across all areas
* Private rooms are also widely available
* Shared rooms are the least common

**Visualization used:** Scatterplot

---

### 3. Hypothesis Testing

**Hypothesis:** Entire home/apartment listings have significantly higher prices than private rooms

* **Null hypothesis (H₀):** Mean price of entire homes = Mean price of private rooms

* **Alternative hypothesis (H₁):** Mean price of entire homes > Mean price of private rooms

* Performed a two-sample t-test and converted it into a one-tailed test

* **Result:**

  * p-value < 0.05
  * Reject the null hypothesis

* **Conclusion:**
  There is strong statistical evidence that entire home listings are more expensive than private rooms

---

## 🔍 Key Insights

* Entire homes/apartments dominate the higher price range
* Location significantly impacts pricing, with Manhattan being the most expensive
* Price variation is highest for entire home listings
* Shared rooms remain the most affordable option
* Pricing is influenced by multiple factors rather than a single variable

---

## 🚀 Future Improvements

* Add more feature engineering (e.g., demand indicators, price categories)
* Perform deeper statistical analysis
* Build predictive models for price estimation
* Explore advanced visualizations

---
