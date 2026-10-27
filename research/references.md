# Research Sources and Literature Review
## Project: AI-Based Road Damage Detection and Visualisation System Using Deep Learning

## 1. Introduction

Road damage detection is an important computer vision application that can support road maintenance, infrastructure monitoring, and transportation safety. Road surfaces may develop different types of damage, including longitudinal cracks, transverse cracks, interconnected cracks, and potholes. Identifying these defects from road images is a potential application of deep learning and object detection.

Traditional road inspection methods may involve visual observation and manual reporting. Computer vision systems offer an alternative approach by analysing road images and automatically identifying possible damage locations. However, an automated detection system must be evaluated carefully because it may produce false detections or fail to identify actual damage.

This project proposes an AI-based road damage detection and visualisation system using a deep learning object detection model. The system will use the RDD2022 dataset to develop a model capable of detecting four categories of road damage. The trained model will subsequently be integrated into a web application that allows users to upload road images and view the model's predictions.

The main purpose of this literature review is to examine the existing road damage dataset, review deep learning approaches used for road damage detection, identify relevant evaluation metrics, and establish a justified direction for the proposed project.

## 2. Research Source 1: RDD2022 Road Damage Dataset

### Reference

Arya, D., Maeda, H., Ghosh, S. K., Toshniwal, D., & Sekimoto, Y., et al. (2024). RDD2022: A multi-national image dataset for automatic road damage detection. *Geoscience Data Journal, 11*(4), 846–862.

Publication DOI: https://doi.org/10.1002/gdj3.260

Dataset DOI: https://doi.org/10.6084/m9.figshare.21431547.v1

### Research problem

Developing a reliable road damage detection model requires a dataset containing road images with annotations identifying the locations and categories of damage. A dataset collected from different geographical locations can help researchers study road damage under different visual conditions.

### Dataset and approach

The RDD2022 dataset contains 47,420 road images collected from six countries: Japan, India, the Czech Republic, Norway, the United States, and China. The dataset includes more than 55,000 annotated road damage instances.

The four principal categories used in this project are:

- D00: Longitudinal cracks.
- D10: Transverse cracks.
- D20: Alligator cracks.
- D40: Potholes.

The dataset was developed to support research into automatic road damage detection and provides annotated images that can be used to train and evaluate object detection models.

### Evaluation methods

RDD2022 is a dataset resource rather than a single proposed detection algorithm. Therefore, its main contribution is the provision of annotated road images for model development and benchmarking. The evaluation metrics for this project will be selected based on established object detection practice.

### Limitations and considerations

The dataset was collected in six countries and does not establish that a model trained on it will perform equally well on Malaysian roads. Differences in road surfaces, lighting, weather, camera angles, and image quality may affect predictions.

The dataset also contains different quantities of each damage category. This class imbalance must be considered when preparing the data and interpreting model performance.

### Relevance to this project

RDD2022 will serve as the primary dataset for training and evaluating the proposed model. Its four damage categories match the intended scope of the project. However, the model's performance on Malaysian road conditions will remain unverified unless additional local road images are collected and evaluated.

## 3. Research Source 2: YOLOv8-PD Road Damage Detection

### Reference

Zeng, J., & Zhong, H. (2024). YOLOv8-PD: An improved road damage detection algorithm based on YOLOv8n model. *Scientific Reports, 14*, Article 12052.

Article URL: https://www.nature.com/articles/s41598-024-62933-z

DOI: https://doi.org/10.1038/s41598-024-62933-z

### Research problem

The researchers investigate challenges in road damage detection, particularly the detection of damage features at different scales and the computational cost of detection.

### Methodology

The paper proposes YOLOv8-PD, an improved road damage detection algorithm based on the YOLOv8n model. The proposed approach introduces modifications intended to improve the detection of pavement damage, including a module designed to extract global information for large-span crack features.

### Dataset

The study uses RDD2022. The researchers selected 10,000 images, allocating 8,000 for training and 2,000 for validation.

### Evaluation methods

The study evaluates road damage detection performance using object detection evaluation measures. Its results and comparisons provide a reference for understanding how an improved YOLO-based model can be assessed against an existing baseline.

### Limitations and considerations

The reported experiments use a selected subset of RDD2022. Their results should therefore be interpreted in the context of the authors' dataset selection, training configuration, and experimental environment. Performance reported by the authors should not be assumed to represent the performance of a separately trained model.

The proposed project will initially use a standard YOLO model rather than claiming to reproduce every architectural modification introduced by YOLOv8-PD.

### Relevance to this project

This paper demonstrates that YOLO-based models have already been investigated for road damage detection. It provides a relevant basis for selecting a YOLO detector as the project's starting point. It also shows why the proposed project should evaluate its own model rather than assume that an existing paper's results will be reproduced.

## 4. Research Source 3: RDD-YOLO

### Reference

Li, Y., Yin, C., Lei, Y., Zhang, J., & Yan, Y. (2024). RDD-YOLO: Road Damage Detection Algorithm Based on Improved You Only Look Once Version 8. *Applied Sciences, 14*(8), 3360.

Article URL: https://www.mdpi.com/2076-3417/14/8/3360

DOI: https://doi.org/10.3390/app14083360

### Research problem

The paper investigates the detection of road damage and the challenges associated with missed detections, detection accuracy, and the computational demands of object detection models.

### Methodology

The researchers propose RDD-YOLO, an improved YOLOv8-based road damage detection algorithm. The paper describes architectural modifications intended to improve detection performance, including changes involving feature processing and feature fusion.

### Dataset

The study uses RDD2022 and considers four road damage categories:

- D00: Longitudinal cracks.
- D10: Transverse cracks.
- D20: Alligator cracks.
- D40: Potholes.

### Evaluation methods

The paper reports metrics including mean Average Precision at an Intersection over Union threshold of 0.5 (mAP@0.5), mAP@0.5:0.95, and F1-score, alongside model complexity measures.

The paper reports an overall mAP@0.5 of 62.5% for RDD-YOLO in its experiments, compared with 59.9% for the YOLOv8x baseline used in the study. These values belong to the authors' experimental setup and are not guaranteed results for the proposed project.

### Limitations and considerations

The results depend on the model architecture, data preparation, training settings, and evaluation procedure used in the study. A more complex model may also introduce additional computational requirements.

The proposed project prioritises a practical implementation that can be trained in Google Colab and deployed through a web application. Consequently, the project will first establish a baseline before considering more complex architectural modifications.

### Relevance to this project

This paper provides evidence that road damage detection with YOLO has already been studied extensively. Therefore, the project should not claim that using YOLO for road damage detection is itself a new contribution.

Instead, the project will focus on developing and evaluating a working end-to-end application that integrates four-class road damage detection, visualisation, category-wise results, and image-based inference.

## 5. Research Source 4: OBC-YOLOv8

### Reference

OBC-YOLOv8: An improved road damage detection model based on YOLOv8. (2025).

Article URL: https://pmc.ncbi.nlm.nih.gov/articles/PMC11784705/

Note: Verify the complete author list, publication details, and final citation format from the article's bibliographic information before submitting the final academic report.

### Research problem

The study examines how an improved YOLOv8-based model can identify different road damage categories and evaluates detection performance alongside computational efficiency.

### Methodology and dataset

The researchers use an improved YOLOv8-based detection approach. The reported experiments use a portion of the RDD2022 data identified in the article as RDD-China, comprising 4,378 images captured using drones and onboard cameras.

The study considers the road damage categories available in its experimental data and discusses the use of object detection metrics to assess model performance.

### Evaluation methods

The paper discusses precision, recall, F1-score, mean Average Precision, model parameters, computational complexity, and inference speed-related measures.

These metrics illustrate that a road damage detection system should be assessed not only by its detection accuracy but also by its computational requirements.

### Limitations and considerations

The experimental results are based on the study's selected dataset and model configuration. They should not be compared directly with results from other papers unless the datasets, evaluation procedures, and experimental settings are sufficiently consistent.

The use of a specific subset of RDD2022 also means that its results should not automatically be interpreted as evidence of generalisation to every country or road environment.

### Relevance to this project

This study supports the use of multiple evaluation measures for road damage detection. The proposed system will report precision, recall, mAP@0.5, mAP@0.5:0.95, and inference time where these measures can be obtained reliably.

The study also provides a reason to consider computational efficiency when selecting a model suitable for an interactive web application.

## 6. Research Source 5: Object Detection Evaluation Metrics

### Reference

Ultralytics. (n.d.). *YOLO Performance Metrics*. Ultralytics Documentation.

URL: https://docs.ultralytics.com/guides/yolo-performance-metrics/

### Purpose

This technical documentation explains evaluation measures used to assess YOLO object detection models. It provides a practical reference for interpreting model evaluation outputs during training and validation.

### Relevant evaluation measures

**Precision**

Precision measures the proportion of predicted detections that are correct.

Precision = TP / (TP + FP)

Here, TP represents true positives and FP represents false positives.

**Recall**

Recall measures the proportion of actual annotated objects that the model successfully detects.

Recall = TP / (TP + FN)

Here, FN represents false negatives.

**Mean Average Precision at IoU 0.5 (mAP@0.5)**

This metric summarises average precision across the detection categories using an Intersection over Union threshold of 0.5 to determine whether a predicted bounding box sufficiently overlaps with a ground-truth box.

**Mean Average Precision at IoU 0.5:0.95 (mAP@0.5:0.95)**

This metric averages detection performance across multiple IoU thresholds from 0.5 to 0.95. It provides a more demanding assessment of both detection and localisation performance than mAP@0.5 alone.

**Inference time**

Inference time measures how long the model takes to produce predictions for an input image under a specified hardware and software configuration. It is relevant to the responsiveness of the proposed web application.

### Limitations and considerations

No single metric fully describes a detection model's performance. A model can achieve reasonable overall performance while performing poorly on a particular damage category. Evaluation should therefore include category-wise results and visual inspection of representative false positives and missed detections.

Inference time also depends on hardware, image size, preprocessing, and implementation. Any reported timing should specify the testing conditions.

### Relevance to this project

These metrics will be used to evaluate the trained model. The final report will include actual experimental results rather than presenting proposed targets as achieved results.

## 7. Comparison of Existing Research

| Source | Main contribution | Dataset or focus | Relevance to the project |
|---|---|---|---|
| Arya et al. (2024) | Introduces and describes the RDD2022 dataset | 47,420 road images from six countries | Provides the primary dataset |
| Zeng and Zhong (2024) | Proposes YOLOv8-PD | Selected 10,000-image RDD2022 subset | Supports selection of YOLO as a baseline approach |
| Li et al. (2024) | Proposes RDD-YOLO | RDD2022 and four damage categories | Provides a comparison with an improved YOLO-based method |
| OBC-YOLOv8 study | Examines an improved YOLOv8-based approach | Selected RDD2022 data | Supports evaluation of accuracy and efficiency |
| Ultralytics documentation | Explains object detection metrics | YOLO evaluation methodology | Guides the proposed model evaluation |

## 8. Research Gap and Project Justification

The reviewed studies demonstrate that deep learning and YOLO-based architectures have already been applied to road damage detection. Existing research has explored model improvements, feature extraction, detection accuracy, and computational efficiency.

Therefore, the research gap for this project is not the absence of AI-based road damage detection methods. Instead, the project will investigate the practical integration of a four-class road damage detector into an accessible image-based web application, supported by transparent evaluation and visualisation.

The proposed system will combine the following functions:

1. Detection of four road damage categories: D00, D10, D20, and D40.
2. Display of predicted bounding boxes, category labels, and confidence scores.
3. Presentation of category-wise detection counts.
4. Download of the annotated output image.
5. Evaluation using precision, recall, mAP@0.5, mAP@0.5:0.95, and inference time.
6. Documentation of model limitations, including possible false positives, missed damage, and uncertain performance on Malaysian road images.

The project's practical contribution will be assessed through the completed implementation, measured model performance, and usability of the application. Claims about improved accuracy, real-world effectiveness, or novelty will only be made if supported by experimental evidence and comparison with relevant existing work.

## 9. Proposed Methodology

The project will follow these stages:

**Stage 1: Dataset preparation**

Obtain RDD2022 from its official repository. Inspect the available images and annotations, select the four intended categories, and convert annotations into the format required by the selected object detection framework.

**Stage 2: Data splitting and preprocessing**

Separate labelled data into training, validation, and test subsets. Use the training subset for model learning, the validation subset for model selection, and the held-out test subset for final evaluation. Where source sequences or closely related images can be identified, keep related images in the same split to reduce data leakage.

**Stage 3: Model training**

Train a pretrained YOLO object detection model using Google Colab. Record the model version, dataset split, image size, batch size, number of epochs, hardware, and training configuration.

**Stage 4: Model evaluation**

Evaluate the selected model using precision, recall, mAP@0.5, mAP@0.5:0.95, and inference time. Report results for individual classes as well as overall performance.

**Stage 5: Web application development**

Develop a Streamlit application in Visual Studio Code. The application will accept road images, run model inference, and display annotated predictions and category-wise counts.

**Stage 6: System testing**

Test the application using images containing different road damage categories, images with no visible damage, and images with challenging lighting or road conditions. Record examples of successful detections, false positives, and missed detections.

**Stage 7: Documentation**

Prepare the final report, model evaluation results, system screenshots, implementation details, limitations, and recommendations for future improvement.

## 10. Responsible AI and Limitations

The proposed system is intended to assist preliminary visual inspection, not replace qualified road inspectors or engineering assessments.

Potential limitations include:

- **False positives:** The model may identify normal road patterns as damage.
- **False negatives:** The model may fail to detect existing damage.
- **Domain generalisation:** Training on images from six countries does not guarantee reliable predictions on Malaysian roads.
- **Class imbalance:** Unequal numbers of examples may affect performance across the four categories.
- **Image quality:** Shadows, low resolution, rain, glare, and camera angle may influence predictions.
- **Privacy:** Uploaded images should be checked for identifiable faces, vehicle registration plates, or other personal information before public sharing.
- **Severity interpretation:** A detection label or bounding box does not establish structural severity, repair urgency, or engineering safety.

These limitations will be stated in the application and final report. The system's predictions should be treated as estimates that require human verification.

## 11. Conclusion

The reviewed literature establishes RDD2022 as a relevant dataset for road damage detection and demonstrates the existing use of YOLO-based deep learning models for identifying pavement damage. Existing studies also provide a foundation for evaluating detection accuracy and computational efficiency.

Building on this research, the proposed project will develop a four-class road damage detection model and integrate it into a Streamlit web application. Its contribution will be the practical implementation, transparent evaluation, and visual presentation of model predictions rather than a claim that the underlying detection task is entirely new.

The system's effectiveness will be determined through measured results on a held-out test set. Its limitations, especially its unverified performance on Malaysian road conditions, will be explicitly acknowledged.

## References

1. Arya, D., Maeda, H., Ghosh, S. K., Toshniwal, D., & Sekimoto, Y., et al. (2024). RDD2022: A multi-national image dataset for automatic road damage detection. *Geoscience Data Journal, 11*(4), 846–862. https://doi.org/10.1002/gdj3.260

2. RDD2022 dataset. (2022). *The multi-national Road Damage Dataset released through CRDDC'2022*. Figshare. https://doi.org/10.6084/m9.figshare.21431547.v1

3. Zeng, J., & Zhong, H. (2024). YOLOv8-PD: An improved road damage detection algorithm based on YOLOv8n model. *Scientific Reports, 14*, Article 12052. https://doi.org/10.1038/s41598-024-62933-z

4. Li, Y., Yin, C., Lei, Y., Zhang, J., & Yan, Y. (2024). RDD-YOLO: Road Damage Detection Algorithm Based on Improved You Only Look Once Version 8. *Applied Sciences, 14*(8), 3360. https://doi.org/10.3390/app14083360

5. OBC-YOLOv8: An improved road damage detection model based on YOLOv8. (2025). Article available at https://pmc.ncbi.nlm.nih.gov/articles/PMC11784705/. Verify the final bibliographic metadata before submission.

6. Ultralytics. (n.d.). *YOLO Performance Metrics*. https://docs.ultralytics.com/guides/yolo-performance-metrics/

7. Arya, D., Maeda, H., Ghosh, S. K., Toshniwal, D., & Sekimoto, Y., et al. (2022). RDD2022: A multi-national image dataset for automatic road damage detection. *arXiv*. https://doi.org/10.48550/arXiv.2209.08538
