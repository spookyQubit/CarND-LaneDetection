# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 
  * Convert the image to gray-scale
  * Apply gaussian blur
  * Apply Canny edge detection
  * Choose a suitable region of interest
  * Apply Hough transform, converting the points gotten from Canny edge detection within the region of interest to lines.
  * In order to identify the full extent of the lanes, draw_lines() function was modified in the following manner:
     * The Hough lines were catagorized into classes with positive and negative slopes. 
     * The median slope and intercept of these two classes are used to draw two lines corresponding to left and right lane.    
     * If only the information from the current image is used, the lines fluctuate a lot and give a poor performance. In order to improve performance, we store the meadian slope and intercept of all previos images in the video stream. If the current calculated median intercept/slope is way too differnt from the mean of the previously seen intercept/slope, we discard the currently calculated intercept/slope, and instead use the mean of the previously calculated intercept/slope to draw the positive and negative slope lines.   


If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline
Even after implementing a smoothing function to average over the stream of previously seen images, the drawn lane lines sometime fluctuate a lot. This can potentially be overcome by fine-tuning the std_threshold in the draw_median_lines() function. Also, if the lanes are too curved, the assumption of using only one line to represent a lane can break down.   

One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline


A possible improvement would be to fine tune the parameters used in the draw_median_lines() function: count_threshold, std_threshold. 

Another potential improvement could be to ..




* mask R-CNN.


