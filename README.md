# 🧠 License Plate Recognition using Visual Language Model (VLM)

This repository contains the source code for a license plate OCR (Optical Character Recognition) system developed as part of the **Computer Vision (RE604)** coursework at Politeknik Negeri Batam.

The system uses a **Visual Language Model (VLM)** (`qwen2-vl-2b-instruct`) via **LMStudio** to read license plate images and evaluate the results using **Character Error Rate (CER)**.

---

## 📌 Project Description

This project is implemented in Python using the following tools:

- `lmstudio` – interface to call the VLM model (`qwen2-vl-2b-instruct`)
- `pandas` – to manage CSV data
- `evaluate` – to calculate Character Error Rate (CER)
- `os`, `csv` – for file processing and path management

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
| Average CER         | 0.0643          |
| Prediction Accuracy | Shown per image |

> The model's performance depends on image quality and label consistency. Lower CER means better OCR performance.

Example Output:

```bash
[✓] val001_1.jpg: GT=B2017PBQ, Pred=B2017PBQ, CER=0.0000
[✓] val002_1.jpg: GT=F1234ABC, Pred=F1234ADC, CER=0.1250
[X] val003_1.jpg: GT=D1234XYZ, Pred=ERROR, CER=1.0000

📊 Average CER: 0.0643
📁 Results saved to: ocr_results.csv
