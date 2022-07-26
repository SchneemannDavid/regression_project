# Predicting Home Value for Zillow


## About the Project
### Project Goals

My goal with this project is to identify Zillow's key drivers of home value and to provide insight into why and how these factors are producing certain home values. With this information and the following recommendations, our organization can work together to improve business processes and procedures in order to more accurately predict home values moving forward.


### Project Description

At Zillow, the ability to predict home value is essential as new homes are built each year and some existing homes don't currently have assessed value within this database.

In order to more accurately predict home value, we will analyze the attributes (features) of homes within a predetermined set of data. This dataset includes Single Family Properties that had a transaction during 2017.
We will then develop models for predicting home value based on these attributes and provide recommendations and predictions to Zillow for improving prediction of home values moving forward.


### Initial Questions

#### 1. Does a higher number of bedrooms increase home value?

- Ho = More bedrooms translates to <= home value
- Ha = More bedrooms translates to > home value

#### 2. Does a higher number of bathrooms increase home value?

- Ho = More bathrooms translates to <= home value
- Ha = More bathrooms translates to > home value

#### 3. Do more garage spaces increase home value?

- Ho = More garage spaces translates to <= home value
- Ha = More garage spaces translates to > home value

#### 4. Does county location affect home value?

- Ho = Population Means of the Home Values for Orange county, LA County, and Ventura County are all equal
- Ha = Population Means of the Home Values for Orange county, LA County, and Ventura County are NOT all equal

#### 5. Does a higher square footage increase home value?

- Ho = More sq_ft translates to <= home value
- Ha = More sq_ft translates to > home value



### Data Dictionary

| Variable      | Meaning |
| ----------- | ----------- |
| home_value      | The total tax assessed value of the parcel       |
| bedrooms   | The total number of bedrooms in a home        |
| bathrooms      | The total number of bathrooms in a home       |
| garage_spaces      | The total number of car slots in a garage       |
| year_built      | The year the home was built       |
| location      | Location of a home by county      |
| sq_ft      | The total square feet of a home       |
| lot_sq_ft      | The total square feet of a property lot       |
| decade_built   | The decade in which the home was built       |



### Steps to Reproduce (edit)

1. You will need an env.py file that contains the hostname, username and password of the mySQL database that contains the zillow dataset. Store that env file locally in the repository.
2. Clone my repo (including the acquire_telco.py, prepare.py and split_telco.py) 
   (confirm .gitignore is hiding your env.py file)
3. To acquire the zillow data, I used the zillow_db in our mySQL server. I selected all columns from the properties_2017 table. I then joined this table with the propertylandusetype and predictions_2017 in order to narrow our data to reflect Single Family Properties that had a transaction during 2017. 
4. Libraries used are pandas, matplotlib, seaborn, numpy, sklearn, scipy, and model. A full list of modules with specific tools are provided in my Full Report.
5. Following these steps, you should be able to run the full report


### The Plan (edit)
Below, I walk through all stages of my pipeline and process.

#### Wrangle
##### Modules (acquire_telco.py + prepare.py + telco_split.py)

1. Test acquire function
2. Add to acquire_telco.py module
3. Write and test function to clean data
4. Add to prepare.py module
5. Write and test function to split data
6. Add to split_telco.py module

#### Explore

1. Ask 4 distinct questions of our data \
  a. Do M2m customers churn more than 1-yr or 2-yr customers? \
  b. Does paying by electronic check influence churn? Do customers paying by electronic check churn more than other        payment types? \
  c. Do customers with Fiber churn more than other internet service types? \
  d. Do adults with dependents churn more than adults without dependents? Furthermore, are single adults more likely to churn than customers with a partner? \
2. Explore these questions through visualizations \
  a. Barplots are used primarily due to our features being categorical variables \
  b. These plots illustrate statistical significance of our chosen features \
3. Statistical Testing is conducted on all relevant features to determine statistical significance \
4. Summary includes key takeaways from all features explored \

#### Modeling and Evaluate

1. Select Evaluation Metric: Accuracy
2. Evaluate a Baseline: ~73%
3. Develop 3 distinct models
4. Evaluate on Train and then on Validate (for promising feature sets)
5. Once a top performing model is selected, evaluate on test dataset


### Conclusion (edit)

#### Summary

In seeking solutions to Telco's churn, we have explored a multiplicity of factors in the dataset that affect churn rate. We have shown that some potential primary drivers of churn are :

- Having a month-to-month contract
- Paying by electronic check 
- Paying for fiber internet
- Having a contract as a single adult, without a partner or dependents.

The statistical significance of these features, combined within our analysis and models, expresses 95% confidence in the validity of our findings. With the addition of the other features within contract type, payment type, internet type, and family type, we have created robust models that perform significantly better than our baseline of 73%.

Having fit the best performing model to our train, validate, and test datasets, we expect this model to perform with 80% accuracy in the future on data it has not seen, given no major changes to our data source.

#### Recommendations

There are a number of recommendations that can be offered based on the above analysis. These suggestions are tied directly to the findings within each of our primary drivers of churn:

1. Month-to-Month contracts (m2m) - Although month-to-month contracts are here to stay, we could feasibly limit churn by offering a discount on 1 and 2 yr contracts. By offering a discount that still maintains a healthy profit margin, we could incentivize customers to sign on for longer contracts which is shown to reduce churn in the long term.

2. Electronic check (e_check) - We have shown that churn is significantly higher for electronic check customers than any other payment type. Although there are multiple potential solutions to this phenomenon, I believe Telco needs to perform a full review of the customer process for submitting payment via electronic check. It is my experience that online portals for submitting payment by e-check can be inefficient, not well designed, and frustrating to the user. This could be a significant reason why customers who use this method of payment are cancelling their contracts.

3. Fiber internet - Customers with this internet type express a significant likelihood of churn, despite Fiber being the optimal option for internet access. Although fiber is undoubtedly more expensive to implement, due to infrastructure costs, the amount of potential churn of this internet type needs to inform our business practices. Options include a potential discount for fiber customers if this is profitably viable. Otherwise, increased company investment in fiber infrastructure may lead to increased profit margin down the road, allowing the company greater leverage for retaining these customers. 

4. Customers with no partner or dependents (no_pod) - This customer demographic has a significant likelihood of churn. Yet, attempting to retain these customers may not be the most effective option for maximizing customer retention. Instead, by observing the likelihood of churn for other partner/dependent statuses, we find that customers with dependents are less likely to churn. Therefore, offering a family discount for those customers who have dependents could attract more customers who fall under this demographic. This customer base has shown to be less likely to churn, thus decreasing potential churn by attracting more stable and committed customers.

#### Next Steps

Despite the overall effectiveness of our best-performing model, there is always room for improvement and optimization. \
If given more time to pursue a better results, I would begin by further exploration and analysis of other features within our dataset. Through additional exploration I've already performed, I can say with confidence that there are a number of features I could analyze and implement into my models to improve prediction accuracy. \
Namely, observing features such as whether a customer has online security or tech support could improve our models' predictions.

Additionally, prompting customers who churn to fill out a simple satisfaction survey could produce meaningful insight into more specific reasons customers choose to cancel their contracts. This information could be analyzed using methods such as Natural Language Processing in order to improve Telco's understanding of its customers' needs and the resulting customer service they provide.


