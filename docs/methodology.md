# Dataset and Methodology
## AI-Based Road Damage Detection and Visualisation System Using Deep Learning

## 1. Introduction

This project proposes a deep learning-based system for detecting and visualising road damage from digital images. The system will use a YOLO-based object detection model trained on the RDD2022 dataset. The trained model will then be integrated into a web application developed using Streamlit.

The methodology consists of seven main stages: dataset acquisition, data exploration and preprocessing, dataset splitting, model training, model evaluation, web application development, and system testing.

The training process will be conducted using Google Colab, while the web application will be developed and tested using Visual Studio Code.

## 2. Research Design

This project will adopt an experimental development approach. A deep learning object detection model will be trained using annotated road images, evaluated on data excluded from training, and integrated into a functional web application.

The project will involve two main components:

1. **AI model development:** Training and evaluating a model that detects and localises four road damage categories.
2. **Application development:** Building a web interface that allows users to upload road images and view the model's predictions.

The overall workflow is illustrated below.

<escape>
Road Damage Dataset (RDD2022)
            ↓
Dataset Exploration and Annotation Preparation
            ↓
Training / Validation / Test Split
            ↓
YOLO Model Training in Google Colab
            ↓
Model Validation and Selection
            ↓
Final Evaluation on Held-Out Test Data
            ↓
Export Trained Model
            ↓
Streamlit Web Application in VS Code
            ↓
Image Upload → Detection → Visualisation → Download
</escape>

## 3. Dataset Acquisition

### 3.1 Dataset source

The project will use the Road Damage Dataset 2022 (RDD2022), a publicly available research dataset designed for automatic road damage detection.

Dataset title: *RDD2022: A Multi-National Image Dataset for Automatic Road Damage Detection*

Dataset DOI: https://doi.org/10.6084/m9.figshare.21431547.v1

Research paper: https://doi.org/10.1002/gdj3.260

GitHub repository: https://github.com/sekilab/RoadDamageDetector

RDD2022 contains 47,420 road images collected from six countries and more than 55,000 annotated road damage instances. The exact number of usable images and annotations in this project will depend on the downloaded files, selected categories, annotation availability, and preprocessing.

### 3.2 Selected damage categories

The project will focus on the following four classes.

| Class code | Damage category | Description |
|---|---|---|
| D00 | Longitudinal cracks | Cracks extending primarily along the direction of the road |
| D10 | Transverse cracks | Cracks extending primarily across the direction of the road |
| D20 | Alligator cracks | Interconnected cracks forming a pattern resembling reptile scales |
| D40 | Potholes | Localised holes or depressions in the road surface |

These categories will be mapped consistently to the model's class labels throughout dataset preparation, training, evaluation, and application development.

### 3.3 Dataset inspection

After downloading the dataset, the images and annotations will be inspected to determine:

- The total number of available images.
- The number of annotations for each selected damage category.
- The annotation format and category naming conventions.
- The presence of missing, corrupted, or duplicate images.
- Whether some images lack annotations or are intended only for testing or prediction.
- Differences in image dimensions and visual quality.

Only images with suitable annotations will be included in supervised model training and quantitative object detection evaluation.

## 4. Data Preprocessing

### 4.1 Image preprocessing

The downloaded road images will be prepared for use with the selected YOLO implementation. The preprocessing stage will include:

1. Checking that image files can be opened successfully.
2. Removing or excluding corrupted files.
3. verifying that each training image has a corresponding annotation file.
4. Converting annotations into the format required by the selected training framework.
5. Mapping the four target categories to consistent class identifiers.
6. Resizing images during model training according to the selected model's input configuration.

For example, if the chosen training configuration uses an image size of 640 × 640 pixels, YOLO's preprocessing pipeline will resize and pad images as needed. The final input size will be documented in the experiment configuration.

### 4.2 Annotation preparation

The dataset annotations will be checked to ensure that each selected road damage instance has the correct class label and bounding box.

If the downloaded annotations use a format such as XML or JSON, they will be converted to YOLO's required text format if necessary.

Each YOLO annotation will contain:

- Class identifier.
- Normalised bounding-box centre coordinates.
- Normalised bounding-box width.
- Normalised bounding-box height.

The coordinates and dimensions must be normalised relative to the image width and height. Annotation conversion will be checked by drawing sample bounding boxes over the original images and visually confirming their alignment with the labelled damage.

### 4.3 Data augmentation

During training, suitable data augmentation techniques may be applied to improve robustness. These may include horizontal flipping, small geometric transformations, scaling, and controlled changes in image appearance.

Augmentation settings will be selected conservatively to avoid producing unrealistic examples or changing the meaning of a damage category. Augmentation will be applied to training data only, not to validation or test data used for final evaluation.

## 5. Dataset Splitting

The labelled data will be separated into training, validation, and test subsets.

The proposed initial split is:

| Subset | Proposed proportion | Purpose |
|---|---:|---|
| Training | 70% | Used to train the model |
| Validation | 15% | Used to monitor performance and select model settings |
| Testing | 15% | Used for final evaluation after model selection |

These percentages are proposed settings and may be adjusted if the dataset structure or assignment requirements require a different approach.

To reduce data leakage, closely related images from the same source sequence should be kept within the same subset wherever the source information allows this. Duplicate images should not appear across different subsets.

The test subset will remain separate from model training and model selection. It will be used only for final performance reporting.

Images without ground-truth annotations may be useful for qualitative demonstrations, but they cannot be used to calculate standard ground-truth-based object detection metrics.

## 6. Model Selection and Training

### 6.1 Model selection

The project will begin with a lightweight pretrained YOLO object detection model, such as YOLOv8n, as a baseline.

A pretrained model provides initial feature representations learned from an existing training dataset. Fine-tuning it on RDD2022 allows the model to adapt to the selected road damage categories.

The final model version will be confirmed before training based on compatibility, available computational resources, documentation, and licensing considerations.

### 6.2 Training environment

Google Colab will be used for model training because it provides a notebook environment and may provide access to GPU acceleration.

The main software and libraries will include:

- Python.
- Ultralytics YOLO.
- PyTorch, as required by the selected implementation.
- OpenCV for image processing.
- Matplotlib for visualising training results.
- Pandas for organising evaluation results.

The exact package versions will be recorded to support reproducibility.

### 6.3 Training procedure

The proposed training procedure is as follows:

1. Open a Google Colab notebook.
2. Select an available GPU runtime if supported.
3. Install the required libraries.
4. Download or upload the prepared dataset to the runtime or mounted storage.
5. Create a dataset configuration file defining the training, validation, and test paths and the four class names.
6. Load the selected pretrained YOLO model.
7. Configure the image size, batch size, number of epochs, and other training settings.
8. Fine-tune the model using the training subset.
9. Monitor training and validation metrics.
10. Select the model checkpoint according to validation performance.
11. Save the training configuration, results, and selected model weights.
12. Evaluate the selected model on the held-out test subset.

The final number of epochs, batch size, image size, and other hyperparameters will be determined through preliminary experiments and available hardware resources. They will be reported as actual settings after training.

### 6.4 Training output

The expected outputs from the training stage include:

- Trained model weights.
- Training and validation loss curves, where available.
- Precision and recall results.
- mAP@0.5 and mAP@0.5:0.95.
- Confusion matrix and per-class performance information, where supported.
- Sample prediction images.
- A record of the model configuration and training environment.

These outputs will be used to assess the model before it is integrated into the application.

## 7. Model Evaluation

The trained model will be evaluated using the held-out test subset. The evaluation will consider detection accuracy, class-specific performance, localisation quality, and inference speed.

### 7.1 Precision

Precision measures the proportion of predicted detections that are correct.

Precision = TP / (TP + FP)

Where:

- TP = true positives.
- FP = false positives.

Higher precision indicates that a larger proportion of the model's predicted detections are correct.

### 7.2 Recall

Recall measures the proportion of actual annotated damage instances that are successfully detected.

Recall = TP / (TP + FN)

Where:

- TP = true positives.
- FN = false negatives.

Higher recall indicates that the model detects a larger proportion of the annotated damage instances.

### 7.3 Mean Average Precision at IoU 0.5

mAP@0.5 summarises average precision across the selected classes using an Intersection over Union threshold of 0.5 to determine whether a predicted bounding box overlaps sufficiently with a ground-truth box.

This metric will be used to assess the model's object detection performance.

### 7.4 Mean Average Precision at IoU 0.5:0.95

mAP@0.5:0.95 averages detection performance across multiple IoU thresholds from 0.5 to 0.95.

This metric provides a stricter assessment of bounding-box localisation and detection performance than mAP@0.5 alone.

### 7.5 Inference time

Inference time measures the time required for the model to generate predictions for an image under specified testing conditions.

The measurement will record the hardware and image input size used. Where possible, model inference time will be distinguished from total application processing time, which may also include image upload, preprocessing, and rendering.

### 7.6 Error analysis

The evaluation will include selected examples of:

- Correctly detected road damage.
- False-positive detections.
- Missed damage instances.
- Differences in detection performance between the four classes.
- Predictions affected by shadows, low image quality, or other challenging visual conditions.

The results will be reported using the actual measured values. Any performance target will be treated as a target, not a result, until supported by experiments.

## 8. Web Application Development

### 8.1 Development environment

The web application will be developed using Visual Studio Code with Python and Streamlit. The selected trained YOLO model will be loaded by the application to perform inference on uploaded road images.

The interface will focus on image-based analysis rather than continuous live video processing.

### 8.2 Application workflow

The application will follow this workflow:

1. The user opens the Streamlit application.
2. The user uploads a supported road image.
3. The application validates the image file.
4. The trained model processes the image.
5. The application displays the annotated image with predicted bounding boxes and category labels.
6. The interface displays confidence scores and category-wise detection counts.
7. The user can download the annotated image.

### 8.3 Main application features

The application will include the following features:

| Feature | Description |
|---|---|
| Image upload | Accept supported image files such as JPG, JPEG, and PNG |
| Image validation | Check that the uploaded file can be read and processed |
| Damage detection | Run inference using the trained YOLO model |
| Bounding-box visualisation | Draw predicted damage locations on the image |
| Class labels | Display D00, D10, D20, and D40 labels in readable form |
| Confidence scores | Display the model's confidence for each predicted detection |
| Category-wise counts | Summarise the number of detections predicted for each category |
| Download results | Allow users to download the annotated image |

The application will clearly distinguish predicted detections from confirmed road defects. A lack of detections will not be presented as proof that a road is undamaged.

## 9. System Testing

System testing will be conducted after integrating the model with the web application.

### 9.1 Functional testing

The application will be tested to verify that:

- Supported images can be uploaded.
- Invalid or corrupted images are handled appropriately.
- The model produces predictions for valid inputs.
- Bounding boxes and labels are displayed correctly.
- Confidence scores and category counts are consistent with the predictions.
- Annotated images can be downloaded.
- The application provides useful feedback when an error occurs.

### 9.2 Prediction testing

Images representing the four damage categories will be used to inspect the system's behaviour. Additional examples with no obvious damage and with challenging lighting or road conditions will be examined.

The purpose of this testing is to identify practical errors and limitations. Images without annotations will be treated as qualitative examples rather than as a basis for calculating ground-truth-based accuracy metrics.

### 9.3 Performance testing

The system's inference time will be measured under documented conditions. The model will also be checked for its ability to process images of different dimensions and to display predictions consistently.

The final report will include relevant test cases, observed results, and any issues that remain unresolved.

## 10. Responsible AI Considerations

The proposed system is designed to support preliminary road image inspection. It is not intended to replace qualified road inspectors or professional engineering assessment.

The following limitations will be considered:

1. **False positives:** The model may incorrectly label shadows, road markings, or surface patterns as damage.
2. **False negatives:** The model may fail to detect actual cracks or potholes.
3. **Dataset bias:** The training images may not represent all road types, weather conditions, or traffic environments.
4. **Local generalisation:** Performance on Malaysian roads must be assessed separately rather than assumed from RDD2022 test results.
5. **Privacy:** Images should be checked for faces and vehicle registration plates before public sharing.
6. **Engineering interpretation:** The predicted category and bounding box do not establish the severity of the defect, its cause, or the appropriate repair method.

These limitations will be documented in the application and final report.

## 11. Expected Deliverables

The expected project deliverables are:

1. A prepared and documented RDD2022 dataset workflow.
2. A trained YOLO-based road damage detection model.
3. A Google Colab notebook containing the training and evaluation procedure.
4. A Streamlit web application developed in Visual Studio Code.
5. Sample annotated road images.
6. Model evaluation results, including class-wise metrics where available.
7. System testing results.
8. Technical documentation describing the methodology, limitations, and possible future improvements.

## 12. Conclusion

This methodology establishes a structured process for developing and evaluating an AI-based road damage detection system. RDD2022 will provide the annotated images for model development, while a YOLO-based detector will be trained in Google Colab and integrated into a Streamlit application developed using Visual Studio Code.

The system will be assessed using standard object detection metrics, inference-time measurements, and functional testing. The final results will be based on experiments rather than assumed performance, and the limitations of using a public dataset for Malaysian road conditions will be acknowledged.

## References

1. Arya, D., Maeda, H., Ghosh, S. K., Toshniwal, D., & Sekimoto, Y., et al. (2024). RDD2022: A multi-national image dataset for automatic road damage detection. *Geoscience Data Journal, 11*(4), 846–862. https://doi.org/10.1002/gdj3.260

2. RDD2022 dataset. https://doi.org/10.6084/m9.figshare.21431547.v1

3. Ultralytics. *YOLO Documentation*. https://docs.ultralytics.com/

4. Ultralytics. *YOLO Performance Metrics*. https://docs.ultralytics.com/guides/yolo-performance-metrics/