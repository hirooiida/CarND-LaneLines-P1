# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps.

1. Convert the images to grayscale.

<img src=./test_images_output/example_original.png width=20%>
<img src=./test_images_output/example_gray.png width=20%>

2. Apply Gaussian smoothing and blurring.

<img src=./test_images_output/example_blur_gray.png width=20%>

3. Find edges by Canny edge detection.

<img src=./test_images_output/example_canny.png width=20%>

4. Localize the region of interest.

<img src=./test_images_output/example_masked.png width=20%>

5. Apply Hough transform to find lines and draw them.

<img src=./test_images_output/example_draw_lane_lines.png width=20%>

In order to draw a single line on the left and right lanes at step 5, I modified the draw_lines() function by introducing the first order least squares polynomial fit for each left and right lines.


### 2. Identify potential shortcomings with your current pipeline

Potential shortcomings are reporesetned below: 

1. Manual tuning of parameters can be time consuming and biased by the set of the images.
2. The parameters for the region of interest at step 4 cannot be always reasonable when vehicle body roll, pitch and yaw occur.
3. Litters on the road can be detected as lines.


### 3. Suggest possible improvements to your pipeline

Possible improvements would be:

1. Automate parameter tuning with more dataset. The dataset should contain the raw images and ground truth.
2. Detect body roll and pitch and calibrate the interpolation algorithm using those values. Algorithm for detecting roll and pitch will need to be developed.
3. Limit the region of interest more tightly and the possible slope amount for interpolated lines using the road witdth and the focus of expansion values.
