# DSND-Seattle-Airbnb

## Description
In this project for the Data Science Nanodegree, I have explored and analysed the Airbnb data of Seattle, in the superhost status and availability rate. As a frequent traveller on Airbnb, I have always wondered whether the superhost status would result in higher revenue (being more fully booked and being able to charge more). 

Superhost as explained on the Airbnb website - "The Superhost programme celebrates and rewards Airbnb’s top-rated and most experienced hosts. As a Superhost, you’ll have more visibility, earning potential, and exclusive rewards. It's our way of saying thank you for your outstanding hospitality." 

I have therefore posed the following questions to explore whether superhosts really help one earn more:

1. Are superhosts' properties more occupied (lower future occupancy) than non-superhosts'? For properties in the same neighbourhood and of similar size, how does availability compare?
2. Are superthosts' properties priced higher than non-superhosts? For properties in the same neighbourhood and of similar size, how does price compare?
3. Other than the superhost status (as a plausible factor), what are the top ten factors that affect future availability?


## Methodology 
This project follows the CRISP-DM process (Business Understanding, Data Understanding, Data Preparation, Modelling, Evaluation, Deployment). Details are narrated in the jupyter notebook and summarised in the blogpost. I will briefly explain the statistical test and model choices in the project.

##### Questions 1 & 2. 
Properties are split by room types, size and neighbourhood subsets. Kruskal test is carried out to test whether availabilities and price  distribution of superhost and non-superhost properties in each subset are from significantly different statistically. Kruskal test is chosen over ANOVA as the distribution of these variables are very skewed and not normally distributed and is only applied to subsets where both the number of superhost and non-superhost properties exceed 5.

##### Question 3.
Availability (for 30, 60, 90, 365 day in the future) are classified into 'high', 'medium' or 'low' based on their quartiles - top quartile is classed as 'high', 25th - 75th quartiles are 'medium' and bottom quartile is 'low'. Random-forest and gradient boosting based multi-output classification models are fitted to uncover the top ten most important features. Features are one-hot encoded and normalised before fitting into the model. A random forest model (70% training acuraccy; 55% testing accuracy) was ultimately chosen as it doesn't overfit as much as gradient boosting (which gives an accuracy of 100% on training set and 58% on testing).


## Findings

#### 1. There is not enough evidence to show that superhost properties have lower future availabilities (i.e. higher potential occupancy) in both the short and long term in Seattle.

Only 8 property subsets (room type, size and neighbourhood combinations) show significant differences (p-values below 0.05) between superhost and non-superhost properties. Unexpectedly, for these subsets, there is a larger propertion of superhost properties that have more availability than non-superhosts. 

The following example is Entire Home/Apartments with 1 bedroom in Downtown area - the blue chart represents the future 30-day availability of superhosts whilst the red represents non-superhosts.

![Q1_p1](/charts/entirehome-1brm-downtown-av30.PNG)

#### 2. There is only enough evidence to show superhosts price higher than non-superhosts in 8 property subsets in Seattle.

Only 8 subsets show significant difference in price distribution at significance level of 10% (p-values below 0.05). In these cases, superhosts properties are pricier than those that do not have such status. 

An example here is a one-bedroom Private Room in the Central Area, where blue represents the price distribution of superhost properties and red non-superhost properties.

![Q2_p1](/charts/privaterm-1brm-central-price.PNG)

#### 3. Top factors influencing availability are features related to past review frequency and timing, prices, response time and rate, and when the host started hosting on Airbnb.

The factors and their respective ranking influencing shorter term (30-/ 60-/ 90-) availabiltiies and long term (360) availability vary slightly, but are more or less the same. 

The number of reviews per month and the time of the latest review show higher relative importance in influencing short-term availability.

Top features influencing 30-day availability

![Q3_p1](/charts/featimp_30.PNG)

Top features influencing 365-day availability

![Q3_p2](/charts/featimp_365.PNG)

## Limitations
For Questions 1 and 2, there are insufficient data points in a lot of property subsets and so the test cannot be conducted for those samples. A potential mitigation method is to take random samples from both the superhost and non-superhost population that is representative of their room type, size and neighbourhood distribution and carry out statistical testing on a bigger set of data. Else, if panel data is available, we could understand whether a hosts' availability or pricing change significantly before and after getting the status.

For Question 3, the feature matrix is quite sparse due to tfidf transformation and hence some of the binary properties might not appear as an important feature. For future research, dimension reduction could be carried out and continuous variables can also converted to classes.



## Installations
Python 3.5 is used to create this project and the following libraries are used:

- Machine Learning Libraries: NumPy, Pandas, Sciki-Learn
- Statistics Libraries: Scipy, Statsmodel
- Natural Language Processing: NLTK
- Date time libraries: datetime, time


## Credits
Credits to Airbnb and Kaggle for providing the data - Seattle Airbnb Open Data is downloaded here.
