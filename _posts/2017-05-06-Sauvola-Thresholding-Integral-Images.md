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

figcaption {
  background-color: black;
  color: white;
  font-style: italic;
  text-align: center;
  font-size:13px;
}

.column {
  float: left;
  width:33%;
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

<h4 style="display: inline;">Team members: <i style="font-size: 16px;">Wahab Aftab, <a href='https://faizanzafar.de'>Faizan Zafar</a>, Saad Raza, Raja Umair</i></h4>
<p class="inner-page">
</p>
<p class="inner-page">
  
In this Project, we developed a method to binarize degraded or historical documents. The method is the implementation of the Adaptive Thresholding Methods for Documents Image
Binarization Research Paper (link given at the bottom).
The image is first converted to grayscale to apply a thresholding technique, then Sauvola method is used to compute the threshold using mean and standard deviation of neighbouring window pixels. Instead of summing over all the pixels to find mean and standard deviation withtin a window, integral images are used to efficienty compute mean and standard deviation with as little as 4 mathematical operations. This makes the method much more efficient and reduces runtime drastically without relying on window size and it doesn't have any impact on original Sauvola method quality.

</p>


<h3> Image Binarization: </h3>

<p class="inner-page">

Image binarization is the process of taking a grayscale image and converting it to black-and-white, essentially reducing the information contained within the image from 256 shades of gray to 2: black and white, a binary image. It's the most important step in pre-processing of scanned documents to save all or maximum subcomponents such us text, background and image. Binarization computes the threshold value that differentiate object and background pixels. As we know grayscale image pixel values range from [0-255] So after conversion to grayscale, image pixel values are converted to white i.e 255 if they are above threshold value and to black i.e 0 if they are below the threshold making 
all the pixels either 0 or 255 hence the term binary.
</p>

<h3>Binarization Techniques: </h3>
<p class="inner-page">

As discussed, binarization converts the image with many shades into an image of black and white depending on the threshold value. There are many methods to compute the threshold value, global thresholding is one method where a global threshold (typically 127) is used to binarize entire image. Many other adaptive thresholding techniques are also used like otsu to binarize image based on region wise thresholding i.e different thresholdss are computed for different regions. These methods work when applying thresholding onto good quality image. However, this task becomes difficult when it deals with degraded image.

</p>

<h3>Sauvola's Method: </h3>

<p class="inner-page">
  
In Sauvola’s binarization method, the threshold t(x, y) is computed using the mean m(x, y) and standard deviation s(x, y) of the pixel intensities in a w × w window centered around the pixel (x, y):

</p>

<img class="middle" src="/images/sauvola_method.jpg"  style="width:50%">

<p class="inner-page">

where k is a control factor in the range of [0.2, 0.5] and R is a predetermined image graylevel value. The author of the original paper suggested k=0.2, R= 125. The local mean m(x, y) and standard deviation s(x, y) adapt the value of the threshold according to the contrast in the local neighborhood of the pixel. When there is high contrast in some region of the image, s(x, y) ≈ R which results in t(x, y) ≈ m(x, y). This is the same result as in Niblack’s method. However, the difference comes in when the contrast in the local neighborhood is quite low. In that case the threshold t(x, y) goes below the mean value thereby successfully removing the relatively dark regions of the background. The parameter k controls the value of the threshold in the local window such that the higher the value of k, the lower the threshold from the local mean m(x, y).

Since this method is good for low contrast and can tackle problems like Shadows, Luminance, Degradation, Noise, smudge, stains etc in an image, So it provided us with a perfect solution for our problem. However, in order to compute the threshold t(x, y), local mean and standard deviation have to be computed for each pixel. Computing m(x, y) and s(x, y) in a naive way results in a computational complexity of O(W^2 x N^2) for an N × N image which makes the process very slow.

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

<img class="middle" src="/images/std.jpg"  style="width:60%">

<p class="inner-page">

Now we can find standard deviation by taking square-root of the variance. After computing the values of mean and standard deviation we can easily substitute them in the original Sauvola formula to find the threshold efficiently, and independent of the local window size. This method reduces the computational complexity from O(W^2 x N^2) to O(N^2) thus making the whole process much quicker. An important hint from implementation point of view is that the values of the squared integral image get very large, so overflow problems might occur if 32-bit integers are used.

</p>


<h3>Results: </h3>

<p class="inner-page">
Values of k, R and window size can be changed to achieve best results depending upon the type of images.You can find some sample results below: 
</p>

<div class="row">
  <div class="column">
    <img src="/images/original1.jpg"  style="width:100%">
    <figcaption class='middle'><b>Original Image</b></figcaption>

  </div>
  <div class="column">
    <img src="/images/otsu1.jpg"  style="width:100%">
    <figcaption><b>Otsu Result</b></figcaption>

  </div>
  <div class="column">
    <img src="/images/sauvola1.jpg" style="width:100%">
    <figcaption><b>Our Result</b></figcaption>

</div>
<p></p>
<div class="row">
  <div class="column">
    <img src="/images/original2.jpg"  style="width:100%">
    <figcaption><b>Original Image</b></figcaption>

  </div>
  <div class="column">
    <img src="/images/otsu2.jpg"  style="width:100%">
    <figcaption><b>Otsu Result</b></figcaption>

  </div>
  <div class="column">
    <img src="/images/sauvola2.jpg" style="width:100%">
    <figcaption><b>Our Result</b></figcaption>

</div>

<p class="inner-page">
You can find the code and the reference paper below!
</p>
<h4><b><a href="https://github.com/wahabaftab/Adaptive-Thresholding-to-Binarize-Degraded-Documents-with-Sauvola-Method-using-Integral-Images">Code</a></b>    <b><a href="https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.182.5334&rep=rep1&type=pdf">Reference Paper</a></b></h4>






