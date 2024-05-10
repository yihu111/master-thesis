# master-thesis
This repository contains the code for the project "Vessel Segmentation in Medical Imaging: A Comparative Study of Deep Learning Methods and Temporal Analysis
of Chorioallantoic Membrane Images" for my master's thesis of the MSc Business Administration and Data Science programme at Copenhagen Business School (CBS).

# Abstract
Studying vessel development is a crucial research area in medicine due to its potential to enhance patient diagnosis and treatment. Deep learning methods can automate the extraction of segmentation masks from vessel images contributing to an automated process flow. Consequently, this thesis addresses the following research question "**_How can image segmentation methods be applied to vessel images and what are potential applications?_**". While deep learning has demonstrated outstanding performances in the field of vessel segmentation, comparison of different deep learning models is required to determine the most suitable methods for this particular task. This thesis compares three models, namely U-Net, SAM, and MedSAM. These models are trained on a combined dataset of retinal fundus images and subsequently evaluated. The U-Net model performs significantly better than the other models with a Dice score of 0.8401. This model is then applied to analyze vessel development in the Chorioallantoic Membrane (CAM) of chicken embryos. The predicted masks are quantified across several metrics including total vessel area, total vessel length, mean vessel thickness, and number of vessel branching points. The analysis on CAM images from day 11 and day 13 are conducted using t-tests and confirmed developmental changes in the chicken embryo between day 11 and day 13 across all metrics. These findings highlight the importance of deep learning in research areas that heavily rely on the quantification of vessel images. In the area of CAM cancer research, where commonly the development of normal and tumor induced chicken embryos are compared, the methods demonstrated in this thesis can be leveraged for automated quantification.

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

# Code Structure
```
.
├── 01_preprocessing
│   ├── exploratory_data_analysis.ipynb
│   └── indexing.ipynb
│   └── train_test_split.ipynb
├── 02_unet
│   ├── unet_dataset.ipynb
│   └── unet_model.ipynb
│   └── unet_training.ipynb
├── 03_sam_medsam
│   ├── sam_dataset.ipynb
│   └── sam_prompt_functions.ipynb
│   └── sam_training.ipynb
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
│   └── indexing.ipynb
│   └── train_test_split.ipynb
├── 02_unet
│   ├── unet_dataset.ipynb
│   └── unet_model.ipynb
│   └── unet_training.ipynb
├── 03_sam_medsam
│   ├── sam_dataset.ipynb
│   └── sam_prompt_functions.ipynb
│   └── sam_training.ipynb
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
