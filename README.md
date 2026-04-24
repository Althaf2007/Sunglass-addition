# Sturdy Octo Disco

**Sturdy Octo Disco** is a fun and creative computer vision project that adds stylish sunglasses to photos using image processing techniques.

## About the Project

Welcome to **Sturdy Octo Disco**, a playful project designed to automatically overlay sunglasses on individual passport-size photos! This project demonstrates how computer vision can transform ordinary images into something cool and engaging.

Whether you're a beginner exploring image processing or someone looking for a unique mini-project, this is a great place to start.

## Features

*  Detects faces in images accurately
*  Adds sunglasses overlay perfectly aligned to the face
*  Works best with passport-size and single-person photos
*  Easily customizable sunglasses styles
*  Fast and lightweight processing


## Technologies Used

* **Python**
* **OpenCV** – for face detection and image processing
* **NumPy** – for handling image arrays

## How to Use

1. Clone this repository
2. Install the required libraries (`opencv-python`, `numpy`)
3. Add your image to the project folder
4. Run the Python script
5. See your "cool" transformed image with sunglasses 

## Program

```python
# Import libraries 
import cv2 
import numpy as np 
import matplotlib.pyplot as plt 

# Load the Face Image 
faceImage = cv2.imread("C:\\Users\\admin\\Documents\\Workshop 1\\Sturdy-Octo-Disco-Adding-Sunglasses-for-a-Cool-New-Look-main\\my pic.jpg") 
plt.imshow(faceImage[:,:,::-1]);plt.title("Face")

faceImage.shape
#resized_faceImage.shape
faceImage.shape

# Load the Sunglass image with Alpha channel
# (http://pluspng.com/sunglass-png-1104.html)
glassPNG = cv2.imread("Image-Source-PlusPNG.com.png",-1)
plt.imshow(glassPNG[:,:,::-1]);plt.title("glassPNG")

# Resize the image to fit over the eye region
glassPNG = cv2.resize(glassPNG,(125,50))
print("image Dimension ={}".format(glassPNG.shape))

# Separate the Color and alpha channels
glassBGR = glassPNG[:,:,0:3]
glassMask1 = glassPNG[:,:,3]

# Display the images for clarity
plt.figure(figsize=[15,15])
plt.subplot(121);plt.imshow(glassBGR[:,:,::-1]);plt.title('Sunglass Color channels');
plt.subplot(122);plt.imshow(glassMask1,cmap='gray');plt.title('Sunglass Alpha channel');

# Make a copy
#faceWithGlassesNaive = resized_faceImage.copy()
faceWithGlassesNaive = faceImage.copy()

# Replace the eye region with the sunglass image
faceWithGlassesNaive[100:150,75:200]=glassBGR

plt.imshow(faceWithGlassesNaive[...,::-1])

# Make the dimensions of the mask same as the input image.
# Since Face Image is a 3-channel image, we create a 3 channel image for the mask
glassMask = cv2.merge((glassMask1,glassMask1,glassMask1))

# Make the values [0,1] since we are using arithmetic operations
glassMask = np.uint8(glassMask/255)

# Make a copy
faceWithGlassesArithmetic = faceImage.copy()

# Get the eye region from the face image
eyeROI= faceWithGlassesArithmetic[100:150,75:200]

# Use the mask to create the masked eye region
maskedEye = cv2.multiply(eyeROI,(1-  glassMask ))

# Use the mask to create the masked sunglass region
maskedGlass = cv2.multiply(glassBGR,glassMask)

# Combine the Sunglass in the Eye Region to get the augmented image
eyeRoiFinal = cv2.add(maskedEye, maskedGlass)

# Display the intermediate results
plt.figure(figsize=[20,20])
plt.subplot(131);plt.imshow(maskedEye[...,::-1]);plt.title("Masked Eye Region")
plt.subplot(132);plt.imshow(maskedGlass[...,::-1]);plt.title("Masked Sunglass Region")
plt.subplot(133);plt.imshow(eyeRoiFinal[...,::-1]);plt.title("Augmented Eye and Sunglass")

# Replace the eye ROI with the output from the previous section
faceWithGlassesArithmetic[100:150,75:200]=eyeRoiFinal

# Display the final result
plt.figure(figsize=[20,20]);
plt.subplot(121);plt.imshow(faceImage[:,:,::-1]); plt.title("Original Image");
plt.subplot(122);plt.imshow(faceWithGlassesArithmetic[:,:,::-1]);plt.title("With Sunglasses");
```

## Algorithm

1. Start
2. Import required libraries (OpenCV, NumPy, Matplotlib)
3. Load the input face image
4. Load the Sunglass image with Alpha channel
5. Resize the sunglasses image
6. Separate color and alpha channels of the sunglasses
7. Display sunglasses and mask for verification
8. Copy the original image
9. Select eye region (ROI) manually
10. Overlay sunglasses directly (naive method)
11. Create a 3-channel mask from alpha channel
12. Normalize mask values to range [0,1]
13. Extract eye region from face image
14. Apply mask to remove background from eye region
15. Apply mask to extract sunglasses region
16. Combine both regions using addition
17. Replace the ROI in original image
18. Display final output
19. Stop

## Applications

* Learning basic computer vision concepts
* Fun photo editing experiments
* Practicing face detection and overlays
* Creative mini-projects

## Customization

* Replace sunglasses image with your own design
* Adjust size and position for better fit
* Extend to support multiple faces
* Add filters or additional accessories

## Contributing

Feel free to **fork**, **modify**, and **improve** this project. Contributions are always welcome!

## Result

The sunglasses are successfully overlaid on the face image with proper alignment and blending, producing a realistic and enhanced output.
