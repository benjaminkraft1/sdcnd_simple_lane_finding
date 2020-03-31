# **Finding Lane Lines on the Road** 

## Writeup

### Pipeline Description

---

**Finding Lane Lines on the Road**

![Example Result Image][result_images/solidWhiteRight.jpg]

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps. 

The Pipeline goes thrugh the following steps to find the lane lines:

* Apply gray scale to the image
* Apply Guassian Blur to reduce noise
* Apply Canny Edge Detection
* Apply a Mask to the resulting image to get the region of interest
* Apply Hough Transform to extract Hough lines
* Draw extrapolated lines over the detected lane markings

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by separating line segments by their 
slope ((y2-y1)/(x2-x1)) to decide which segments are part of the left line vs. the right line. The average position of each of the lines and  are extrapolate afterwards to the top and bottom of the lane.


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the lanes are bending more. The current algorythm is only feasible for nearly linear lane lines.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to apply higher order polynomials to describe the lane lines.