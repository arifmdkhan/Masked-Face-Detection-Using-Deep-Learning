# Masked Face Detection Using Deep Learning

A deep learning project that detects whether a person is wearing a face mask or not using a transfer learning approach with VGG16 and Keras.

## Overview

This repository contains a Jupyter notebook that:
- loads a custom dataset of masked and unmasked faces,
- preprocesses images,
- trains a VGG16-based classifier,
- evaluates the model,
- runs live detection from webcam input.

The project is implemented in Python and uses OpenCV, TensorFlow/Keras, NumPy, and scikit-learn.

## Project Goal

The goal is to build a face mask detection system that can identify whether a person is wearing a mask in real time.

## Features

- Mask vs no-mask binary classification
- Transfer learning using VGG16
- Image preprocessing and normalization
- Train/test split for evaluation
- Real-time webcam prediction
- Visual label overlay on detected frames

## Repository Contents

- `Masked Face Detection.ipynb` — complete training and inference workflow in a Jupyter notebook
- `README.md` — project documentation

## Tech Stack

- Python 3
- OpenCV
- Keras / TensorFlow
- NumPy
- scikit-learn
- Matplotlib
- Jupyter Notebook

## Dataset

This project expects a dataset folder with two classes:

- `with mask`
- `without mask`

The notebook currently references a Windows local dataset path:

```python
path = os.path.join('C:\Users\HP\Downloads\FinalDet\dataset', category)
```

To run it on your machine, organize your dataset like this:

```text
dataset/
├── with mask/
│   ├── image_1.jpg
│   ├── image_2.jpg
│   └── ...
└── without mask/
    ├── image_1.jpg
    ├── image_2.jpg
    └── ...
```

You can then update the dataset path in the notebook accordingly.

## Installation

1. Clone the repository:

```bash
git clone https://github.com/arifmdkhan/Masked-Face-Detection-Using-Deep-Learning.git
cd Masked-Face-Detection-Using-Deep-Learning
```

2. Create a virtual environment (optional but recommended):

```bash
python -m venv venv
source venv/bin/activate   # Linux/macOS
venv\Scripts\activate      # Windows
```

3. Install dependencies:

```bash
pip install tensorflow keras opencv-python matplotlib numpy scikit-learn notebook
```

Optional if you are using Jupyter Notebook:

```bash
pip install jupyter
```

## Running the Notebook

Open the notebook:

```bash
jupyter notebook "Masked Face Detection.ipynb"
```

Then run all cells in sequence.

## Model Approach

The notebook uses VGG16 as a feature extractor and then adds a custom output layer for binary classification:

- VGG16 base model
- Freeze convolutional layers
- Add a sigmoid output layer for mask/no-mask classification
- Train with binary cross-entropy loss
- Use Adam optimizer

## Training Result

The notebook shows training over 5 epochs with strong validation performance, reaching around 95% validation accuracy in the recorded run.

## Real-Time Prediction

The notebook includes a webcam-based detection loop that:
- captures video frames,
- resizes each frame to 224x224,
- passes it through the trained model,
- overlays a label such as `Mask` or `No Mask` on the live frame.

To stop the webcam stream, press:

```text
q
```

## Notes

- This project is a learning-oriented implementation and is meant to demonstrate transfer learning for image classification.
- The notebook contains a local dataset path and may need to be adjusted for your environment.
- A real-world deployment would also benefit from face detection models (such as Haar cascades or MTCNN/YOLO-based detectors) before classification.

## License

This project is provided for educational and research purposes.

## Author

- Arif Md Khan

## Acknowledgements

This project uses:
- VGG16 pretrained model from Keras
- OpenCV for image processing and webcam access
- TensorFlow/Keras for model implementation
