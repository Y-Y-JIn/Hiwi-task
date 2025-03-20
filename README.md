# Hiwi-task: 


## If you wanna open the code, files related to the different models in the VSCode directly, 
Go to the "open recent" - "~/Python [WSL:Ubuntu]" & open the folder

## If you wanna see the LSTM-UNet folder, 
Go to the "open recent" - "/home/nemolinux/[WSL: Ubuntu]" & open the folder [You can save your own download directory for the new copied LSTM-UNet repository]


## Model Classification 

### 1. Automatic Segmentation model
LSTM-UNet (mask dataset is missing & issue with the image crop size)<br />
Mask R-CNN (Fail)<br />
Detectron2 (Fail)<br />
U-net (include those files: U-net_final_v2 & inference_v2 & implementation of U-net model) (issue)<br />

### 2. Classification and labeling model
ResNet50<br />
CNN<br />

### 3. Hands-on segmentation model
SAM2<br />
<br /><br />



## How to access and build SAM2 for segmentation


### Prerequisite
1. sam2_image_predictor_update_2nd.ipynb ,
   "literally sam2 model script"

3. image_editor.ipynb ,   "image editor script to crop the bottom of SEM image about setting"

4. original_image , 
     "original image dataset: 5 different image folders (tif.file)"<br /><br />



### Path in "Nemo"
1. Sam2: <br /> Ubuntu/home/nemolinux/Python/sam2/notebooks/SAM_model_test/sam2_image_predictor_update_2nd.ipynb

2. Image editor script for cropping the bottom of SEM image: <br /> Ubuntu/home/nemolinux/Python/sam2/notebooks/SAM_model_test/image_editor.ipynb

3. Original image dataset:<br />  Ubuntu/home/nemolinux/Python/sam2/notebooks/image_SEM/original_image/...<br /><br /> 
   Segmented image dataset:<br />  Ubuntu/home/nemolinux/Python/sam2/notebooks/image_SEM/segmented_images/...<br /><br />



### Data
The input data is below:<br /> 
- File name: "original_image"<br /> 
'20210215' <br /> 
'20210412' <br /> 
'20210415'<br /> 
'HR_np'<br /> 
'soil_extracts'<br /> 


- File name: "segmented_images"<br /> 
'20210215_v3' <br /> 
'20210412_v3' <br /> 
'20210415_v3'<br /> 
'HR_np_v3'<br /> 
'soil_extracts_v3'<br /> 

Make sure that original images are .tif files & segmented images are .jpg files.<br /><br />

### Running sam2.ipynb

- go to the "sam2_image_predictor_update_2nd.ipynb"

- Do not run this code, checkpoints are already created in the environment, "Ubuntu/home/nemolinux/Python/sam2/notebooks/configs/sam2..."<br /><br />
code line[19]<br />

!wget -q https://dl.fbaipublicfiles.com/segment_anything_2/072824/sam2_hiera_tiny.pt -P {HOME}/checkpoints<br />
!wget -q https://dl.fbaipublicfiles.com/segment_anything_2/072824/sam2_hiera_small.pt -P {HOME}/checkpoints<br />
!wget -q https://dl.fbaipublicfiles.com/segment_anything_2/072824/sam2_hiera_base_plus.pt -P {HOME}/checkpoints<br />
!wget -q https://dl.fbaipublicfiles.com/segment_anything_2/072824/sam2_hiera_large.pt -P {HOME}/checkpoints<br /><br />

- Change the path of the target image like the code below<br /><br />
code line[55]<br />

IMAGE_PATH = f"{HOME}/image_SEM/original_images/soil_extracts/sample8_03.tif"<br />
image_bgr = cv2.imread(IMAGE_PATH)<br />
image_rgb = cv2.cvtColor(image_bgr, cv2.COLOR_BGR2RGB)<br /><br />

- Change the path of the target image in the same way<br /><br />
code line[61]<br />

(updated_version_Load image and create a copy for reset)<br />
IMAGE_PATH = f"{HOME}/image_SEM/original_images/soil_extracts/sample8_03.tif"<br />
image_bgr = cv2.imread(IMAGE_PATH)<br />
original_image = image_bgr.copy()<br /><br />


- Create the bounding boxes for segmentation<br /><br />
code line[62]<br />

```python
import cv2
(Set up OpenCV window and mouse callback)
cv2.namedWindow("Draw Bounding Boxes", cv2.WINDOW_NORMAL)
cv2.setMouseCallback("Draw Bounding Boxes", draw_rectangle)

print("Use your mouse to draw bounding boxes. Press 'd' to delete the last box, 'r' to reset all boxes, and 'q' to finish.")

while True:
    ("Display the image with bounding boxes")
    cv2.imshow("Draw Bounding Boxes", image_bgr)

    # Wait for key press and handle events
    key = cv2.waitKey(10) & 0xFF  # Increase wait time for better event handling

    if key == ord('q'):  # Quit the loop
        break
    elif key == ord('d') and bounding_boxes:  # Delete the last bounding box
        bounding_boxes.pop()
        redraw_image()
    elif key == ord('r'):  # Reset all bounding boxes
        bounding_boxes.clear()
        image_bgr = original_image.copy()
        cv2.imshow("Draw Bounding Boxes", image_bgr)

cv2.destroyAllWindows()



...



- Saving the output data in your directory path
code line[65]

import os
import cv2

save_folder = "/home/nemolinux/Python/sam2/notebooks/image_SEM/segmented_images/soil_extracts"


# Ensure the folder exists
os.makedirs(save_folder, exist_ok=True)

# Define the path to save the image
save_path = os.path.join(save_folder, "sample8_03.jpg")

# Save the image using OpenC
cv2.imwrite(save_path, segmented_image)

print(f"Annotated image saved to {save_path}")
---



