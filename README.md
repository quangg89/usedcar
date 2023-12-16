# Used Car Pricing Analysis

I conducted an analysis to assess which factors drive used car price. Based on these analyses, I will provide insights that can guide my client (a used car dealership) on what consumers value in a car. This could have implications to the clients supply strategy, inventory strategy, and future revenue growth strategy as a business.

The following summary follows the CRISP-DM framework, meant to characterize and define the problem prior to building models.

**Business Understanding:**

The core business question is to understand what makes a car more or less expensive / what customers value in a car. The downstream question behind this is -- if this can be informed by data / modelling, can our client use this information to guide their business strategy (as a used car dealership). 

**Data Understanding**

There are multitudes of used car data from various sources. The Kaggle dataset we have access to included many variables - some numerical, some categorical. 

Having a look at the data prior to preparation was insightful. I looked at the initial pricing distribution which showed a large range of prices. This implied that we would need to focus / filter the input data to have a usable model given the limited sample in the outer ranges of price.

I also visualized categorical variables to understand the distribution by manufacturer, condition, cylinders, fuel, title status, and transmission. This enabled understanding of how the data may need to be manipulated / filtered prior to building the models. The interesting assumption here is that type of car would play a big role on cylinders and drive. I was unsure on impact of fuel, transmission.

**Data Preparation**

After looking at the architecture of the dataset, there were multiple data preparation steps prior to modelling.

This involved filtering for certain types of cars based on price + mileage + age, removing columns that may not have a major role (e.g., cars can be shipped, titles transferred across state borders), inference steps for filling data gaps (median / mode), and one-hot encoding certain categorical variables that may play a role. In initial iterations, over-selecting factors and one-hot encoding too many variables made the model cumbersome and so multiple simplifying assumptions were needed.

**Modelling**

We employed multiple regression techniques, including Lasso, Ridge, and Linear Regression, to develop our initial models. Particular attention was paid to the R² values in linear regression to understand the influence of different factors on pricing. 

Work can be seen in the ipynb file.

**Evaluation**

This phase also involved reassessing the initial filtering criteria for selecting cars in our dataset. The impact of outliers or car selection on model performance is extremely important and was refined after a couple modifications. 

For the models, we used RMSE to assess which models may offer the best insight into used car pricing. All 3 models demonstrated <8000 RMSE - this number could be further refine in additional iterations of the models, through different filtering, and different parameter optimization. In my assessment, evaluation stage focused on applying alpha parameter optimization and k-fold analysis to assess if RMSE could further be reduced.

Work can be seen in the ipynb file.

**Recommendations**
Returning back to our central questions -- what are the factors that make a car more or less expensive? What do customers value in a car, and are wliling to pay for? Our assessment of the dataset provides several insights that can inform our client on their business strategy. 

The models offer valuable insights into what attributes make a car more or less expensive. The first insight for the client is to decide what will be assessed model-based vs. which may be outliers, such as antique or high-durability cars, which might deviate from standard pricing patterns. Models are good only insofar as there is adequate robust data to support the model. For more custom purchases, the price may be decided by customer willingness to pay and may require customized research.

For more standard cars, the analysis suggests that age and mileage are significant price determinants, but there are potential value pockets. For instance, older cars with low mileage present a unique value proposition that may still have extreme durability. Newer cars with lower mileage could mimic the new car market (e.g., post-lease market) which could be impacted by new car sales dynamics. Older cars with high mileage may be more dependent on the manufacturer reputation for durable cars (e.g., Toyota) -- the buyer may be considering cost of maintenance, remaining miles on car prior to next purchase. Ultimately, the age and mileage are related to the car's ability to get the customer from point A to point B until the car no longer works.

Customer segmentation data would also be extremely useful for the remaining factors including manufacturer, type, model. The type of car may depend on the use case for the purchaser -- going to work, going to soccer practice, carrying work tools, luxury cars. The type is related to some of the other factors that impact performance. Customer segmentation for in-person purchases (smaller universe, local demographic data) vs online purchars (larger universe) could also help inform which inventory goes in the front row or on the advertisements. Another consideration is that some cars may not fetch a high price but move a higher volume which could be assessed in future analyses (e.g., Toyota Camry vs. Ford F150).

The dealership should also consider broader market trends and external factors that may impact ability to predict future car prices based on historical sales. Some examples of recent context are the increase in new car pricing due to rising cost of materials,  electric vehicle incentives. These could either help or hurt used car pricing -- by the time our client would built an inventory, certain exogenous factors could have changed, impacting their business strategy.

For future steps, the client should consider expanding datasets to include other sources -- historical, other current reference, and current sale. Historical datasets may look similar to the Kaggle dataset that was analyzed. Current references could include sources like KBB, where API would allow quick data integrations. Current sale could leverage web scrapers to build a database of current pricing -- this would enable accounting for current market trends to complement historical datasets.

