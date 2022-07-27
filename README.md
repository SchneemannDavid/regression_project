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



### Steps to Reproduce

1. You will need an env.py file that contains the hostname, username and password of the mySQL database that contains the zillow dataset. Store that env file locally in the repository.
2. Clone my repo (including the acquire_telco.py, prepare.py) 
   (confirm .gitignore is hiding your env.py file)
3. To acquire the zillow data, I used the zillow_db in our mySQL server. I selected all columns from the properties_2017 table. I then joined this table with the propertylandusetype and predictions_2017 in order to narrow our data to reflect Single Family Properties that had a transaction during 2017. 
4. Libraries used are pandas, matplotlib, seaborn, numpy, sklearn, scipy, and model. A full list of modules with specific tools are provided in my Full Report.
5. Following these steps, you should return the exact dataset I used to in my report.


### The Plan
Below, I walk through all stages of my pipeline and process.

#### Wrangle
##### Modules (acquire.py + prepare.py)

1. Test acquire function
2. Add to acquire.py module
3. Write and test function to clean data
4. Add to prepare.py module
5. Write and test function to split data
6. Add to prepare.py module

#### Explore 
##### Modules (explore.py)

1. Ask 5 distinct questions of our data \
  a. Does a higher number of bedrooms increase home value? \
  b. Does a higher number of bathrooms increase home value? \
  c. Do more garage spaces increase home value? \
  d. Does location by county affect home value? \
  e. Does a higher square footage increase home value? \
2. Explore these questions through visualizations, calling explore.py as needed \
  a. Barplots are used primarily due to our features being categorical variables \
  b. For our continuous variable, lmplots with line of best fit is used \
  c. These plots illustrate correlation of our chosen features with home value \
3. Statistical Testing is conducted on all relevant features to determine statistical significance \
4. Summary includes key takeaways from all features explored \

#### Modeling and Evaluate
##### Modules (model.py)

1. Select Evaluation Metric: Correlation, namely RMSE
2. Scale the data utilizing our model.py scaling function
3. Evaluate a Baseline: 272,118 (error in dollars)
4. Develop 3 distinct models
    a. Linear Regression
    b. Lasso Lars
    c. TweedieRegressor
5. Evaluate on Train and then on Validate (for promising feature sets)
6. Once a top performing model is selected, evaluate on test dataset


### Conclusion

#### Summary

In seeking solutions to more accurately predict home value for Zillow, we have explored a multiplicity of factors in the dataset that affect home value. We have shown that some potential primary drivers of home value are :

- The number of bedrooms in a home
- The number of bathrooms in a home 
- The number of garage spaces in a home
- The location of a home by county
- The square footage of a home

The correlation of these features with home value, combined within our analysis and models, expresses confidence in the validity of our findings. We have created robust models that perform significantly better than our baseline estimated error of 270,460.

Having fit the best performing model to our train, validate, and test datasets, we expect this model to perform 21% better than our baseline in the future on data it has not seen, given no major changes to our data source.

#### Recommendations

There are a number of recommendations that can be offered based on the above analysis. These suggestions are tied to the findings within our primary drivers of home value:

1. Based on our exploration of bedroom and bathroom counts, collecting additional data on how many rooms are in a home, including more specific data on living spaces versus kitchens and other spaces
2. Kitchen data, namely which major appliances and amenities are available in a given home. (ie. dishwasher, kitchen island, etc.)
3. In collecting more nuanced data about a home, I suggest we send out emails prompting home owners with limited data on their home in the Zillow database to provide additional details about their residence.

#### Next Steps

Despite the overall effectiveness of our best-performing model, there is always room for improvement and optimization. \
If given more time to pursue a better results, I would begin by conducting further exploration and analysis of other features within our dataset. These features could include:
- Whether a home has a pool
- The square footage of the property, not just the home

In addition to exploring other features, I would look into methods for more appropriately separating our data into additional housing categories. For example:
- Calculating a ratio of home square footage against square footage of the entire property. This home to property ratio could be valuable.
- Narrowing a home's location to pinpoint the city and specific neighborhood a home is in. 

By optimizing our dataset to include the above categories, I believe we could increase the correlation of our feature set with home value and improve model prediction accuracy.

