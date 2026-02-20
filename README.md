# Project Background
As a leading retail company in the B2C apparel space, **Meridian Retail Group** relies on high transaction volumes across diverse product categories, including Clothing, Accessories, Footwear, and Outerwear. The management team has noticed recent changes in purchasing patterns across demographics and sales channels, prompting a need to better understand customer shopping behavior.

Acting as a data analyst, my objective is to leverage this complete consumer dataset to uncover the key factors driving consumer decisions, repeat purchases, and long-term loyalty. By cleaning the data in Python, querying transactions in PostgreSQL, and building interactive visualizations in Tableau, this project provides stakeholders with actionable strategies to optimize marketing campaigns, inventory planning, and subscription positioning.

Insights and recommendations are provided on the following key areas:

- **Category 1:** Demographics & Customer Segmentation
- **Category 2:** Product Performance & Seasonality
- **Category 3:** Purchasing Behavior & Discounts
- **Category 4:** Subscription Velocity & Loyalty

The python code used to inspect and clean the data for this analysis can be found here [[link](https://github.com/kdy0820/shopping_behavior/blob/44b7ec22477ef807bd67a0dde09a206a7e9f6182/shopping_behavior.ipynb)].

Targed SQL queries regarding various business questions can be found here [[link](https://github.com/kdy0820/shopping_behavior/blob/44b7ec22477ef807bd67a0dde09a206a7e9f6182/shopping_behavior.sql)].

An interactive Tableau dashboard used to report and explore trends can be found here [[link](https://public.tableau.com/app/profile/keith.herrick.dy/viz/CustomerShoppingBehaviorAnalysis_17713824538000/Dashboard1?publish=yes)].


# Data Structure & Initial Checks

The company's data for this analysis consists of a master dataset with a total row count of 3,900 records representing individual purchases. To better understand the relational logic of the business, the data can be conceptually grouped into the following dimensions:
- **Demographics:** Contains customer details including Age, Gender, and Location.
- **Product:** Contains inventory details such as Item Purchased, Category, Size, and Color.
- **Transactions:** Records the financial metrics, including Purchase Amount, Season, and Shipping Type.
- **Behavioral:** Tracks engagement metrics such as Discount Applied, Previous Purchases, Frequency of Purchases, and Review Rating.

# Executive Summary

### Overview of Findings

Male customers and Young Adults are the primary absolute revenue drivers for the business. However, when evaluating the velocity of spend, our subscription model is quietly proving its worth, driving higher daily revenue generation and successfully increasing annual purchase frequencies for our Middle-aged and Senior demographics. Furthermore, a deeper look into seasonality reveals counter-intuitive product peaks (e.g., Outerwear peaking in the Fall rather than Winter), highlighting major opportunities to re-align our promotional calendars.


# Insights Deep Dive
### Category 1: Demographics & Segmentation

* **Main insight 1**: Male customers drove significantly more total revenue ($157,890) compared to female customers ($75,191).
  
* **Main insight 2**: Young Adults are the most lucrative demographic in terms of sheer volume, generating $62,143 in revenue, while Seniors contributed the least total volume at $55,763.
  
* **Main insight 3**: The vast majority of the customer base is highly established. 3,116 customers fall into the "Loyal" segment (more than 10 previous purchases).
  
* **Main insight 4**: Customer acquisition is currently a bottleneck. There are only 83 users classified as "New" customers, compared to 701 "Returning" customers.


### Category 2: Product Performance & Seasonality

* **Main insight 1**: Clothing is by far the highest-performing category in terms of overall revenue and volume, but it experiences significant seasonal fluctuation—peaking in the Spring ($27,692) and dipping lowest in the Summer ($23,078).
  
* **Main insight 2**: Outerwear is the lowest-performing overall category, but counter-intuitively peaks in the Fall ($5,259), drastically outperforming its Winter sales ($4,562).
  
* **Main insight 3**: The overall average product review rating across the entire catalog is 3.75 out of 5.00.
  
* **Main insight 4**: The top 5 highest-rated specific products are Gloves (3.86), Sandals (3.84), Boots (3.82), Hats (3.80), and Skirts (3.78).


### Category 3: Purchasing Behavior & Discounts

* **Main insight 1**: The overall average purchase amount across all transactions is $59.76.
  
* **Main insight 2**: Discounts do not inherently lower total spend. 839 customers applied a discount but still managed to spend above the overall average purchase amount.
  
* **Main insight 3**: Hats are the most heavily discounted items in the catalog, with a 50.00% discount rate, followed closely by Sneakers at 49.66%.
  
* **Main insight 4**: Customers using Express shipping have a slightly higher average purchase amount ($60.48) than those using Standard shipping ($58.46).


### Category 4: Subscription Velocity & Loyalty

* **Main insight 1**: While non-subscribers boast a slightly higher average basket size, subscribers generate higher daily revenue velocity, bringing in $2.48 per day compared to the non-subscriber average of $2.40 per day.
  
* **Main insight 2**: The subscription model successfully increases purchasing frequency for older demographics; Middle-Aged subscribers buy ~19.46 times a year (vs. 17.35 for non-subscribers), and Senior subscribers buy ~19.09 times a year (vs. 16.37).
  
* **Main insight 3**: Conversely, the subscription program fails to engage younger groups. Adult non-subscribers actually buy more frequently (18.35 times/year) than Adult subscribers (16.27 times/year).
  
* **Main insight 4**: Despite the financial viability of the subscription model, only 27% of the customer base is enrolled, representing a massive untapped expansion opportunity.


# Recommendations:
Based on the insights and findings above, we recommend the marketing and product management teams consider the following:

* **Targeted Subscription Marketing**: The data proves subscriptions successfully drive repeat purchases for Middle-aged and Senior demographics. We recommend targeting these segments heavily with subscription sign-up offers, while auditing the program to understand why it suppresses purchase frequency among younger adults.

* **Seasonal Inventory Realignment**: Outerwear peaks in the Fall, not Winter. We recommend shifting the bulk of the Outerwear marketing budget and inventory stocking to late Q3/early Q4 to capture this early demand.

* **Low New Customer Acquisition**: The data shows only 83 new customers versus 3,116 loyal ones. We recommend launching aggressive top-of-funnel marketing campaigns targeted at acquiring new users to ensure long-term pipeline health.

* **High Discount Rates on Specific Items**: Hats and Sneakers are heavily discounted (around 50%). We recommend reviewing the pricing and margin strategy for these specific items to ensure these discounts are actually driving profitable volume.

* **Shipping Preferences**: Express shipping correlates with a higher average spend ($60.48). We recommend offering subsidized or free express shipping thresholds (e.g., "Free Express Shipping over $75") to organically increase the average order value.


# Assumptions and Caveats:

Throughout the analysis, multiple assumptions were made to manage challenges with the data. These assumptions and caveats are noted below:

* **Assumption 1**: There were 37 missing records in the Review Rating column. These were imputed using the median rating of their respective product categories to prevent the loss of demographic data in those rows.
* **Assumption 2**: The promo_code_used and discount_applied columns contained identical boolean logic for every row. The promo_code_used column was dropped from the dataset to eliminate redundancy.
* **Assumption 3**: Customer segmentation was defined categorically: "New" = 1 previous purchase, "Returning" = 2-10 previous purchases, and "Loyal" = more than 10 previous purchases.
* **Assumption 4**: To measure spend velocity, avg_annual_purchases and revenue_per_day were calculated by standardizing categorical text strings like "Fortnightly" and "Quarterly" into specific day-count integers (e.g., 14 and 90, respectively).
