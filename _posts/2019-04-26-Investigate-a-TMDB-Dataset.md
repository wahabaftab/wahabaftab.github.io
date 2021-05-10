---
title: "TMDB Dataset Investigation and Analysis"
last_modified_at:
excerpt: I performed Data Wrangling and Exploratory Data Analysis on TMDB dataset and shared some insights as part of Udacity's Data Analyst Nanodegree.  

layout: inner_page
---
<style>
ul,li,p{font-size:16px;}  

</style>


<p class="inner-page">
I completed this project as part of Udacity's Nanodegree progam, in this project I was given a task to choose a dataset and perform data wrangling and EDA techniques. For this task I chose The Movie Dataset which contains information about 10,000 movies,short films and tv series of the last 50+ years collected from The Movie Database (TMDb), including user ratings, revenue, runtime and budget. You can find the dataset in the code link given at the end.

</p>
  
<p class="inner-page">
  
ThE  
In this project I have presented a model which will decide for you whether you will like a movie or not based on your previous ratings.For this, I have extracted all the movies info I have rated on IMDB (IMDB provides a feature to download all rated movies info on the site in a csv). This became my dataset and after performing feature engineering, EDA and analysis. I have come up with a model trained on my previously rated films, which can predict what rating will I give to an unseen movie  based on its length, year of release, genre etc etc with great precision.
I have simply used linear regression for modelling as we had to predict continous data and also because rating trend of one person arn't that complex. I have tested it on movies/shows which I then watched later and predicted rating was pretty similar to what I would have given it myself.
</p>
  
<p class="inner-page">
This helps me and can help others in deciding what to watch next! You can check the code below!
</p>
 
<h4><b><a href="https://github.com/wahabaftab/IMDB-Rating-Prediction">Code</a></b></h4>





