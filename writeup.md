# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)


---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

####Pipline:
##### fun: open img
def readImg(filename):
##### fun: save img
def saveImg(path, img):
##### fun: debug img
def debugImg(img, debug=False, helpword = ''):
This is to facilitate debugging process.        
##### fun: process single img
def laneDetect(initial_img, debug=False): 
###### Initial Image
<img src="debug/Original Image.jpg" width="480" alt="Combined Image" />
###### change img to grey scale    
<img src="debug/grey scale.jpg " width="480" alt="Combined Image" />
###### apply gaussian blur
Here uses kernel_size = 7

<img src="debug/Gaussian blur.jpg " width="480" alt="Combined Image" />
###### apply canny edge detection
The parameters are difined for Canny edge detection

<img src="debug/Canny edge detection.jpg " width="480" alt="Combined Image" />    
###### apply roi   
Spends sometime in finding the right vertices  

<img src="debug/After applying ROI.jpg " width="480" alt="Combined Image" />

###### apply Hough transformation    
Here do Hough transformation. The maxh_roi and height are additional arguments passed into the function to facilitate the line drawings

<img src="debug/Lines from Hough transformation.jpg " width="480" alt="Combined Image" />
###### combine lines and original img
use weighted_img function to combine line and original images

<img src="debug/Resulting image.jpg " width="480" alt="Combined Image" />
###### return new img

##### Display a test image
File test_images/solidWhiteCurve.jpg is displayed for test 
##### fun: process all images in one folder
def laneDetectBatch(src, dst):
src: source folder
dst: output folder
###### get file list

###### for each file

###### process each image
        
###### save results with the same filename but in output folder
        

#### draw_lines()
This file is the one spending most of my time. I did following changes:

1. Classify left and right

First calculate the slops. Left with slop > 0; and right with slop < 0.

2. Calculate mean line


Calculate mean values for x1, y1, x2, y2 values for left and right lines

3. Extropolation

Extropolate the left and right mean lines to the bottom of the frame and top of the ROI. 



### 2. Identify potential shortcomings with your current pipeline


One potential shortcomings is that the left or right lines could disappear. I deal with via raising a flag. If one of the line is disappeared, the draw function will ignore it. 


### 3. Suggest possible improvements to your pipeline

Kalman filter could be applied to fill the void of loss of detection of the lines.
