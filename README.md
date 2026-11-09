<div align="center">

# 😷 Masked Face Detection

**A computer vision project for classifying face images as mask or no mask using transfer learning with VGG16.**

[![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-Keras-FF6F00?logo=tensorflow&logoColor=white)](https://www.tensorflow.org/)
[![OpenCV](https://img.shields.io/badge/OpenCV-Computer%20Vision-5C3EE8?logo=opencv&logoColor=white)](https://opencv.org/)
[![Jupyter](https://img.shields.io/badge/Notebook-Jupyter-F37626?logo=jupyter&logoColor=white)](https://jupyter.org/)

</div>

## Project Overview

This project demonstrates a deep-learning workflow for **binary face-mask classification**. It uses a pretrained VGG16 network as a feature extractor, adds a sigmoid classification layer, and includes a webcam inference loop in the notebook.

> **What it does:** classifies a resized image as **with mask** or **without mask**. The notebook's webcam example runs the classifier on each frame.

## Highlights

- Transfer learning with pretrained VGG16 weights
- Binary classification with a sigmoid output and binary cross-entropy loss
- Image resizing and normalization
- Train/test split and validation evaluation
- OpenCV webcam prediction with on-screen labels

## Project Structure

```text
.
├── Masked Face Detection.ipynb  # Training and webcam inference workflow
└── README.md
```

## Model and Recorded Results

The notebook freezes the VGG16 layers and trains a new sigmoid output layer for five epochs using Adam. In the notebook's recorded run, the final validation accuracy is approximately **94.9%**.

This is the result from one run on the notebook's dataset and split; it is not a guarantee of performance on other data. The notebook uses a random train/test split without a fixed seed, so results may vary.

## Getting Started

### Requirements

- Python 3
- A webcam for the live inference section
- A local image dataset arranged into the two class folders shown below

### 1. Clone the repository

```bash
git clone https://github.com/arifmdkhan/Masked-Face-Detection-Using-Deep-Learning.git
cd Masked-Face-Detection-Using-Deep-Learning
```

### 2. Create and activate a virtual environment (recommended)

```bash
python -m venv .venv
```

On macOS/Linux:

```bash
source .venv/bin/activate
```

On Windows:

```powershell
.venv\Scripts\Activate.ps1
```

### 3. Install dependencies

```bash
pip install tensorflow keras opencv-python matplotlib numpy scikit-learn notebook
```

### 4. Prepare the dataset

The notebook expects two folders, with each folder containing images for that label:

```text
dataset/
├── with mask/
└── without mask/
```

Update the dataset path in the notebook to point to your local `dataset` directory. The current notebook contains a machine-specific Windows path, so it must be changed before running on another computer.

### 5. Run the notebook

```bash
jupyter notebook "Masked Face Detection.ipynb"
```

Run the cells in order. The notebook loads and preprocesses the images, trains the model, and then starts the webcam example. Press **`q`** in the OpenCV window to stop the webcam loop.

## How It Works

1. Load images from the `with mask` and `without mask` folders.
2. Resize images to **224 × 224** and normalize pixel values.
3. Split the data into training and test sets.
4. Use pretrained VGG16 without its original classification layer as a feature extractor.
5. Add a sigmoid output layer and train it for binary classification.
6. Pass webcam frames through the classifier and display the predicted label.

## Current Scope and Limitations

- **Classification, not face localization:** the notebook classifies the resized frame; face detection and cropping are commented out. For scenes with multiple people or a face that does not fill the frame, add a face detector and classify each detected face.
- **Local dataset required:** the dataset is not included in this repository; configure the local path before training.
- **Notebook compatibility:** the notebook uses older Keras APIs, including `model.predict_classes`, which may need updating for current TensorFlow/Keras versions.
- **Use responsibly:** predictions may be inaccurate and should not be used as the sole basis for health, safety, access, or other consequential decisions.

## Built With

- [Python](https://www.python.org/)
- [TensorFlow / Keras](https://www.tensorflow.org/)
- [VGG16](https://keras.io/api/applications/vgg/#vgg16-function)
- [OpenCV](https://opencv.org/)
- [NumPy](https://numpy.org/)
- [scikit-learn](https://scikit-learn.org/)
- [Jupyter Notebook](https://jupyter.org/)

## Author

**Arif Md Khan**

## License

No license file is currently included in this repository. Please contact the repository owner before reusing or distributing this project.
