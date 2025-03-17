# Brain-tumor-Segmentation

Brain Tumor Segmentation using U-Net:

This project focuses on brain tumor segmentation from MRI scans using Deep Learning (U-Net architecture). The model is trained using the Binary Cross Entropy (BCE) loss function, which performed better than the Dice Loss. The dataset was obtained from Kaggle, and preprocessing steps such as normalization, augmentation, and conversion to PyTorch tensors were applied.

Dataset:
 
The dataset used for this project is from Kaggle:

Brain Tumor MRI Dataset ((https://www.kaggle.com/datasets/mateuszbuda/lgg-mri-segmentation))

This dataset contains brain MR images together with manual FLAIR abnormality segmentation masks.
The images were obtained from The Cancer Imaging Archive (TCIA).
They correspond to 110 patients included in The Cancer Genome Atlas (TCGA) lower-grade glioma collection with at least fluid-attenuated inversion recovery (FLAIR) sequence and genomic cluster data available

Preprocessing Steps :

Before training the model, the following preprocessing steps were applied:

1️⃣ Resizing → Resized all images to 256x256 for uniform input.
2️⃣ Normalization → Scaled pixel values between [0, 1].
3️⃣ Augmentation → Applied transformations such as:

Random Flipping (Horizontal & Vertical)
Random Rotation (0° to 15°)
Random Zoom & Shift

Model: U-Net Architecture
The model used is U-Net, a powerful architecture for medical image segmentation.

🔹 U-Net Overview
U-Net is a Fully Convolutional Network (FCN) designed for segmentation tasks. It consists of:

Encoder (Contracting Path) → Extracts high-level features (Convolutions + Pooling).
Bottleneck → Captures global context.
Decoder (Expanding Path) → Upsamples & refines predictions using skip connections.
🔹 Model Architecture
Encoder 1	Conv2D	64	3x3	ReLU
Encoder 2	Conv2D	128	3x3	ReLU
Encoder 3	Conv2D	256	3x3	ReLU
Bottleneck	Conv2D	512	3x3	ReLU
Decoder 1	Conv2D	256	3x3	ReLU
Decoder 2	Conv2D	128	3x3	ReLU
Decoder 3	Conv2D	64	3x3	ReLU
Output	Conv2D	1	1x1	Sigmoid

Loss Function & Optimization
To train the model, we experimented with different loss functions:

🔹 Dice Loss (Not Effective)
Dice Loss was initially tested, but it did not provide good results.
It struggled with learning small tumor regions.
🔹 Binary Cross Entropy (BCE) Loss (Used)
BCE Loss was more effective for this task.
The final BCE Loss achieved:
Training Loss: 0.0310
Test Loss: 0.0334
BCE was optimized using the Adam optimizer
📊 Results
🔹 Performance Metrics

Training Loss	0.0310
Test Loss	0.0334

Best Model	U-Net + Adam + BCE loss
🔹 Visualization
The following MRI scan shows Ground Truth (Red) vs. Model Prediction (Green):

(Replace with actual image from results)

