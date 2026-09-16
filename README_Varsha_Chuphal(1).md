# Handwritten Digit Recognition with CNN

A local machine-learning application for recognizing handwritten digits using a Convolutional Neural Network (CNN). The project provides a Streamlit interface where users can draw a digit or upload an image and receive a prediction with a confidence score.

## Project Overview

This project uses the MNIST handwritten-digit dataset to train a CNN that recognizes digits from 0 through 9. The trained model can be used locally through a Streamlit web interface.

### Main Goals

- Train a CNN on the MNIST dataset
- Save and reload the trained model
- Preprocess handwritten input images for prediction
- Provide an interactive local web interface
- Evaluate the model using standard classification metrics

## Key Features

- CNN trained on 60,000 MNIST training images
- Reported test accuracy of **99.04%**
- Draw digits directly in the browser
- Upload PNG, JPG, or BMP digit images
- Display the predicted digit and confidence
- Show probability scores for all 10 classes
- Run predictions locally without an API
- Includes an automated test suite with 14 tests

## Technologies

| Technology | Role |
|---|---|
| Python 3.12 | Application and ML development |
| TensorFlow / Keras | CNN training and inference |
| NumPy | Numerical and array operations |
| Matplotlib | Training and evaluation visualizations |
| scikit-learn | Evaluation metrics and confusion matrix |
| Pillow | Image processing |
| Streamlit | Interactive web interface |
| streamlit-drawable-canvas | Browser drawing canvas |
| pytest | Automated testing |

## Dataset

The project uses the **MNIST** dataset.

- 70,000 grayscale handwritten-digit images
- 60,000 images for training
- 10,000 images for testing
- Image size: 28 × 28 pixels
- 10 output classes: 0–9
- Pixel values normalized to the range 0.0–1.0
- Loaded through `tensorflow.keras.datasets.mnist`

## CNN Model

The network follows this structure:

```text
Input: 28 × 28 × 1
        ↓
Conv2D — 32 filters, 3 × 3, ReLU
        ↓
MaxPooling2D — 2 × 2
        ↓
Conv2D — 64 filters, 3 × 3, ReLU
        ↓
MaxPooling2D — 2 × 2
        ↓
Flatten
        ↓
Dense — 128 units, ReLU
        ↓
Dropout — 50%
        ↓
Dense — 10 units, Softmax
        ↓
Digit probabilities (0–9)
```

### Training Configuration

- **Loss:** `sparse_categorical_crossentropy`
- **Optimizer:** Adam
- **Metric:** Accuracy
- **Maximum epochs:** 15
- **Early stopping:** patience of 3
- **Model checkpoint:** saves the best weights/model

## Prediction Pipeline

```text
MNIST Dataset
     ↓
Normalize and reshape input
     ↓
Train CNN
     ↓
Evaluate model
     ↓
Save trained model
     ↓
Draw or upload a digit
     ↓
Convert to grayscale
     ↓
Invert, crop, pad and resize
     ↓
Normalize image
     ↓
Run CNN inference
     ↓
Display digit + confidence
```

## Installation

### 1. Get the project

Replace the repository address below with the actual repository URL:

```bash
git clone https://github.com/<your-username>/<your-repository>.git
cd <your-repository>
```

### 2. Create a virtual environment

**Windows**

```bash
python -m venv .venv
.venv\Scripts\activate
```

**macOS / Linux**

```bash
python -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

## Running the Project

### Train the model

```bash
python train.py
```

The training script saves the trained model in:

```text
model/digit_model.keras
```

### Evaluate the model

```bash
python evaluate.py
```

This generates the evaluation output, including the classification report and confusion matrix.

### Start the Streamlit application

```bash
streamlit run app.py
```

The application runs locally and can be opened in the browser.

### Run tests

```bash
python -m pytest tests/test_prediction.py -v
```

## Model Results

The README reports the following results from the trained model:

| Metric | Result |
|---|---:|
| Test Accuracy | 99.04% |
| Test Loss | 0.0293 |
| Training stopped | Epoch 8 |

### F1 Scores

| Digit | F1 Score |
|---:|---:|
| 0 | 0.99 |
| 1 | 1.00 |
| 2 | 0.99 |
| 3 | 0.99 |
| 4 | 0.99 |
| 5 | 0.99 |
| 6 | 0.99 |
| 7 | 0.99 |
| 8 | 0.99 |
| 9 | 0.98 |

## Project Layout

```text
handwritten-digit-recognizer/
│
├── app.py
├── train.py
├── predict.py
├── preprocess.py
├── evaluate.py
├── visualize.py
├── requirements.txt
├── .gitignore
├── README.md
│
├── model/
│   └── digit_model.keras
│
├── data/
│   └── README.md
│
├── screenshots/
│   ├── mnist_samples.png
│   ├── training_history.png
│   └── confusion_matrix.png
│
└── tests/
    └── test_prediction.py
```

## Possible Next Improvements

- Add data augmentation for different handwriting styles
- Experiment with batch normalization
- Export the trained model to TensorFlow Lite
- Support recognition of multiple digits
- Deploy the application as a public Streamlit app

## Author

**Varsha Chuphal**

