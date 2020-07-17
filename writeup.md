## Writeup 

---

**Advanced Lane Finding Project**


[//]: # (Image References)

[image1]: ./examples/undistort_output.png "Undistorted"
[image3]: ./examples/warped2.png "Transformed"
[image5]: ./examples/slidingwindow2.png "Sliding Window Visual"
[image6]: ./examples/final2.png "Final output"
[image7]: ./examples/thresholded2.png "Thresholded"

[video1]: ./project_video.mp4 "Video"

## [Rubric](https://review.udacity.com/#!/rubrics/571/view) Points


### Pipeline (single images)


#### 1. Distortion
I used the images in "camera_cal" folder to find the camera matrix and distortion coefficients. Using the coefficients I undistorted the images.


![alt text][image1]

#### 2. Perspective Transform
I manually found the 4 source points which marked the region of interest of the image, and then transformed it to my 4 destination points.

![alt text][image3]





#### 3. Thresholding 
I applied thresholds to 3 colorspaces - HLS, LUV, LAB. I then combined the images to create my final binary image.

![alt text][image2]
![alt text][image7]

#### 4. Lane finding
I used a sliding window search for finding the lane line pixels. This started with using a histogram to find the bottom of the lane lines, and then using 10 windows that were 100 pixels wide to go up from there. Then inside those windows we find the position of every non-zero pixel and save them. Lastly we use these points to calculate a polynomial to fit the line. 

![alt text][image5]

#### 5. Radius of curvature & distance from center
To find the distance from center I just took the average of the bottom left and bottom right point and subtracted it from the center of the car(the width of the image/2). 

For the radius I found the curvature of each line individually and then averaged that. 

#### 6. Examples of lanes
This is an example of an image that was proccessed by the pipeline

![alt text][image6]

---

### Pipeline (video)

#### 1. Video

Here's a [link to my video result](./project_video_output.mp4)

---

### Discussion

#### 1. Briefly discuss any problems / issues you faced in your implementation of this project.  Where will your pipeline likely fail?  What could you do to make it more robust?

The pipeline was having problems with the challenge videos, I think this is mostly due to the thresholding of the image. This could probably be fixed with further tuning of the numbers. 
