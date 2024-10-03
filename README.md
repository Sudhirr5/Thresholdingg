# THRESHOLDING
## Aim
To segment the image using global thresholding, adaptive thresholding and Otsu's thresholding using python and OpenCV.

## Software Required
1. Anaconda - Python 3.7
2. OpenCV

## Algorithm

### Step1:
Load the required libraries like OpenCV, NumPy, and Matplotlib.

### Step2:
Read the input image from the file and convert it to grayscale using OpenCV.

### Step3:
Apply different thresholding techniques:
Global thresholding (binary, binary inverse, truncate, to zero, to zero inverse). Otsu’s thresholding. Adaptive thresholding (mean, Gaussian).

### Step4:
Store the results of each thresholding operation in a list for easy visualization.

### Step5:
Display the original grayscale image and the thresholded images side by side using Matplotlib to compare results.


## Program

```
Developed by : SUDHIR KUMAR. R
Register number : 212223230221
```

```python
# Load the necessary packages

import numpy as np
import cv2
import matplotlib.pyplot as plt

# Read the Image and convert to grayscale

image = cv2.imread(r"C:\Users\admin\dig-img-process\fie.jpg")
image_gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Use Global thresholding to segment the image

ret, thresh_dipt1 = cv2.threshold(image_gray, 86, 255, cv2.THRESH_BINARY)
ret, thresh_dipt2 = cv2.threshold(image_gray, 86, 255, cv2.THRESH_BINARY_INV)
ret, thresh_dipt3 = cv2.threshold(image_gray, 86, 255, cv2.THRESH_TOZERO)
ret, thresh_dipt4 = cv2.threshold(image_gray, 86, 255, cv2.THRESH_TOZERO_INV)
ret, thresh_dipt5 = cv2.threshold(image_gray, 100, 255, cv2.THRESH_TRUNC)

ret, thresh_dipt6 = cv2.threshold(image_gray, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU)

# Use Adaptive thresholding to segment the image

thresh_dipt7 = cv2.adaptiveThreshold(image_gray, 255, cv2.ADAPTIVE_THRESH_MEAN_C, cv2.THRESH_BINARY, 11, 2)
thresh_dipt8 = cv2.adaptiveThreshold(image_gray, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C, cv2.THRESH_BINARY, 11, 2)

# Use Otsu's method to segment the image 

titles = [
    "Gray Image", 
    "Threshold Image (Binary)", 
    "Threshold Image (Binary Inverse)", 
    "Threshold Image (To Zero)", 
    "Threshold Image (To Zero-Inverse)", 
    "Threshold Image (Truncate)", 
    "Otsu's Threshold", 
    "Adaptive Threshold (Mean)", 
    "Adaptive Threshold (Gaussian)"
]

images = [
    image_gray, thresh_dipt1, thresh_dipt2, thresh_dipt3, 
    thresh_dipt4, thresh_dipt5, thresh_dipt6, thresh_dipt7, thresh_dipt8
]

# Display the results

for i in range(9):
    plt.figure(figsize=(8, 8))
    plt.subplot(1, 2, 1)
    plt.title("Original Image")
    plt.imshow(image)
    plt.axis("off")
    plt.subplot(1, 2, 2)
    plt.title(titles[i])
    plt.imshow(cv2.cvtColor(images[i],cv2.COLOR_BGR2RGB))
    plt.axis("off")
    plt.show()

```
## Output

### Original Image

![Screenshot 2024-10-03 091740](https://github.com/user-attachments/assets/c357c564-aa2a-42f5-96fe-7dd98abec73f)

### Global Thresholding

![Screenshot 2024-10-03 091755](https://github.com/user-attachments/assets/bca395fc-4ef1-4821-931a-917a0c107b56)

![Screenshot 2024-10-03 091813](https://github.com/user-attachments/assets/80251fea-88c6-4149-8ca6-3752100d6d42)

![Screenshot 2024-10-03 091825](https://github.com/user-attachments/assets/804de5b5-54d3-4b11-95b9-9505ce130ba2)

![Screenshot 2024-10-03 091837](https://github.com/user-attachments/assets/32e78149-7bd2-4afc-bca9-87c7e3f986b0)

![Screenshot 2024-10-03 091853](https://github.com/user-attachments/assets/0b7b2fc7-b7de-431f-8fac-462cccd7db81)

### Adaptive Thresholding

![Screenshot 2024-10-03 091921](https://github.com/user-attachments/assets/6c524d67-53a8-4b7f-823d-f422639a0f7b)

![Screenshot 2024-10-03 091937](https://github.com/user-attachments/assets/70861d7b-6fd4-4d8c-9a43-258d77c923c3)

### Optimum Global Thesholding using Otsu's Method

![Screenshot 2024-10-03 091905](https://github.com/user-attachments/assets/0c50a059-1011-407f-a13c-6477727339a8)

## Result
Thus the images are segmented using global thresholding, adaptive thresholding and optimum global thresholding using python and OpenCV.
