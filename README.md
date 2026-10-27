# AI-Based Road Damage Detection and Visualisation System Using Deep Learning

## 1. Project Overview

Road damage can affect road safety, driving comfort, and infrastructure maintenance. Traditional road inspections often require personnel to inspect roads manually, which can be time-consuming and may not provide consistent documentation across large areas.

This project aims to develop an **AI-based Road Damage Detection and Visualisation System** using deep learning and computer vision. The system will analyse road images and identify four categories of road damage using a YOLO-based object detection model.

The detected damage will be displayed through a web application, allowing users to upload road images and view the predicted damage locations, class labels, confidence scores, and category-wise detection counts.

The project is intended as a prototype to support road inspection and documentation. It is not a replacement for professional engineering assessment.

## 2. Problem Statement

Manual road inspection can require substantial time and effort, particularly when inspecting extensive road networks. Recording and reviewing road damage consistently can also be challenging.

Although deep learning models can detect road damage in images, their practical usefulness depends on detection performance, clear visualisation, and accessibility to users who may not have machine learning expertise.

Therefore, this project proposes an integrated system combining deep learning-based road damage detection with a simple web interface. The system will be evaluated using established object detection metrics and functional testing.

## 3. Project Objectives

The project has three main objectives:

1. To develop a YOLO-based object detection model for identifying four road damage categories.
2. To develop a web application that displays detected damage, class labels, confidence scores, and category-wise detection counts.
3. To evaluate the model using precision, recall, mean Average Precision (mAP), and inference time.

## 4. Road Damage Categories

The proposed system focuses on four categories from the RDD2022 dataset:

| Class | Description |
|---|---|
| D00 | Longitudinal cracks |
| D10 | Transverse cracks |
| D20 | Alligator cracks |
| D40 | Potholes |

The model will predict the locations of these damage categories within an uploaded road image.

## 5. Dataset

The project will use the **Road Damage Detection 2022 (RDD2022)** dataset.

RDD2022 contains road images collected from multiple countries and provides annotations for road damage detection research.

- Dataset: RDD2022
- Dataset DOI: https://doi.org/10.6084/m9.figshare.21431547.v1
- Research paper: https://doi.org/10.1002/gdj3.260
- Dataset repository: https://github.com/sekilab/RoadDamageDetector

The dataset will be prepared in the format required by the selected YOLO implementation. Training, validation, and test data will be separated to support model development and fair evaluation.

The dataset will not be uploaded directly to this repository if its size or licensing conditions make that inappropriate. Users should obtain the data from the official source and follow its applicable terms.

## 6. Methodology

The project will follow these stages:

1. **Literature review:** Review existing research on road damage detection, YOLO-based object detection, and evaluation methods.
2. **Dataset preparation:** Obtain the dataset, inspect the annotations, and prepare the required training, validation, and test splits.
3. **Model training:** Fine-tune a pretrained lightweight YOLO model using the training dataset.
4. **Model evaluation:** Evaluate the trained model on held-out test data using precision, recall, mAP@0.5, mAP@0.5:0.95, and inference time.
5. **Application development:** Build a Streamlit application that accepts road images and displays the model's predictions.
6. **System testing:** Test image uploads, prediction display, confidence scores, category counts, and annotated image output.
7. **Documentation:** Record the experimental setup, results, limitations, and recommendations for future development.

The specific model version, dataset split, and training configuration will be documented after implementation.

## 7. System Features

The planned application will provide the following features:

- Upload a road image for analysis.
- Detect the four selected road damage categories.
- Display bounding boxes around predicted damage.
- Show predicted class labels and confidence scores.
- Display category-wise detection counts.
- Report image inference time.
- Display the annotated image.
- Allow users to download the annotated result.

These features describe the intended system. Their implementation status will be updated as development progresses.

## 8. Technologies and Tools

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| YOLO / Ultralytics | Object detection model |
| PyTorch | Deep learning framework used by the selected YOLO implementation |
| OpenCV | Image processing and visualisation |
| Streamlit | Web application interface |
| Google Colab | Model training and experimentation |
| Visual Studio Code | Application development and project management |
| Git and GitHub | Version control and source code hosting |

## 9. Evaluation Metrics

The model will be evaluated using the following metrics:

- **Precision:** Measures the proportion of predicted detections that are correct.
- **Recall:** Measures the proportion of ground-truth damage instances that are detected.
- **mAP@0.5:** Measures mean Average Precision using an Intersection over Union threshold of 0.5.
- **mAP@0.5:0.95:** Measures mean Average Precision averaged across IoU thresholds from 0.5 to 0.95.
- **Inference time:** Measures the time required to process an image under a documented hardware and software configuration.

Results will be reported after the model has been trained and evaluated. No performance results are claimed at this stage.

## 10. Project Structure

The repository is intended to follow this structure:

```text
road-damage-detection/
├── README.md
├── requirements.txt
├── app.py
├── src/
│   ├── inference.py
│   ├── image_utils.py
│   └── visualisation.py
├── notebooks/
│   ├── 01_dataset_exploration.ipynb
│   └── 02_model_training.ipynb
├── configs/
│   └── dataset.yaml
├── docs/
│   ├── project_scope.md
│   ├── problem_statement.md
│   ├── literature_review.md
│   ├── objectives_and_research_questions.md
│   ├── methodology.md
│   └── responsible_ai.md
├── evaluation/
│   ├── evaluation_plan.md
│   ├── metrics.csv
│   ├── results_summary.md
│   └── confusion_matrix.png
└── tests/
    └── test_image_validation.py
```

Some files may be added as development progresses. The repository structure should be updated to reflect the files that actually exist.

## 11. Installation

### Prerequisites

- Python 3.10 or another Python version supported by the selected Ultralytics release.
- Git.
- Visual Studio Code or another Python development environment.

### Clone the repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
cd road-damage-detection
```

Replace `YOUR_GITHUB_REPOSITORY_URL` with the actual URL of your GitHub repository.

### Create a virtual environment

On Windows:

```bash
python -m venv .venv
.venv\Scripts\activate
```

On macOS or Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### Install dependencies

After creating `requirements.txt`, install the dependencies:

```bash
pip install -r requirements.txt
```

The dependency file should contain the packages and compatible versions required by the implemented application.

## 12. Running the Application

Once `app.py`, the inference code, dependencies, and trained model weights are ready, run:

```bash
streamlit run app.py
```

Open the local address shown in the terminal to access the application.

The application will require a compatible trained model weights file. The actual model path should be configured in the application after training.

**Note:** The command above describes the intended launch procedure. It will not work until the application code, dependencies, and model weights have been created.

## 13. Results and Performance

The following table will be completed after experimentation.

| Evaluation metric | Result |
|---|---|
| Precision | Pending evaluation |
| Recall | Pending evaluation |
| mAP@0.5 | Pending evaluation |
| mAP@0.5:0.95 | Pending evaluation |
| Average inference time | Pending evaluation |
| Per-class performance | Pending evaluation |

The final report will include the evaluation configuration, hardware used, per-class results, and examples of correct and incorrect predictions.

## 14. Responsible AI and Limitations

The system has several limitations that must be considered:

- **Detection errors:** The model may miss road damage or incorrectly identify road features as damage.
- **Dataset generalisation:** Performance on RDD2022 images may not represent performance on Malaysian roads or other unseen environments.
- **Class imbalance:** Differences in the number of examples per class may affect detection performance.
- **Image quality:** Lighting, shadows, weather, camera angle, image resolution, and occlusion may influence predictions.
- **Privacy:** Images may contain vehicle registration plates, faces, or other identifying information. Images should be handled responsibly and anonymised where appropriate.
- **Engineering limitations:** The model identifies visual patterns; it does not independently determine structural safety, damage severity, repair urgency, or engineering compliance.

The system should be treated as a decision-support prototype. Road maintenance decisions should involve qualified personnel and appropriate inspection procedures.

## 15. Future Improvements

Potential future improvements include:

- Collecting and evaluating road images from Malaysia.
- Improving detection performance for underrepresented classes.
- Comparing different YOLO model sizes or architectures.
- Testing model robustness under different lighting and weather conditions.
- Adding video-based road damage detection.
- Developing a map-based interface for recording inspection locations.
- Exploring integration with a mobile application or road inspection workflow.

These improvements are proposed future work and are not claimed as completed features.

## 16. References

1. Arya, D., et al. (2024). *RDD2022: A multi-national image dataset for automatic road damage detection*. Geoscience Data Journal, 11(4), 846–862. https://doi.org/10.1002/gdj3.260
2. Zeng, X., & Zhong, Z. (2024). *YOLOv8-PD: An improved road damage detection algorithm based on YOLOv8n model*. Scientific Reports. https://doi.org/10.1038/s41598-024-62933-z
3. Li, et al. (2024). *RDD-YOLO: Road Damage Detection Algorithm Based on Improved You Only Look Once Version 8*. Applied Sciences, 14(8), 3360. https://doi.org/10.3390/app14083360
4. Ultralytics. *YOLO Performance Metrics*. https://docs.ultralytics.com/guides/yolo-performance-metrics/
5. Sekilab. *RoadDamageDetector — RDD2022 dataset repository*. https://github.com/sekilab/RoadDamageDetector

Full bibliographic details should be verified against the original publications before final academic submission.

## 17. Project Status

**Current status:** Project planning and documentation.

The implementation, model training, quantitative evaluation, and application testing will be documented as they are completed. Reported results will be based on actual experiments rather than assumed performance.

