# Edge-Linking-using-Hough-Transformm
## Name : Iniya E
## REG NO : 212224230096
## Aim:
To write a Python program to detect the lines using Hough Transform.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:

Import all the necessary modules for the program.
### Step2:

Load a image using imread() from cv2 module.
### Step3:

Convert the image to grayscale.
### Step4:

Using Canny operator from cv2,detect the edges of the image.
### Step5:

Using the HoughLinesP(),detect line co-ordinates for every points in the images.Using For loop,draw the lines on the found co-ordinates.Display the image.
## Program
```py
import numpy as np
import cv2
import matplotlib.pyplot as plt

# READ THE IMAGE IN COLOR
img_c = cv2.imread("sevenwonder.jpg")
# CONVERT THE COLOR FROM BGR TO RGB
img_c = cv2.cvtColor(img_c, cv2.COLOR_BGR2RGB)
# CONVERT THE COLOR IMAGE TO GRAYSCALE
gray = cv2.cvtColor(img_c, cv2.COLOR_RGB2GRAY)
# APPLY GAUSSIAN BLUR TO REDUCE NOISE
gray = cv2.GaussianBlur(gray, (3, 3), 0)
```
```py
# DISPLAY ORIGINAL AND GRAY IMAGES
plt.figure(figsize=(8, 8))
plt.subplot(1, 2, 1)
plt.imshow(img_c)
plt.title("Original Image")
plt.axis("off")
plt.subplot(1, 2, 2)
plt.imshow(gray, cmap='gray')
plt.title("Gray Image")
plt.axis("off")
plt.show()
```
```py
# CANNY EDGE DETECTION
canny = cv2.Canny(gray, 120, 150)

# DISPLAY THE CANNY IMAGE
plt.figure(figsize=(5, 8))
plt.imshow(canny, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis("off")
plt.show()
```
```py
# HOUGH LINE TRANSFORM
lines = cv2.HoughLinesP(canny, 1, np.pi / 180, threshold=80, minLineLength=50, maxLineGap=250)

# DRAW THE DETECTED LINES ON THE ORIGINAL IMAGE
for line in lines:
    x1, y1, x2, y2 = line[0]
    cv2.line(img_c, (x1, y1), (x2, y2), (255, 0, 0), 3)  # Red color lines

```
```py
# DISPLAY THE RESULT IMAGE WITH LINES
plt.figure(figsize=(5, 8))
plt.imshow(img_c)
plt.title("Result Image")
plt.axis("off")
plt.show()
```
## Output

### Input image and grayscale image
<img width="819" height="341" alt="image" src="https://github.com/user-attachments/assets/a3227569-4aba-45c8-9515-48a1c3f5399c" />



### Canny Edge detector output
<img width="534" height="454" alt="image" src="https://github.com/user-attachments/assets/8b831eb1-046c-4a90-968d-2694965b2a80" />



### Display the result of Hough transform
<img width="524" height="455" alt="image" src="https://github.com/user-attachments/assets/0c5e0538-3612-4230-b445-8f949a4910b7" />



## Result
The final result will be your original image with detected straight lines overlaid in red.
