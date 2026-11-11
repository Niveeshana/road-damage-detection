
# Week 3 — V1 Data Pipeline Decisions

## 1. Project Information

**Project:** AI-Based Road Damage Detection and Visualisation System

**Dataset:** Road Damage Detection 2022 (RDD2022)

**Data Type:** Computer Vision / Images

**Selected Pathway:** Pathway C

## 2. Requirements Traceability

The image pipeline supports the requirement to ingest and
prepare road images for subsequent road-damage detection.


The prepared images will be used as input for the
future object detection model.

## 3. Data Source Selection

**Selected source:** RDD2022 dataset

**Source URL:**
https://www.kaggle.com/datasets/aliabdelmenam/rdd-2022

**Pipeline sample:** 20 selected road images

**Reason for selection:**
RDD2022 contains road images and damage annotations
relevant to detecting road damage.

## 4. Part B Preparation Comparison

**Selected method:**
Convert images to RGB while preserving original dimensions.

**Alternative considered:**
Resize images to a fixed resolution.

**Reason for selected method:**
RGB conversion provides a consistent colour format.
Preserving original dimensions avoids changing the
spatial coordinates used by the road-damage bounding boxes.

**Limitation:**
The images may have different dimensions. A later
model-specific preprocessing stage may be needed.

## 5. V1 Pipeline Configuration

| Parameter | Selected Configuration |
|---|---|
| Data type | Images |
| Image formats | JPG, JPEG, PNG |
| Sample size | 20 images |
| Colour conversion | RGB |
| Resizing | None |
| Output format | PNG |
| Output directory | data/pipeline_v1/images/ |

## 6. ETL / ELT Decision

The pipeline follows an ETL-style workflow.

Images are ingested, inspected, transformed into RGB
format, validated and stored as prepared outputs.

## 7. Batch / Streaming Decision

Batch processing was selected because the current
RDD2022 dataset consists of stored road images.

Streaming is not required for this offline dataset
preparation activity.

## 8. Pipeline Stage Contracts

| Stage | Expected Result | Failure Response |
|---|---|---|
| Ingest | Source images found | Stop if source is missing |
| Inspect | Images are readable | Flag or stop on invalid images |
| Prepare | RGB images generated | Report transformation failure |
| Validate | Outputs exist and are non-empty | Stop on missing or empty outputs |
| Lineage | Source-output mapping recorded | Report missing mapping or metadata |

## 9. Output and Provenance

**Part C output:**
data/pipeline_v1/images/

**Pipeline manifest:**
data/pipeline_v1/images/pipeline_manifest.json

The manifest records source fingerprints, output
fingerprints, processing configuration and
source-to-output relationships.

RDD2022 annotation files are not transformed by
this image-only pipeline. Their association with the
original images must be preserved separately.

Dataset redistribution permissions and source-version
details must be verified before sharing the data.

## 10. Limitations and Future Improvements

1. Only 20 images are used for the V1 pipeline test.
2. The sample is not intended to represent the full dataset.
3. Bounding-box annotations are not transformed by this pipeline.
4. Image dimensions are not standardised.
5. Future work should include annotation validation,
   dataset-level quality checks and model-specific preprocessing.
