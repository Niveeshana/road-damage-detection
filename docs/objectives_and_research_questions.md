
## Project Title

**AI-Based Road Damage Detection and Visualisation System Using Deep Learning**

## 1. Aim of the Project

The aim of this project is to develop a deep learning-based road damage detection system that identifies four categories of road damage from images and presents the detection results through a web-based visualisation application.

The system will use the RDD2022 dataset to train and evaluate a YOLO-based object detection model. The trained model will be integrated into a Streamlit web application that allows users to upload road images, view predicted damage locations, inspect detection confidence scores, and download annotated images.

## 2. Project Objectives

### Objective 1: Develop a Road Damage Detection Model

To develop and fine-tune a YOLO-based object detection model using the RDD2022 dataset to detect four categories of road damage: longitudinal cracks (D00), transverse cracks (D10), alligator cracks (D20), and potholes (D40).

**Expected output:**
- A trained object detection model.
- A prepared and documented dataset.
- Training and validation results.
- A model capable of predicting bounding boxes and damage categories.

**Measurement of achievement:**
- Successful completion of model training.
- Detection of the four target categories.
- Evaluation using precision, recall, mAP@0.5, and mAP@0.5:0.95.

### Objective 2: Develop a Web-Based Visualisation Application

To develop a Streamlit web application that allows users to upload road images and visualise the road damage detection results produced by the trained model.

**Expected output:**
- An image upload interface.
- An annotated image displaying predicted bounding boxes and class labels.
- Confidence scores for individual detections.
- Category-wise detection counts.
- An option to download the annotated image.

**Measurement of achievement:**
- The application successfully accepts supported image formats.
- The trained model produces predictions through the application.
- The interface displays the detection results correctly.
- Users can download the annotated output image.

### Objective 3: Evaluate Model Performance and System Efficiency

To evaluate the trained road damage detection model using established object detection metrics and measure its inference time under documented testing conditions.

**Expected output:**
- Overall model evaluation results.
- Category-wise precision and recall where available.
- mAP@0.5 and mAP@0.5:0.95 results.
- Inference time measurements.
- Examples of correct detections, false positives, and missed detections.

**Measurement of achievement:**
- The model is evaluated using a held-out test set that was not used for training or model selection.
- The evaluation metrics are recorded and reported accurately.
- The model's strengths and limitations are discussed using experimental evidence.

## 3. Research Questions

### Research Question 1

**How effectively can a YOLO-based deep learning model detect and localise the four selected road damage categories using the RDD2022 dataset?**

This question examines the model's ability to identify longitudinal cracks, transverse cracks, alligator cracks, and potholes.

It will be investigated using precision, recall, mAP@0.5, mAP@0.5:0.95, and category-wise evaluation results.

### Research Question 2

**How can a web-based visualisation application present road damage detection results in a clear and interpretable manner?**

This question focuses on integrating the trained model into a Streamlit application and presenting its predictions through annotated images, category labels, confidence scores, and category-wise detection counts.

It will be investigated through functional testing of the application and inspection of its displayed outputs.

### Research Question 3

**What limitations affect the detection performance and computational efficiency of the proposed road damage detection system?**

This question investigates errors and practical constraints, including false positives, missed detections, differences in performance between damage categories, and inference time.

It will be investigated by analysing the model's evaluation results and testing it on road images with different visual conditions.

## 4. Alignment Between Objectives and Research Questions

| Project objective | Related research question | Evaluation method |
|---|---|---|
| Objective 1: Develop the detection model | RQ1: How effectively does the model detect road damage? | Precision, recall, mAP@0.5, mAP@0.5:0.95, and class-wise results |
| Objective 2: Develop the web application | RQ2: How can the results be presented clearly? | Functional testing and inspection of application outputs |
| Objective 3: Evaluate performance and efficiency | RQ3: What limitations affect performance and efficiency? | Error analysis, category-wise metrics, and inference time |

## 5. Scope and Boundaries

The project will focus on image-based road damage detection rather than continuous real-time road surveillance.

The model will classify detected objects into four predefined categories: D00, D10, D20, and D40. The application will display the detected objects and their confidence scores, but it will not determine the engineering severity of damage, recommend repairs, or automatically certify road safety.

The primary evaluation will use a held-out test set derived from labelled RDD2022 data. The model's suitability for Malaysian road conditions will not be assumed without separate local validation.

## 6. Expected Project Outcomes

Upon completion, the project is expected to produce:

1. A trained YOLO-based road damage detection model.
2. A documented dataset preparation and model training workflow.
3. A Streamlit web application for uploading and analysing road images.
4. Annotated images containing predicted road damage locations and labels.
5. Quantitative model evaluation results.
6. Documentation of system limitations and possible future improvements.

The final performance values will be determined by the experiments. No specific accuracy or mAP result is guaranteed in advance.

## 7. Conclusion

The objectives and research questions establish a clear direction for developing and evaluating the proposed road damage detection system. The project will combine model development, web application implementation, and quantitative evaluation to produce a functional prototype.

The research questions will be answered using experimental evidence, application testing, and documented analysis rather than assumptions about model performance.