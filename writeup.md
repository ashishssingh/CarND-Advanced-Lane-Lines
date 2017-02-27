**Advanced Lane Finding Project**

[//]: # (Image References)

[image1]: ./output_images/undistorted-checkered.png "Undistorted"
[image2]: ./output_images/undistorted.png "Road Transformed"
[image3]: ./output_images/thresholded.png "Binary Example"
[image4]: ./output_images/perspectiveT.png "Warp Example"
[image5]: ./output_images/slidingwindow.png "Fit Visual"
[image6]: ./output_images/polyfit.png "Fit Visual"
[image7]: ./output_images/lanedetected.png "Output"
[video1]: ./marked_video.mp4 "Video"

## [Rubric](https://review.udacity.com/#!/rubrics/571/view) Points
###Here I will consider the rubric points individually and describe how I addressed each point in my implementation.  

---
###Writeup / README

####1. Provide a Writeup / README that includes all the rubric points and how you addressed each one.  You can submit your writeup as markdown or pdf.  [Here](https://github.com/udacity/CarND-Advanced-Lane-Lines/blob/master/writeup_template.md) is a template writeup for this project you can use as a guide and a starting point.  

Resoures:
Code is in a IPython notebook CarND-Advanced-Lane-Lines-master.ipynb, also CarND-Advanced-Lane-Lines-master.html
Output videa is named marked_video.mp4

###Camera Calibration

####1. Briefly state how you computed the camera matrix and distortion coefficients. Provide an example of a distortion corrected calibration image.

In this step all calibration images are read and a list of image points and object points are constructed. This list is used to undistort the images with the computed camera matrix. cal_undistort function is takes care of undistorting images. Below is an example of undistorted image

![alt text][image1]

###Pipeline (single images)

####1. Provide an example of a distortion-corrected image.
Below is an image from test images using cal_undistort.

![alt text][image2]

####2. Describe how (and identify where in your code) you used color transforms, gradients or other methods to create a thresholded binary image.  Provide an example of a binary image result.
abs_sobel_thresh and hsv_select are the functions used to calculate gradients and color transform respectively. Image is thresholded in for grandient in x direction and H channel of HSV. Result shown below

![alt text][image3]

####3. Describe how (and identify where in your code) you performed a perspective transform and provide an example of a transformed image.

Perspective transform is done in laneDetectPipeline using cv2.warpPerspective. Result image below.

![alt text][image4]

####4. Describe how (and identify where in your code) you identified lane-line pixels and fit their positions with a polynomial?

Lane-lines pixels are identified using modified Udacity provided function find_window_centroids in laneDetectPipeline. The modifications are done to add a list for y values of corresponding centroids

polyFit is done in laneDetectPipeline as well using np.polyfit.

![alt text][image5]

####5. Describe how (and identify where in your code) you calculated the radius of curvature of the lane and the position of the vehicle with respect to center.

In laneDetectPipeline using the Rcurve formula after fitting the polynomical on detected lane lines.

![alt text][image6]

####6. Provide an example image of your result plotted back down onto the road such that the lane area is identified clearly.

![alt text][image7]

---

###Pipeline (video)

####1. Provide a link to your final video output.  Your pipeline should perform reasonably well on the entire project video (wobbly lines are ok but no catastrophic failures that would cause the car to drive off the road!).

Here's a [link to my video result](./marked_video.mp4)

---

###Discussion

####1. Briefly discuss any problems / issues you faced in your implementation of this project.  Where will your pipeline likely fail?  What could you do to make it more robust?

Here I'll talk about the approach I took, what techniques I used, what worked and why, where the pipeline might fail and how I might improve it if I were going to pursue this project further.  

