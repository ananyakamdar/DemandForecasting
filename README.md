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
