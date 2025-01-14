# Dog Breed Classification with Fine-Grained Image Recognition

## Overview  
This project focuses on classifying dog breeds using fine-grained image classification techniques. With 120 dog breeds and significant inter-class similarities, this task presents a challenging problem for machine learning models.  

Our models and inference pipeline have been developed to tackle this problem efficiently and reliably. The dataset used is the **Stanford Dogs Dataset**, and additional synthetic data generated using **GANs (Generative Adversarial Networks)** has been incorporated to enhance training.

---

## Problem Statement  
Identifying dog breeds can be challenging for the average person due to the vast number of breeds and similarities between them. This project trains machine learning models for accurate and efficient dog breed classification. Fine-grained classification tasks like this can help expand our understanding of similar challenges in other domains.

---

## Dataset Details  
- **Source**: Stanford Dogs Dataset (Khosla et al., 2011)  
- **Classes**: 120 dog breeds  
- **Images**: 20,580 images (~150 per class)  
- **Annotations**: Bounding boxes and class labels  

We also augmented the dataset using **BigGAN 256**, generating 30 additional images per class to enhance performance.

---

## Models and Results  
We implemented and compared the following models:  
1. **ResNet-50**  
2. **MobileNetV2**  
3. **Vision Transformer (ViT)**  
4. **Ensemble Model** (Combination of ResNet-50, MobileNetV2, and ViT)  

### Testing Set Accuracies  
| Model              | Unbounded | Bounded | GAN+Unbounded |  
|--------------------|-----------|---------|---------------|  
| ResNet-50          | 81.29%    | 81.97%  | 81.63%        |  
| MobileNetV2        | 72.40%    | 74.10%  | 75.36%        |  
| Vision Transformer | 86.97%    | 87.85%  | 87.02%        |  
| Ensemble           | N/A       | 84.45%  | N/A           |  

ViT achieved the best performance across all cases, demonstrating its ability to generalize fine-grained features effectively.

---

## Experimental Setup  
1. **Data Split**: 70% Training, 20% Validation, 10% Testing  
2. **Data Preprocessing**:  
   - Images resized to 224x224 pixels  
   - Pixel values normalized by dividing by 255  
3. **Augmentations**:  
   - **Bounding Boxes**: Used bounding box annotations to focus on the dog regions.  
   - **GANs**: Synthetic images were merged with the original dataset.  

### Hyperparameters  
- Optimizer: Adam  
- Learning Rates:  
  - ViT: `1e-5`  
  - ResNet-50, MobileNetV2: `1e-4`  
- Batch Sizes:  
  - ResNet-50: 128  
  - Others: 32  

---

## Observations  
- ViT outperformed all baseline models, achieving the highest test accuracy.  
- Overfitting was observed across all models, requiring further exploration for generalization.  
- Ensemble models showed limited improvement compared to individual models like ViT.  
- Classes with high inter-class similarity, such as Staffordshire Bull Terrier vs. American Staffordshire Terrier, remain challenging for all models.

---

## Project Report
[View the Project Report](./DL_Project_Final.pdf)

## How to Use  
### Clone the Repository  
```bash
git clone https://github.com/<your-username>/dog-breed-classification.git
cd dog-breed-classification
