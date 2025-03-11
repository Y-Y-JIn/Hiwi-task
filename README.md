# Hiwi-task

## How to access and build SAM2 for segmentation


### Prerequisite
1. sam2_image_predictor_update_2nd.ipynb ,
   "literally sam2 model script"

3. image_editor.ipynb ,   "image editor script to crop the bottom of SEM image"

4. original_image & segmented_images , 
     "original image dataset: 5 different image folders (tif.file) + segmented image dataset: 5 different image folders (jpg.file)"



### Path in "Nemo"
1. Sam2: Ubuntu/home/nemolinux/Python/sam2/notebooks/SAM_model_test/sam2_image_predictor_update_2nd.ipynb

2. Image editor script for cropping the bottom of SEM image: Ubuntu/home/nemolinux/Python/sam2/notebooks/SAM_model_test/image_editor.ipynb

3. Original image dataset: Ubuntu/home/nemolinux/Python/sam2/notebooks/image_SEM/original_image/ (20210215 + 20210412 + 20210415 + HR_np + soil_extracts)
   Segmented image dataset: Ubuntu/home/nemolinux/Python/sam2/notebooks/image_SEM/segmented_images/ (20210215_v3 + 20210412_v3 + 20210415_v3 + HR_np_v3 + soil_extracts_v3)



### Data
The input data is below: < br / > 
File name: "original image"< br / > 
'20210215' < br / > 
'20210412' < br / > 
'20210415'< br / > 
'HR_np'< br / > 
'soil_extracts'< br / > 



cd <PATH TO CELLTRACKINGCHALLENGE DATA>/Training
tar -xzvf  <PATH TO REPOSITORY>/metadata_files.tar.gz
make sure that metadata_01.pickle and metadata_02.pickle are located in each dataset directory (Only of 2D datasets)


## Private Data:
If you would like to train on your private data, please create a metadata_.pickle file. Run the script './create_sequence_metadat.py' with the paths and formats for your data:

--root_dir : Root directory of sequence, example: '~/CellTrackingChallenge/Train/Fluo-N2DH-SIM+

--seq : Sequence number (two digit) , example: '01' or '02'

--raw_file_template : Template for image sequences, example: '01/t{:03d}.tif' where {:03d} will be replaced by a three digit number 000,001,...

-- seg_file_template : TemplateTemplate for image sequences segmentation , example: '01_GT/SEG/man_seg{:03d}.tif' where {:03d} will be replaced by a three digit number 000,001,...

--tra_file_template : Optional!. Template for image sequences tracking lables , example: '01_GT/TRA/man_track{:03d}.tif' where {:03d} will be replaced by a three digit number 000,001,...

--force : Force overwrite existing metadata pickle
