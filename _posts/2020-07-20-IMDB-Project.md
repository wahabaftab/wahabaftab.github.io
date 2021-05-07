---
title: "IMDB Movie Rating Prediction"
last_modified_at:
excerpt: A Beginners project to predict your imdb ratings of upcoming or unseen movies.
layout: inner_page

---
<style>
.inner-page {font-size: 17px;}
</style>

<!-- <img src="https://quizdoo.com/wp-content/uploads/2015/06/5574ade93e41c.jpg" class="center" width="400" height="400"> -->

Being an avid film lover, I do occasionally rate movies or shows on IMDB based on my preference. Now, I know many people who do the same.Sometimes you need some assurance or a trusted review before deciding to put some time and effort into watching a certain movie. People always seem to watch movies recommended by someone As the most trust worthy person when it comes to movie recommendation is you yourself, So its better to watch something you know you will like based on your previous history.

In this project I have presented a model which will decide for you whether you will like a movie or not based on your previous ratings.For this, I have extracted all the movies info I have rated on IMDB (IMDB provides a feature to download all rated movies info on the site in a csv). This became my dataset and after performing feature engineering, EDA and analysis. I have come up with a model trained on my previously rated films, which can predict what rating will I give to an unseen movie  based on its length, year of release, genre etc etc with great precision.
I have simply used linear regression for modelling as we had to predict continous data and also because rating trend of one person arn't that complex. I have tested it on movies/shows which I then watched later and predicted rating was pretty similar to what I would have given it myself.

This helps me and can help others in deciding what to watch next! You can check the code below!
 
 
<h4><b><a href="https://github.com/wahabaftab/IMDB-Rating-Prediction">Code</a></b></h4>




