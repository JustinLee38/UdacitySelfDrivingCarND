# **Finding Lane Lines on the Road**

[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

## Overview

### When we drive, we use our eyes to decide where to go. The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle. Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

### Reflection

### 1. The Pipeline

These are the different steps that are taken for finding lane lines on the road.

1. Convert original image to HSL
2. Isolate yellow and white from HSL image
3. Combine isolated HSL with original image
4. Convert image to grayscale for easier manipulation
5. Apply Gaussian Blur to smoothen edges
6. Apply Canny Edge Detection on smoothed gray image
7. Trace Region Of Interest and discard all other lines identified by our previous step that are outside this region
8. Perform a Hough Transform to find lanes within our region of interest and trace them in red
9. Separate left and right lanes
10. Interpolate line gradients to create two smooth lines

The input to each step is the output of the previous step.

### 2. Potential shortcoming of the current pipeline

As shown in the last section of the jupyter notebook. A potential shortcoming happens when the lane lines are not straight. Curved lane lines will confuse the current pipeline.
