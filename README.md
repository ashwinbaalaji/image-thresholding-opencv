# Image Segmentation Using Thresholding Techniques in OpenCV

## Aim

To segment an image using Global Thresholding, Adaptive Thresholding, and Otsu's Thresholding techniques using Python and OpenCV.

The program performs the following operations:

- Global Thresholding
- Adaptive Thresholding
- Otsu's Thresholding

## Software Used

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (cv2)
- NumPy
- Matplotlib

## Algorithm

### Step 1:

Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:

Load the input image using OpenCV.

### Step 3:

Convert the input image into grayscale format.

### Step 4: Global Thresholding

- Select a fixed threshold value.
- Apply thresholding to separate foreground and background pixels.
- Display the thresholded image.

### Step 5: Adaptive Thresholding

- Compute threshold values for small regions of the image.
- Apply Adaptive Mean Thresholding.
- Apply Adaptive Gaussian Thresholding.
- Display the segmented images.

### Step 6: Otsu's Thresholding

- Automatically determine the optimal threshold value.
- Apply Otsu's thresholding technique.
- Display the segmented image.

### Step 7:

Compare the results obtained from Global, Adaptive, and Otsu's thresholding methods.

## Program

## Developed By

**Name:** ASHWIN BAALAJI V K

**Register No:** 212225230026


## PROGRAM

### Original Grayscale Image

- The grayscale version of the input image is displayed.
- Serves as the input for thresholding operations.
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread("Downloads/WALT.jpg")
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

plt.figure(figsize=(10, 5))
plt.subplot(1, 2, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.imshow(gray, cmap="gray")
plt.title("Grayscale Image")
plt.axis("off")
plt.show()
```

### Global Thresholding

- Original image is displayed.
- Thresholded image is displayed.
- A fixed threshold value is used for segmentation.
- Pixels are classified as foreground or background.
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread("Downloads/WALT.jpg")
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

# Fixed threshold: pixels above 127 become 255 (white), the rest become 0 (black)
ret, global_thresh = cv2.threshold(gray, 127, 255, cv2.THRESH_BINARY)

plt.figure(figsize=(10, 5))
plt.subplot(1, 2, 1)
plt.imshow(gray, cmap="gray")
plt.title("Original Grayscale Image")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.imshow(global_thresh, cmap="gray")
plt.title("Global Thresholding (T = 127)")
plt.axis("off")
plt.show()
```
### Adaptive Thresholding

- Original image is displayed.
- Adaptive Mean Thresholded image is displayed.
- Adaptive Gaussian Thresholded image is displayed.
- Threshold values vary across different regions of the image.
- Suitable for images with uneven illumination.
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread("Downloads/WALT.jpg")
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

# Block size (11) must be odd. C (2) is subtracted from the local mean.
adaptive_mean = cv2.adaptiveThreshold(gray, 255, cv2.ADAPTIVE_THRESH_MEAN_C,
                                      cv2.THRESH_BINARY, 11, 2)

adaptive_gaussian = cv2.adaptiveThreshold(gray, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C,
                                          cv2.THRESH_BINARY, 11, 2)

plt.figure(figsize=(15, 5))
plt.subplot(1, 3, 1)
plt.imshow(gray, cmap="gray")
plt.title("Original Grayscale Image")
plt.axis("off")

plt.subplot(1, 3, 2)
plt.imshow(adaptive_mean, cmap="gray")
plt.title("Adaptive Mean Thresholding")
plt.axis("off")

plt.subplot(1, 3, 3)
plt.imshow(adaptive_gaussian, cmap="gray")
plt.title("Adaptive Gaussian Thresholding")
plt.axis("off")
plt.show()
```
### Otsu's Thresholding

- Original image is displayed.
- Otsu segmented image is displayed.
- Optimal threshold value is calculated automatically.
- Produces improved segmentation for bimodal histograms.
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread("Downloads/WALT.jpg")
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

# Threshold value is ignored (0); Otsu's method calculates the best one automatically
otsu_value, otsu_thresh = cv2.threshold(gray, 0, 255,
                                        cv2.THRESH_BINARY + cv2.THRESH_OTSU)
print("Optimal threshold value found by Otsu:", otsu_value)

plt.figure(figsize=(10, 5))
plt.subplot(1, 2, 1)
plt.imshow(gray, cmap="gray")
plt.title("Original Grayscale Image")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.imshow(otsu_thresh, cmap="gray")
plt.title(f"Otsu's Thresholding (T = {otsu_value:.0f})")
plt.axis("off")
plt.show()
```

## Output

### Original Grayscale Image

- The grayscale version of the input image is displayed.
- Serves as the input for thresholding operations.
<img width="1180" height="503" alt="Screenshot 2026-11-18 090813" src="https://github.com/user-attachments/assets/9119007b-ec55-4218-85dd-b75dbaeaa22c" />


### Global Thresholding

- Original image is displayed.
- Thresholded image is displayed.
- A fixed threshold value is used for segmentation.
- Pixels are classified as foreground or background.
<img width="1042" height="511" alt="Screenshot 2026-11-18 090819" src="https://github.com/user-attachments/assets/38c1c88a-48d8-4c03-99be-b292dc4ccaab" />

### Adaptive Thresholding

- Original image is displayed.
- Adaptive Mean Thresholded image is displayed.
- Adaptive Gaussian Thresholded image is displayed.
- Threshold values vary across different regions of the image.
- Suitable for images with uneven illumination.
<img width="1372" height="448" alt="Screenshot 2026-11-18 090830" src="https://github.com/user-attachments/assets/53a8ef96-a848-4564-a4ea-2a86f0c174d9" />


### Otsu's Thresholding

- Original image is displayed.
- Otsu segmented image is displayed.
- Optimal threshold value is calculated automatically.
- Produces improved segmentation for bimodal histograms.
<img width="1030" height="495" alt="Screenshot 2026-11-18 090840" src="https://github.com/user-attachments/assets/322c4566-a230-4cf0-bc85-fab0050da52c" />



## Result

Thus, image segmentation is successfully performed using **Global Thresholding, Adaptive Thresholding, and Otsu's Thresholding** techniques in OpenCV. 
