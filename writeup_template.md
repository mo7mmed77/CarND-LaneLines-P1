# **Finding Lane Lines on the Road** 



---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
- Finding lane lines of a road using computer vision techniques. 

[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. PipeLine Describtion

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I used Guassian Blur to remove small unneeded parts. Then I use Canny technique to find the edges of the gray image, and I tried to tune the two thresholds as the best of my ability. Once we have the results of the canny as I wanted, I applied the region of interest (a trapezoid to contain only the left and right lanes).   

After that, I used Hough method to highlight the lanes and by tuning rho and theta I was able to get most of the lanes in all of the given test images. Moreover, I tuned the min lane length and gap to make sure that the pipline will detect the most extreme cases in which was have small lane lines. The output of the hough algorthim is the lane lines coordinates on the image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by incudling a method to find the average of the lines for each side (left and right). Then I calculated the slope of the average line and I extrapolate to extend the line in both directions to cover all the lane. This was done in a single image, for multiple images (a video), I included a moving average function that takes 5 readings at a time. This will help reduce any lane detection failures due to low pixels of lane. 


Finally the output of the averaged lane line, will be combined with the original image and the results are verified. 

## Hough Output
[image2]: ./houghLines.png "Hough Lines Output"

![alt text][image2]


[image3]: ./yellowLane.png "Hough Lines Output 2"

![alt text][image3]

[image4]: ./drawLines.png "Draw Lines Output"

## PipeLine Output
![alt text][image3]


### 2.  Potential Shortcomings of the Pipeline
- Some some lane lines are not detected by this pipeline. 
- This pipeline only applicable for this weather condition (sunlights, shadows and rain will affect its robustness).
- The moving average can restrict the detection when the car is changing lanes, (it will create some sort of a lag). 
- The color of the lanes can effect the detection greatly.




### 3. Suggest possible improvements to your pipeline

- apply a method to detect all lane lines without including any other unrelated objects.
- develop a method to eliminate the effects of the weather conditions. 
- Use a more robust method other than moving average. 
- eliminate the effects of the color changes on the detection.


Thank you for reading this. 
Kind regards
