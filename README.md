# __ALFICC - Active Learning For Improved landCover Classification__

This repository is intended to share some results and materials from my Master's dissertation project. These deliverables are intended for open access. Everyone is free to use them for research purposes, __as long as this work and the resources' origin are properly cited__.

## __Introduction__

The goal was to use _Sentinel-2 Surface Reflectance_ geospatial data in order to identify cashew orchards with Machine Learning (ML) tools across a region of interest (ROI) comprised of two parts: the country of Guinea-Bissau, and the neighboring region of the Republic of Guinea up to the _Kogon_ river. Active Learning techniques were employed to develop an optimized training dataset from samples scattered across the ROI.

<p align="center">
  <img src="Images/roi_image.png" alt="drawing" width="600"/>
</p>

The labels were acquired for the year of 2021. For more details about the project, the data and application, the full dissertation can be found in the [UPorto open repository](https://hdl.handle.net/10216/164196)

## Contents

The contents shared in this repository regard the following:
* The two datasets of labeled samples that were created during the project's execution.
* Cashew land cover maps obtained with ML model predictions.

## Datasets

Two new datasets of labeled pixels scattered across the ROI were created during the project's execution. Namely:
* __Random Sampling dataset:__ corresponds to $4498$ samples randomly selected in the ROI.
* __Margin Sampling dataset:__ $1816$ points selected by the margin sampling heuristic. This dataset shows a smaller geographical distribution and sample diversity than the Random Sampling one, but demonstrated its usefulness for ML purposes.

The labeling process included eight different classes, from 1 to 8: Closed Forest, Open Forest, Mangrove, Savanna (sparse vegetation), Cashew, Non-Forest, Water, and Non-Cashew. We note that class 8 - Non-Cashew contains pixels that are evidently not cashew orchards, but either contain a mixture of the other six classes (for example, Savanna and Non-Forest), or correspond to samples that could not be classified as any of the aforementioned categories. Therefore, class 8 samples are very useful for a binary classification setting: when trying to simply distinguish between cashew and non-cashew classes, they can be part of a broader Non-Cashew class, which also includes Forest, Mangrove, and so on. However, in other scenarios, these samples should be discarded from further consideration.

The .csv files include information about the pixels' coordinates __in the EPSG:4326 projection__ and category following the aforementioned system. The pixels were acquired in $3 \times 3$ polygons or patches, with each patch being assigned a different number, which is represented in column _polygonID_ - this can be important to analyze spatial distribution and correlation of the acquired samples. Besides these, the first __67__ columns of _randomsampling.csv_ and _marginsampling.csv_ regard the training features that were considered for ML tasks. They correspond to a subset of a group of features formed by the spectral bands directly obtained from Sentinel-2 measurements, spatial features obtained with the GLCM method, and temporal CCDC coefficients. _normalizers.csv_ stores the min, max, mean and std values for each of the 67 features, for feature normalization purposes.

## Programming requirements

Scripts have been developed using __JavaScript__ (in Google Earth Engine's code editor) and __Python__.

* For the __Python__ scripts, the following packages were used:
  * numpy
  * pandas
  * sklearn
  * geopandas
  * rasterio
  * rioxarray
____

* Author: Miguel Ribeiro Pereira, MSc, Faculty of Sciences, University of Porto
* Supervisors: João Pedro Pedroso, INESC TEC, Faculty of Sciences, University of Porto
* Co-Supervisor: Sofia Cardoso Pereira, PhD, Faculty of Engineering, University of Porto
