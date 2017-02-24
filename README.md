#**Lane Detection Project using openCV** 

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

## Reflection

##1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

I have used the following steps to create a pipeline:
 
1. Extract Yellow and White Lanes from an image

2. Applying gray scale filter

3. Applying Gaussian Blur

4. Applying Canny Edge Detection 

5. Selecting region of interest and applying masking





### Start with potting sample test image
Let's perform lane detection on 'test_images/solidYellowCurve2.jpg'
This image has a yellow and white lane lines to help us optimize for both types of lane lines

![alt text][image11]
---

### 1. Extract Yellow and White Lanes from an image
### Colorspaces and applying color selection thresholds
From [1] and [2], it can be inferred that detecting white is fairly easy in HLS colorspace. 
The input test image is first converted from RGB to HLS colorspace using ```cv2.cvtColor(img, cv2.COLOR_RGB2HLS)```
After converting the image, white and yellow color thresholds are applied to the image to extract the yellow and white lane lines
The following image is the output of applying color thresholds to the original image.

![alt text][image1]
---
### 2. Applying gray scale filter
From [3] it makes sense to apply gray scale filter on our image so that the thresholds for Canny Edge Detection are reasonable values in tens or hundreds. 
Gray scaled image converts the colored image to an 8 bit image. Each pixel can then take 2^8 = 256 values. This allows using reasonable threshold values to run Canny Edge Detection. Gray Scale filter is applied using ```cv2.cvtColor(img, cv2.COLOR_RGB2GRAY)```

![alt text][image2]
---
### 3. Applying Gaussian smoothing
Averaging functions like Gaussian Blur helps eliminate sudden spikes and remove noise to a certain extent. Gaussian Smoothing acts like a Low Pass Filter. It is a pre-processing method used for edge detection algorithms, since many edge detection algorithms are sensitive to noise[4]. Kernel size of 9 seemed optimal based on the output, the image shows smoothened edges. Gaussian Smoothing is applied using the function ```cv2.GaussianBlur(img, (kernel_size, kernel_size), 0)``` 

![alt text][image3]
---
### 4. Applying Canny Edge Detection
Using low threshold of 50 and high threshold of 150, the edges on the given image are identified using ```cv2.Canny(img, low_threshold, high_threshold)```

![alt text][image4]
---
### 5. Selecting region of interest and applying masking
Using the helper function 'region of interest', a polygon is defined such that other objects are ignored (eg. adjacent lanes, trees, traffic signs).
Following images show the highlighted area (red box) as our region of interest and after applying this mask on Canny's output, we are able to keep the left and the right lanes in our final image. 

![alt-text-1][image8]|![alt-text-2][image5]
---
##2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


##3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...

##4. References:

[1] https://en.wikipedia.org/wiki/HSL_and_HSV

[2] http://stackoverflow.com/questions/22588146/tracking-white-color-using-python-opencv 
    'You might also consider using HSL color space, which stands for Hue, Saturation, Lightness. Then you would only have to look at lightness for detecting white and recognizing other colors would stay easy.'

[3] Lesson 1, Chapter 11 - 'What would make sense as a reasonable range for these parameters? In our case, converting to grayscale has left us with an 8-bit image, so each pixel can take 28 = 256 possible values. Hence, the pixel values range from 0 to 255.'

[4] https://en.wikipedia.org/wiki/Gaussian_blur
