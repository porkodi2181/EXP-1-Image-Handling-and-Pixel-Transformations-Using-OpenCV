# Image-Handling-and-Pixel-Transformations-Using-OpenCV 
## NAME:PORKODI B
## REG NO:212224240114
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
Split the image (boy.jpg) into B, G, R components and display the channels.

## Program Developed By:
- **Name:** VENKATANATHAN P R
- **Register Number:** 212223240173

### Ex. No. 01

#### 1. Read the image ('city.jpg') using OpenCV imread() as a grayscale image.
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread("PORKO.jpg", cv2.IMREAD_GRAYSCALE)
```

#### 2. Print the image width, height & Channel.
```python
height, width = img.shape

print("Width :", width)
print("Height:", height)
print("Channel: 1")
```

#### 3. Display the image using matplotlib imshow().
```python
plt.imshow(img, cmap="gray")
plt.title("Grayscale Image")
plt.axis("off")
plt.show()
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```python
cv2.imwrite("PORKO.png", img)
print("Image saved successfully.")
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
img_gray = cv2.imread("city.png", cv2.IMREAD_GRAYSCALE)
img_color = cv2.cvtColor(img_gray, cv2.COLOR_GRAY2RGB)
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```python
plt.imshow(img_color)
plt.title("Colour Image")
plt.axis("off")
plt.show()

height, width, channel = img_color.shape

print("Width :", width)
print("Height:", height)
print("Channel:", channel)
```

#### 7. Crop the image to extract any specific object from the image.
```python
cropped = img_color[150:450, 200:500]

plt.imshow(cropped)
plt.title("Cropped Image")
plt.axis("off")
plt.show()
```

#### 8. Resize the image up by a factor of 2x.
```python
resized = cv2.resize(
    img_color,
    None,
    fx=2,
    fy=2,
    interpolation=cv2.INTER_LINEAR
)

plt.imshow(resized)
plt.title("Resized Image (2x)")
plt.axis("off")
plt.show()
```

#### 9. Flip the cropped/resized image horizontally.
```python
flipped = cv2.flip(cropped, 1)

plt.imshow(flipped)
plt.title("Horizontally Flipped Image")
plt.axis("off")
plt.show()
```

#### 10. Read in the image ('city.jpg').
```python
img = cv2.imread("PORKO.jpg")
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image).
```python
text = "Smart City View"
font_face = cv2.FONT_HERSHEY_PLAIN

text_position = (180, img_rgb.shape[0] - 20)

cv2.putText(
    img_rgb,
    text,
    text_position,
    font_face,
    2,
    (255, 255, 255),
    2,
    cv2.LINE_AA
)
```

#### 12. Draw a magenta rectangle that encompasses any prominent object in the image.
```python
rect_color = (255, 0, 255)

cv2.rectangle(
    img_rgb,
    (250, 180),
    (500, 450),
    rect_color,
    3
)
```

#### 13. Display the final annotated image.
```python
plt.imshow(img_rgb)
plt.title("Annotated City Image")
plt.axis("off")
plt.show()
```

#### 14. Read the image ('city.jpg').
```python
img = cv2.imread("PORKO.jpg")
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```

#### 15. Adjust the brightness of the image.
```python
# Create a matrix of ones (with data type float64)

matrix = np.ones(img.shape, dtype="uint8") * 50
```

#### 16. Create brighter and darker images.
```python
img_brighter = cv2.add(img, matrix)
img_darker = cv2.subtract(img, matrix)
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```python
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(cv2.cvtColor(img_darker, cv2.COLOR_BGR2RGB))
plt.title("Darker Image")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(cv2.cvtColor(img_brighter, cv2.COLOR_BGR2RGB))
plt.title("Brighter Image")
plt.axis("off")

plt.show()
```

#### 18. Modify the image contrast.
```python
# Create two higher contrast images using the 'scale' option
# with factors of 1.1 and 1.2 (without overflow fix)

img_higher1 = cv2.convertScaleAbs(img, alpha=1.1, beta=0)
img_higher2 = cv2.convertScaleAbs(img, alpha=1.2, beta=0)
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```python
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(cv2.cvtColor(img_higher1, cv2.COLOR_BGR2RGB))
plt.title("Contrast 1.1")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(cv2.cvtColor(img_higher2, cv2.COLOR_BGR2RGB))
plt.title("Contrast 1.2")
plt.axis("off")

plt.show()
```

#### 20. Split the image into the B, G, R components & Display the channels.
```python
B, G, R = cv2.split(img)

plt.figure(figsize=(12,4))

plt.subplot(1,3,1)
plt.imshow(B, cmap="gray")
plt.title("Blue")

plt.subplot(1,3,2)
plt.imshow(G, cmap="gray")
plt.title("Green")

plt.subplot(1,3,3)
plt.imshow(R, cmap="gray")
plt.title("Red")

plt.show()
```

#### 21. Merge the R, G, B displays along with the original image.
```python
merged_rgb = cv2.merge((R, G, B))

plt.figure(figsize=(10,5))

plt.subplot(1,2,1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original")

plt.subplot(1,2,2)
plt.imshow(merged_rgb)
plt.title("Merged RGB")

plt.axis("off")
plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```python
hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)

H, S, V = cv2.split(hsv)

plt.figure(figsize=(12,4))

plt.subplot(1,3,1)
plt.imshow(H, cmap="gray")
plt.title("Hue")

plt.subplot(1,3,2)
plt.imshow(S, cmap="gray")
plt.title("Saturation")

plt.subplot(1,3,3)
plt.imshow(V, cmap="gray")
plt.title("Value")

plt.show()
```

#### 23. Merge the H, S, V displays along with the original image.
```python
merged_hsv = cv2.merge((H, S, V))
merged_bgr = cv2.cvtColor(merged_hsv, cv2.COLOR_HSV2BGR)

plt.figure(figsize=(10,5))

plt.subplot(1,2,1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original")

plt.subplot(1,2,2)
plt.imshow(cv2.cvtColor(merged_bgr, cv2.COLOR_BGR2RGB))
plt.title("Merged HSV")

plt.axis("off")
plt.show()
```

## Output:
<img width="348" height="512" alt="WhatsApp Image 2026-10-30 at 10 42 31 PM" src="https://github.com/user-attachments/assets/a1e2cb9f-2f42-4401-873e-1e7a9e13737b"/>
<br>

<img width="407" height="521" alt="WhatsApp Image 2026-10-30 at 10 49 57 PM" src="https://github.com/user-attachments/assets/f33807b1-1b8d-44c0-b0dc-b04d9ddfe31f" />
<br>

<img width="401" height="513" alt="WhatsApp Image 2026-10-30 at 10 49 57 PM (1)" src="https://github.com/user-attachments/assets/cb522b1f-b00c-4936-a13c-c047e01dafa7" />
<br>

<img width="401" height="513" alt="WhatsApp Image 2026-10-30 at 10 49 57 PM (1)" src="https://github.com/user-attachments/assets/4c614dba-131a-4657-9b62-bc0c76b2c8f2" />
<br>

<img width="373" height="512" alt="WhatsApp Image 2026-10-30 at 10 50 08 PM" src="https://github.com/user-attachments/assets/1f4289f2-1663-49dc-928d-530c5b7fccf6" />
<br>

<img width="393" height="517" alt="WhatsApp Image 2026-10-30 at 10 49 59 PM (1)" src="https://github.com/user-attachments/assets/005986d1-06a0-4f23-9ae4-38d2829b0a36" />
<br>

<img width="392" height="517" alt="WhatsApp Image 2026-10-30 at 10 50 01 PM" src="https://github.com/user-attachments/assets/6ff70cd5-e79b-4104-a151-ec0a93820e08" />
<br>

<img width="367" height="522" alt="WhatsApp Image 2026-10-30 at 10 50 01 PM (1)" src="https://github.com/user-attachments/assets/85da0536-3c4e-408b-b5cf-8e3fdae669ec" />
<br>

<img width="395" height="523" alt="WhatsApp Image 2026-10-30 at 10 50 02 PM" src="https://github.com/user-attachments/assets/9c77551c-ee38-4f91-9442-c434c1486393" />
<br>

<img width="383" height="521" alt="WhatsApp Image 2026-10-30 at 10 50 02 PM (1)" src="https://github.com/user-attachments/assets/ee04fedd-bfc3-4eef-874d-05774e98448e" />
<br>

<img width="401" height="505" alt="WhatsApp Image 2026-10-30 at 10 50 02 PM (2)" src="https://github.com/user-attachments/assets/e50bedba-1830-4143-a356-a9834f7cd6db" />
<br>

<img width="635" height="505" alt="WhatsApp Image 2026-10-30 at 10 50 07 PM" src="https://github.com/user-attachments/assets/518e59d7-803a-45c8-a99e-ddab4d2b36d3" />
<br>

<img width="506" height="522" alt="WhatsApp Image 2026-10-30 at 10 50 07 PM (1)" src="https://github.com/user-attachments/assets/20877732-5393-4a68-9d9d-5c491c528d1b" />
<br>

<img width="372" height="521" alt="WhatsApp Image 2026-10-30 at 10 50 07 PM (2)" src="https://github.com/user-attachments/assets/a45c8401-ab1c-44c3-a343-db6a88666276" />
<br>


<img width="385" height="528" alt="WhatsApp Image 2026-10-30 at 10 50 07 PM (3)" src="https://github.com/user-attachments/assets/049d7b86-8754-41d1-80d1-835310c49d5c" />
<br>





## Result:
Thus, the image was read and displayed successfully. Brightness and contrast adjustments were performed, the BGR and HSV channels were split and merged successfully, and the required image processing operations were implemented using OpenCV.
