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
Properties are split by room types, size and neighbourhood subsets. Kruskal test is carried out to test whether availabilities and price  distribution of superhost and non-superhost properties in each subset are from significantly different statistically. Kruskal test is chosen over ANOVA as the distribution of these variables are very skewed and not normally distributed.

##### Question 3.
Availability (for 30, 60, 90, 365 day in the future) are classified into 'high', 'medium' or 'low' based on their quartiles - top quartile is classed as 'high', 25th - 75th quartiles are 'medium' and bottom quartile is 'low'. Random-forest and gradient boosting based multi-output classification models are fitted to uncover the top ten most important features. Features are one-hot encoded and normalised before fitting into the model.


## Findings

##### 1. There is not enough evidence to show that superhost properties have lower future availabilities (i.e. higher potential occupancy) in both the short and long term in Seattle.



## Installations
Python 3.5 is used to create this project and the following libraries are used:

- Machine Learning Libraries: NumPy, Pandas, Sciki-Learn
- Statistics Libraries: Scipy, Statsmodel
- Natural Language Processing: NLTK
- Date time libraries: datetime, time


## Credits
Credits to Airbnb and Kaggle for providing the data - Seattle Airbnb Open Data is downloaded here.
