---
title: "Secure HTTP Server using Steganography"
layout: inner_page
last_modified_at:
excerpt: An HTTP secure client server model made with Python networking sockets using Least 3 Bits Steganography.


---
<style>
ul,li,p{font-size:16px;}  
  
img{     
display: block;
margin-left: auto;
margin-right: auto;
max-width: 50%;
max-height: 50%;
    }
</style>

<!-- <img src="/images/color_blind.jpg" class="center" width="400" height="400"> -->

<p class="inner-page">
<h4 style="display: inline;">Team members: <i style="font-size: 16px;">Wahab Aftab, Ibrahim Usmani, Asfa Mumtaz</i></h4>
</p>
<p class="inner-page">

In this Project we built a secure HTTP server that is able to serve web clients with secure contents. The server encodes the data requested by the client which the client can decode upon receiving. 

</p>

<p class="inner-page">
Assume that the server has 10 different text files numbered file1.txt to file10.txt as well as 5 different PNG images all located in the current directory. The server will parse the client request and if it has the requested text file then it randomly selects one of the five images and then encodes the text file inside the image file. It then transfers the image file back to the client, Thus keeping the content of the text file secure.The client on receipt of the encoded image file, runs the decoder and extracts the original .txt file from the image. The server uses basic Image <b>Steganography</b> for encoding the text file inside the image.
</p>

<p class="inner-page">

Steganography is the technique of hiding secret data within an ordinary, non-secret, file or message in order to avoid detection; the secret data is then extracted at its destination. The simplest form of digital steganography is the Least Significant Bit (LSB) method, where the binary representation of the data that's to be hidden is written into the LSB of the pixel data produced from the image file. Suppose we have 8 bits representing each of the three RGB color values (red, green, and blue) at each pixel. If we consider just the blue there will be 2^8 different values of blue. The difference between 11111111 and 11111110 in the value for blue intensity is likely to be undetectable by the human eye. Therefore, the least significant bit can be altered (more or less undetectably). If we do it with the green and the red as well, we can get one letter of ASCII text for every three pixels. In this project, we will employ 24-bit PNG images, which use a byte each for the red (R), green (G), and blue (B) channels. Detailed explanation of the process is given below:

</p>


<p class="inner-page">
  

<p class="inner-page">Figure 1 shows the first stage of the process, when the image data is accessed as a series of bytes. </p>
<img  src="/images/steganography1.jpg" >

<p class="inner-page">Figure 2 shows the ASCII character representation in terms of byte/bits. </p>
<img src="/images/steganography2.jpg"  >

<p class="inner-page">Next you have to insert the bits of the text file into the image. The LSB approach only modifies the least significant bit of each image byte, as illustrated by Figure 3.</p>
<img src="/images/steganography3.jpg" >

</p>

<p class="inner-page">
The encoding is spread over the image by modifying each byte's LSB. This means that 1 byte of text data requires the modification of 8 bytes of the image (i.e. 1 data bit is stored in 1 image byte). Since this would require very large image files, So we modified the method to use least 3 significant bits instead of one for encoding to achieve better storage. In this way we can store more text in smaller images and upon testing we found out that this method made no significant/visible changes in our image quality.
</p>


<p class="inner-page">
You can check the code and Report below!
</p>
 
<h4><b><a href="https://github.com/wahabaftab/HTTP-Server-using-Steganography">Code</a>    <a href="/Documents/Project_Report_Steganography.pdf">Report</a></b></h4>





