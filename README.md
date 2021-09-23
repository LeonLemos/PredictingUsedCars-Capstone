![GA logo](https://user-images.githubusercontent.com/63846429/134559884-acdb53c9-af69-4a30-a52e-238ab0240ad2.png)

# PredictingUsedCars-Capstone
# Overview
My project creates a Machine Learning Model to detect which features are used to better predict used car prices. And also the effect that Covid-19 may have on these prices.

# Background
With the current world situation regarding shortage of auto semiconductor chips, demand for used car prices has skyrocketed. Since there has been a halt on the production of new cars, due to the factories inability to cope with the sudden demand to produce, after recent bans on transportation due to the Covid-19 Pandemic, consumers that want to avoid public transportation are now opting to buy their own cars to protect themselves. Now more than ever, there is a need for a new system to better understand what drives the prices of cars being bought or sold, and if the pandemic has had an influence in driving such prices. This project will benefit the average consumer, used car dealerships, and web services that estimate car prices using simpler models that prioritize speed instead of efficiency.


# Brief
To Run our project, I took a couple of steps :
- Firstly I must obtain the datasets and load them into Jupyter-Notebook.
- Secondly, we perform the exploratory data analysis and merge them into one unified dataset, through their common columns.
- Lastly, we run our chosen models on the dataset and analyse the results.



## Prerequisites
* Install Anaconda (https://docs.anaconda.com/anaconda/install/mac-os/) through the graphical install.

### Project Contents
- Obtain the Datasets. 
- Exploratory Data Analysis.
- Dataset Trend Analysis.
- Merge Datasets.
- Models.
- Findings.
- Conclusion.

#### Obtain Datasets
Download and load the datasets : 
https://www.kaggle.com/austinreese/craigslist-carstrucks-data
https://github.com/nytimes/covid-19-data


#### Exploratory Data Analysis
Used Vehicles Scraped Data. 
The first dataset was downloaded from Kaggle. The author scraped this data from craigslist for daily listings over the period of a month. It contains all relevant information that Craigslist provides on car sales including columns like price, year, manufacturer, posting_date, and 22 other categories. 

This dataset contains 426.880 observations.

<img width="1015" alt="Screenshot 2021-08-12 at 02 44 56" src="https://user-images.githubusercontent.com/63846429/133591841-61d8e911-e8c0-4edf-bdc3-59b27ed04646.png">

The final Vehicle Dataset after performing EDA and Data Munging. 
It contains 16 columns and 245.484 observations.

<img width="1012" alt="Screenshot 2021-08-12 at 02 54 40" src="https://user-images.githubusercontent.com/63846429/133591702-37e5dc44-f750-46e7-b1d6-c538fbd388fc.png">

Covid-19 Data in the United States.
The next dataset published here, is the daily cumulative number of cases and deaths, reported in every state across the U.S, since the beginning of the pandemic.
It is constantly updated live by the NYtimes Covid-19 bot.

It contains 5 features and 28.999 observations before the EDA and 4 features and 25.955 observations after the EDA.
    
  <img width="309" alt="Screenshot 2021-08-12 at 03 24 36" src="https://user-images.githubusercontent.com/63846429/133592039-1c4f2b47-b3ab-418b-84b1-274ab427e601.png"> → <img width="255" alt="Screenshot 2021-08-12 at 03 36 15" src="https://user-images.githubusercontent.com/63846429/133592594-a70e3526-b700-422d-b4b9-afde6feab2c4.png">

#### Dataset Trend Analysis
In the first dataset, we can clearly observe that prices are skewed to the right, representing a positive distribution. Meaning that cars are sold less, the higher their price is. Which makes sense, as people on the market for used cars are usually looking for the best value for money.

<img width="501" alt="trydown" src="https://user-images.githubusercontent.com/63846429/133594734-6466b871-4d2e-4973-a34d-60f6adbc8a2d.png">

In the second dataset, we can see that there is a positive correlation between covid cases and covid deaths in the US. 

As cases went down, so did the deaths. 

<img width="709" alt="covidcasesdeath" src="https://user-images.githubusercontent.com/63846429/133595035-d533b3b0-cde7-4148-933b-0abdb30ace32.png">

#### Datasets Merge
Our final dataset has all the features we consider relevant, resulting from the merge of the two previous datasets, we end up with 16 categories and 245.484 observations.

<img width="1012" alt="Screenshot 2021-08-12 at 04 19 06" src="https://user-images.githubusercontent.com/63846429/133593215-1d95fe16-c2be-4e0d-a9fd-7709c6597eaa.png">

#### Models
Since we are dealing with a regression problem, our models of choice were : 
Random Forest Regressor, Decision Tree Regressor, Bagging Regressor and we also implemented a Neural Network with deep Learning. 
As stated before, our objective is to obtain the R2 scores from each model and compare them. The Highest R2 Score is the best model fit.

![types-of-regression](https://user-images.githubusercontent.com/63846429/133595483-29c0b57b-aa24-4cbe-a2f2-ef5281311531.png)


#### Findings
By analyzing the feature scores from our best model, we can observe that covid cases and deaths are not very significant features to predict car prices.  They’re respective scores are 0.04 and 0.05. 
On the other hand, the vehicle’s year, odometer and model, play a significant role in predicting prices, their respective scores were 0.35, 0.18, 0.16.

01    |    Year - 0.35
02    |    Odometer - 0.18
03    |    Model - 0.16
04    |    Deaths - 0.05
05    |    Cases - 0.04

<img width="588" alt="features" src="https://user-images.githubusercontent.com/63846429/133595262-db39390d-ddd4-4c4d-88f6-d9fe5e3c7a8c.png">

#### Limitations
Given the lack of numerical features on our dataset, the numerical correlations were not very useful. Also the lack of wider datetime observations, limited us in some very insightful data. 

#### Challenges
A proper project cannot be done without the right data and since we were working with two datasets, it was important that they had common denominator columns, to make them possible to merge. In this case we used the “posting_date’’ and ‘’state’’ columns. We had to do some feature engineering to make sure that they had the same datetime format and also, use dictionaries to transform state names to their respective abbreviations.


#### Conclusion
Overall, our R2 score of 0.81, means that 81% of the data variance can be explained by our Random Forest model. This means that it generalizes well in predicting used car prices. Even though covid cases and deaths are not significant on their own, they were still useful in improving our model score from 0.80 to 0.81.


![Random-Forest-Regression](https://user-images.githubusercontent.com/63846429/133595366-05b1887d-43d2-441c-9819-2f84d3f2d841.png)


#### Future Work
A few other things we could have done to further improve our model's scores, would be to further optimize the parameters of our Deep Neural Network, to make it closer or superior to our Random Forest. Some more extensive EDA could have been done in the description and cylinder columns, given more time. Another method I would also like to try would be to implement Natural Language Processing, to identify words that could further predict our price on the Description column. I believe that would increase our accuracy even further.   
#### Key Learnings
Through the execution of this project, I was able to polish my skills and solidify my mental fortitude. I learned to work much better under pressure and better manage my time. Learning to use web scraping and the website API has given me more options and tools to extract data in future projects. When extracting the data I developed better intuition in analyzing it and judging whether it will be useful for the project. Before merging the datasets, I had to make sure that my EDA practices and data munging were also well developed, otherwise they wouldn’t be possible to merge.
