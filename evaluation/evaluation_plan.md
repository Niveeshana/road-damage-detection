# Evaluation Plan
## AI-Based Road Damage Detection and Visualisation System Using Deep Learning

## 1. Introduction

The purpose of this evaluation plan is to establish a systematic approach for assessing the performance, reliability, and functionality of the proposed road damage detection system.

The system will use a YOLO-based object detection model trained on the RDD2022 dataset to detect four road damage categories: longitudinal cracks (D00), transverse cracks (D10), alligator cracks (D20), and potholes (D40).

The evaluation will cover two main components: the performance of the trained deep learning model and the functionality of the Streamlit web application. Quantitative evaluation will be conducted using a held-out test dataset, while functional testing will verify that the application processes images and displays predictions correctly.

All performance results will be recorded after the experiments have been conducted. No evaluation result will be assumed in advance.

## 2. Evaluation Objectives

The evaluation has the following objectives:

1. To measure the road damage detection model's performance using established object detection metrics.
2. To assess the model's detection performance across all four damage categories.
3. To measure inference time under documented hardware and software conditions.
4. To verify that the web application correctly processes uploaded images and presents detection results.
5. To identify model errors and document limitations that may affect practical use.

## 3. Model Evaluation Metrics

### 3.1 Precision

Precision measures the proportion of predicted detections that are correct.

\[
\text{Precision}=\frac{TP}{TP+FP}
\]

Where:

- TP = true positives.
- FP = false positives.

A high precision value indicates that fewer predicted detections are false positives.

### 3.2 Recall

Recall measures the proportion of actual annotated damage instances that are detected by the model.

\[
\text{Recall}=\frac{TP}{TP+FN}
\]

Where:

- TP = true positives.
- FN = false negatives.

A high recall value indicates that the model identifies a larger proportion of the annotated damage instances.

### 3.3 Mean Average Precision at IoU 0.5 (mAP@0.5)

mAP@0.5 summarises the average precision across the four detection categories using an Intersection over Union (IoU) threshold of 0.5.

IoU measures the overlap between a predicted bounding box and its corresponding ground-truth bounding box. A higher IoU indicates greater overlap.

This metric will be used to evaluate the model's overall object detection performance.

### 3.4 Mean Average Precision at IoU 0.5:0.95 (mAP@0.5:0.95)

mAP@0.5:0.95 averages detection performance across multiple IoU thresholds ranging from 0.5 to 0.95.

This metric provides a stricter assessment of detection and localisation performance because predictions must satisfy increasingly demanding overlap thresholds.

### 3.5 Inference Time

Inference time measures the time required for the trained model to generate predictions for an input image.

The measurement will be recorded in milliseconds or seconds per image. The hardware, image dimensions, model input size, and measurement procedure will also be documented.

Model inference time will be distinguished from total application response time where possible, because image uploading, preprocessing, and visualisation can introduce additional delays.

## 4. Category-Wise Evaluation

The model will be evaluated across the four target categories.

| Class code | Damage category | Evaluation focus |
|---|---|---|
| D00 | Longitudinal cracks | Ability to detect and localise longitudinal cracks |
| D10 | Transverse cracks | Ability to detect and localise transverse cracks |
| D20 | Alligator cracks | Ability to detect interconnected crack patterns |
| D40 | Potholes | Ability to detect and localise potholes |

Precision, recall, and average precision will be examined for individual categories where the evaluation framework provides these results.

Category-wise evaluation is important because an acceptable overall score may conceal poor performance for a particular damage category.

## 5. Dataset and Experimental Procedure

The model will be evaluated using a held-out test subset prepared from labelled RDD2022 images.

The test subset will not be used to train the model or select its hyperparameters. Where source sequences or related images can be identified, these will be kept within the same data split to reduce the risk of data leakage.

The evaluation procedure will consist of the following steps:

1. Prepare and validate the labelled dataset.
2. Separate the data into training, validation, and test subsets.
3. Train the YOLO-based model using the training subset.
4. Select the model checkpoint using validation results.
5. Run the selected model on the held-out test subset.
6. Record the overall and category-wise evaluation metrics.
7. Generate a confusion matrix and inspect representative prediction images where supported.
8. Record inference time using a documented test configuration.
9. Analyse false positives, false negatives, and localisation errors.
10. Save the final evaluation results for inclusion in the project report.

The final evaluation will use the same selected model and test subset for all reported model metrics.

## 6. Proposed Performance Target

The project will use the following preliminary target to guide model development.

| Metric | Proposed target | Purpose |
|---|---|---|
| mAP@0.5 | At least 0.70 (70%) | Initial target for overall detection performance |
| Precision | Record actual result | Assess the proportion of correct predicted detections |
| Recall | Record actual result | Assess the proportion of annotated damage detected |
| mAP@0.5:0.95 | Record actual result | Assess localisation performance across multiple IoU thresholds |
| Inference time | Measure and report | Assess model responsiveness under documented conditions |

The mAP@0.5 target of 0.70 is a project goal, not a guaranteed result or an established requirement of the RDD2022 dataset. The achieved value will be reported honestly, even if the model does not reach the target.

Inference time will be reported as a measured value rather than an arbitrary target because it depends on the hardware, image size, model configuration, and software environment.

## 7. Web Application Functional Testing

The Streamlit application will be tested to confirm that its main features operate as intended.

| Test ID | Test case | Expected result | Status |
|---|---|---|---|
| FT01 | Upload a valid JPG image | The image is accepted and displayed | To be tested |
| FT02 | Upload a valid PNG image | The image is accepted and displayed | To be tested |
| FT03 | Upload an unsupported or corrupted file | The application displays an appropriate error message | To be tested |
| FT04 | Process a valid road image | The model generates predictions | To be tested |
| FT05 | Display predicted bounding boxes | Detected locations are displayed on the image | To be tested |
| FT06 | Display category labels | Predicted damage categories are shown correctly | To be tested |
| FT07 | Display confidence scores | Each displayed detection includes its confidence score | To be tested |
| FT08 | Display category-wise counts | Counts match the detections returned by the model | To be tested |
| FT09 | Download the annotated image | The output image can be downloaded and opened | To be tested |
| FT10 | Process an image with no predicted detections | The application handles the empty prediction result without crashing | To be tested |

The status of each test will be updated after the application has been implemented and tested.

## 8. Error Analysis

The evaluation will examine representative examples of incorrect or uncertain predictions.

### 8.1 False positives

A false positive occurs when the model predicts a damage instance that does not correspond to an annotated object of the predicted category under the evaluation criteria.

Examples may include shadows, road markings, surface texture, or other visual patterns incorrectly classified as damage.

### 8.2 False negatives

A false negative occurs when an annotated damage instance is not detected by the model under the evaluation criteria.

Possible contributing factors include low image resolution, poor lighting, small damage regions, occlusion, or insufficient representation of a particular damage pattern in the training data.

### 8.3 Localisation errors

A localisation error occurs when the model predicts the correct damage category but the bounding box does not overlap sufficiently with the ground-truth box at the specified IoU threshold.

### 8.4 Class-specific performance differences

The results will be compared across D00, D10, D20, and D40 to determine whether some categories are more difficult to detect than others.

Any explanation of performance differences will be presented as an interpretation supported by the observed results, rather than as a confirmed cause without further investigation.

## 9. Results Recording Template

The following table will be completed after model training and evaluation.

| Evaluation metric | Actual result |
|---|---|
| Overall precision | To be measured |
| Overall recall | To be measured |
| mAP@0.5 | To be measured |
| mAP@0.5:0.95 | To be measured |
| D00 average precision | To be measured |
| D10 average precision | To be measured |
| D20 average precision | To be measured |
| D40 average precision | To be measured |
| Mean model inference time | To be measured |
| Test set size | To be recorded |
| Evaluation hardware | To be recorded |

The final report will include the actual results, the experimental configuration, and an interpretation of the model's strengths and weaknesses.

## 10. Evaluation of Project Success

The project will be considered functionally successful if the trained model can process road images and the web application can display and export its predictions as intended.

Model performance will be assessed separately using the quantitative metrics. Achieving the proposed mAP@0.5 target will indicate that the initial performance goal has been met, but it will not by itself demonstrate suitability for operational road inspection.

The final assessment will consider:

- Whether the four target categories can be detected.
- The measured model performance.
- Differences in performance between categories.
- Inference speed under documented conditions.
- Successful operation of the web application.
- Observed errors and limitations.
- The need for further validation on Malaysian road images.

## 11. Limitations of Evaluation

The evaluation results will reflect the dataset, model configuration, and testing conditions used in the project. They will not automatically establish performance on all road types, countries, weather conditions, or camera systems.

In particular, performance on RDD2022 will not be treated as proof of generalisation to Malaysian road conditions. Local validation would require an appropriate collection of Malaysian road images and, for quantitative evaluation, reliable ground-truth annotations.

The system will not be evaluated as a tool for determining engineering damage severity, repair priority, or road safety certification.

## 12. Conclusion

This evaluation plan defines how the proposed road damage detection model and web application will be assessed. The model will be evaluated using precision, recall, mAP@0.5, mAP@0.5:0.95, category-wise results, and inference time. The web application will undergo functional testing to verify image upload, prediction, visualisation, and download features.

The final project report will present measured results, explain important errors, and acknowledge the limitations of the dataset and model. This approach will provide a transparent assessment of the prototype's performance without making unsupported claims about its effectiveness in real-world road inspection.

## References

1. Arya, D., Maeda, H., Ghosh, S. K., Toshniwal, D., & Sekimoto, Y., et al. (2024). RDD2022: A multi-national image dataset for automatic road damage detection. *Geoscience Data Journal, 11*(4), 846–862. https://doi.org/10.1002/gdj3.260

2. Ultralytics. (n.d.). *YOLO Performance Metrics*. https://docs.ultralytics.com/guides/yolo-performance-metrics/