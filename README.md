# Image-Handling-and-Pixel-Transformations-Using-OpenCV 
## Program Developed By:
### NAME: SHARON STEFFANI.F
### REG NO: 212223110049

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
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
## Ex. No. 01

#### 1. Read the image using OpenCV
```python
import cv2
import matplotlib.pyplot as plt
img = cv2.imread('sharon.jpeg', cv2.IMREAD_COLOR)

```

#### 2. Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
```python
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img.shape

```

#### 3. Display the image using Matplotlib
```python
plt.imshow(img_rgb, cmap='viridis')  # You can change 'viridis' to another cmap or use None for RGB images
plt.title("Original Image")
plt.axis('off')  # Removes axis ticks and labels
plt.show()
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```python
img=cv2.imread("sharon.jpeg")
cv2.imwrite("sharon.png",img)
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
image = cv2.imread('sharon.jpeg')
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```

#### 6. Draw a line from top-left to bottom-right 
```python
line_img = cv2.line(img_rgb, (0, 0), (768, 600), (255, 0, 0), 2)
plt.imshow(line_img, cmap='viridis')  
plt.title("Image with Line")
plt.axis('off')  
plt.show()
```

#### 7. Draw a circle at the center of the image.
```python
image = cv2.imread('sharon.jpeg') 
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape
circle_img = cv2.circle(img_rgb,(400,300),150,(255,0,0),10)
plt.imshow(circle_img, cmap='viridis')  
plt.title("Image with Circle")
plt.axis('off')  
plt.show()
```

#### 8. Draw a rectangle around  the whole image
```python
image = cv2.imread('sharon.jpeg') 
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img.shape
rectangle_img = cv2.rectangle(img_rgb, (0, 0), (768, 600), (0, 0, 255), 10)
plt.imshow(rectangle_img, cmap='viridis')  
plt.title("Image with Rectangle")
plt.axis('off')  
plt.show()

```

#### 9. Add the text "OpenCV Drawing" at the top-left corner of the image.
```python
image = cv2.imread('sharon.jpeg') 
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
text_img = cv2.putText(img_rgb, "OpenCV Drawing", (10, 30), cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 255, 255), 10)
plt.imshow(text_img, cmap='viridis')  
plt.title("Image with Text")
plt.axis('off')  
plt.show()
```

#### 10.Convert the image from RGB to HSV and display it.
```python
image = cv2.imread('sharon.jpeg')
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
plt.imshow(image_rgb)
plt.title("Original RGB Image")
plt.axis("off")
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)
plt.imshow(image_hsv)
plt.title("HSV Image")
plt.axis("off")
```

#### 11. Convert RGB to GRAY
```python
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)
plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("off")
```

#### 12. Convert RGB to YCrCb
```python
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)
plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis("off")
```

#### 13. Convert HSV back to RGB
```python
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)
plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis("off")
```

#### 14. Modify a block of pixels (300x300) to white, starting from (200, 200)
```python
image[200:500, 200:500] = [255, 255, 255]
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
plt.imshow(image_rgb)
plt.title("Image with 300x300 White Block")
plt.axis("off")
plt.show()
```

#### 15. Resize the original image to half its size and display it.
```python
image = cv2.imread('sharon.jpeg')
image.shape
resized_image = cv2.resize(image, (768 // 2, 600 // 2)) 
resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)
resized_image_rgb.shape
plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis("off")
plt.show()
```

#### 16. Crop a region of interest (ROI) from the image (e.g., a 100x100 pixel area starting at (50, 50)) and display it.
```python
image = cv2.imread('sharon.jpeg')
image.shape
roi = image[50:350, 50:350]
roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)
plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis("off")
plt.show()
```

#### 17. Flip the original image horizontally and display it.
```python
image = cv2.imread('sharon.jpeg') 
flipped_horizontally = cv2.flip(image, 1)
flipped_horizontally_rgb = cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB)
plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("off")
```

#### 18. Flip the original image vertically and display it.
```python
flipped_vertically = cv2.flip(image, 0)
flipped_vertically_rgb = cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB)
plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("off")
```


## Output:
 1. Read the image using OpenCV

 
 <img width="297" height="409" alt="download" src="https://github.com/user-attachments/assets/033b6aff-4cc7-4f5d-8c58-17f6ba941562" />





2.  Draw a line from top-left to bottom-right


<img width="297" height="409" alt="download" src="https://github.com/user-attachments/assets/954918a4-a910-4d3a-a82d-1d539e0ffbf2" />



3)Draw a circle at the center of the image.


<img width="297" height="409" alt="download" src="https://github.com/user-attachments/assets/bd584f17-2014-4ad3-b6bd-499e604d6886" />




4)Draw a rectangle around  the whole image


<img width="297" height="409" alt="download" src="https://github.com/user-attachments/assets/53ffcbbe-31ce-4c56-90eb-99125c8cec45" />



5)Add the text "OpenCV Drawing" at the top-left corner of the image.


<img width="297" height="409" alt="download" src="https://github.com/user-attachments/assets/ca4f1165-e74e-40ae-8be6-eea9f090e9ab" />



6)Convert the image from RGB to HSV and display it.

<img width="297" height="409" alt="download" src="https://github.com/user-attachments/assets/e3fc136c-ac50-4fd5-909d-cb6752a9ab8a" />


7) Convert the image from RGB to GRAY and display it. 


<img width="297" height="409" alt="download" src="https://github.com/user-attachments/assets/ffa11fc0-49f1-4596-9274-78c64308dd23" />




8) Convert the image from RGB to YCrCb and display it. 


<img width="297" height="409" alt="download" src="https://github.com/user-attachments/assets/3bb0d498-3d4c-4eb2-b97b-4e646ddd7834" />



9)Convert the HSV image back to RGB and display it.


<img width="297" height="409" alt="download" src="https://github.com/user-attachments/assets/2856ea25-3839-44a8-a205-991f074b1f15" />


10) Modify the color of the pixel at (200, 200) to white.


<img width="297" height="409" alt="download" src="https://github.com/user-attachments/assets/38b49f63-44a6-4c56-91d2-ef4b89b5cfb4" />


11)  Resize the original image to half its size and display it.

    
<img width="493" height="409" alt="download" src="https://github.com/user-attachments/assets/e3a45bc6-f04a-4890-bc33-dfb5961c76aa" />


12)Crop a region of interest (ROI) from the image (e.g., a 100x100 pixel area starting at (50, 50)) and display it.


<img width="389" height="409" alt="download" src="https://github.com/user-attachments/assets/dfbf1f9a-1531-486c-8d1b-bae93e8327d9" />




13) Flip the original image horizontally and display it.


<img width="297" height="409" alt="download" src="https://github.com/user-attachments/assets/473cff69-993e-410c-ae78-f1a6798a8826" />

14) Flip the original image vertically and display it.

<img width="297" height="409" alt="download" src="https://github.com/user-attachments/assets/e8ccb941-4251-4f80-9555-31ee2f96bbfb" />



## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.
