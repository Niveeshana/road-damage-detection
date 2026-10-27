AI-Based Road Damage Detection and Visualisation System Using Deep Learning

### 1. Overview of Related Work

Existing research has explored the use of deep learning and computer vision to detect road damage automatically. Researchers have developed road damage datasets and object detection models to identify defects such as cracks and potholes. The RDD2022 dataset provides a common resource for studying road damage detection, while several studies have investigated improvements to YOLO-based detection algorithms.

This section compares four relevant research sources and identifies a practical direction for the proposed project.

### 2. Comparison of Existing Research

| Research | Approach or contribution | Strengths | Limitations or considerations |
|---|---|---|---|
| Arya et al. (2024) — RDD2022 | Introduces a multinational road damage image dataset with annotated damage instances. | Provides a large dataset covering multiple countries and four relevant damage categories. | Dataset availability does not guarantee that a model trained on it will generalise to Malaysian road conditions. |
| Zeng and Zhong (2024) — YOLOv8-PD | Proposes an improved road damage detection algorithm based on YOLOv8n. | Investigates model modifications intended to improve road damage detection. | Results depend on the experimental dataset, training configuration, and evaluation procedure. |
| Li et al. (2024) — RDD-YOLO | Proposes an improved YOLOv8-based algorithm for road damage detection. | Provides an example of evaluating model accuracy and detection performance using established metrics. | A specialised architecture may require additional implementation and computational effort. |
| OBC-YOLOv8 study | Investigates an improved YOLOv8-based road damage detection model. | Demonstrates the continued investigation of detection accuracy and computational efficiency. | Results from a particular dataset subset and experimental configuration may not transfer directly to other environments. |

**References for verification**

1. Arya et al. (2024): https://doi.org/10.1002/gdj3.260
2. Zeng and Zhong (2024): https://doi.org/10.1038/s41598-024-62933-z
3. Li et al. (2024): https://doi.org/10.3390/app14083360
4. OBC-YOLOv8 study: https://pmc.ncbi.nlm.nih.gov/articles/PMC11784705/

### 3. Critical Analysis of Existing Research

The reviewed studies demonstrate that automated road damage detection using deep learning is an established research area. The RDD2022 dataset provides labelled images for model development, while YOLO-based studies investigate ways to improve detection accuracy and computational efficiency.

However, the performance reported in one study cannot automatically be assumed for another implementation. Differences in data selection, train-validation-test splits, image preprocessing, model architecture, training settings, and hardware may influence the results.

Furthermore, an object detection model's overall performance does not necessarily indicate how well it detects every damage category. For example, a model may detect potholes effectively but miss some thin cracks. Therefore, evaluation should include category-wise performance, not only an overall score.

Another consideration is usability. Model evaluation results are important for researchers, but an operational prototype also needs an interface through which users can submit images and interpret the predictions. Presenting bounding boxes, category labels, confidence scores, and detection counts can make model outputs easier to inspect.

Finally, results obtained from multinational public datasets do not establish that a model will perform reliably under Malaysian road conditions. Additional local testing would be necessary to investigate that question.

### 4. Identified Research Gap

The literature indicates that YOLO-based road damage detection, four-class detection, and performance evaluation have already been investigated in previous studies. Therefore, this project does not claim that these techniques are new.

Instead, the project addresses a practical implementation objective: integrating a four-class road damage detection model into an accessible web application and presenting its outputs alongside a transparent evaluation of model performance.

The proposed implementation will combine:

1. **Four-class detection:** Identify longitudinal cracks (D00), transverse cracks (D10), alligator cracks (D20), and potholes (D40).
2. **Visualisation:** Display predicted bounding boxes, damage categories, and confidence scores on uploaded road images.
3. **Category-wise summaries:** Present the number of detections for each predicted damage category.
4. **Performance evaluation:** Report precision, recall, mAP@0.5, mAP@0.5:0.95, and inference time using a held-out test set.
5. **Accessible interface:** Allow users to upload road images and download the annotated results through a Streamlit application.
6. **Limitations reporting:** Document false positives, missed detections, and the limitations of applying a model trained on public data to Malaysian road conditions.

The contribution will be demonstrated through the implementation and evaluation of the complete system. Whether it offers practical advantages over existing systems will depend on the experimental results and any comparison that can be conducted fairly.

### 5. Proposed Research Contribution

The project is expected to contribute a functional prototype that combines deep learning-based road damage detection with visualisation and performance reporting.

The system will be developed using the following technologies:

- **Dataset:** RDD2022.
- **Deep learning framework:** Ultralytics YOLO.
- **Training environment:** Google Colab.
- **Programming language:** Python.
- **Web application framework:** Streamlit.
- **Development environment:** Visual Studio Code.
- **Image processing:** OpenCV.

The model will be fine-tuned using labelled training data, with validation data used for model selection. A separate test set will be retained for final evaluation to reduce the risk of reporting overly optimistic results.

The web application will accept an image, perform inference, and display the predicted damage locations and categories. The final report will include measured evaluation results and examples of successful and unsuccessful predictions.

### 6. Conclusion

Existing research provides a strong foundation for developing road damage detection systems using deep learning. The RDD2022 dataset and previous YOLO-based approaches offer relevant resources for the proposed implementation.

The main focus of this project is the integration of four-class detection, visualisation, and quantitative evaluation into a single web-based prototype. The project will also document the model's limitations and avoid treating automated predictions as definitive engineering assessments.

The claimed contribution will be evaluated through the completed prototype, measured results, and a clear comparison with relevant existing research.