# Urine Strip Image Preprocessing and Dataset Versioning

## Overview

This project focuses on preprocessing urine strip images, extracting RGB features from reagent pads, cleaning the dataset, and versioning datasets using **Data Version Control (DVC)** to enable reproducible machine learning workflows.

The repository provides a structured pipeline for preparing urine strip image datasets before they are used for machine learning model development.

---

## Objectives

- Preprocess urine strip images.
- Extract RGB color features from reagent pads.
- Clean and organize datasets.
- Track dataset versions using DVC.
- Ensure reproducible ML workflows.

---

## Project Structure

```
.
├── data/
│   ├── raw/                 # Original urine strip images
│   ├── processed/           # Preprocessed images
│   └── features/            # Extracted RGB feature datasets
│
├── notebooks/              # Jupyter notebooks for experimentation
├── scripts/
│   ├── preprocess.py       # Image preprocessing
│   ├── extract_rgb.py      # RGB feature extraction
│   ├── clean_dataset.py    # Dataset cleaning
│
├── dvc.yaml                # DVC pipeline
├── dvc.lock
├── .dvc/
├── requirements.txt
├── README.md
└── .gitignore
```

---

## Workflow

### 1. Image Preprocessing

The preprocessing stage prepares urine strip images for analysis by:

- Resizing images
- Noise reduction
- Color normalization (if required)
- Cropping reagent pads
- Image enhancement

Output images are stored in:

```
data/processed/
```

---

### 2. RGB Feature Extraction

For every reagent pad, the pipeline extracts:

- Mean Red (R)
- Mean Green (G)
- Mean Blue (B)

The extracted RGB values are stored in CSV format for downstream machine learning tasks.

Example:

| Image | Pad | R | G | B |
|------|------|------|------|------|
| img01.jpg | Glucose | 182 | 154 | 97 |
| img01.jpg | Protein | 205 | 188 | 121 |

---

### 3. Dataset Cleaning

Cleaning includes:

- Removing duplicate entries
- Handling missing values
- Verifying image-label consistency
- Standardizing file names
- Removing corrupted images

The cleaned dataset is stored in:

```
data/features/
```

---

## Dataset Versioning with DVC

This project uses **Data Version Control (DVC)** for tracking datasets and ensuring reproducibility.

### Initialize DVC

```bash
dvc init
```

### Track a Dataset

```bash
dvc add data/raw
```

### Commit Changes

```bash
git add data/raw.dvc .gitignore
git commit -m "Track raw dataset using DVC"
```

### Configure Remote Storage

Example:

```bash
dvc remote add -d storage <remote-url>
```

Push data:

```bash
dvc push
```

Pull data:

```bash
dvc pull
```

---

## Installation

Clone the repository:

```bash
git clone https://github.com/<username>/<repository>.git
cd <repository>
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate the environment:

### Linux/macOS

```bash
source venv/bin/activate
```

### Windows

```bash
venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Running the Pipeline

### Preprocess Images

```bash
python scripts/preprocess.py
```

### Extract RGB Features

```bash
python scripts/extract_rgb.py
```

### Clean Dataset

```bash
python scripts/clean_dataset.py
```

---

## Technologies Used

- Python
- OpenCV
- NumPy
- Pandas
- DVC (Data Version Control)
- Git

---

## Reproducibility

Using DVC ensures:

- Dataset version tracking
- Reproducible preprocessing pipelines
- Easy collaboration
- Storage of large datasets outside Git

---

## Future Improvements

- Automated reagent pad detection
- HSV/LAB color feature extraction
- Feature normalization
- DVC pipeline automation
- Integration with ML model training

---

## License

This project is licensed under the MIT License.
