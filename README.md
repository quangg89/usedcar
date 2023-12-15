# Used Car Pricing Analysis

I conducted an analysis to assess which factors drive used car price. Based on these analyses, I will provide insights that can guide my client (a used car dealership) on what consumers value in a car. This could have implications to the clients supply strategy, inventory strategy, and future revenue growth strategy as a business.

The following summary follows the CRISP-DM framework, meant to characterize and define the problem prior to building models.

**Business Understanding:**
The core business question is to understand what makes a car more or less expensive / what customers value in a car. The downstream question behind this is -- if this can be informed by data / modelling, can our client use this information to guide their business strategy (as a used car dealership). 

**Data Understanding / Preparation**
There are multitudes of used car data from various sources. The Kaggle dataset we have access to included many variables - some numerical, some categorical. After looking at the architecture of the dataset, there were multiple data inference steps, and simplification steps to ensure a robust analysis could be conducted. 

Given pricing is our desired outcome output, I visualized the price distribution of the dataset. This gave me a sense on potential outliers to account for. One may assume that cars of ultra high value (e.g., >250k) would require a more custom approach, and have factors that may not be included in the dataset (prestige, limited edition) - the willingness to pay is more unique to the buyer. Similarly, I excluded cars with ultra high odometers and/or cars that are quite old given the type of buyer may be different than the conventional buyer and may see value differently.

Other logic I applied is that purchases may be relatively location agnostic (to a state level). This is because shipping for purchases is relatively affordable, and shipping cars across states is commonplace with online marketplaces. Colors of cars may be easy to change, and gasoline types are available at gas stations. Additional logic steps can be seen in the notebook.

Once I made some simplifying assumptions, I conducted multiple steps were involved in preparing the data. This involved filling gaps for numerical figures with medians / modes, one-hot encoding certain categorical variables.

**Modelling**
From here, I created initial models using various regression techniques -- Lasso, Ridge, and Linear. I wanted to assess in a couple ways to ensure that the client receives the best model to inform the ultimate recommendations. 




**Evaluation**
I then started evaluating the models to ensure that they were optimized. This involved playing with certain parameters to assess if the models could be improved from the initial pass.

**Recommendations**
Returning back to our central questions -- what are the factors that make a car more or less expensive? What do customers value in a car, and are wliling to pay for? Our assessment of the dataset provides several insights that can inform our client on their business strategy. A couple of themes:

Durability / Utility Factors:

Impact of Brand:

Impact of Geography:

Other Factors:


