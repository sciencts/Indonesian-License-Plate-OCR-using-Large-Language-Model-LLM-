# 🧠 License Plate Recognition using Large Language Model (LLM)

This repository contains the source code for a license plate OCR (Optical Character Recognition) system developed as part of the **Computer Vision (RE604)** coursework at Politeknik Negeri Batam.

The system uses a **Large Language Model (LLM)** (`qwen2-vl-2b-instruct`) via **LMStudio** to read license plate images and evaluate the results using **Character Error Rate (CER)**.

---

## 🗂 Directory Structure

```
project/
├── generate_ground_truth.py                  # Convert YOLO labels to text
├── run_ocr_and_evaluate.py                   # Run OCR and evaluate results
├── ground_truth.csv                          # Ground truth text for each image
├── ocr_results.csv                           # OCR results and CER scores
└── archive/
    └── Indonesian License Plate Recognition Dataset/
        ├── classes.names                     # Class ID to character mapping
        ├── images/
        │   └── test/                         # Test images of license plates
        └── labels/
            └── test/                         # YOLO label files
```

---

## 📌 Project Description

This project is implemented in Python using the following tools:

- `lmstudio` – interface to call the VLM model (`qwen2-vl-2b-instruct`)
- `pandas` – to manage CSV data
- `evaluate` – to calculate Character Error Rate (CER)
- `os`, `csv` – for file processing and path management

The dataset used is the **Indonesian License Plate Dataset**, available on Kaggle:  
👉 [Indonesian License Plate Dataset on Kaggle](https://www.kaggle.com/datasets/juanthomaswijaya/indonesian-license-plate-dataset)

> The license plate dataset is the **Indonesian License Plate Recognition Dataset**, consisting of images and YOLO-format labels.

---

## ⚙️ Methodology

1. **Ground Truth Generation**
   - Read YOLO `.txt` labels
   - Map class IDs to characters using `classes.names`
   - Sort characters by x-axis position
   - Save as `ground_truth.csv` (image name and license plate text)

2. **OCR with VLM**
   - Load each image
   - Send prompt to `qwen2-vl-2b-instruct` via LMStudio
   - Get model prediction

3. **Evaluation**
   - Compare prediction vs ground truth using **CER**
   - Log the results
   - Save to `ocr_results.csv`

---

## 🧪 Evaluation Results

| Metric              | Value (example) |
|---------------------|-----------------|
| Average CER         | 0.0384          |
| Prediction Accuracy | Shown per image |

> The model's performance depends on image quality and label consistency. Lower CER means better OCR performance.

Example Output:

```bash
[✓] test001_1.jpg: GT=B9140BCD, Pred=B9140BCD, CER=0.0000
[✓] test001_2.jpg: GT=B2407UZO, Pred=B2407UZ0, CER=0.1250
[✓] test001_3.jpg: GT=B2842PKM, Pred=B2842PKM, CER=0.0000

📊 Average CER: 0.0384
📁 Results saved to: ocr_results.csv

---

## 👤 Biodata

**Nama**: Daipansyah Arya Saputra  
**Universitas**: Politeknik Negeri Batam  
**Program Studi**: Robotika  
**Kelas**: RE 6A Pagi  

---

## 🎥 Link Video
👉 [Link](https://youtu.be/C5xjHdheqzM?si=izJjLAq8hDd4vg7L)


## 🛠️ Installation

To install the required dependencies, run:

```bash
pip install scikit-learn scikit-image matplotlib numpy scipy