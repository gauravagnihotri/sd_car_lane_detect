#**Lane Detection Project using openCV for SDC Nanodegree** 

###The objective of this project is to identify lane lines on the road using combination of tools learnt in Lesson 1 (color selection, region of interest masking, grayscaling, Gaussian smoothing, Canny Edge Detection and Hough Tranform line detection). 

---

**Finding Lane Lines on the Road**

The goals of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./readme_ref/_colored_img.jpeg "White and Yellow Filter"
[image2]: ./readme_ref/gray_image.jpeg "Gray Scale"
[image3]: ./readme_ref/blur_gray.jpeg "Gaussian Blur"
[image4]: ./readme_ref/edges.jpeg "Canny Edge Detect"
[image5]: ./readme_ref/masked_edges.jpeg "Region of Interest Resultant"
[image6]: ./readme_ref/lane_sketched.jpeg "Hough Transform in action"
[image7]: ./readme_ref/result.jpeg "Final Result"
[image8]: ./readme_ref/region_of_interest_red.png "Marked Region of interest"
[image9]: ./readme_ref/all_test_images.png "Input Test Images"
[image10]: ./readme_ref/all_test_images_proc.png "Processed Test Images"
[image11]: ./test_images/solidYellowCurve2.jpg "Input Test Image"
---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

I have used the following steps to create a pipeline 
1. Extract Yellow and White Lanes from an image
2. 
3.
4. 


### Start with potting sample test image
Let's perform lane detection on 'test_images/solidYellowCurve2.jpg'
This image has a yellow and white lane lines to help us optimize for both types of lane lines

![alt text][image11]
---

### Colorspaces and applying thresholds
From [1] and [2], it can be inferred that detecting white is fairly easy in HSL colorspace.
Function gotohls converts the RGB image to HLS image
and function ident_white_yellow applies threshold to extract yellow and white colors from the original image
![alt text][image1]

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I .... 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


###3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...

###4. References
[1] https://en.wikipedia.org/wiki/HSL_and_HSV
[2] http://stackoverflow.com/questions/22588146/tracking-white-color-using-python-opencv 
    'You might also consider using HSL color space, which stands for Hue, Saturation, Lightness. Then you would only have to look at lightness for detecting white and recognizing other colors would stay easy.'
