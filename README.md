# Atrium-Segmentation-using-UNet
This project aims to perform atrium segmentation on MRI scan data using a UNet architecture. The dataset used for this project is obtained from the Medical Decathlon, specifically designed for multi-modal medical image analysis.

### Dataset
The dataset consists of MRI scans and corresponding masks, each representing different subjects. The data is preprocessed and augmented to enhance the segmentation performance.

#### Preprocessing
1. Storing Slices: MRI scan data and masks for each subject are stored as slices in separate directories.
2. Cropping: Each slice is cropped to focus on the region of interest.
3. Normalization and Standardization: The pixel intensity values of the slices are normalized and standardized to ensure consistent input for the neural network.

#### Data Augmentation
To improve the generalization capability of the model, several data augmentation techniques are applied:

1. Resizing: Adjusting the size of the slices to fit the input dimensions required by the UNet.
2. Scaling: Zooming in and out to simulate different perspectives.
3. Rotation: Rotating the slices to make the model invariant to orientation.
4. Elastic Transformation: Applying random elastic deformations to simulate realistic variations in the anatomy.
   
The sample augmentations have been visualized below
![Augmentations](https://github.com/vaibhavmallya98/Atrium-Segmentation-using-UNet/assets/45683079/b487d96d-9a73-45a6-8ff5-de39973bb83e)



### Model Architecture
The segmentation is achieved using a UNet architecture, which is well-suited for medical image segmentation tasks due to its ability to capture both local and global context through its contracting and expansive paths. The UNet architecture consists of the following components:

1. Encoder: Consists of a series of convolutional layers, each followed by a max-pooling layer, to capture the context of the input slices.
2. Bottleneck: A series of convolutional layers without pooling to act as a bridge between the encoder and decoder.
3. Decoder: Consists of upsampling layers followed by convolutional layers to reconstruct the segmented mask from the encoded features.

The model architecture used for this task has been depicted below. The dimensions of the input image used is 256 x 256 x 1 as each slice is a gray scale image. 
![UNet_Architecture](https://github.com/vaibhavmallya98/Atrium-Segmentation-using-UNet/assets/45683079/43b94a15-dcf6-402e-86b0-9027f8cb5c69)



### Loss Function and Optimizer 
1. Loss Function: Binary Cross Entropy with Logits Loss (BCEWithLogitsLoss) is used to measure the discrepancy between the predicted and actual masks.
2. Optimizer: Adam optimizer is used to minimize the loss function and update the network weights.

### Training
The model is trained over multiple epochs, with training and validation losses monitored to ensure proper learning. The training loop involves the following steps:

1. Forward pass: Compute the predicted mask.
2. Compute loss: Calculate the loss between the predicted and actual masks using BCEWithLogitsLoss.
3. Backward pass: Compute the gradients and update the network weights using the Adam optimizer.

### Results 
The following segmentation output has been obtained for one particular subject. It has been compiled into a video to capture all the slices

https://github.com/vaibhavmallya98/Atrium-Segmentation-using-UNet/assets/45683079/84c58c8f-11cd-4dce-a82a-016cbfd80b5b



