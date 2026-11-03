# Week 2 – Part B: Evaluation Criteria

## 1. Introduction

This document defines the evaluation criteria for the AI-Based Road Damage Detection and Visualisation System. The evaluation focuses on the road damage detection model, application functionality, prediction visualisation, and system performance.

The system will be evaluated using a held-out test dataset and functional testing. The evaluation criteria are linked to the project objectives, functional requirements, non-functional requirements, and Responsible AI requirements.

All thresholds stated in this document are proposed targets. They are not actual experimental results.

## 2. Evaluation Criteria

| ID | Evaluation Criterion | Linked Objective / Requirement | Capability Bucket | Evaluation Method | Metric | Proposed Threshold | Expected User / Business Outcome |
|---|---|---|---|---|---|---|---|
| EC1 | Four-class road damage detection performance | O1, FR2, NFR1, RAI3 | Domain-specific capability | Evaluate model predictions against ground-truth annotations from the held-out test dataset. | mAP@0.5 and per-class recall | Overall mAP@0.5 ≥ 0.70; recall for each of the four classes ≥ 0.50. | The model can identify the four supported road damage categories and provide measurable detection performance. |
| EC2 | Detection result visualisation and transparency | O2, FR3, RAI1 | Domain-specific capability | Conduct functional testing using at least 30 road images. Check whether the application displays bounding boxes, class labels, confidence scores, and the AI prediction disclaimer. | Visualisation pass rate and disclaimer display rate | At least 95% of test images display the required prediction information correctly; disclaimer appears on 100% of result screens. | Users can interpret model predictions while understanding that the output is AI-generated and not a professional engineering assessment. |
| EC3 | Category-wise detection summary correctness | O2, FR4 | Domain-specific capability | Compare the category-wise counts displayed by the application with the detection results returned by the model for at least 30 images. | Exact count agreement rate | 100% agreement between displayed counts and model detection outputs. | Users can obtain a consistent summary of detected road damage categories without manually counting bounding boxes. |
| EC4 | Model inference latency | O3, NFR2 | Cost and latency | Measure model inference time across at least 100 test images using the same documented hardware and software environment. | Average inference time per image | Average inference time ≤ 2 seconds per image. | Users receive predictions within a reasonable processing time during image-based analysis. |
| EC5 | Image processing reliability and annotated image download | O2, FR1, FR5, NFR3 | Domain-specific capability | Test at least 50 valid image uploads and conduct separate tests to download annotated results. | Successful image processing rate and successful download rate | At least 95% successful processing of valid uploads; at least 95% successful annotated image downloads. | Users can reliably upload road images, obtain predictions, and save annotated results for further reference. |

## 3. Additional Responsible AI Verification

The following check evaluates the system's privacy requirement. It is included separately because the four capability buckets are primarily intended to organise AI capability evaluation, while privacy is an operational and Responsible AI control.

| ID | Responsible AI Requirement | Evaluation Method | Metric | Proposed Threshold |
|---|---|---|---|---|
| RAI-EC1 | Uploaded images and annotated results should not be persistently stored without explicit user action. | Inspect application file handling and test whether temporary uploaded images and generated results are removed after the session. | Number of unauthorised persisted uploaded images or annotated results. | Zero unauthorised persisted images or results. |

## 4. Evaluation Methods and Procedures

### 4.1 Model Performance Evaluation

The trained model will be evaluated using a held-out test dataset containing ground-truth bounding-box annotations.

The following metrics will be reported:

- **Precision:** Measures the proportion of predicted detections that are correct.
- **Recall:** Measures the proportion of actual damage instances that are successfully detected.
- **mAP@0.5:** Measures object detection performance at an Intersection over Union (IoU) threshold of 0.5.
- **Per-class recall:** Measures detection recall separately for D00, D10, D20, and D40.

The test dataset must remain separate from the training and validation datasets.

### 4.2 Application Functional Evaluation

Functional testing will verify whether the application performs the required tasks:

1. Accept valid road images.
2. Process the uploaded images using the trained model.
3. Display bounding boxes, class labels, and confidence scores.
4. Display category-wise detection counts.
5. Display the AI-generated prediction disclaimer.
6. Allow users to download annotated images.

Each function will be tested using suitable test images and recorded test outcomes.

### 4.3 Performance Evaluation

Inference time will be measured across at least 100 test images. The hardware and software environment must be documented to ensure that the reported results can be interpreted consistently.

Inference time refers to model prediction time only. Image uploading, application rendering, and downloading time will not be included unless separately reported.

### 4.4 Responsible AI Evaluation

Responsible AI evaluation will focus on:

- **Transparency:** Verify that users are informed that predictions are AI-generated.
- **Privacy:** Verify that uploaded images and annotated results are not retained without explicit user action.
- **Detection bias:** Report recall separately for all four damage categories to identify differences in detection performance.

Any class that fails to meet the proposed per-class recall threshold must be highlighted and investigated.

## 5. Evaluation Limitations

The evaluation has several limitations:

1. The model is trained using the RDD2022 dataset, so its performance on Malaysian road conditions may differ from its performance on the test dataset.
2. Detection performance depends on image quality, lighting, road surface conditions, and the visibility of damage.
3. Class imbalance may affect the model's ability to detect certain damage categories.
4. Inference time depends on the hardware and software environment.
5. The system evaluates static road images and does not provide real-time video monitoring or professional road condition assessments.

## 6. Summary

The evaluation framework focuses on five main areas: model detection performance, prediction visualisation, category-wise summary correctness, inference latency, and application reliability. An additional Responsible AI check addresses privacy.

The evaluation results will be used to determine whether the developed system meets its proposed requirements and project objectives. Any unmet thresholds and limitations will be documented transparently.

## 7. References

1. Arya, D., et al. (2024). RDD2022: A multi-national image dataset for automatic road damage detection. *Geoscience Data Journal, 11*(4), 846–862. https://doi.org/10.1002/gdj3.260
2. Ultralytics. YOLO Performance Metrics. https://docs.ultralytics.com/guides/yolo-performance-metrics/