# Capstone Project: Predicting YouTube Views

## Table of Contents
[1.0 Directory Structure](#10-Directory-Structure)<br>
[2.0 Executive Summary](#20-Executive-Summary)<br>
[3.0 Description of Data](#30-Description-of-Data)<br>
-[3.1 Size](#31-Size)<br>
-[3.2 Sources](#32-Sources)<br>
-[3.3 Data Dictionary](#33-Data-Dictionary)<br>
[4.0 Conclusion](#50-Conclusion)<br>
[5.0 Next Steps](#60-Next-Steps)<br>

## 1.0 Directory Structure

```
.
├── project_5
    ├── code
        ├── EDA.ipynb
        ├── kaggle_data_EDA.ipynb
        ├── modeling.ipynb
        ├── YouTube_Scraper.ipynb

    ├── data
        ├── clean_data.csv
        ├── result.csv
        ├── USvideos.csv
        ├── yt-YouTube_API_Project_With_Authentication.csv
    ├── Pictures
        ├── fixed_trending_lag.png
        ├── trending_lag_time.png
        ├── views_by_trending_lag_time.png
    ├── project5_slides.pdf
    └── README.md
```

## 2.0 Executive Summary

The ultimate goal here is to create to create value insights for YouTubers.

### Problem Statement

How the YouTube algorithm works is a mystery to all of us. This analysis was the first step in uncovering the steps necessary to crack the YouTube algorism .


### Project Goals

The goal of this project was to predict YouTube views based on how it's metrics: likes, comments, dislikes, ect.

---
## 3.0 Description of Data
The data for this analysis can be found on Kaggle
### 3.1 Size

|dataset|num. rows|num. columns|file size|
|---|---|---|---|
|USvideos.csv|60000+|16|61.73 MB|



### 3.2 Sources

- https://www.kaggle.com/datasnaek/youtube-new
### 3.3 Data Dictionary

|Feature|Type|Description|
|---|---|---|
|video_id|object|The uinique ID of the video|
|trending_date|object|When this video was trending|
|title|object|title of the video|
|channel_title|object|Title of YouTube Channel|
|category_id|int|An anonymus id number for catergory of video |
|publish_time|datatime object|The time and date when a video was published|
|tags|object|The tags on the video|

---
## 4.0 Conclusion

Before fitting any linear model one needs to consider all of
the OLS assumptions:

- Linearity
- Independence of error (No endogeneity)
- Normality and homoscedasticity (heteroscedasticity)
- No Autocorrelation
- No Multicollinearity


In this analysis, I discovered that I have violated two of the key assumptions. The features in my data are highly correlated with eachother, which indicates that there is at least partial multicollinearity. Think about this led me to think deeper about my analysis and allowed me to realize that I violated another assumption. The likes & comments a video gets are entirely dependent of the views a video get. You can't have likes without views. Ultimately, the work done thus far is redundant because you can’t predict values with those same values that you are trying to predict. Of course my model performed well, because I should have never been fitting a regression anyway. The high correlation between all of the variables in my model proves that there’s a lot of multicollinearity.

As for no autocorrelation - every single variable is dependent on my the thing I’m trying to predict. You can’t have like and comments without views,  - meaning this model needs views to predict views. It’s flawed! You want to predict the views before you make the video, If you make a video to analyze you might as well see what happens with the video right?

## 5.0 Next Steps

**Utilize NLP to identify trends via social media (twitter & reddit)**<br>
Gathering data that will be useful for the true objective behind this analysis.
**Scrape YouTube for the same timeline (look at trending topic videos)**
I would like to validate that my trend identifier has an impact on viewership.
**Create recommendation system to recommend video topics for YouTubers based on what is trending trending.**
This will be super valuable for any Youtuber out there and is a project that I would like to see to completion. 


---
