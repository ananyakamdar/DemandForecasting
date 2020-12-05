# Demand Forecasting

I recently participated in [Analytics Vidhya's Demand Forecasting Hackathon](https://datahack.analyticsvidhya.com/contest/janatahack-demand-forecasting/) where the aim was to forecast the demand for every product-store combination accurately, given the historical sales and promotional information.

## Dataset description and Evaluation metric

The data consists of sales records at 76 different stores for the past 3 years on a week-on-week basis. The variables in the dataset are as follows:
* **record_ID** - Unique ID for each week store sku combination
* **week** - Starting Date of the week
* **store_id** - Unique ID for each store (no numerical order to be assumed)
* **sku_id** - Unique ID for each product (no numerical order to be assumed)
* **total_price** - Sales Price of the product 
* **base_price** - Base price of the product
* **is_featured_sku** - Was part of the featured item of the week
* **is_display_sku** - Product was on display at a prominent place at the store
* **units_sold (Target)** - Total Units sold for that week-store-sku combination

The evaluation metric for this competition is **100*RMSLE** (Root Mean Squared Log Error).

## Exploration of data and Feature Engineering

Key takeaways:
* Number of unique SKUs and stores is low, indicating a possibility of creating models particular to each SKU-store combination for better prediction
* Correlation between Total price and Base price is extremely high, so one of them can be removed to avoid multicollinearity
* Certain records have extremely high number of units sold

New variables created:
* **price_diff** - Difference between total_price and base_price
* **feat_disp** - Sum of is_featured_sku and is_displayed_sku
* **One Hot Encoding of the Year**
* **One Hot Encoding of the Month**

## Approach

To predict the units sold, five algorithms (**Linear Regression, Random Forest Regression, XGBoost Regression, CatBoost Regression and Light GBM Regression**) were each used on different subsets of the data which are as follows:

**1. Using original features** - Features used: store_id, sku_id, total_price, base_price, is_featured_sku, is_displayed_sku

**2. Removing base_price from original features** - Features used: store_id, sku_id, total_price, is_featured_sku, is_displayed_sku

**3. Using original and new features** - Features used: store_id, sku_id, total_price, base_price, is_featured_sku, is_displayed_sku, price_diff, feat_disp, one hot encoded variables for year and month

**4. SKU-Store combination subsets using original features** 

**5. SKU-Store combination subsets using original features (except base_price)** 

**6. SKU-Store combination subsets using original and new features** 

Submissions are made for the predictions of each algorithm-data subset combination and parameters are tuned to achieve the best score. 

## Results

My rank on the Public Leaderboard was **22 out of 13500+ participants**, with a score of 396.43606. On the Private Leaderboard my rank was 38 with a score of 457.48456
