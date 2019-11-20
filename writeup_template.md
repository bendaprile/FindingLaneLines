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

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I .... 

Applied a gaussian blur, applied canny edge detection, and created a region of interest to mask the parts of the image that shouldn't be included. I then applied a hough transformation on the masked image and ran the weighted_img function to overlay the lines on the initial image. 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

I first found the slope for each hough point and depending on whether the slope of that line was positive or negative I appended it to a different list. Each of those lists contained four points for each line. These points are an x1, y1, x2, and y2. I then passed these points into a function that found the highest and lowest y point in the image. These served as my two end points for my line. I then created the line with the cv2.line function and put it on the original image. 

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

There is a very bumpy road and the camera is moving all over the place. In this circumstance, it would make the cropping of the image wrong in some frames and wouldn't detect the lines correctly. 

Another shortcoming could be ...

My line extrapolation sometimes does not extend the lines all the way to the bottom of the image.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ... 

Have the cropping of the images dynamically change depending on the orientation and position of the camera at a certain point in time. This would ensure that the lines are always within the portion of the image that is being classified.

Another potential improvement could be to...

I could improve my draw lines function to extend the line all the way to the bottom of the image every time. This could be done by using the slope and intercept to figure out where the point at the bottom would be. This would give the car more information about where the lines are right next to it.