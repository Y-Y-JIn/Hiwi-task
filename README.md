# Hiwi-task

## How to access and build SAM2 for segmentation


### Prerequisite
1. sam2_image_predictor_update_2nd.ipynb ,
   "literally sam2 model script"

3. image_editor.ipynb ,   "image editor script to crop the bottom of SEM image"

4. original_image & segmented_images , 
     "original image dataset: 5 different image folders (tif.file) + segmented image dataset: 5 different image folders (jpg.file)"<br /><br />



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



