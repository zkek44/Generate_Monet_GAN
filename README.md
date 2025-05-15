# Generate_Monet_GAN

Monet Style Transfer with CycleGAN

This project is a solution to the Kaggle "I'm Something of a Painter Myself" competition. The objective is to build a Generative Adversarial Network (GAN) model that transforms real-world photos into Monet-style paintings using unpaired image-to-image translation.

Project Overview:
Claude Monet is known for his unique impressionist style. In this project, we train a CycleGAN model to apply Monet’s artistic style to real-world photos without using paired training data.

Goal: 
Generate 7,000–10,000 Monet-style images from photographs and submit a .zip file of these images for evaluation.

Challenge Type

Domain: Computer Vision

Task: Unsupervised Image-to-Image Translation

Model: CycleGAN (with 2 Generators and 2 Discriminators)

Evaluation Metric: MiFID (Memorization-informed Fréchet Inception Distance)

Dataset:
Directory	Description
monet_jpg	300 Monet paintings (256x256 JPEG)
photo_jpg	7,028 real-world photos (256x256 JPEG)
monet_tfrec & photo_tfrec	Same as above in TFRecord format

All images are RGB with shape (256, 256, 3).

Exploratory Data Analysis (EDA):
Compared visual differences between Monet paintings and photos

Verified uniform image shape and format

Observed domain imbalance: 300 Monet paintings vs. 7,000+ photos

Augmentation applied to Monet images to balance training

Model Architecture:
We used a CycleGAN consisting of:

Generator G (Photo → Monet)

Generator F (Monet → Photo)

Discriminator X (Monet Discriminator)

Discriminator Y (Photo Discriminator)

Key Features:

ResNet-based generator with 9 residual blocks

PatchGAN discriminators

Losses: Adversarial, Cycle Consistency, Identity Loss

Training Setup:
Framework: TensorFlow 2.x (Kaggle Kernel)

Hardware: GPU (via Kaggle's free accelerator)

Input scaling: Pixel values normalized to [-1, 1]

Training: 40+ epochs on shuffled, augmented datasets

Submission:
7,000–10,000 Monet-style images generated using the trained G generator

Images written to /kaggle/working/images.zip

Submitted to Kaggle for MiFID evaluation

Results and Analysis:
Image quality improved significantly after ~25 epochs

Identity loss helped preserve color palette

Augmenting the Monet dataset helped reduce mode collapse

MiFID scores improved with tuned hyperparameters and longer training

Key Takeaways:
CycleGAN works well for unpaired image translation tasks

Training on GPU is essential — CPU is too slow

Direct-to-zip image writing is a great way to avoid Kaggle’s disk quota issues

