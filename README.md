# Grass Segmentation
Use machine learning model to detect length of grass on roadside (short, medium, long)

## Dataset
- 5996 images with ground truth masks
![Dataset distribution]("class_combination_distribution.png")
- splitted into 8:1:1 training, validation and testing sets
![Splitting distribution]("split_distribution.png")
- Example of samples
![Sample images]("sample_images.png")

## Model 1: U-Net with MobileNetv2 encoder
- use class weight to overcome class imbalance 
{class 0: 0.19, class 1: 0.92, class 2: 1.33, class 3: 1.57}
- input size: (128,128,3)
- augmentation: random horizontal flip, vertical clip, brightness, contrast, saturation, hue value

![train history 1]("training_history_phase1.png")
![train history 2]("training_history_phase2.png")

### Evaluation
Metrics: Accuracy, IoU (Intersection Over Union), Weighted Sparse Categorical Cross Entropy
Test Loss           : 0.1019
Test Accuracy   : 0.9373
Test Mean IoU : 0.4523

 Per Class IoU:
 - background          : 0.9547
 - grass_short          : 0.4946
 - grass_medium    : 0.1898
 - grass_long           : 0.1698

![confusion matrix]("confusion_matrix.png")

![test pred]("test_predictions.png")
