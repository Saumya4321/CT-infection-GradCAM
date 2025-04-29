# Brain CT Infection Classification with Grad-CAM-Based Interpretability

## Project Overview
This project proposes a Convolutional Neural Network (CNN) for classifying the level of infection in Brain CT images. The model is designed to effectively capture features from medical scans while 
incorporating Grad-CAM for interpretability, allowing visualization of the regions influencing classification decisions.


## Motivation
This project was undertaken as an assignment for 'AI in Medical Image Analysis (DS261)' course , offered by the Computational and Data Science Department (CDS) at the Indian Institute of Science.

## Dataset used
![image](https://github.com/user-attachments/assets/e00bd5ae-3447-4edd-b8df-5f965d141d94)
<br>
<br>
The datasets were provided by the course coordinator as part of the course. All the datasets can be found in this [drive link](https://drive.google.com/file/d/1dAipNcsiv03DObxnhFwcaG2mTySoG7Ba/view?usp=sharing). The dataset consists of Brain CT images in three .mat
files named train, test and val. These .mat files in turn contained the image data and its corresponding label. Three classes of images were present in the dataset - No infection,
Mild infection and sever infection. Example images from the dataset has been shown above for reference.

## Model architecture
The model is a Convolutional Neural Network (CNN) consisting of:

+ Input Layer: Accepts 224×224 grayscale images (1 channel).

+ Convolutional Blocks: Five convolutional layers with increasing filters (64, 128, 256, 512, 1024), each followed by max pooling and dropout (0.1) to prevent overfitting. L2 regularization is applied to all convolutional layers.

+ Fully Connected Layers: A flattened output is passed through a dense layer with 512 units (ReLU activation) and dropout (0.3).

+ Output Layer: A softmax activation layer with three units for multi-class classification.

## Training
+ The model was compiled using the Adam optimizer (learning rate = 1e-4) and Focal Loss to handle class imbalance, with accuracy as the evaluation metric.
+ Training was carried out for 10 epochs.
  
## Results of Classification
#### Training Graph
![image](https://github.com/user-attachments/assets/2adf6f9d-af61-417a-a603-d6c9c9b7be28)

#### Classification Report
![image](https://github.com/user-attachments/assets/f52fc7f7-2ae4-4f8f-aa95-d312abd298d6)

#### Confusion matrix
![image](https://github.com/user-attachments/assets/e2b37301-0029-4d42-b0bd-b632b4ff1b66)






## Interpretability using GradCAM
<br>

Grad-CAM was applied to visualize the discriminative regions contributing to the model’s classification decision across varying infection severity levels. 
The results are presented as triplets: the original MRI slice, the Grad-CAM heatmap, and the overlay.

<br>

![Screenshot 2025-04-29 153348](https://github.com/user-attachments/assets/bc265def-7195-4938-99a9-b4953157306f)


<br>

In the mild infection scenario, the activation regions are more diffuse and spread across multiple small zones. This reflects the subtle and scattered nature of early-stage disease symptoms,
which the model is attempting to capture.

<br>



In the no infection case, the activation maps show sparse and low-intensity attention, suggesting the model finds no abnormal regions of interest.
This aligns with expectations and confirms that the model is not falsely attributing significance to healthy tissue.

![Screenshot 2025-04-29 153806](https://github.com/user-attachments/assets/a51c0bb6-f62d-4d39-9bc5-452e9371daea)


For severe infection, the heatmaps show strong, centralized, and spatially broader activation patterns. These regions likely correspond to extensive tissue damage or 
high-contrast features in the image, indicating that the model has learned to associate such patterns with severe infection.



## Future Work

Some degree of attention spillover beyond the brain region is observed, particularly in severe cases. While the primary focus remains within the anatomical boundaries, applying brain masks in future iterations could refine these activations further.
