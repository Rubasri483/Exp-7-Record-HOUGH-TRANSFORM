# Hough Transform for Line Detection Using OpenCV

## NAME:  Rubasri R 
## REG NO: 212224240139

## Aim

To detect straight lines in an input image using the Probabilistic Hough Transform technique with OpenCV and Python.

## Software Requirements

- Python
- Anaconda
- Jupyter Notebook
- OpenCV
- NumPy
- Matplotlib

## Hough Transform

The Hough Transform is a feature extraction technique used in digital image processing to detect straight lines in an image.

The Probabilistic Hough Transform detects line segments from an edge-detected image. In this experiment, Canny Edge Detection is used to identify edges, and HoughLinesP() is used to detect straight lines.

## Algorithm

1. Import the required libraries: OpenCV, NumPy, and Matplotlib.
2. Read the input image using `cv2.imread()`.
3. Convert the input image into grayscale using `cv2.cvtColor()`.
4. Display the original image.
5. Apply Canny Edge Detection using `cv2.Canny()`.
6. Detect line coordinates using `cv2.HoughLinesP()`.
7. Extract the starting and ending coordinates of the detected lines.
8. Draw the detected lines on the original image using `cv2.line()`.
9. Display the final image with detected lines.

## Implementation

### 1. Import Libraries

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

### 2. Read and Convert the Image

```python
image = cv2.imread('Image.png')

gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
```

### 3. Display Original Image

```python
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Input Image")
plt.axis('off')
```

**OUTPUT:**

<img width="348" height="413" alt="Screenshot 2026-10-30 160311" src="https://github.com/user-attachments/assets/c813b920-1200-4ccd-9b16-fdd9755b5d13" />

### 4. Grayscale Image

```python
plt.imshow(gray_image, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')
```

**OUTPUT:**

<img width="301" height="365" alt="image" src="https://github.com/user-attachments/assets/4c35f947-b99d-4e8f-bc17-ed6660143b43" />

### 5. Canny Edge Detection

```python
edges = cv2.Canny(gray_image, 50, 150)

plt.imshow(edges, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis('off')
```

**OUTPUT:**

<img width="321" height="362" alt="image" src="https://github.com/user-attachments/assets/ba5ad41c-d242-4f44-b3cd-42a3294c706f" />

### 6. Hough Transform for Line Detection

```python
lines = cv2.HoughLinesP(
    edges,
    1,
    np.pi / 180,
    100,
    minLineLength=50,
    maxLineGap=10
)
```

### 7. Draw the Detected Lines

```python
if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line[0]
        cv2.line(image, (x1, y1), (x2, y2),
                 (0, 255, 0), 2)
```

### 8. Display the Result of Hough Transform

```python
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Result of Hough Transform")
plt.axis('off')
```

**OUTPUT:**

<img width="405" height="366" alt="image" src="https://github.com/user-attachments/assets/5c9eebe3-d438-43e9-9dfa-d9e01a4dfcb4" />

## Result

Thus, straight lines in the input image were successfully detected using the Probabilistic Hough Transform technique with OpenCV and Python.
