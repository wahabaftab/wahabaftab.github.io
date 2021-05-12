---
title: "Efficient Implementation of Sauvola Method Using Integral Images"
last_modified_at:
excerpt: We optimized a local adaptive thresholding technique with the help of integral images to binarize degraded and historical documents. 

layout: inner_page
---
<style>
ul,li,p{font-size:16px;}  
  
* {
  box-sizing: border-box;
}

.column {
  float: left;
  width:20%;
  padding: 5px;
}

/* Clearfix (clear floats) */
.row::after {
  content: "";
  clear: both;
  display: table;
}
</style>

<p class="inner-page">
  
In this Project, we developed a method to binarize degraded or historical documents. The method was the implementation of the Adaptive Thresholding Methods for Documents Image
Binarization Research Paper (link given at the bottom).
The image is first converted to grayscale to apply a thresholding technique, then Sauvola method is used to compute the threshold using mean and standard deviation of neighbouring window pixels. Instead of summing over all the pixels to find mean and standard deviation withtin a window, integral images are used to efficienty compute mean and standard deviation with as little as 4 mathematical operations. This makes the method much more efficient and reduces runtime drastically without relying on window size and it doesn't have any impact on original Sauvola method quality.

</p>


<h3> Image Binarization: </h3>

<p class="inner-page">

Image binarization is the process of taking a grayscale image and converting it to black-and-white, essentially reducing the information contained within the image from 256 shades of gray to 2: black and white, a binary image.It's the most important step in pre-processing of scanned documents to save all or maximum subcomponents such us text, background and image.Binarization computes the threshold value that differentiate object and background pixels.As we know grayscale image pixel values range from [0-255] So after conversion to grayscale, image pixel values are converted to white i.e 255 if they are above threshold value and to black i.e 0 if they are below the threshold making 
all the pixels either 0 or 255 hence the term binary.
</p>

<h3>Binarization Techniques: </h3>
<p class="inner-page">

As discussed, binarization converts the image with many shades into an image of black and white depending on the threshold value. There are many methods to compute the threshold value to achieve best results, global thresholding is one method where a global threshold (typically 127) is used to binarize entire image but its outdated. Many other adaptive thresholding techniques are also used like otsu to binarize image based on region wise thresholding i.e different threshold is computed for different regions. Otsu gives good results but it fails when there are Shadows, Luminance, Degradation, Noise, smudge, stains etc in the image So for that we used another method.
![image](https://user-images.githubusercontent.com/25950715/118025573-6e6d3e80-b379-11eb-924a-b40b0cbd9b08.png)

</p>

<h3>Sauvola's Method: </h3>
<p class="inner-page">
  
  

In Sauvola’s binarization method, the threshold t(x, y) is computed using the mean m(x, y) and standarddeviation s(x, y) of the pixel intensities in a w × w window centered around the pixel (x, y):

![image](https://user-images.githubusercontent.com/25950715/118027658-9bbaec00-b37b-11eb-8721-cbd81771c9d2.png)

</p>


<h3>Screenshots: </h3>

<div class="row">
  <div class="column">
    <img src="/images/screenshot1.jpg"  style="width:100%">
  </div>
  <div class="column">
    <img src="/images/screenshot2.jpg"  style="width:100%">
  </div>
  <div class="column">
    <img src="/images/screenshot3.jpg" style="width:100%">
  </div>
  <div class="column">
    <img src="/images/screenshot4.jpg"  style="width:100%">
  </div>
  <div class="column">
    <img src="/images/screenshot5.jpg" style="width:100%">
  </div>
</div>

<p class="inner-page">
</p>
<h4><b><a href="https://github.com/wahabaftab/Snakes-And-Ladders">Github Repo</a></b></h4>







