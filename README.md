# Finger-Detection-and-Counting

## Abstract
This programe detects hand and counts the number of fingers shown to the camera.

## Contents

This repository contains two .ipynb files

1. **Main.ipynb**
   * This code has functions with fixed parameters
   * Only one final output image is displayed
  
  
2. **Developers.ipynb**
   * This code contains functions whose parameters can be changed using trackbars
   * Outputs image from each of the intermidiate steps - to have a better understanding of each process


## Explanation

* Initially, 60 Consecutive frames of ROI are taken and are averaged to make one background ROI image
* Then, an absolute difference of every frame and background is taken. This enables us to separate the foreground from the background

* A binary threshold is applied to the obtained frame

* External contours are obtained for the binary image and are drawn. This puts an outline around the hand for visualization purposes
* A convex hull is formed around the contours detected

* Now to find the center of hand, Topmost, bottommost, rightmost and leftmost points of convex hull are obtained, and their center is assumed to be the center of the hand

* Euclidian distance of these extreme points from the center is calculated. It is assumed that the length of our smallest finger(or thumb) is atleast 90% of the most extended finger. Thus a circle centered at the center with radius 90% of the maximum distance is drawn 

* The updated frame is masked with this circle. This outputs all the fingertips and the wrist

* Now the number of contours left in the frame are counter
* To remove wrist from being counted, a constraint on the area of contours(as wrist contour has an exceptionally large area as compared to fingertips) is applied
* Also, limiting length constrain is applied up to which the contours will be detected

* The number of fingers is displayed in the corner of the ROI 
