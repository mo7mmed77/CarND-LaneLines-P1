# **Finding Lane Lines on the Road** 

## Computer Vision Methods to Identify and Mark Lanes on the Road


---

**Finding Lane Lines on the Road**


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describtion of the pipeline

My pipeline consisted of saveral steps. First, I converted the images to grayscale, then I applied Guassian blur to remove any small objects. After that I applied the Canny technique to find the edges of the lane lines. This required me to tune the two parameters the low and high threshold. A region of interest is then introduced to eliminate other objects from the field of view, and to ensure that only the lane lines are being detected. 

Then Hough line function is used to identify the lane lines in image coordinates. These multiple lines are then used to get an average line for each lane. In order to draw a single line on the left and right lanes, I modified the draw_lines() function by getting the average as I mentioned earlier, as well as, developing a moving average for all images. This was done using the moving average method with 5 images. 


![alt text][image1]


### 2. Potential shortcomings


1. This method is only applicable under the same FOV for the lane. 
2. This method might not work under different weather conditions such as sunlights or rain or fog.
3. Camera distortion will cause this pipeline to fail, as it was designed to detect straight lines.
4. shorter lane length or colours could affect the performance of this pipeline.

### 3. Possible Improvements 

1. include camera calibrations for some cases. 
2. include different methods to eliminate the effect of different sun reflections and shadows. 
3. Test the pipeline on more roads and try to tune the parameters further to achieve a robust result.
