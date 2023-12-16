# Used Car Pricing Analysis

I conducted an assessesment of the factors contributing to used car prices. Based on these analyses, I will provide insights that can guide my client (a used car dealership) on what consumers value in a car. This could have implications to the clients supply strategy, inventory strategy, and future revenue growth strategy as a business.

The following summary follows the CRISP-DM framework, meant to characterize and define the problem prior to building models.
Notebook can be found here: https://github.com/quangg89/usedcar/blob/main/Used%20Car%20Pricing%20Analysis.ipynb

**Business Understanding:**

The core business question is to understand what makes a car more or less expensive / what customers value in a car. The downstream question behind this is -- by using datasets and modelling, can our client use this information to guide their business strategy (as a used car dealership)?

**Data Understanding**

There are multitudes of used car data from various sources. The provided Kaggle dataset included many variables - some numerical, some categorical. 

 0   id - removed             
 1   region - removed        
 2   price - boxplot          
 3   year - boxplot         
 4   manufacturer - bar chart  
 5   model          
 6   condition - bar chart     
 7   cylinders - bar chart     
 8   fuel - bar chart          
 9   odometer - box plot     
 10  title_status - bar chart   
 11  transmission   
 12  VIN - removed            
 13  drive - bar chart          
 14  size - removed          
 15  type - bar chart           
 16  paint_color - removed    
 17  state - removed     

Having a look at the data prior to preparation was insightful. I looked at the initial pricing distribution which showed a large range of prices. This implied that we would need to focus / filter the input data to have a usable model given the limited sample in the outer ranges of price.

I also visualized categorical variables to understand the distribution by manufacturer, condition, cylinders, fuel, title status, transmission, and type. This enabled understanding of how the data may need to be manipulated / filtered prior to building the models. The interesting assumption here is that type of car would play a big role on cylinders and drive. I was unsure on impact of fuel, transmission and was curious to investigate further.

From these visualizations, the distribution for each of the categories, and sample sizing for each guided decision on data preparation.

**Data Preparation**

After looking at the architecture of the dataset, there were multiple data preparation steps prior to modelling.

I first created filters for certain types of cars based on price + mileage + age to try to reduce the impact of outliers. From the distribution visualizations earlier, I had a sense of where to establish some filtering parameters. I then conducted some inference steps for filling data gaps (median / mode) given the data gaps, particularly in categories that had >60% sample. 

For categorical variables, the initial iteration over-selected factors and one-hot encoding too many variables made the model cumbersome -- multiple simplifying assumptions were made in order to avoid this. As an example, I deprioritized location (region / state) of the car. This is because of the rise of online marketplaces and the relatively affordable shipping for vehicles for cross-state title transfer. I removed other columns that should not have a direct relationship with the price including the ID / VIN. I also assumed that car color is not a major driver as it could be re-painted relatively easily.

**Modelling**

I employed multiple regression techniques, including Lasso, Ridge, and Linear Regression to develop our initial models. 
Particular attention was paid to the R² values in linear regression to understand the influence of different factors on pricing. 

Work can be seen in the ipynb file.

**Evaluation**

This phase also involved reassessing the initial filtering criteria for selecting cars in our dataset. The impact of outliers or car selection on model performance is extremely important and was refined after a couple modifications. 

For the models, I used RMSE to assess which models may offer the best insight into used car pricing. All 3 models demonstrated <8000 RMSE - this number could be further refine in additional iterations of the models, through different filtering, and different parameter optimization. In my assessment, evaluation stage focused on applying alpha parameter optimization and k-fold analysis to assess if RMSE could further be reduced.

Work can be seen in the ipynb file.

**Recommendations**
Returning back to our central questions -- what are the factors that make a car more or less expensive? What do customers value in a car, and are wliling to pay for? Our assessment of the dataset provides several insights that can inform our client on their business strategy. 

The models offer valuable insights into what attributes make a car more or less expensive. The first insight for the client is to decide what will be assessed model-based vs. which may be outliers, such as antique or high-durability cars, which might deviate from standard pricing patterns. Models are good only insofar as there is adequate robust data to support the model. For more custom purchases, the price may be decided by customer willingness to pay and may require customized research.

For more standard cars, the analysis suggests that age and mileage are significant price determinants, but there are potential value pockets. For instance, older cars with low mileage present a unique value proposition that may still have extreme durability. Newer cars with lower mileage could mimic the new car market (e.g., post-lease market) which could be impacted by new car sales dynamics. Older cars with high mileage may be more dependent on the manufacturer reputation for durable cars (e.g., Toyota) -- the buyer may be considering cost of maintenance, remaining miles on car prior to next purchase. Ultimately, the age and mileage are related to the car's ability to get the customer from point A to point B until the car no longer works.

Customer segmentation data would also be extremely useful for the remaining factors including manufacturer, type, model. The type of car may depend on the use case for the purchaser -- going to work, going to soccer practice, carrying work tools, luxury cars. The type is related to some of the other factors that impact performance. Customer segmentation for in-person purchases (smaller universe, local demographic data) vs online purchars (larger universe) could also help inform which inventory goes in the front row or on the advertisements. Another consideration is that some cars may not fetch a high price but move a higher volume which could be assessed in future analyses (e.g., Toyota Camry vs. Ford F150).

The dealership should also consider broader market trends and external factors that may impact ability to predict future car prices based on historical sales. Some examples of recent context are the increase in new car pricing due to rising cost of materials,  electric vehicle incentives. These could either help or hurt used car pricing -- by the time our client would built an inventory, certain exogenous factors could have changed, impacting their business strategy.

For future steps, additional work can be done on the current dataset to see if it impacts model optimization. Filling data gaps with median / mode can work, but we could consider removing rows altogether. The filtering parameters could also be modified if there is a specific focus for our client (e.g., European luxury cars vs. trucks vs. any type of car. Further model optimization can also be done in these revised datasets (e.g., k fold, alpha).

The client should consider expanding datasets to include other sources -- historical, other current reference, and current sale. Historical datasets may look similar to the Kaggle dataset that was analyzed. Current references could include sources like KBB, where API would allow quick data integrations. Current sale could leverage web scrapers to build a database of current pricing -- this would enable accounting for current market trends to complement historical datasets.

