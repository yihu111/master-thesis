# master-thesis
This repository contains the code for the project "**Blood Vessel Segmentation: A Comparative Study of Deep Learning Methods and Analysis
of Chorioallantoic Membrane Images**" for my master's thesis of the MSc Business Administration and Data Science programme at Copenhagen Business School (CBS).

Link to the dataset and all trained models: https://drive.google.com/drive/folders/1JjC2dDPVhb58oBZ3RjcZVwKTYX0dD95c?usp=drive_link 

# Abstract
Studying blood vessel development is a crucial research area in medicine due to its potential to enhance patient diagnosis and treatment. Deep learning methods can automate the extraction of segmentation masks from blood vessel images contributing to an automated process flow. Consequently, this thesis addresses the research question "**How can deep learning models be applied to blood vessel images and what are the potential applications?**". While deep learning has demonstrated outstanding performances in the field of blood vessel segmentation, comparison of different deep learning models is required to determine the most suitable method for this particular task. This thesis compares three models, namely U-Net, SAM, and MedSAM. These models are trained on a combined dataset of retinal fundus images and subsequently evaluated. The U-Net model performs significantly better than the other models with a Dice score of 0.8401. This model is then applied to analyze blood vessel development in the Chorioallantoic Membrane (CAM) of chicken embryos. The predicted masks are quantified across several metrics including total vessel area, total vessel length, mean vessel thickness, and number of vessel branching points. The analysis on CAM images from embryonic day 11 and day 13 are conducted using t-tests and confirmed an increased extent of blood vessels across all metrics. These findings highlight the suitability of deep learning in research areas that heavily rely on the quantification of blood vessel images. In the area of CAM cancer research, where commonly the normal and tumor induced developments are compared, the methods can save time and financial resources and improve research outcomes as the quantification process is automated and based on reliable and robust models.

# Overview of Methodology

![pipeline](https://github.com/yihu111/master-thesis/assets/112397235/d16df2e9-01b7-4a14-8337-d5cf3a36791c)

# Data Sources
To understand the best for vessel segmentation, this project combines multiple retinal fundus images datasets:
- DRIVE (Staal et al., 2004)
- CHASE-DB1 (Owen et al., 2009)
- HRF (Odstrcilik et al., 2013)
- FIVES (Jin et al., 2022)

Before usage, the images are tested for their quality. For example, blurry images were removed. The preprocessing pipeline, including image graying, image normalization, CLAHE, and gamma correction, further improved segmentation performance. For SAM and MedSAM, the image graying step was skipped but the other steps included.

Overview of the preprocessing steps inspired by Liu et al. (2023):

![preprocessing_pipeline](https://github.com/yihu111/master-thesis/assets/112397235/18fbfc42-b026-4e35-ac4a-c6b30b893efb)

The follow-up analysis of CAM image from day 11 and day 13 (25 images each) are manually created in collaboration with the University of Bonn:

<img width="592" alt="cam_imaging" src="https://github.com/yihu111/master-thesis/assets/112397235/678610cb-8749-42aa-8cde-77ffd3c2dd84">

# Results and Evaluation
The U-Net demonstrated to be the most suitable model based on the evaluation metrics whereas the Dice similarity coefficient is considered the main evaluation metric:

Model | Accuracy | Precision | Recall | Dice
|-----|----------|-----------|--------|-----|
| U-Net | 0.9759 | 0.8571 | 0.8398 | 0.8451
| SAM | 0.9665 | 0.8091 | 0.7575 | 0.7806
| MedSAM | 0.9657 | 0.8016 | 0.7546 | 0.7758

Also. the U-Net predictions show the best visual result:

![error_analysis](https://github.com/yihu111/master-thesis/assets/112397235/0535e364-ecf9-4420-baa7-0b613828aa53)

The follow-up analysis confirmed that the CAM images have developmental changes from day 11 and day 13 across all quantification metrics. The following quantification metrics were included:
- Total Vessel Area
- Total Vessel Length
- Mean Vessel Thickness
- Number of Vessel Branching Points

Visual example of the quantification process based on U-Net segmentation prediction:

![quantification](https://github.com/yihu111/master-thesis/assets/112397235/44583192-5024-4cf2-a4aa-7307e91b1200)

# Code Structure

The folders are structured as follows:

```
.
├── 01_preprocessing
│   ├── exploratory_data_analysis.ipynb
│   |── indexing.ipynb
│   └── train_test_split.ipynb
├── 02_unet
│   ├── unet_dataset.ipynb
│   |── unet_model.ipynb
│   └── unet_training.ipynb
├── 03_sam_medsam
│   ├── sam_dataset.ipynb
│   |── sam_prompt_functions.ipynb
│   |── sam_training.ipynb
│   └── medsam_training.ipynb
├── 04_evaluation
│   ├── evaluation_utils.ipynb
│   └── evaluation.ipynb
├── 05_analysis
│   ├── fine_tune_and_save_masks.ipynb
│   └── quantification.ipynb
├── gitattributes
└── README.md
```

# Acknowledgments/References
I would like to thank Nicolai Frost Jacobsen for supervising my thesis. Also, I would like to thank the University of Bonn for their collaboration, in particular Prof. Dr. Stefanie Kürten, Prof. Dr. Ruijin Huang, and Longfei Cheng. 

# Contributors
Yile Huang
