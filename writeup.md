# **Finding Lane Lines Advance** 

---

## Pipline
* **Calibration camera and undistortion image**
	- calibration matrix (**mtx** and **dist**) can be saved using pickle, no need to go through all chessboard images every time.
* **Thresholding**
	- absolute sobel
	- magnitude gradient
	- direction of gradient
	- HLS thresholding
	- comined
* **Use histogram and sliding window to find lane lines pixcels**
* **Fit polynomial**
* **Use polynomial parameters to calculate curvature**
* **Sanity check**
	- check if right curvature is similar to left curvature
	- check if min(right_x) > max(left_x)
* **Draw result on image**
* **Next frame, skip the line searching if found lines last time. +/- your margin from your polynomial lines**
	- if sanity check not pass, reset the lane search using sliding window algorithm.

---

## Results
### [Test Images Results](test_images_output)
**example**

<img src="test_images_output/test3_fit.jpg" width="480" alt="Result Image" align="middle"/>
<img src="test_images_output/test3.jpg" width="480" alt="Result Image" align="middle"/>

### [Project Video Output](https://youtu.be/lNBVuSydREM)

---

## 2. Identify potential shortcomings with your current pipeline

One shortcoming in my current work is the 4 corners selection before perspective transform. For now, I manually choose 4 pixcels in the image by observation, however, it should not be best way to do that. 
1. It takes time to try different src and dst pixcels.
2. It just depends on a single image condition. If the road type change (ex. big curve) or use other video or image, the current corners won't work.

---

## 3. Suggest possible improvements to your pipeline

A possible improvement would be using hough transfer to find the line, extend the line until ROI and use the start and end point of the extended line as corners. 