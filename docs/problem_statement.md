# Problem Statement
## AI-Based Road Damage Detection and Visualisation System Using Deep Learning

### 1. Background

Road infrastructure is essential for transportation, accessibility, and economic activities. However, road surfaces can develop various forms of damage, including longitudinal cracks, transverse cracks, alligator cracks, and potholes. Identifying these defects is important for supporting road inspection and maintenance planning.

Manual road inspection requires people to examine road conditions and identify visible defects. Although this approach remains important, analysing large numbers of road images manually can be time-consuming. Computer vision and deep learning offer a potential approach to automate the identification and localisation of road damage in images.

The RDD2022 dataset provides a research resource for developing road damage detection models. It contains 47,420 road images collected from six countries, with more than 55,000 annotated road damage instances. The dataset includes the four damage categories considered in this project: D00, D10, D20, and D40.

### 2. Problem Identification

Despite the availability of road damage datasets and deep learning techniques, developing a practical road damage detection system involves several challenges.

First, different types of road damage have different visual characteristics. Cracks may appear as thin, irregular lines, while potholes may appear as larger damaged regions. A detection model must learn these visual patterns to identify and localise the relevant damage categories.

Second, a model's performance cannot be assumed to be equally reliable across all damage categories and road conditions. Factors such as lighting, shadows, image quality, and variations in road surfaces may affect detection results. Therefore, model performance must be evaluated using appropriate object detection metrics.

Third, model predictions are not always easy for users to interpret when they are presented only as numerical outputs. A practical application should display the detected damage locations, predicted categories, confidence scores, and category-wise detection counts in an understandable format.

Finally, a model trained using a public dataset may not generalise equally well to road conditions in Malaysia. Its performance on local roads must be evaluated separately before the system can be considered suitable for practical local use.

### 3. Problem Statement

There is a need to develop and evaluate an accessible computer vision application that can automatically detect and localise multiple categories of road damage from uploaded road images. The proposed system will use a deep learning object detection model trained on the RDD2022 dataset to identify longitudinal cracks (D00), transverse cracks (D10), alligator cracks (D20), and potholes (D40).

The system will integrate the trained model into a web application that presents annotated road images, predicted damage categories, confidence scores, and category-wise detection counts. Its effectiveness will be evaluated using precision, recall, mean Average Precision at IoU 0.5 (mAP@0.5), mAP@0.5:0.95, and inference time.

The project will also document detection errors and limitations, particularly the possibility of false positives, missed damage, and reduced performance on road conditions that differ from the training data. The system is intended to support preliminary visual inspection rather than replace professional road condition assessment.

### 4. Project Objectives

The project has the following objectives:

1. To develop a deep learning object detection model capable of identifying four road damage categories (D00, D10, D20, and D40) using the RDD2022 dataset.
2. To develop a web-based application that displays detected road damage through annotated images, category labels, confidence scores, and category-wise detection counts.
3. To evaluate the model's detection performance and computational efficiency using precision, recall, mAP@0.5, mAP@0.5:0.95, and inference time.

### 5. Research Questions

This project will investigate the following questions:

1. How effectively can a YOLO-based object detection model detect the four selected road damage categories in the RDD2022 dataset?
2. How can the model's predictions be presented through a web application to make the detected damage easier to interpret?
3. What limitations can be observed in the model's detection performance, including false positives, missed detections, and variations between damage categories?

### 6. Scope of the Project

The project will focus on:

- **Input:** Road images uploaded by users.
- **Dataset:** RDD2022, subject to dataset access and annotation-format requirements.
- **Detection categories:** D00 longitudinal cracks, D10 transverse cracks, D20 alligator cracks, and D40 potholes.
- **Model:** A pretrained YOLO object detection model fine-tuned using the selected dataset.
- **Training environment:** Google Colab.
- **Application development:** Python and Streamlit in Visual Studio Code.
- **Output:** Annotated images, bounding boxes, predicted categories, confidence scores, category-wise detection counts, and downloadable results.
- **Evaluation:** Precision, recall, mAP@0.5, mAP@0.5:0.95, and inference time.
- **Limitations:** The system will not determine engineering damage severity, prescribe repairs, or guarantee reliable performance on Malaysian roads without further validation.

### 7. Expected Outcome

The expected outcome is a working prototype that integrates a trained road damage detection model with a web-based visualisation interface. Users will be able to upload a road image, view the model's predictions, inspect the detected damage categories, and download the annotated image.

The model's actual performance will be reported after training and testing. Any target accuracy or mAP value will be treated as a development goal rather than a guaranteed result.

### 8. References

Arya, D., Maeda, H., Ghosh, S. K., Toshniwal, D., & Sekimoto, Y., et al. (2024). RDD2022: A multi-national image dataset for automatic road damage detection. *Geoscience Data Journal, 11*(4), 846–862. https://doi.org/10.1002/gdj3.260

RDD2022 dataset. https://doi.org/10.6084/m9.figshare.21431547.v1