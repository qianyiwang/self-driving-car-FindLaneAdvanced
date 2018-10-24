# **Finding Lane Lines Advance** 

---

## Pipline
* calibration camera and undistortion image
	- calibration matrix (**mtx** and **dist**) can be saved using pickle, no need to go through all chessboard images every time.
* thresholding
	- absolute sobel
	- magnitude gradient
	- direction of gradient
	- HLS thresholding
	- comined
* use histogram and sliding window to find lane lines pixcels.
* Skip the line searching if found lines last time. +/- your margin from your polynomial lines
* fit polynomial
* Use polynomial parameters to calculate curvature. 