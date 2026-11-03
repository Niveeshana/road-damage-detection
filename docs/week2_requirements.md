# Topic 2 — Project Framing, Application Scope & Requirements

**Project Title:** AI-Based Road Damage Detection and Visualisation System Using Deep Learning

**Version:** 1.0

**Course:** AI Engineering

---

# Section 0 — Project Framing & Application Scope

## 0.1 Problem Evidence

Road damage, including cracks and potholes, can affect road safety, driving comfort, and infrastructure maintenance. Identifying and documenting road damage across extensive road networks can require significant inspection time and human effort.

The Road Damage Detection 2022 (RDD2022) dataset provides evidence of the scale and relevance of this problem for computer vision research. It contains 47,420 road images collected from six countries, with more than 55,000 annotated road damage instances. The dataset includes different categories of road damage, demonstrating the potential for automated image-based detection.

**Supporting sources:**

1. Arya, D., et al. (2024). *RDD2022: A multi-national image dataset for automatic road damage detection*. Geoscience Data Journal, 11(4), 846–862. https://doi.org/10.1002/gdj3.260

2. Sekilab. *Road Damage Detector — RDD2022 Dataset*. https://github.com/sekilab/RoadDamageDetector

These sources establish the availability of annotated road damage images and the relevance of automated road damage detection. They do not, by themselves, quantify the time or cost savings of an automated inspection system.

## 0.2 Existing Approaches

Several existing approaches have explored automated road damage detection.

| Existing approach | What it already addresses | Remaining consideration |
|---|---|---|
| Traditional manual road inspection | Human inspectors visually examine roads and identify visible damage. | Requires human effort and may be time-consuming across large road networks. |
| RDD2022 research and dataset | Provides a multi-country dataset with annotated road damage images for training and evaluating detection models. | The dataset itself does not provide a complete user-facing inspection application. |
| YOLOv8-PD | Proposes an improved YOLOv8n-based approach for road damage detection. | Model performance and suitability must be assessed using the intended dataset and evaluation conditions. |
| RDD-YOLO | Proposes an improved YOLOv8-based road damage detection algorithm. | A detection algorithm alone does not necessarily provide an accessible image-upload and visualisation workflow for end users. |

**Supporting research:**

1. Arya, D., et al. (2024). RDD2022 dataset research. https://doi.org/10.1002/gdj3.260
2. Zeng, X., & Zhong, Z. (2024). *YOLOv8-PD: An improved road damage detection algorithm based on YOLOv8n model*. https://doi.org/10.1038/s41598-024-62933-z
3. Li, et al. (2024). *RDD-YOLO: Road Damage Detection Algorithm Based on Improved You Only Look Once Version 8*. Applied Sciences, 14(8), 3360. https://doi.org/10.3390/app14083360

The proposed project builds on existing object detection research rather than claiming that YOLO-based road damage detection is a new concept.

## 0.3 Project / Engineering Gap

Existing research demonstrates that deep learning and YOLO-based models can be applied to road damage detection. However, a practical inspection workflow also requires an accessible way for users to submit road images, view predicted damage locations, understand prediction confidence, and review detection summaries.

The engineering gap addressed by this project is the integration of a trained road damage detection model with a simple visualisation application that presents detection results in an understandable format.

The project will also evaluate model performance across all four selected road damage categories rather than relying only on overall detection results.

This is a practical engineering gap and does not claim scientific novelty in the development of the YOLO architecture.

## 0.4 Project Objectives

**O1 — Model Development**

To develop a deep learning-based object detection model capable of identifying four road damage categories: longitudinal cracks, transverse cracks, alligator cracks, and potholes.

**O2 — Application Development**

To develop a web-based application that allows users to upload road images and visualise detected damage through bounding boxes, category labels, confidence scores, and category-wise detection counts.

**O3 — Model and System Evaluation**

To evaluate the detection model and application using precision, recall, mAP@0.5, mAP@0.5:0.95, inference time, and functional testing.

## 0.5 Intended Users

The intended users of the proposed application are:

1. **Road maintenance personnel:** To review road images and identify possible visible road damage.
2. **Local authority or infrastructure personnel:** To explore AI-assisted road inspection and documentation.
3. **Researchers and students:** To experiment with deep learning techniques for road damage detection and visualisation.

The application is developed as an academic prototype and is not intended to replace professional road inspection personnel.

## 0.6 Supported Tasks

The application will support the following tasks:

1. Upload a road image through the web application.
2. Analyse the uploaded image using the trained object detection model.
3. Detect the four selected road damage categories.
4. Display bounding boxes around predicted damage locations.
5. Display the predicted damage category and confidence score.
6. Calculate and display the number of detections for each category.
7. Display the image inference time.
8. Allow users to download the annotated road image.

## 0.7 Information / Knowledge Domain

The system operates within the domain of road infrastructure inspection and computer vision-based road damage detection.

The information domain includes:

- Road surface images.
- Road damage categories and their annotations.
- Object detection bounding boxes.
- Predicted class labels.
- Model confidence scores.
- Detection counts.
- Model evaluation results.

The four road damage categories are:

| Class | Damage category |
|---|---|
| D00 | Longitudinal cracks |
| D10 | Transverse cracks |
| D20 | Alligator cracks |
| D40 | Potholes |

The project uses the RDD2022 dataset as its primary source of training and evaluation data.

## 0.8 Operating Context

The proposed system will operate as a web-based image analysis application.

Users will access the application through a web browser, upload a road image, and receive the detection results.

The initial V1 system will focus on static image analysis rather than continuous video processing or real-time road monitoring.

The model will be trained using Google Colab, while the web application will be developed and tested using Python and Streamlit in Visual Studio Code.

## 0.9 Important Constraints

The project has the following constraints:

1. **Dataset availability:** Model development depends on access to the RDD2022 dataset and its annotations.
2. **Computational resources:** Model training depends on available computing resources, including Google Colab GPU availability.
3. **Dataset generalisation:** RDD2022 images originate from multiple countries, and the model may not perform equally well on Malaysian road conditions.
4. **Class distribution:** Differences in the number of annotated examples across damage categories may affect model performance.
5. **Project duration:** Model development, application integration, testing, and documentation must be completed within the academic project timeline.
6. **Application scope:** The initial version focuses on uploaded images rather than live camera feeds or continuous video.
7. **Model limitations:** Detection accuracy depends on image quality, lighting, viewing angle, and visibility of road damage.

## 0.10 Explicit Out-of-Scope Tasks

The proposed V1 application will NOT:

1. Determine the structural severity of road damage.
2. Decide whether a road is safe or unsafe for public use.
3. Recommend specific repair methods or calculate repair costs.
4. Automatically dispatch maintenance teams or create official maintenance reports.
5. Perform continuous real-time road monitoring using live video.
6. Automatically determine the geographical location of detected damage.
7. Replace professional engineering inspections or decisions.

The system will identify visible damage patterns in images only. Its predictions should be treated as decision-support information.

## 0.11 Evaluation Focus

The evaluation will determine whether the proposed system can detect the four selected road damage categories with acceptable performance and present the results in a useful and understandable format.

The evaluation will focus on:

1. **Detection performance:** Whether the model can identify the four damage categories using precision, recall, mAP@0.5, and mAP@0.5:0.95.
2. **Processing performance:** Whether the application can process uploaded images within an acceptable inference time.
3. **Visualisation functionality:** Whether bounding boxes, class labels, confidence scores, and category-wise detection counts are displayed correctly.
4. **System usability and functionality:** Whether users can upload images, view detection results, and download annotated images successfully.
5. **Reliability and limitations:** Whether model errors, including false positives and false negatives, can be identified and documented.

The final evaluation results will be obtained from actual experiments using a held-out test dataset and documented application tests.

---

## Section 0 Summary

| Framing element | Defined project direction |
|---|---|
| Problem | Manual road damage inspection requires human effort. |
| Evidence | RDD2022 dataset and related research. |
| Existing approaches | Manual inspection and YOLO-based detection research. |
| Engineering gap | Integration of detection results into an accessible visualisation application. |
| O1 | Develop a four-class road damage detection model. |
| O2 | Develop an image-based visualisation application. |
| O3 | Evaluate model performance and application functionality. |
| Intended users | Road maintenance personnel, infrastructure personnel, researchers, and students. |
| Operating context | Browser-based static road image analysis. |
| Evaluation focus | Detection performance, processing time, visualisation, and functionality. |

**End of Section 0 — Project Framing & Application Scope**

# Section 1 — Functional Requirements

**Project:** AI-Based Road Damage Detection and Visualisation System Using Deep Learning

**Version:** 1.0

Functional requirements define the specific functions and behaviours that the proposed system must provide to its intended users.

| ID | Requirement — The system SHALL | Scope Boundary — SHALL NOT |
|---|---|---|
| FR1 | Allow users to upload a road image in a supported image format for road damage analysis. | Accept unsupported file formats or files that cannot be processed as valid images. |
| FR2 | Analyse uploaded road images and identify the four defined road damage categories: longitudinal cracks (D00), transverse cracks (D10), alligator cracks (D20), and potholes (D40). | Classify road damage outside the four categories defined within the project scope. |
| FR3 | Display the detected road damage locations using bounding boxes, predicted category labels, and corresponding confidence scores. | Present model predictions as confirmed engineering assessments or guaranteed detections. |
| FR4 | Generate and display a category-wise summary showing the number of detected instances for each of the four road damage categories. | Interpret detection counts as measurements of road damage severity or repair urgency. |
| FR5 | Allow users to view and download the annotated road image containing the model's detection results. | Modify the original uploaded image or claim that the annotated image is an official road inspection report. |

## 1.1 Functional Requirement Summary

| Requirement ID | Main Function | Related Objective |
|---|---|---|
| FR1 | Road image upload | O2 |
| FR2 | Four-class road damage detection | O1 |
| FR3 | Detection visualisation | O2 |
| FR4 | Category-wise detection summary | O2 |
| FR5 | Annotated image download | O2 |

## 1.2 Functional Requirement Verification

The functional requirements will be verified through application testing.

| Requirement ID | Proposed Test Scenario | Expected Result |
|---|---|---|
| FR1 | Upload a valid JPG or PNG road image. | The application accepts and displays the uploaded image. |
| FR2 | Upload an image containing one or more examples of the selected road damage categories. | The model returns predictions for the supported categories. |
| FR3 | Process an image containing detectable road damage. | Bounding boxes, category labels, and confidence scores are displayed. |
| FR4 | Process an image containing multiple predicted damage instances. | The application displays the correct count of model predictions for each category. |
| FR5 | Process an image and select the download function. | The application provides the annotated image for download. |

**Note:** These are proposed requirements and test scenarios. Their successful implementation will be confirmed during development and testing.

**End of Section 1 — Functional Requirements**

# Section 2 — Non-Functional Requirements

**Project:** AI-Based Road Damage Detection and Visualisation System Using Deep Learning

**Version:** 1.0

Non-functional requirements define the quality attributes and expected performance of the proposed application. These requirements establish measurable targets for evaluating the system's performance, reliability, and maintainability.

| ID | Quality Attribute | Requirement | Measurement Method | Metric | Threshold |
|---|---|---|---|---|---|
| NFR1 | Detection Correctness | The system shall achieve an acceptable level of road damage detection performance across the four supported damage categories. | Evaluate the trained model using a separate held-out test dataset containing ground-truth annotations. | mAP@0.5 | ≥ 0.70 |
| NFR2 | Performance | The system shall process an uploaded road image and produce detection results within an acceptable processing time. | Measure inference time across at least 100 test images using the same hardware and software configuration. | Average inference time per image | ≤ 2 seconds |
| NFR3 | Reliability | The system shall process valid supported image uploads without unexpected application failures during testing. | Conduct functional testing using at least 50 valid image uploads and record successful and failed processing attempts. | Successful image processing rate | ≥ 95% |
| NFR4 | Maintainability | The system shall allow the trained model weights to be replaced or updated without requiring changes to the main image-upload and visualisation interface. | Perform a controlled model-weight replacement test and verify that the application continues to operate without modifying its main interface code. | Successful model replacement test | 100% successful completion of the defined test |

## 2.1 Explanation of Non-Functional Requirements

### NFR1 — Detection Correctness

The model must demonstrate acceptable road damage detection performance across the four supported categories.

The evaluation will use mAP@0.5, which measures object detection performance at an Intersection over Union (IoU) threshold of 0.5.

The proposed threshold of 0.70 is a project target, not a guaranteed result. Performance will be determined through actual testing using the held-out test dataset.

### NFR2 — Performance

The application should produce detection results within a reasonable processing time after a user uploads an image.

Average inference time will be measured across at least 100 test images. The hardware, image dimensions, and model configuration must be documented to make the measurement meaningful.

The proposed target is an average inference time of no more than 2 seconds per image.

This measurement focuses on model inference time, not necessarily the complete time taken for uploading, displaying, and downloading an image.

### NFR3 — Reliability

The application should process valid road images consistently without unexpected crashes or processing failures.

Testing will use at least 50 valid supported image uploads. Successful processing means the application completes inference and produces the expected result without an unexpected error.

The proposed target is a successful processing rate of at least 95%.

### NFR4 — Maintainability

The application should allow future model updates without requiring major modifications to its user interface.

This will be tested by replacing the existing model weights with another compatible trained model and checking whether the application can still perform image analysis and display results.

The target is successful completion of the defined model replacement test.

## 2.2 Non-Functional Requirement Summary

| Requirement ID | Quality Attribute | Main Evaluation Focus |
|---|---|---|
| NFR1 | Detection Correctness | Object detection performance |
| NFR2 | Performance | Image inference time |
| NFR3 | Reliability | Successful image processing rate |
| NFR4 | Maintainability | Model replacement without interface modification |

**Important:** All numerical thresholds are proposed engineering targets for this project. They must be evaluated through actual experiments. They should not be presented as achieved results before testing.

**End of Section 2 — Non-Functional Requirements**

# Section 3 — Responsible AI Requirements

**Project:** AI-Based Road Damage Detection and Visualisation System Using Deep Learning

**Version:** 1.0

Responsible AI requirements define the controls needed to ensure that the proposed system operates transparently, protects user privacy, and communicates its limitations appropriately.

The following requirements address the main ethical and operational risks associated with AI-based road damage detection.

| ID | Responsible AI Risk | Requirement | Measurement Method | Metric | Threshold |
|---|---|---|---|---|---|
| RAI1 | Transparency and Misinterpretation | The system shall display a clear notice explaining that detection results are AI-generated predictions and are not professional engineering assessments. | Conduct functional testing on all result-display screens and verify that the notice is visible whenever detection results are presented. | Percentage of result screens displaying the required notice | 100% |
| RAI2 | Privacy and Data Protection | The system shall not permanently store uploaded road images or annotated results after the user session ends unless the user explicitly initiates a download. | Conduct privacy testing by uploading test images, checking application storage, and verifying that temporary files are removed after the session ends. | Number of uploaded images or results remaining in persistent application storage without user authorisation | 0 |
| RAI3 | Detection Bias and Unequal Performance | The system shall evaluate and report detection performance separately for all four supported road damage categories to identify categories with weaker detection performance. | Evaluate a held-out test dataset and calculate recall separately for D00, D10, D20, and D40. | Per-class recall | ≥ 0.50 for each class; any class below the target must be explicitly reported and investigated. |

## 3.1 Explanation of Responsible AI Requirements

### RAI1 — Transparency and Misinterpretation

**Risk:**

Users may interpret the model's predictions as confirmed road damage assessments. This could lead to inappropriate decisions if the model produces false positives or false negatives.

**Responsible AI control:**

The application shall display a disclaimer explaining that its outputs are AI-generated predictions and should not replace professional road inspections.

**Measurement:**

Test every application screen that displays detection results and verify that the disclaimer is visible.

**Acceptance threshold:**

100% of result-display screens must show the required notice.

### RAI2 — Privacy and Data Protection

**Risk:**

Uploaded road images may contain sensitive visual information, such as vehicle registration plates, faces, or identifiable surroundings.

**Responsible AI control:**

The application shall avoid permanently storing uploaded images and generated results. Temporary files must be removed after the user session ends. Users may still download annotated images through the intended download function.

**Measurement:**

Upload test images, inspect the application's persistent storage, and verify that uploaded files and generated results are not retained after the session ends without user authorisation.

**Acceptance threshold:**

Zero uploaded images or generated results remain in persistent application storage without user authorisation.

### RAI3 — Detection Bias and Unequal Performance

**Risk:**

The model may perform better on some road damage categories than others because of differences in dataset size, image quality, and visual characteristics.

For example, the model may detect potholes effectively but struggle to identify certain crack patterns.

**Responsible AI control:**

The system shall evaluate and report recall separately for all four road damage categories instead of relying only on an overall performance score.

**Measurement:**

Calculate per-class recall using the held-out test dataset and compare the results across D00, D10, D20, and D40.

**Acceptance threshold:**

The proposed target is a recall of at least 0.50 for each category. Any category that does not achieve this target must be clearly identified and discussed in the evaluation report.

This threshold is a project target, not a guaranteed model outcome.

## 3.2 Responsible AI Requirement Summary

| Requirement ID | Risk Category | Main Control |
|---|---|---|
| RAI1 | Transparency | Display AI prediction disclaimer. |
| RAI2 | Privacy | Avoid unauthorised persistent image storage. |
| RAI3 | Detection Bias | Evaluate and report performance separately for all four categories. |

## 3.3 Reflection

**Question: Which Responsible AI requirement in your project will be the most difficult to measure or enforce technically? Why?**

**Answer:**

RAI3 — Detection Bias and Unequal Performance — will be the most difficult requirement to address technically.

The difficulty arises because the model's detection performance may differ across road damage categories due to class imbalance, differences in visual characteristics, and variations in image quality. Some damage categories may have fewer training examples or may be more difficult to distinguish from normal road surfaces.

Although per-class recall can be measured using a labelled test dataset, achieving consistent performance across all categories may require additional data preparation, model optimisation, and experimentation. Therefore, the system must report category-wise results and investigate underperforming categories rather than relying only on overall mAP.

**End of Section 3 — Responsible AI Requirements**