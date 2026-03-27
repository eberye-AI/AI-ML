

Manufacturing Defect Detection VQA - Visual Question Answering for Quality Control

===================================================================================

A multimodal deep learning system that answers natural language questions about 

manufacturing product images for automated defect detection and classification.



Key Features:

\- Multi-question capability on single image (defect?, product?, defect type?)

\- Smart defect categorization (50+ types → 18 semantic categories)

\- ResNet18 + LSTM multimodal fusion architecture

\- Trained on MVTec Anomaly Detection dataset (5,354 images, 15 products)

\- Handles class imbalance with stratified splitting and per-class evaluation

\- Strong data augmentation for robust generalization



Question Types Supported:

&nbsp; 1. "Is there a defect?" → Binary classification (yes/no)

&nbsp; 2. "What product is this?" → Product identification (15 categories)

&nbsp; 3. "What type of defect?" → Defect classification (18 types)



Architecture:

\- Vision Encoder: ResNet18 (pretrained on ImageNet) → 512-D features

\- Language Encoder: LSTM with word embeddings → 256-D features

\- Multimodal Fusion: Concatenation + 2-layer MLP with dropout

\- Output: 36 unique answer classes (yes, no, product names, defect types)



Dataset Details:

\- MVTec Anomaly Detection benchmark

\- 5,354 total images (3,629 defect, 1,725 good)

\- 15 product categories (bottle, cable, carpet, etc.)

\- 50+ original defect types reduced to 18 via intelligent grouping

\- 16,062 Q\&A pairs (3 questions per image)

\- 80/20 stratified train-test split (12,850 / 3,212)



Training Configuration:

\- Epochs: 30 (with early stopping)

\- Batch Size: 32

\- Optimizer: AdamW (lr=0.0001, weight\_decay=1e-4)

\- Scheduler: ReduceLROnPlateau

\- Augmentation: Rotation, flip, color jitter (training only)

\- Regularization: Dropout (0.3-0.5), weight decay, gradient clipping



Performance Results:

\- Best Validation Accuracy: 86.09%

\- Training Accuracy: 83.72%

\- Overfitting Gap: -1.11% (excellent generalization!)

\- Macro F1: 0.85 | Weighted F1: 0.87

\- Class Imbalance Ratio: 11.4x (handled via stratification)



Key Innovation:

Smart defect categorization function that maps similar defects to semantic 

categories (e.g., 'broken\_large' + 'broken\_small' → 'broken'), increasing 

samples per class from 20-30 to 100+ and improving model accuracy significantly.



Technical Stack:

\- PyTorch 2.0+ (Deep learning framework)

\- torchvision (Pretrained models and transforms)

\- PIL, OpenCV (Image processing)

\- scikit-learn (Metrics and evaluation)

\- Gradio (Interactive web interface)



