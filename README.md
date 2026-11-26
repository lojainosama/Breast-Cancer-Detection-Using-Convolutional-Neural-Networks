# Breast-Cancer-Detection-Using-Convolutional-Neural-Networks
This project focuses on the critical task of medical diagnostics through the development of an automated system designed to predict the presence of cancer from tissue images. Using advanced deep learning techniques, our primary objective is to enhance diagnostic accuracy and support healthcare professionals in early detection.
DATASET _LINK:https://www.kaggle.com/datasets/paultimothymooney/breast-histopathology-images
About Dataset
Context
Invasive Ductal Carcinoma (IDC) is the most common subtype of all breast cancers. To assign an aggressiveness grade to a whole mount sample, pathologists typically focus on the regions which contain the IDC. As a result, one of the common pre-processing steps for automatic aggressiveness grading is to delineate the exact regions of IDC inside of a whole mount slide.

Content
The original dataset consisted of 162 whole mount slide images of Breast Cancer (BCa) specimens scanned at 40x. From that, 277,524 patches of size 50 x 50 were extracted (198,738 IDC negative and 78,786 IDC positive). Each patch’s file name is of the format: u_xX_yY_classC.png — > example 10253_idx5_x1351_y1101_class0.png . Where u is the patient ID (10253_idx5), X is the x-coordinate of where this patch was cropped from, Y is the y-coordinate of where this patch was cropped from, and C indicates the class where 0 is non-IDC and 1 is IDC.

Acknowledgements
The original files are located here: http://gleason.case.edu/webdata/jpi-dl-tutorial/IDC_regular_ps50_idx5.zip Citation: https://www.ncbi.nlm.nih.gov/pubmed/27563488 and http://spie.org/Publications/Proceedings/Paper/10.1117/12.2043872

Inspiration
Breast cancer is the most common form of cancer in women, and invasive ductal carcinoma (IDC) is the most common form of breast cancer. Accurately identifying and categorizing breast cancer subtypes is an important clinical task, and automated methods can be used to save time and reduce error. 
Slide 3 – Introduction

This project focuses on the critical task of medical diagnostics through the development of an automated system designed to predict the presence of cancer from tissue images. Using advanced deep learning techniques, our primary objective is to enhance diagnostic accuracy and support healthcare professionals in early detection.

Selected Method:

Convolutional Neural Network (CNN)

Application:

Analyze histopathological tissue images.
Distinguish between cancerous and non-cancerous cells.

Objectives:

Build a robust model capable of identifying malignant features.
Provide a fast and reliable tool for early cancer diagnosis.

Slide 4 – Dataset Description
Breast Histopathology Images (IDC Regular) dataset from Kaggle.
Binary classification:
Benign (0)
Malignant (1) – Invasive Ductal Carcinoma (IDC)
Folder structure:
Folder 0 → Benign
Folder 1 → Malignant
RGB images of size 50×50 pixels.
Patient-level split to avoid data leakage.
Images normalized to [0,1].
Class weighting used because benign images are more common.Exploratory analysis counted images in each class.

Dataset contains:

198,738 Non-Cancer images
78,786 Cancer images

This identifies class imbalance for CNN training.
Preprocessing Steps
Data Organization and Loading
Patient-Level Data Splitting
Image Resizing
Image Normalization
Dataset Creation Using TensorFlow
Data Augmentation
Handling Class Imbalance
Training the Model
Evaluating the Model
Preprocessing Details
Collect image paths, labels, and patient IDs.
Store information in a pandas DataFrame.
Split:
80% Training
10% Validation
10% Testing
Stratified patient-level split.
Resize all images to 50×50.

Slide 12 – Preprocessing (Continued)

Image Normalization:

Divide pixel values by 255.
Normalize to [0,1].

TensorFlow Dataset:

Batch size: 32
Shuffle
Prefetch

Data Augmentation:

Random horizontal flip
Random rotation
Random zoom

Handling Class Imbalance:

Apply class weights.

Slide 13

Example before and after preprocessing.

After preprocessing:

Min pixel = 0.42745098
Max pixel = 0.972549

Before preprocessing:

Min pixel = 109
Max pixel = 248

Slide 14

Data augmentation using:

Random flipping
Random rotation

Slide 15 – CNN Architecture

Model Components:

Input Layer (50×50×3 RGB)
Data Augmentation Layer
Convolution + Pooling Layers
Conv32
Conv64
Conv128
Fully Connected Layer
Dense 128
Dropout 0.5
Output Layer
Sigmoid activation
Slide 17 – Hyperparameters
Batch Size: 32
Optimizer: Adam
Epochs: 40
Dropout: 0.5

Loss Function:

Binary Crossentropy

Evaluation Metrics:

Accuracy
Recall

Slide 18 – Model Training Performance
Training accuracy increased steadily.
Validation accuracy also improved.
Loss decreased.
Recall improved for malignant cases.
Early stopping and learning-rate reduction used.

Slide 19 – Results

Performance:

AUC = 0.92
Benign Precision = 94%
Malignant Recall = 86%
Overall Accuracy = 83%

Slide 20 – ROC Curve
AUC = 0.92
Excellent discrimination.
High True Positive Rate.
Low False Positive Rate.
Outperforms random guessing.

Slide 21 – Discussion

Strengths:

Patient-level split.
Data augmentation.
Class weighting.

Challenges:

Small image patches (50×50).
Some benign/malignant misclassifications.

Slide 22 – Conclusion

The project successfully implemented a CNN for breast histopathology image classification.

Lessons learned:

Applying deep learning to real medical datasets.
Image preprocessing techniques.
Data augmentation.
Class weighting.
CNN implementation with TensorFlow and Keras.

Slide 23 – References
Kaggle Breast Cancer Detection with CNN
Google Share Link
GitHub Breast Cancer Detection Repository
