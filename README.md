# MRI Brain Tumor Segmentation

This project focuses on the segmentation of brain tumors from MRI scans using a U-Net deep learning model. The goal is to accurately identify and segment tumor regions within brain MRI images, which can assist in the diagnosis and treatment planning for patients.

## Table of Contents
- [Dataset](#dataset)
- [Installation](#installation)
- [Project Structure](#project-structure)
- [Model Architecture](#model-architecture)
- [Training](#training)
- [Evaluation](#evaluation)
- [Results](#results)
- [Acknowledgements](#acknowledgements)

## Dataset
The dataset consists of MRI images of brain scans along with their corresponding masks that indicate tumor regions. The data is stored in the `kaggle_3m` directory and is organized as follows:

- **Images**: `.tif` files of MRI scans
- **Masks**: `.tif` files indicating tumor regions (binary masks)

### Dataset Statistics
- **Total Images**: 3,929
- **Tumor Images**: 1,373
- **Non-Tumor Images**: 2,556

## Installation

To run this project, you will need to use Google Colab with a GPU runtime. Follow the steps below:

1. Open the notebook in Google Colab.
2. Change the runtime to GPU: `Runtime` -> `Change runtime type` -> `Hardware accelerator: GPU`.
3. Install the required dependencies (Colab usually handles this automatically).

### Required Libraries
- `torch`
- `opencv-python`
- `albumentations`
- `matplotlib`
- `tqdm`
- `pandas`
- `numpy`

## Project Structure
The project is structured as follows:

├── data.csv
├── README.md
├── TCGA_DU_6400_19830518/ # Folders containing MRI images and masks
├── ...
└── main.ipynb # Main notebook with code


## Model Architecture
The model used in this project is a U-Net, a type of convolutional neural network designed for image segmentation. The U-Net model has an encoder-decoder structure, where the encoder captures the context and the decoder enables precise localization.

### U-Net Layers
- **Encoder**: Series of convolutional layers followed by max-pooling layers to downsample the input.
- **Decoder**: Upsampling layers combined with high-resolution features from the encoder to reconstruct the spatial dimensions of the image.

## Training
The dataset is split into training, validation, and test sets with the following proportions:

- **Training Set**: 75% of the dataset
- **Validation Set**: 10% of the dataset
- **Test Set**: 15% of the dataset

The model is trained on the training set and evaluated on the validation set. The final evaluation is done on the test set.

### Data Augmentation
To increase the diversity of the training data, various augmentation techniques are applied:
- Horizontal and vertical flips
- Random rotations
- Shifts and scaling
- Normalization

## Evaluation
The model is evaluated using the Dice coefficient and Intersection over Union (IoU) metrics, which are common measures for image segmentation tasks.

### Evaluation Metrics
- **Dice Coefficient**: Measures the overlap between the predicted and ground truth masks.
- **IoU**: Measures the intersection over union between the predicted and ground truth masks.


Sample outputs of MRI scans, their corresponding masks, and the model's predictions can be found in the `results/` directory.

## Acknowledgements
This project is based on the [Kaggle Brain MRI Dataset](https://www.kaggle.com/sartajbhuvaji/brain-tumor-detection) and leverages the U-Net architecture for image segmentation.
