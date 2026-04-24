# Sturdy-Octo-Disco - Adding Sunglasses

## Aim

To develop a system that overlays sunglasses on a face image using image processing techniques.

## Objective

* To understand image overlay techniques
* To apply masking and blending operations
* To work with Region of Interest (ROI)
* To create a simple augmented image

## Introduction

Image processing allows us to manipulate digital images to achieve desired outputs. In this project, sunglasses are added to a face image using masking and blending techniques.

A sunglasses image with a transparent background is placed on the eye region of a face. The transparency (alpha channel) helps in blending the sunglasses naturally with the face.


## Methodology

1. Load the face image
2. Load the sunglasses image (PNG with transparency)
3. Resize the sunglasses to match eye region
4. Extract alpha channel to create mask
5. Select eye region (ROI) manually
6. Remove unwanted background using mask
7. Blend sunglasses with the face
8. Replace the processed region back into original image


## Algorithm

1. Start
2. Load face image
3. Load sunglasses image
4. Resize sunglasses
5. Extract color and alpha channel
6. Create mask from alpha channel
7. Select eye region (ROI)
8. Apply mask on ROI
9. Apply mask on sunglasses
10. Combine both using addition
11. Replace ROI in original image
12. Display final image
13. Stop

## Output

### 1. Original Image

<img width="461" height="536" alt="image" src="https://github.com/user-attachments/assets/380cb9eb-208e-49b2-a038-aa9fd584915b" />


### 2. Masked Eye Region

<img width="453" height="195" alt="image" src="https://github.com/user-attachments/assets/1cf9d4d2-32b5-4b1b-9858-93b05d0da041" />


### 3. Masked Sunglass Region

<img width="458" height="218" alt="image" src="https://github.com/user-attachments/assets/0888b039-88ba-4ec3-a90d-6a7bb923ee3d" />


### 4. Augmented Eye + Sunglasses

<img width="429" height="219" alt="image" src="https://github.com/user-attachments/assets/53bd8ae7-0d43-4d06-92b7-f04d565bb2af" />


### 5. Final Output

<img width="1371" height="823" alt="image" src="https://github.com/user-attachments/assets/abb6b00f-b58b-4db2-8e30-0196e27c6bd8" />


## Limitations

* Eye region is selected manually
* Not suitable for multiple faces
* Placement may vary for different images


## Future Enhancements

* Automatic face & eye detection
* Real-time webcam support
* Multiple accessories (hat, mask, etc.)

## Result

The sunglasses are successfully overlaid on the face image using masking and blending, producing a realistic output.
