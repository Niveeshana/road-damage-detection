# Week 2 – Part C: Architecture Decisions and Traceability

**Project:** AI-Based Road Damage Detection and Visualisation System  
**Version:** 1.0

## 1. Introduction

This document presents the architecture needs, key architecture decisions, trade-offs, and requirements traceability for the V1 conceptual architecture of the AI-Based Road Damage Detection and Visualisation System.

The architecture is derived from the functional requirements, non-functional requirements, Responsible AI requirements, and evaluation criteria defined in the previous sections.

The main purpose of the architecture is to support four-class road damage detection, image-based result visualisation, system evaluation, and responsible handling of uploaded images.

## 2. Architecture Needs from Requirements

The following table identifies the architectural capabilities and components required to support the important project requirements.

| Requirement ID | What Does the Requirement Need? | Architecture Response |
|---|---|---|
| FR1 | Users must be able to upload valid road images. | An application interface and input-processing component to accept and validate uploaded images. |
| FR2 | The system must identify D00, D10, D20, and D40 road damage categories. | An AI detection capability supported by a trained road damage detection model. |
| FR3 | Users must see bounding boxes, category labels, and confidence scores. | A results-processing and visualisation component to convert model predictions into understandable outputs. |
| FR4 | Users must see category-wise detection counts. | A results-processing component to group model predictions by damage category and calculate counts. |
| FR5 | Users must be able to download annotated images. | An output component that generates and provides downloadable annotated images. |
| NFR1 / EC1 | Detection performance must be measured against labelled ground truth. | A model evaluation point using a held-out labelled test dataset and object detection metrics. |
| NFR2 / EC4 | Model inference must meet the proposed latency target. | An inference-time measurement capability within the detection and evaluation workflow. |
| NFR3 / EC5 | Valid image processing must meet the proposed reliability target. | Input validation, controlled image processing, and functional testing. |
| RAI1 / EC2 | Users must understand that predictions are AI-generated. | A transparency control that displays a clear disclaimer with the prediction results. |
| RAI2 / RAI-EC1 | Uploaded images and annotated results must not be persistently stored without explicit user action. | Temporary file handling and deletion controls. |
| RAI3 / EC1 | Differences in detection performance across the four categories must be identified. | Per-class evaluation using separate recall measurements for D00, D10, D20, and D40. |

## 3. V1 Architecture Components

The V1 architecture contains the following components:

### 3.1 User

The user interacts with the application by uploading a road image, viewing the detection results, and downloading an annotated image.

### 3.2 AI Application / Interface

The application interface provides the main interaction between the user and the AI system. It accepts image uploads and presents the processed results.

### 3.3 Input Processing

The input-processing component validates the uploaded image and prepares it for the AI detection capability. Invalid or unsupported files should be rejected appropriately.

### 3.4 AI Detection Capability

The AI detection capability processes the validated road image and identifies the four supported damage categories:

- D00 – Longitudinal cracks
- D10 – Transverse cracks
- D20 – Alligator cracks
- D40 – Potholes

It returns structured prediction information, including bounding-box coordinates, category labels, and confidence scores.

### 3.5 Model and Data Support

The RDD2022 dataset provides the labelled images used during model development and evaluation.

A trained model artifact is produced through the model training process and supplied to the AI detection capability.

The held-out labelled test set is kept separate from model training and is used for performance evaluation.

### 3.6 Results Processing

The results-processing component prepares the model predictions for presentation. It generates annotated images, calculates category-wise detection counts, and records inference time.

### 3.7 Responsible AI Controls

The architecture incorporates two important controls:

- **Transparency control:** Displays an AI-generated prediction disclaimer.
- **Privacy control:** Manages temporary uploaded and generated files and removes them according to the system's privacy requirement.

### 3.8 Evaluation Point

The evaluation point measures the model and application against the defined evaluation criteria. It includes detection performance, per-class recall, inference time, and functional testing.

## 4. Architecture Decision Records (ADR)

The following architecture decisions explain the alternatives considered, selected options, and trade-offs accepted.

### ADR-01: Modular Application Architecture

| Decision Element | Description |
|---|---|
| Decision | Use a modular architecture that separates the interface, input processing, AI detection, and results processing. |
| Requirement / Constraint | FR1, FR2, FR3, FR4, FR5 and maintainability requirements. |
| Alternatives Considered | A single combined application component; a modular architecture with separate functional components. |
| Selected Option | Modular architecture with clearly defined component responsibilities. |
| Trade-off Accepted | Additional component interfaces and integration work are required, but the design improves maintainability, testing, and future model replacement. |

**Justification:**

Separating the application into functional components allows the detection model to be updated without requiring major changes to the user interface. It also allows input processing, prediction handling, and output generation to be tested independently.

### ADR-02: Static Image Processing for V1

| Decision Element | Description |
|---|---|
| Decision | Support uploaded static road images rather than real-time video processing in V1. |
| Requirement / Constraint | FR1, FR2, project timeline, available computing resources, and the need for controlled model evaluation. |
| Alternatives Considered | Static image upload and detection; continuous real-time video detection. |
| Selected Option | Static road-image upload and detection. |
| Trade-off Accepted | The system cannot continuously monitor roads, but development complexity is reduced and detection performance can be evaluated using labelled images. |

**Justification:**

Static image processing provides a manageable initial scope. It allows the system to be developed and evaluated using the annotated RDD2022 dataset without introducing additional video-processing requirements.

### ADR-03: Separate Model Detection from Results Processing

| Decision Element | Description |
|---|---|
| Decision | Separate AI prediction generation from the processing and presentation of detection results. |
| Requirement / Constraint | FR3, FR4, FR5, EC2 and EC3. |
| Alternatives Considered | Generate all visualisation and summaries inside one combined detection component; return structured predictions to a separate results-processing component. |
| Selected Option | Separate results processing from the AI detection capability. |
| Trade-off Accepted | Additional processing and data exchange are required, but the system becomes easier to test, modify, and extend. |

**Justification:**

The AI detection capability should focus on identifying road damage and returning prediction information. A separate component can then generate annotated images, calculate category counts, and prepare the information for display.

### ADR-04: Temporary Image Handling and Privacy Control

| Decision Element | Description |
|---|---|
| Decision | Use temporary image handling instead of persistent image storage in V1. |
| Requirement / Constraint | RAI2 and the privacy requirement for uploaded road images. |
| Alternatives Considered | Persistently store uploaded images and results; process images temporarily and remove them after processing or session completion. |
| Selected Option | Temporary file handling with deletion controls. |
| Trade-off Accepted | Users will not have automatic historical access to previous uploads, but unnecessary retention of potentially identifiable image data is reduced. |
 
**Justification:**

Road images may contain identifiable information, including vehicle registration plates and people. Limiting image retention reduces privacy risks. The deletion behaviour must be implemented and verified through testing.

## 5. Initial Requirements Traceability Matrix

The following matrix connects the project objectives, requirements, evaluation criteria, architecture elements, and evidence that will be collected later.

| Objective | Requirement | Evaluation Criterion | Architecture Element | Later Evidence |
|---|---|---|---|---|
| O1 – Develop a four-class road damage detection model. | FR2, NFR1, RAI3 | EC1 – Four-class detection performance | AI Detection Capability and Evaluation Point | Held-out test results showing mAP@0.5 and per-class recall for D00, D10, D20, and D40. |
| O2 – Develop an application for road damage detection and visualisation. | FR1, FR3, FR4, FR5 | EC2 – Detection visualisation; EC3 – Category-wise count correctness; EC5 – Image processing and download reliability | Application Interface, Input Processing, Results Processing, and Output | Functional test records, screenshots of detection results, count comparison results, and image download tests. |
| O3 – Evaluate the model and application. | NFR2, NFR3, RAI2 | EC4 – Inference latency; EC5 – Reliability; RAI-EC1 – Privacy verification | Evaluation Point, Input Processing, and Temporary File Handling | Inference-time measurements, successful processing rate, and privacy test results. |

## 6. Key Architecture Trade-offs

The most important trade-off is the decision to use static image processing for V1 instead of real-time video processing.

Although real-time video monitoring could provide continuous road observation, it would introduce additional technical requirements such as video-frame processing, continuous inference, higher computational demand, and more complex performance testing.

By selecting static image processing, the project can focus on building a reliable four-class detection capability and evaluating it using labelled road images.

The modular architecture also introduces additional component interfaces. However, this is accepted because it supports independent testing, easier maintenance, and future improvements.

## 7. Architecture Review

The V1 architecture was reviewed against the following questions:

1. Does every major architecture component support a defined requirement or evaluation need? Yes. Each component is linked to functional, non-functional, or Responsible AI requirements.
2. Is an important data source included? Yes. The RDD2022 dataset, trained model artifact, and held-out labelled test set are represented.
3. Are Responsible AI controls included? Yes. Transparency and temporary-file handling are included.
4. Is an evaluation point included? Yes. The architecture supports detection performance, latency, reliability, and functional evaluation.
5. Are unnecessary technologies included? No specific framework, model version, database, or deployment platform is fixed in the conceptual architecture.

## 8. Reflection

The architecture decision involving the most important trade-off is selecting static image processing instead of real-time video processing.

This decision is driven by the project scope, available computing resources, and the requirement to evaluate detection performance using labelled images.

The accepted trade-off is that continuous road monitoring is not supported in V1. However, static image processing reduces implementation complexity and allows more attention to be given to the accuracy, visualisation, and evaluation of the four road damage categories.

## 9. Conclusion

The V1 conceptual architecture provides a requirement-driven design for the AI-Based Road Damage Detection and Visualisation System.

It includes the main application workflow, AI detection capability, model and data support, results processing, Responsible AI controls, and evaluation point.

The architecture decisions document the alternatives and trade-offs behind the design, while the traceability matrix connects the project objectives to requirements, evaluation criteria, architecture components, and future evidence.

The architecture is conceptual and will be refined as implementation and evaluation progress.