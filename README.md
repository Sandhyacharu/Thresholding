# Thresholding of Images
## Aim
To segment the image using global thresholding, adaptive thresholding and Otsu's thresholding using python and OpenCV.

## Software Required
1. Anaconda - Python 3.7
2. OpenCV

## Algorithm
### Step 1:
Load the necessary packages.

### Step 2:
Read the Image and convert to grayscale.

### Step 3:
Use Global thresholding to segment the image.

### Step 4:
Use Adaptive thresholding to segment the image.

### Step 5:
Use Otsu's method to segment the image.

### Step 6:
Display the results.

# Load the necessary packages

import cv2
import matplotlib.pyplot as plt
import numpy as np

# Read the Image and convert to grayscale

image=cv2.imread("Tvd.jpg")
image1=cv2.cvtColor(image,cv2.COLOR_BGR2GRAY)

# Use Global thresholding to segment the image

ret, thresh1 = cv2.threshold(image1,100,200,cv2.THRESH_BINARY)
ret, thresh2 = cv2.threshold(image1,100,200,cv2.THRESH_BINARY_INV)
ret, thresh3 = cv2.threshold(image1,100,200,cv2.THRESH_TRUNC)
ret, thresh4 = cv2.threshold(image1,100,200,cv2.THRESH_TOZERO)
ret, thresh5 = cv2.threshold(image1,100,200,cv2.THRESH_TOZERO_INV)


# Use Adaptive thresholding to segment the image

th1=cv2.adaptiveThreshold(image1,255,cv2.ADAPTIVE_THRESH_MEAN_C,cv2.THRESH_BINARY,11,2)
th2=cv2.adaptiveThreshold(image1,255,cv2.ADAPTIVE_THRESH_GAUSSIAN_C,cv2.THRESH_BINARY,11,2)

# Use Otsu's method to segment the image 

ret2,th3 = cv2.threshold(image1,0,255,cv2.THRESH_BINARY+cv2.THRESH_OTSU)

# Display the results

titles=["Gray Image","THRESH_BINARY","THRESH_BINARY_INV","THRESH_TRUNC"
       ,"THRESH_TOZERO","THRESH_TOZERO_INV","ADAPTIVE_THRESH_MEAN_C","ADAPTIVE_THRESH_GAUSSIAN_C","OTSU"]
images=[image1,thresh1,thresh2,thresh3,thresh4,thresh5,th1,th2,th3]
for i in range(0,9):
    plt.figure(figsize=(10,10))
    plt.subplot(1,2,1)
    plt.title("Original Image")
    plt.imshow(image)
    plt.axis("off")
    plt.subplot(1,2,2)
    plt.title(titles[i])
    plt.imshow(cv2.cvtColor(images[i],cv2.COLOR_BGR2RGB))
    plt.axis("off")
    plt.show()
```
## Output

### Original Image
![image](https://user-images.githubusercontent.com/75235167/169636908-0b1e7ce6-8dd7-44ea-b768-ce646479f1ba.png)

### Global Thresholding
![image](https://user-images.githubusercontent.com/75235167/169636917-13aa8386-1dc4-4a6d-8055-680536aa150b.png)
![image](https://user-images.githubusercontent.com/75235167/169636943-adf7cb6e-6de8-4a1b-b2be-927bfb990df9.png)
![image](https://user-images.githubusercontent.com/75235167/169636958-5a6934b9-886e-494d-bcae-a230838c420b.png)

### Adaptive Thresholding
![image](https://user-images.githubusercontent.com/75235167/169636976-706f9e8a-cdce-4415-9424-4563163b7832.png)

### Optimum Global Thesholding using Otsu's Method
![image](https://user-images.githubusercontent.com/75235167/169636979-aa3e1823-9042-47fe-96f2-239b8a2c74a9.png)

## Result
Thus the images are segmented using global thresholding, adaptive thresholding and optimum global thresholding using python and OpenCV.

