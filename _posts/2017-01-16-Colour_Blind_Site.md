---
title: "Blogging Website for the Visually impaired and Colour Blind"
layout: inner_page
last_modified_at:
excerpt: A blogging website designed for normal people as well as those who are visually impaired or suffer from color-blindness.
image: 
  thumbnail: /images/blog.jpg

---


<!-- <img src="/images/color_blind.jpg" class="center" width="400" height="400"> -->

<p class="inner-page">
<h4 style="display: inline;">Team members: <i style="font-size: 16px;">Wahab Aftab, Zain Abbas, Saad Raza</i></h4>
</p>
<p class="inner-page">
The goal of this project was to facilitate users who suffer from colourblindness to read blogs as normal users.
  
Upon research we got the figure that 8% males and 0.8 females are born colorblind.Some article’s directed us to information such as most colour blind people are able to see things as clearly as other people but they unable to fully ‘see’ red, green or blue light. [<a style="font-size: 10px" href="http://www.colourblindawareness.org">Source 1</a>,<a style="font-size: 10px" href="http://www.color-blindness.com/coblis-color-blindness-simulator/">Source 2</a>]

Further research and awareness articles concluded that there were 3 Types of colourblindness [<a style="font-size: 10px" href="https://www.nei.nih.gov/learn-about-eye-health/eye-conditions-and-diseases/color-blindness/types-color-blindness">Source</a>].
Details on the 3 Types of Colorblindness and their subtypes are given below:
<ul>
<b><li>Red-Green ColorBlindness</li></b>
  <ul>
    <li>Protanomaly: Red, orange, and yellow appear greener and colors are not as bright</li>
    <li>Deuteranomaly: Yellow and green appear redder and it is difficult to tell violet from blue.</li>
  </ul>
<b><li>Blue-Yellow ColorBlindness</li></b>
  <ul>
    <li>Tritanomaly: Blue appears greener and it can be difficult to tell yellow and red from pink.</li>
    <li>Tritanopia makes you unable to tell the difference between blue and green, purple and red, and yellow and pink.</li>
  </ul>
<b><li>Complete ColourBlindness</li></b>
</ul>
</p>

<p>
Being an avid film lover, I do occasionally rate movies or shows on IMDB based on my preference. Now, I know many people who do the same.Sometimes you need some assurance or a trusted review before deciding to put some time and effort into watching a certain movie. People always seem to watch movies recommended by someone As the most trust worthy person when it comes to movie recommendation is you yourself, So its better to watch something you know you will like based on your previous history.
</p>
  
<p class="inner-page">
In this project I have presented a model which will decide for you whether you will like a movie or not based on your previous ratings.For this, I have extracted all the movies info I have rated on IMDB (IMDB provides a feature to download all rated movies info on the site in a csv). This became my dataset and after performing feature engineering, EDA and analysis. I have come up with a model trained on my previously rated films, which can predict what rating will I give to an unseen movie  based on its length, year of release, genre etc etc with great precision.
I have simply used linear regression for modelling as we had to predict continous data and also because rating trend of one person arn't that complex. I have tested it on movies/shows which I then watched later and predicted rating was pretty similar to what I would have given it myself.
</p>
  
<p class="inner-page">
This helps me and can help others in deciding what to watch next! You can check the code below!
</p>
 
<h4><b><a href="https://github.com/wahabaftab/IMDB-Rating-Prediction">Code</a></b></h4>




