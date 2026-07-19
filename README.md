# DIPT_EX_01 - Image-Handling-and-Pixel-Transformations-Using-OpenCV-Completion-requirements

### DEVELOPED BY : TAMIZHSELVAN B
### REG NO : 212223230225 

## AIM :
Write a Python program using OpenCV that performs the following tasks:

1. Read and Display an Image.
2. Adjust the brightness of an image.
3. Modify the image contrast.
4. Generate a third image using bitwise operations.

## SOFTWARE REQUIRED :
```
--> Anaconda - Python 3.7
--> Jupyter Notebook (for interactive development and execution)
```
## ALGORITHM :

### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels


## PROGRAM :


1. Load an image from your local directory and display it.
```py 
import cv2
import matplotlib.pyplot as plt

# Read the image using OpenCV
img = cv2.imread('Tamizh.jpeg', cv2.IMREAD_COLOR)

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Display the image using Matplotlib
plt.imshow(img_rgb, cmap='viridis')  # You can change 'viridis' to another cmap or use None for RGB images
plt.title("Original Image")
plt.axis('on')  # Removes axis ticks and labels
plt.show()
```
2 . Draw a line from the top-left to the bottom-right of the image.
```py
# Load the image
image = cv2.imread('Tamizh.jpeg')

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape

# Draw a line from top-left to bottom-right
line_img = cv2.line(img_rgb, (0, 0), (1064, 1279), (0, 255, 0), 10) # cv2.line(image, start_point, end_point, color, thickness)
plt.imshow(line_img, cmap='viridis')  
plt.title("Image with Line")
plt.axis('on')  
plt.show()

```
3. Draw a circle at the center of the image.

```py
# Load the image
image = cv2.imread('Tamizh.jpeg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape

circle_img = cv2.circle(img_rgb,(532,600),500,(0,0,255),10) # cv2.circle(image, center, radius, color, thickness)

plt.imshow(circle_img, cmap='viridis')  
plt.title("Image with Circle")
plt.axis('off')  
plt.show()

```
4. Draw a rectangle around  the whole image.
```py
# Load the image
image = cv2.imread('Tamizh.jpeg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img.shape

# Draw a rectangle around the Whole image
rectangle_img = cv2.rectangle(img_rgb, (0, 0), (1064, 1279), (255, 0, 0), 30)  # cv2.rectangle(image, start_point, end_point, color, thickness)

plt.imshow(rectangle_img, cmap='viridis')  
plt.title("Image with Rectangle")
plt.axis('off')  
plt.show()

```

5. Add the text "OpenCV Drawing" at the top-left corner of the image.
```py
# Load the image
image = cv2.imread('Tamizh.jpeg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Add text to the image
text_img = cv2.putText(img_rgb, "OpenCV Drawing", (10, 30), cv2.FONT_HERSHEY_SIMPLEX, 1, (0, 0, 255), 10)  ## cv2.putText(image, text, position, font, font_scale, color, thickness)

plt.imshow(text_img, cmap='viridis')  
plt.title("Image with Text")
plt.axis('on')  
plt.show()
```
6. Original RGB image and display it.
```py
# Load the image
image = cv2.imread('Tamizh.jpeg') 
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# Original RGB Image
plt.imshow(image_rgb)
plt.title("Original RGB Image")
plt.axis("on")
```
7. Convert the image from RGB to HSV and display it.
```py
# Convert RGB to HSV
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)

# HSV Image
plt.imshow(image_hsv)
plt.title("HSV Image")
plt.axis("on")
```
8. Convert the image from RGB to GRAY and display it.
```py
# Convert RGB to GRAY
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)

# Grayscale Image
plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("on")
```
9. Convert the image from RGB to YCrCb and display it.
```py
# Convert RGB to YCrCb
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)

# YCrCb Image
plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis("on")
```   
10. Convert the HSV image back to RGB and display it.
```py
# Convert HSV back to RGB
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)

plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis("on")
```

11. Modify a block of pixels (300x300) to white, starting from (200, 200).
```py
# Modify a block of pixels (300x300) to white, starting from (200, 200)
image[200:500, 200:500] = [255, 255, 255]  # Rows: 200-499, Columns: 200-499

# Convert BGR to RGB for displaying with Matplotlib
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# Display the modified image
plt.imshow(image_rgb)
plt.title("Image with 300x300 White Block")
plt.axis("on")
plt.show()

```

12. Resize the original image to half its size and display it.
```py
# Load the image
image = cv2.imread('Tamizh.jpeg') 
image.shape

# Resize the image to half its size
resized_image = cv2.resize(image, (1280 // 2, 1065 // 2))  # (new_width, new_height)

# Convert BGR to RGB for displaying with Matplotlib
resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)
resized_image_rgb.shape

# Display the resized image
plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis("on")
plt.show()
```
13. Crop a region of interest (ROI) from the image (e.g., a 100x100 pixel area starting at (50, 50)) and display it.

```py
# Load the image
image = cv2.imread('Tamizh.jpeg') 
image.shape

# Crop a 300x300 region starting from (50, 50)
roi = image[50:350, 50:350]  # Rows: 50-349, Columns: 50-349

# Convert BGR to RGB for displaying with Matplotlib
roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)

# Display the cropped region (ROI)
plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis("on")
plt.show()
```

14.  Flip the original image horizontally and display it.
```py

# Flip the image horizontally (left-right)
flipped_horizontally = cv2.flip(image, 1)

# Convert BGR to RGB for displaying with Matplotlib
flipped_horizontally_rgb = cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB)

# Horizontal flip
plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("on")

```
15. Flip the original image vertically and display it.
```py
# Flip the image vertically (up-down)
flipped_vertically = cv2.flip(image, 0)

# Convert BGR to RGB for displaying with Matplotlib
flipped_vertically_rgb = cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB)

# Vertical flip
plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("on")

```

### OUTPUT :

1. Original Image.

<img width="448" height="511" alt="image" src="https://github.com/user-attachments/assets/874c9398-fc49-4e2d-958c-76c1eb55be14" />

2. Image with Line.

<img width="450" height="506" alt="image" src="https://github.com/user-attachments/assets/e94d5fb7-4bf2-48ea-b4dc-d6c160b26e3e" />

3. Image with Circle.

<img width="406" height="481" alt="image" src="https://github.com/user-attachments/assets/69ce284c-f864-49bc-a672-d26018a40400" />

4. Image with Rectangle.

<img width="432" height="482" alt="image" src="https://github.com/user-attachments/assets/cde5456a-fef3-4a13-8d58-64068d19256e" />

5. Image with Text.

<img width="480" height="513" alt="image" src="https://github.com/user-attachments/assets/63d87309-5f66-4cd6-a7f4-e9b32abe991b" />

6. Original RBG Image.

<img width="476" height="503" alt="image" src="https://github.com/user-attachments/assets/4ceeca46-2c47-4d85-94a2-be3f095857ac" />

7. HSV Image .

<img width="440" height="493" alt="image" src="https://github.com/user-attachments/assets/b59c9ea9-cedb-4469-bd0b-7aa314f96f80" />


8. GrayScale Image.

<img width="466" height="492" alt="image" src="https://github.com/user-attachments/assets/f887d728-a36f-4c12-ad22-59e2931eb826" />

9. YCrCb Image.

<img width="465" height="503" alt="image" src="https://github.com/user-attachments/assets/69c6d8a6-36a9-4bf0-ba36-730752d66cf5" />

10. HSV to Original RGB Image.

<img width="452" height="503" alt="image" src="https://github.com/user-attachments/assets/f539e803-222d-4616-a6ed-603dc2fa8ce1" />

11. Image with White Block

<img width="487" height="513" alt="image" src="https://github.com/user-attachments/assets/14ef6d56-b190-40ae-aaaa-c840920f4de7" />

12. Resized Image(Half Image).

<img width="635" height="507" alt="image" src="https://github.com/user-attachments/assets/f4a6e08a-6778-416b-b9d4-3dc66fe56d58" />

13. Cropped Region Image .

<img width="552" height="510" alt="image" src="https://github.com/user-attachments/assets/1b162031-0774-4aab-b82d-f1b7b9264ebd" />

14. Flipped Vertical Image.

<img width="620" height="541" alt="image" src="https://github.com/user-attachments/assets/19117805-f85d-443b-88d1-0386f8c7d83c" />

15. Flipped Horizontal Image.

<img width="617" height="533" alt="image" src="https://github.com/user-attachments/assets/f02393de-7133-4c91-a2d6-8a2a20f63653" />


## RESULT :

Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.
