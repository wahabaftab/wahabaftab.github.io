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

.middle{     
  display: block;
  margin-left: auto;
  margin-right: auto;
    }
    
   
/* Clearfix (clear floats) */
.row::after {
  content: "";
  clear: both;
  display: table;
}
</style>

<p class="inner-page">
  
In this Project, we developed a method to binarize degraded or historical documents. The method is the implementation of the Adaptive Thresholding Methods for Documents Image
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

</p>

<h3>Sauvola's Method: </h3>

<p class="inner-page">
  
In Sauvola’s binarization method, the threshold t(x, y) is computed using the mean m(x, y) and standard deviation s(x, y) of the pixel intensities in a w × w window centered around the pixel (x, y):

</p>

<img class="middle" src="/images/sauvola_method.jpg"  style="width:50%">

<p class="inner-page">

where k is a control factor in the range of [0.2, 0.5] and R is a predetermined image graylevel value. The author of the original paper suggested k=0.2, R= 125. The local mean m(x, y) and standard deviation s(x, y) adapt the value of the threshold according to the contrast in the local neighborhood of the pixel. When there is high contrast in some region of the image, s(x, y) ≈ R which results in t(x, y) ≈ m(x, y). This is the same result as in Niblack’s method. However, the difference comes in when the contrast in the local neighborhood is quite low. In that case the threshold t(x, y) goes below the mean value thereby successfully removing the relatively dark regions of the background. The parameter k controls the value of the threshold in the local window such that the higher the value of k, the lower the threshold from the local mean m(x, y).

Since this method is good for low contrast and can tackle problems like Shadows, Luminance, Degradation, Noise, smudge, stains etc in an image So this was a perfect solution for us. However, in order to compute the threshold t(x, y), local mean and standard deviation have to be computed for each pixel.Computing m(x, y) and s(x, y) in a naive way results in a computational complexity of O(W^2xN^2) for an N × N image. This slows up computation for larger images.

</p>

<h3>Integral Images: </h3>

<p class="inner-page">
  
  
The Integral Image is used as a quick and effective way of calculating the sum of values (pixel values) in a given image. An integral image i of an input image g is defined as the image in which the intensity at a pixel position is equal to the sum of the intensities of all the pixels above and to the left of that position in the original
image. So the intensity at position (x, y) can be written as:

</p>

<img class="middle" src="/images/integral.jpg"  style="width:30%">

<p class="inner-page">

The integral image of any grayscale image can be easily computed in OpenCV in a single pass with 1 line of code. Once we have the integral image, the local mean m(x, y) for any window size can be computed simply by using two addition and two subtraction operations instead of the summation over all pixel values within that window:

</p>

<img class="middle" src="/images/mean.jpg"  style="width:70%">

<p class="inner-page">

Similarly, we can compute the variance like:

</p>

<img class="middle" src="/images/std.jpg"  style="width:70%">

<p class="inner-page">

Now taking square-root of the variance to find standard deviation and using the computed values of mean and standard deviation in the original Sauvola formula we can find the optimal local thresholds for pixels in the image very efficiently,independent of the local window size. Using this method reduces the computational complexity from O(W^2 x N^2) to O(N^2).An important hint from implementation point of view is that the values of the squared integral image get very large, so overflow problems might occur if 32-bit integers are used.

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







