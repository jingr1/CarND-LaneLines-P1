# **Finding Lane Lines on the Road**

## Writeup

---

[//]: # (Image References)

[image1]: ./test_images_output/whiteCarLaneSwitch.jpg

---


### 1. Overview of the pipeline.

* Read in and grayscale the image
* Define a kernel size and apply Gaussian smoothing
* Define Canny thresholds and apply canny transform to get the edges image
* Define a four sided polygon to create a masked edges image using cv2.fillpoly()
* Define the Hough transform parameters,Run Hough Transform to find lines in the image
* Separate lines into left and right lines, draw a single line on the left and right lanes

In order to draw a single line on the left and right lanes, I create a new help function draw_lane_lines(), this function :
1. Separate lines into left and right lines by computing the slope of the line
    * If the slope is positive, the line belongs to the right lane.
    * If the slope is negative, the line belongs to the left lane.
2. find a best fit line using the least square method,it’s possible to easily calculate that by using np.polyfit().
3. draw a line from the bottom of the region of interest to the top of it

If you'd like to include images to show how the pipeline works, here is how to include an image:

The image below shows the final output of the pipeline:
![alt text][image1]


### 2. potential shortcomings


* Straight Lines aren’t able to detect lane lines properly in curves


### 3. Suggest possible improvements

* use quadratic functions to fit the lane markings

