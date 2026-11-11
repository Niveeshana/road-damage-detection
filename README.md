# AI-Based Road Damage Detection and Visualisation System

## 1. Project Overview

This project aims to develop an AI-based system for detecting and visualising road damage using computer vision.

The system focuses on identifying four road damage categories from the RDD2022 dataset:

- **D00:** Longitudinal crack
- **D10:** Transverse crack
- **D20:** Alligator crack
- **D40:** Pothole

The project uses an image-processing and machine-learning approach to support road condition assessment.

## 2. Dataset

**Dataset:** Road Damage Detection 2022 (RDD2022)

**Source:** [RDD2022 Dataset – Kaggle](https://www.kaggle.com/datasets/aliabdelmenam/rdd-2022?resource=download)

The dataset contains road images with annotations for different types of road damage.

Only a selected sample is used for the initial Week 3 pipeline test. This sample is intended for pipeline development and validation, not for claiming representative model performance.

## 3. Project Scope

The project is developed in stages:

- **Topic 2:** Requirements analysis and system architecture planning.
- **Topic 3:** Dataset inspection, preparation, pipeline development, and validation.
- **Later stages:** Model development, evaluation, and visualisation.

## 4. Week 3 Data Pipeline

The Week 3 pipeline follows these main stages:

1. **Ingest:** Load the selected road images from the dataset.
2. **Inspect:** Examine image properties, formats, dimensions, and data quality.
3. **Prepare:** Convert images into the selected standard format.
4. **Validate:** Check that the prepared images exist and are readable.
5. **Store:** Save the processed images in the pipeline output directory.
6. **Record lineage:** Generate a manifest containing source information, processing configuration, output details, and SHA-256 checksums.

## 5. Project Structure

```text
road-damage-detection/
│
├── data/
│   ├── raw/
│   ├── processed/
│   ├── pipeline_v1/
│   └── week3_manifest.json
│
├── docs/
│   ├── week3_data_inventory.md
│   ├── week3_pipeline_decisions.md
│   └── week3_pipeline_diagram.png
│
├── notebooks/
│   └── week3_pipeline.ipynb
│
├── evaluation/
│
├── research/
│
├── README.md
└── requirements.txt
```

*Note: The actual folders and files may vary as the project develops.*

## 6. Pipeline Outputs

The Week 3 pipeline produces:

- Prepared road images.
- A pipeline execution manifest.
- Source-to-output mapping information.
- Validation results.
- SHA-256 checksums for traceability and repeatability checks.

## 7. Tools and Technologies

- Python
- Google Colab
- OpenCV
- Pillow (PIL)
- NumPy
- Git and GitHub
- Draw.io

## 8. Current Development Status

**Completed / In Progress:**

- Project requirements and architecture planning.
- RDD2022 dataset selection.
- Dataset inspection and inventory.
- Image preparation pipeline development.
- Pipeline validation and lineage recording.
- Pipeline architecture documentation.

**Future Development:**

- Road damage detection model development.
- Model training and performance evaluation.
- Road damage visualisation.
- Integration into a web-based application.

## 9. Important Notes

- The Week 3 sample is used for pipeline testing and does not represent the entire RDD2022 dataset.
- Dataset annotations must be preserved and correctly mapped to their corresponding images for later object-detection training.
- Dataset licensing and redistribution conditions must be checked before sharing the dataset or its contents.
- The current pipeline is a data preparation workflow; it is not yet a trained road damage detection model.
