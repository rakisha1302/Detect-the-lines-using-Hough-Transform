# Detect-the-lines-using-Hough-Transform

##  Aim

To implement a basic lane detection pipeline using OpenCV by completing missing code segments at specified locations.

---

## Learning Objective

* Understand each stage of image processing
* Learn how to build a complete computer vision pipeline
* Practice writing code in guided sections

**Important Instruction:**
👉 Write code **ONLY in places marked as `# Your Code Here`**
👉 Do NOT modify any other part of the code

---

##  Software Used

* Anaconda – Python 3.7
* Jupyter Notebook / VS Code
* OpenCV (cv2)
* NumPy
* Matplotlib

---

##  Program and Output


```
import cv2
import numpy as np
import matplotlib.pyplot as plt
# Step 2: Load the image using imread() from cv2 module
image = cv2.imread('road.webp')  # Replace 'image.jpg' with your image path
# Step 3: Convert the image to grayscale
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
# Input image and grayscale image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Convert image to RGB for displaying
plt.title("Input Image")
plt.axis('off')

```

<img width="631" height="442" alt="image" src="https://github.com/user-attachments/assets/fe5ec65f-4563-4387-bd20-49a23031ed04" />


```
plt.imshow(gray_image, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')
```

<img width="617" height="452" alt="image" src="https://github.com/user-attachments/assets/578dace0-0416-4054-84b3-66ad370239d4" />


```
# Step 4: Using Canny operator from cv2, detect the edges of the image
edges = cv2.Canny(gray_image, 50, 150)  # Canny edge detection with threshold values 50 and 150
# Canny Edge Detector output
plt.imshow(edges, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis('off')
```


<img width="610" height="456" alt="image" src="https://github.com/user-attachments/assets/11541195-2034-4587-837f-93744ef618bc" />



```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Read image
image = cv2.imread("road.webp")

# Step 2: Convert to grayscale
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Step 3: Detect edges
edges = cv2.Canny(gray, 50, 150)

# Step 4: Detect lines using Hough Transform
lines = cv2.HoughLinesP(
    edges,
    1,
    np.pi / 180,
    100,
    minLineLength=50,
    maxLineGap=10
)

# Step 5: Draw detected lines
if lines is not None:
    lines = np.asarray(lines).reshape(-1, 4)

    for x1, y1, x2, y2 in lines:
        cv2.line(image, (x1, y1), (x2, y2), (0, 255, 0), 2)

# Step 6: Display result
plt.figure(figsize=(10, 6))
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.axis("off")
plt.show()
```


<img width="632" height="487" alt="image" src="https://github.com/user-attachments/assets/b139d138-8947-4b19-8c0d-1dfe36d67c4d" />





