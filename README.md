# Skin_Detection
Project Description: Skin Segmentation Using U-Net Deep Learning Model

This project implements a deep learning–based skin segmentation system using a U-Net convolutional neural network. The goal is to accurately detect and segment skin regions from color images by training a pixel-wise binary classifier.

1. Dataset Preparation

The project uses two main folders:

Input images: RGB images containing people or body parts.

Output masks: Corresponding ground-truth skin segmentation masks in grayscale.

All images are automatically:

Loaded using OpenCV

Resized to 256 × 256

Normalized to the [0, 1] range

Converted to proper shapes (RGB images and single-channel binary masks)

2. Model Architecture — U-Net

A custom U-Net model is built using TensorFlow/Keras. The architecture consists of:

Encoder (Downsampling Path)

Three levels of stacked Conv2D + ReLU layers

MaxPooling2D after each level

Feature extraction with increasing depth (64 → 128 → 256 filters)

Bottleneck

Two 512-filter convolution layers

Captures the most abstract representation of the image

Decoder (Upsampling Path)

Conv2DTranspose layers to increase resolution

Skip connections using concatenate() that combine encoder and decoder features

Reconstruction with 256 → 128 → 64 filters

Output Layer

A 1×1 convolution with sigmoid activation to generate a binary mask for each pixel

3. Training Setup

The model is compiled with:

Adam optimizer (learning rate = 1e-4)

Binary cross-entropy loss

Accuracy metric

Two callbacks are applied:

ReduceLROnPlateau – automatically lowers learning rate if validation loss stops improving

EarlyStopping – stops training when convergence is reached and restores best weights

Training uses:

10 epochs

Batch size of 2

90% training / 10% validation split

4. Prediction & Result Saving

After training, the model:

Predicts a segmentation mask for every input image

Applies a 0.5 threshold to produce a binary mask

Saves each result as result_X.png in the output folder

5. Output

The final output consists of:

A trained U-Net model capable of segmenting skin regions

Binary predicted masks for all input images

Stored results for further processing and evaluation
Before:
<img width="3840" height="2400" alt="leo messi" src="https://github.com/user-attachments/assets/93e94a60-7478-4006-9c8e-d69e04affccb" />
After:
![leo messi](https://github.com/user-attachments/assets/70007491-8bdb-4da3-8236-bae040a54bf5)

