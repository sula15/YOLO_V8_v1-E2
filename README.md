# Cutlet & Dhal Wade Detection - YOLO Training Task

## Dataset Summary
- **Total Images**: 35
- **Classes**: 3 (Cutlet, Dhal Wade, Objects)
- **Split**: Train: 20, Valid: 10, Test: 5
- **Format**: YOLO format
- **Annotation Tool**: Roboflow

## Approach & Methodology

This project represents my first experience with image annotation for object detection. The workflow followed was:

1. **Image Annotation**: Used Roboflow platform to annotate all images with bounding boxes
2. **Dataset Export**: Exported annotations in YOLO format from Roboflow
3. **Local Development**: Downloaded the dataset and trained the model locally using YOLOv8
4. **Model Training**: Utilized pretrained YOLOv8n weights and fine-tuned on the custom dataset

As this is my first annotation project, there is room for improvement in annotation consistency and accuracy.

## Training Configuration
- **Model**: YOLOv8n
- **Epochs**: 50
- **Image Size**: 640x640
- **Batch Size**: 16
- **Device**: CPU

## Results
- **mAP50**: 0.6613
- **mAP50-95**: 0.3222
- **Precision**: 0.8194
- **Recall**: 0.3490

## Inference Results
- 12_jpg.rf.fe5822c1cd816ff92cacc33d36978377.jpg: 1 objects detected
- 2_jpg.rf.19ad3c49c83b8e59f030d90568b6166b.jpg: 2 objects detected
- 5686_jpg.rf.4b0a14a8a7400a9b4af7a31a5f01bf08.jpg: 1 objects detected
- 5731_jpeg_jpg.rf.6858ccf13cb0e0ae016bae31f2fd1cca.jpg: 0 objects detected
- cutlet26_jpg.rf.b0848a0f6a40131411796786a4eecc82.jpg: 1 objects detected

## Limitations & Difficulties

1. **First-Time Annotation Experience**
   - This is my first time annotating images for object detection
   - Annotation quality may be inconsistent across images
   - Learning curve in determining optimal bounding box boundaries
   - Potential for subjective interpretation of object boundaries

2. **Small Dataset (30 images)**
   - Risk of overfitting
   - Limited generalization capability

3. **Limited Diversity**
   - Similar backgrounds and lighting
   - May not work well on different settings

4. **Annotation Challenges**
   - Cutlet vs Dhal Wade similarity makes classification subjective
   - Difficulty in maintaining consistent bounding box standards
   - Small or partially visible objects harder to annotate accurately

5. **CPU Training**
   - Slow training (15-30 min)
   - Cannot experiment with larger models

## Suggestions for Improvement

1. **Annotation Quality Enhancement**
   - Review and refine all annotations with more experience
   - Use multiple annotators and calculate inter-annotator agreement
   - Establish clear annotation guidelines before starting
   - Consider re-annotating with improved understanding of the task

2. **Data Augmentation**
   - Rotation, flipping, brightness adjustments
   - Mosaic augmentation

3. **Collect More Data**
   - Aim for 100-200 images per class
   - Diverse backgrounds, lighting, angles

4. **Refine Annotations**
   - Review consistency across all images
   - Consider merging/removing "objects" class if too vague

5. **Model Improvements**
   - Try YOLOv8s/m with GPU
   - Increase epochs to 100+
   - Hyperparameter tuning

6. **Use GPU**
   - Google Colab or cloud platforms
   - 5-10x faster training

## Conclusion
Successfully trained YOLOv8n model achieving mAP50 of 0.6613. This being my first annotation project, the main limitations are dataset size and potential annotation inconsistencies. With improved annotation skills, more diverse data, and GPU access, performance could improve significantly.

The complete workflow from Roboflow annotation to local training has been successfully demonstrated.

## File Structure
```
submission/
├── README.md
├── inference_outputs/ (5 images)
├── trained_model/best.pt
└── training_results/results.png
```

## Usage
```python
from ultralytics import YOLO
model = YOLO('trained_model/best.pt')
results = model.predict('image.jpg', conf=0.25)
```
