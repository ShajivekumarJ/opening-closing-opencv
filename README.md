# Exp 10 - Opening and Closing Operations Using OpenCV
## Developed by: SHAJIVE KUMAR J 
## Reg No: 212225230258
## Date: 27/08/2026

## Aim

To write a Python program using OpenCV to perform morphological Opening and Closing operations on an image.

The program performs the following operations:

- Morphological Opening
- Morphological Closing

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

Create or load an input image containing foreground objects.

### Step 3:

Display the original image.

### Step 4:

Create a structuring element (kernel) of suitable size.

### Step 5: Opening Operation

- Apply the Opening operation using the structuring element.
- Opening consists of Erosion followed by Dilation.
- Remove small foreground noises while preserving the shape of larger objects.
- Display the opened image.

### Step 6: Closing Operation

- Apply the Closing operation using the structuring element.
- Closing consists of Dilation followed by Erosion.
- Fill small holes and gaps within foreground objects.
- Display the closed image.

### Step 7:

Compare the original, opened, and closed images.

## Program
```py
import cv2
import matplotlib.pyplot as plt
import numpy as np

# Step 2: Create a synthetic binary image with noise and holes
# (You can replace this with cv2.imread('your_image.png', 0) to load a custom image)
image = np.zeros((300, 300), dtype=np.uint8)

# Draw main foreground objects (rectangles)
cv2.rectangle(image, (50, 50), (120, 120), 255, -1)
cv2.rectangle(image, (180, 50), (250, 120), 255, -1)

# Add noise (small foreground dots) for Opening test
cv2.circle(image, (30, 200), 3, 255, -1)
cv2.circle(image, (100, 220), 4, 255, -1)

# Add small holes inside a foreground object for Closing test
cv2.circle(image, (85, 85), 3, 0, -1)
cv2.circle(image, (215, 85), 4, 0, -1)

# Step 4: Create a 5x5 rectangular structuring element (kernel)
kernel = np.ones((5, 5), np.uint8)

# Step 5: Perform Morphological Opening (Erosion followed by Dilation)
opened_image = cv2.morphologyEx(image, cv2.MORPH_OPEN, kernel)

# Step 6: Perform Morphological Closing (Dilation followed by Erosion)
closed_image = cv2.morphologyEx(image, cv2.MORPH_CLOSE, kernel)

# Step 7: Display and compare the Original, Opened, and Closed Images
plt.figure(figsize=(12, 4))

plt.subplot(1, 3, 1)
plt.imshow(image, cmap="gray")
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 3, 2)
plt.imshow(opened_image, cmap="gray")
plt.title("Opening (Noise Removed)")
plt.axis("off")

plt.subplot(1, 3, 3)
plt.imshow(closed_image, cmap="gray")
plt.title("Closing (Holes Filled)")
plt.axis("off")

plt.tight_layout()
plt.show()
```

## Output

### Original Image

- The input image is displayed.
- The image serves as the source for morphological processing.

<img width="405" height="426" alt="image" src="https://github.com/user-attachments/assets/957b4ff8-34ba-430a-9e71-1dfa173ebfba" />


### Opening Operation

- Original image is displayed.
- Opened image is displayed.
- Small foreground noise is removed.
- Thin protrusions and isolated pixels are eliminated.
- Object boundaries become smoother.

<img width="405" height="445" alt="image" src="https://github.com/user-attachments/assets/ca897b7e-1596-4ac2-8d96-67ed9ee76d1e" />


### Closing Operation

- Original image is displayed.
- Closed image is displayed.
- Small holes and gaps inside objects are filled.
- Broken regions are connected.
- Object boundaries become more continuous.

<img width="417" height="432" alt="image" src="https://github.com/user-attachments/assets/9536a12c-6b9e-4175-b32c-c4a32bfe501f" />


## Applications

### Opening

- Noise removal in binary images.
- Separation of connected objects.
- Preprocessing for object detection.

### Closing

- Filling small holes in objects.
- Connecting nearby components.
- Enhancing segmented regions.

## Advantages

### Opening

- Removes unwanted foreground noise.
- Preserves major object structures.
- Improves segmentation quality.

### Closing

- Restores object continuity.
- Eliminates small background gaps.
- Improves object representation.

## Result

Thus, the morphological operations **Opening** and **Closing** are successfully implemented using OpenCV. 
