# Blood Cell Classification and Martian Terrain Segmentation

Welcome to the repository showcasing two distinct deep learning projects, focusing on:
1. Classifying blood cells into multiple categories.  
2. Segmenting Martian terrain into various semantic classes.  

Each project addresses unique challenges and employs tailored methodologies to achieve optimal results.

---

## Project 1: Blood Cell Classification

### **Overview**
The goal of this project was to classify images of blood cells into 8 distinct classes, each representing a specific cell state. The dataset presented challenges such as class imbalance, variations in image quality, and limited resolution (96x96 pixels). A robust pipeline was developed to preprocess the data and train models capable of accurately predicting cell types.

### **Methodology**
1. **Dataset Preprocessing:**  
   - Illumination correction and contrast enhancement to improve image clarity.  
   - Cell segmentation to isolate relevant features.  
   - Data augmentation (random flips, rotations, etc.) to increase diversity.

2. **Model Development:**  
   - A simple CNN served as the baseline but exhibited overfitting.  
   - Transfer learning approaches with architectures like ConvNeXt-Base and ResNet50V2 were explored.  
   - EfficientNetV2B0, optimized for small images, was selected as the final model after extensive hyperparameter tuning.

3. **Model Training and Optimization:**  
   - Early stopping and dropout layers were applied to combat overfitting.  
   - Class weights were used to address imbalance in the dataset.

### **Results**
- Data cleaning reduced the dataset from 13,759 to 10,530 images by removing duplicates and outliers.
- Model performance comparison:  
  - CNN baseline: 28% accuracy (test).  
  - ConvNeXt-Base: 38% accuracy (test).  
  - ResNet50V2: 77% accuracy (test).  
  - **EfficientNetV2B0 (final model): 87% accuracy (test).**

### **Key Takeaways**
- Effective preprocessing and augmentation techniques significantly enhanced model generalization.  
- EfficientNetV2B0 excelled in handling low-resolution images.  
- Future improvements could leverage ensemble learning and higher-resolution datasets.

---

## Project 2: Martian Terrain Semantic Segmentation

### **Overview**
This project focused on pixel-level segmentation of Martian terrain into 5 classes: background, soil, bedrock, sand, and large rocks. The dataset included grayscale images of size 64x128 and posed challenges such as extreme class imbalance (0.13% for the “large rocks” class) and limited resolution.

### **Methodology**
1. **Dataset Preprocessing:**  
   - Cleaning reduced the dataset to 2,505 labeled images by removing 110 outliers.  
   - Comprehensive augmentation (rotations, flips, brightness adjustments, Gaussian noise, etc.) to balance underrepresented classes.

2. **Model Development:**  
   - A basic U-Net architecture served as the baseline.  
   - Enhancements included supervision at intermediate layers, attention mechanisms, and the integration of transformer blocks.  
   - A specialized “small object” U-Net was designed to capture fine-grained details for small classes.

3. **Training Strategy:**  
   - Composite loss functions (Dice Loss, Focal Loss, Boundary Loss, and Cross-Entropy) were utilized to handle class imbalance and improve edge precision.  
   - Early stopping and model checkpointing ensured optimal training.

4. **Ensemble Learning:**  
   - Weighted averaging of predictions from complementary models improved overall performance.  
   - Final ensemble included a transformer U-Net, augmented U-Net, and a small object U-Net.

### **Results**
- Individual models achieved comparable validation mIoU scores (0.44 to 0.49).  
- The ensemble model delivered the best performance: **test mIoU of 0.51698.**

### **Key Takeaways**
- Ensemble learning was critical to achieving robust performance.  
- Preprocessing and augmentation techniques ensured better data quality and model generalization.  
- Future work could explore higher-resolution data, dynamic ensemble strategies, and multi-modal inputs.

---

## Repository Structure
- **`Challenge1/`**: Contains code, data preprocessing scripts, and trained models for the blood cell classification project.
- **`Challenge2/`**: Includes scripts for data cleaning, model development, and ensemble learning for the segmentation task.
- **`Labs/`**: Contains the work realized in labs session.
---

