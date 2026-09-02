# Image Classification Using Convolutional Neural Network (CNN)

## Overview

This project implements an **Image Classification system using a Convolutional Neural Network (CNN)** to classify handwritten digit images.

The model is trained to recognize digits from **0 to 9** using image pixel data stored in a CSV file. Each image is represented by numerical pixel values and is reshaped into an **8 × 8 grayscale image** before being processed by the CNN.

This project demonstrates a complete deep learning workflow, including data loading, preprocessing, normalization, image reshaping, model development, training, evaluation, visualization, prediction, and model saving.

---

## Objective

The primary objective of this project is to design, train, and evaluate a **Convolutional Neural Network (CNN)** for handwritten digit image classification.

The specific objectives are:

* To load image data from a CSV dataset.
* To preprocess and normalize pixel values.
* To reshape numerical data into image format.
* To build a CNN model using TensorFlow and Keras.
* To train the model using labeled image data.
* To evaluate the performance of the trained model.
* To visualize training and validation performance.
* To predict handwritten digits from unseen test images.
* To save the trained CNN model for future use.

---

## Problem Statement

Traditional machine learning algorithms require manual feature extraction when working with image data. Convolutional Neural Networks automatically learn important visual features from images through convolutional layers.

This project addresses the problem of automatically classifying handwritten digit images into their corresponding categories using a CNN-based deep learning approach.

---

## Dataset

The project uses a CSV-based handwritten digits dataset.

Each row in the dataset represents one image, where:

* The `label` column represents the actual digit.
* The remaining columns represent pixel intensity values.
* Each image contains **64 pixel values**.
* The pixel values are reshaped into an **8 × 8 grayscale image**.
* The dataset contains digits from **0 to 9**.

### Dataset Details

| Property           | Description     |
| ------------------ | --------------- |
| Total Samples      | 1,797           |
| Number of Classes  | 10              |
| Classes            | Digits 0–9      |
| Image Size         | 8 × 8 pixels    |
| Number of Features | 64 pixel values |
| Target Column      | `label`         |
| Dataset Format     | CSV             |

### Dataset File

```text
cnn_image_classification_digits.csv
```

---

## Technologies Used

The following technologies and libraries are used in this project:

| Technology   | Purpose                                 |
| ------------ | --------------------------------------- |
| Python       | Programming Language                    |
| Google Colab | Development Environment                 |
| TensorFlow   | Deep Learning Framework                 |
| Keras        | Neural Network API                      |
| Pandas       | Data Manipulation                       |
| NumPy        | Numerical Computation                   |
| Matplotlib   | Data Visualization                      |
| Scikit-learn | Data Preprocessing and Model Evaluation |

---

## Project Workflow

The project follows the following workflow:

```text
CSV Dataset
     │
     ▼
Data Loading
     │
     ▼
Data Inspection
     │
     ▼
Feature and Label Separation
     │
     ▼
Pixel Normalization
     │
     ▼
Image Reshaping (8 × 8 × 1)
     │
     ▼
Label Encoding
     │
     ▼
Train-Test Split
     │
     ▼
CNN Model Development
     │
     ▼
Model Training
     │
     ▼
Model Evaluation
     │
     ▼
Performance Visualization
     │
     ▼
Prediction
     │
     ▼
Saved CNN Model
```

---

## Data Preprocessing

Before training the CNN model, the dataset undergoes several preprocessing steps.

### 1. Dataset Loading

The CSV dataset is loaded using the Pandas library.

### 2. Feature and Label Separation

The dataset is divided into:

* **Features (`X`)**: Pixel values representing the images.
* **Labels (`y`)**: Digit classes from 0 to 9.

### 3. Pixel Normalization

The pixel values are normalized to improve the efficiency of the neural network during training.

```text
Normalized Pixel Value = Pixel Value / 16.0
```

### 4. Image Reshaping

The original feature data is reshaped from:

```text
(1797, 64)
```

to:

```text
(1797, 8, 8, 1)
```

This format is suitable for the CNN model.

### 5. Label Encoding

The output labels are converted into categorical format using one-hot encoding.

For example:

```text
Digit: 3

One-Hot Encoding:
[0, 0, 0, 1, 0, 0, 0, 0, 0, 0]
```

### 6. Train-Test Split

The dataset is divided into:

* Training Dataset: 80%
* Testing Dataset: 20%

---

## CNN Model Architecture

The CNN model consists of multiple layers designed to automatically learn features from image data.

### Model Layers

1. **Convolutional Layer**

   * Filters: 32
   * Kernel Size: 3 × 3
   * Activation Function: ReLU

2. **Max Pooling Layer**

   * Pool Size: 2 × 2

3. **Second Convolutional Layer**

   * Filters: 64
   * Kernel Size: 3 × 3
   * Activation Function: ReLU

4. **Flatten Layer**

   * Converts the feature maps into a one-dimensional vector.

5. **Dense Layer**

   * Neurons: 128
   * Activation Function: ReLU

6. **Dropout Layer**

   * Dropout Rate: 0.3

7. **Output Layer**

   * Neurons: 10
   * Activation Function: Softmax

---

## Model Architecture Summary

```text
Input Image (8 × 8 × 1)
        │
        ▼
Conv2D (32 Filters)
        │
        ▼
MaxPooling2D
        │
        ▼
Conv2D (64 Filters)
        │
        ▼
Flatten
        │
        ▼
Dense (128 Neurons)
        │
        ▼
Dropout (0.3)
        │
        ▼
Dense (10 Classes)
        │
        ▼
Output Prediction
```

---

## Model Training

The CNN model is compiled and trained using the following configuration:

| Parameter         | Value                    |
| ----------------- | ------------------------ |
| Optimizer         | Adam                     |
| Loss Function     | Categorical Crossentropy |
| Evaluation Metric | Accuracy                 |
| Epochs            | 20                       |
| Batch Size        | 32                       |
| Validation Split  | 20%                      |

---

## Performance Evaluation

The trained CNN model is evaluated using the test dataset.

The following metrics and visualizations are used:

* Training Accuracy
* Validation Accuracy
* Test Accuracy
* Training Loss
* Validation Loss

### Accuracy Graph

The accuracy graph compares:

* Training Accuracy
* Validation Accuracy

This helps evaluate how well the model learns during training.

### Loss Graph

The loss graph compares:

* Training Loss
* Validation Loss

This helps analyze the learning behavior of the model and identify possible overfitting or underfitting.

---

## Prediction

After training, the CNN model predicts the class labels of unseen test images.

The predicted digit is compared with the actual digit to evaluate the model's classification performance.

Example:

```text
Actual Digit:    7
Predicted Digit: 7
```

The project also visualizes sample images along with their actual and predicted labels.

---

## Project Structure

```text
CNN-Image-Classification/
│
├── cnn_image_classification.ipynb
│
├── cnn_image_classification_digits.csv
│
├── cnn_image_classification_model.keras
│
└── README.md
```

### File Description

| File                                   | Description                                                  |
| -------------------------------------- | ------------------------------------------------------------ |
| `cnn_image_classification.ipynb`       | Google Colab notebook containing the complete implementation |
| `cnn_image_classification_digits.csv`  | Dataset used for training and testing                        |
| `cnn_image_classification_model.keras` | Saved trained CNN model                                      |
| `README.md`                            | Project documentation                                        |

---

## Installation

To run this project locally, install the required Python libraries.

```bash
pip install tensorflow pandas numpy matplotlib scikit-learn
```

---

## How to Run the Project

### Step 1: Clone the Repository

```bash
git clone <repository-url>
```

### Step 2: Navigate to the Project Directory

```bash
cd CNN-Image-Classification
```

### Step 3: Open the Notebook

Open the following file:

```text
cnn_image_classification.ipynb
```

You can use:

* Google Colab
* Jupyter Notebook
* JupyterLab

### Step 4: Upload the Dataset

Upload:

```text
cnn_image_classification_digits.csv
```

### Step 5: Run the Notebook

Execute all cells sequentially.

The notebook will perform:

1. Dataset loading
2. Data preprocessing
3. Pixel normalization
4. Image reshaping
5. Dataset splitting
6. CNN model development
7. Model training
8. Model evaluation
9. Performance visualization
10. Image prediction
11. Model saving

---

## Expected Output

After successfully running the project, the following outputs will be generated:

* Dataset information
* Training progress
* Training accuracy
* Validation accuracy
* Test accuracy
* Accuracy visualization
* Loss visualization
* Predicted digit labels
* Actual versus predicted image visualization
* Saved CNN model file

---

## Learning Outcomes

This project provides practical knowledge of:

* Image Classification
* Deep Learning
* Convolutional Neural Networks
* Image Data Preprocessing
* Pixel Normalization
* Image Reshaping
* One-Hot Encoding
* Train-Test Splitting
* CNN Architecture Design
* Model Training
* Model Evaluation
* Data Visualization
* Image Prediction
* TensorFlow and Keras

---

## Applications

Convolutional Neural Networks can be applied to several real-world image classification problems, including:

* Handwritten Digit Recognition
* Facial Recognition
* Medical Image Classification
* Object Detection
* Traffic Sign Recognition
* Document Classification
* Image-Based Quality Inspection

---

## Future Improvements

The project can be enhanced in the future by:

* Using larger image datasets.
* Implementing data augmentation techniques.
* Adding more convolutional layers.
* Using Batch Normalization.
* Applying advanced CNN architectures.
* Using MNIST or CIFAR-10 datasets.
* Implementing real-time image prediction.
* Deploying the trained model using Flask or Streamlit.
* Creating a web-based interface for image classification.

---

## Conclusion

This project successfully demonstrates the implementation of an **Image Classification system using a Convolutional Neural Network (CNN)**.

The CNN automatically learns important features from handwritten digit images and classifies them into one of ten categories. The project provides a practical understanding of deep learning workflows, including data preprocessing, CNN model development, training, evaluation, visualization, and prediction.

---

## Author

**Prema Latha V**

---

## License

This project is developed for **educational and academic purposes**.

---

## Repository

**Repository Name:** `CNN-Image-Classification`

**Project Type:** Deep Learning / Image Classification

**Framework:** TensorFlow and Keras
