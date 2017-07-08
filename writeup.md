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

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I use gaussian blur to reduce the noise in the image, then I use the canny function to get the edge of the image, then I clip the region where potential lane lines would lies. Then I use the houghlines function to get the potential straight line.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by calcuate the slope of those houghlines on the right and left separately, then I calculate the 2 points of the left lane and right lane based on the slope, and draw them use the cv2.line function

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![](test_images/solidWhiteCurve.jpg)
![](test_images/solidWhiteRight.jpg)
![](test_images/solidYellowCurve.jpg)
![](test_images/solidYellowCurve2.jpg)
![](test_images/solidYellowLeft.jpg)
![](test_images/whiteCarLaneSwitch.jpg)


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the road condition changes because the sun light changes. it would be difficult for the algorithm to identify the yellow lines as the differencesa re too small.

I now set the draw_line function as if the lane length are fixed, in real life the lane-length may be highly variable


### 3. Suggest possible improvements to your pipeline

adjust to use calculated number for lane line point, instead of hard-code the specualated 100 difference in y.

add another layer to higher the contrast when the image is very homegenous.
