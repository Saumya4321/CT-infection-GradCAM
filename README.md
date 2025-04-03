# Brain CT Infection Classification with Grad-CAM-Based Interpretability

## Project Overview

## Motivation
This project was undertaken as an assignment for 'AI in Medical Image Analysis (DS261)' course , offered by the Computational and Data Science Department (CDS) at the Indian Institute of Science.

## Dataset used
![image](https://github.com/user-attachments/assets/e00bd5ae-3447-4edd-b8df-5f965d141d94)
<br>
<br>
The datasets were provided by the course coordinator as part of the course. All the datasets can be found in this repo. <add link>. The dataset consists of Brain CT images in three .mat
files named train, test and val. These .mat files in turn contained the image data and its corresponding label. Three classes of images were present in the dataset - No infection,
Mild infection and sever infection. Example images from the dataset has been shown above for reference.

## Model architecture
The model is a Convolutional Neural Network (CNN) consisting of:

+ Input Layer: Accepts 224×224 grayscale images (1 channel).

+ Convolutional Blocks: Five convolutional layers with increasing filters (64, 128, 256, 512, 1024), each followed by max pooling and dropout (0.1) to prevent overfitting. L2 regularization is applied to all convolutional layers.

+ Fully Connected Layers: A flattened output is passed through a dense layer with 512 units (ReLU activation) and dropout (0.3).

+ Output Layer: A softmax activation layer with three units for multi-class classification.

## Training
+ The model is compiled using the Adam optimizer (learning rate = 1e-4) and Focal Loss to handle class imbalance, with accuracy as the evaluation metric.
+ Model was trained for 8 epochs.
  
## Results

## Interpretability using GradCAM
