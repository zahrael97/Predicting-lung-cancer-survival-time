# Predicting-lung-cancer-survival-time
predict the survival time of a patient (remaining days to live) from one three-dimensional CT scan (grayscale image) and a set of pre-extracted quantitative imaging features, as well as clinical data.
# Context
Owkin mission


Owkin works to improve patient treatment, drug discovery and augment medical research by developing machine-learning models on real-world clinical data. On this clinical data, our company build machine learning algorithms to predict toxicity, resistance, and sensitivity to treatments outcomes and diseases evolution. Owkin provides cutting edge expertise in machine learning technologies, specifically deep learning on histopathology and radiology images, as well as multimodal data integration with omics and clinical data. We believe that by combining large amounts of medical data with advanced machine learning algorithms, we can better understand diseases and heterogeneity of treatment effects. At the heart of the medicine of the future, OWKIN collaborates with pharmaceutical companies (Roche, Novartis, Amgen, Ipsen) and developed partnerships with hospitals and first-rank academic research laboratories, such as Institut Curie, Inserm, or Centre Léon Berard. Thanks to those outstanding partnerships, Owkin was able to recently publish breakthrough discovery in ​Nature Medicine​.

Clinical context


The goal of this challenge is to develop new methods to predict survival time of patients diagnosed with lung cancer, based 3-dimensional radiology images (Computed Tomography scanner). Radiology data refers to various kinds of imaging modalities such as MRI, Echography or CT scans. In a clinical context, such modalities are very valuable because, unlike biopsies, those images are non invasive​: the pathology and the patient’s body remain untouched. Furthermore, those are much cheaper to operate and can, hence, be acquired at multiple timepoints and be used to track the disease through time. CT scan is a widely spread and popular exam in oncology: it reflects the density of the tissues of the human body. It is, then, adapted to the study of lung cancer because lungs are mostly filled with air (low density) while tumors are made of dense tissues.
# Goal
The challenge proposed by Owkin is a supervised survival prediction problem: predict the survival time of a patient (remaining days to live) from one three-dimensional CT scan (grayscale image) and a set of pre-extracted quantitative imaging features, as well as clinical data. To each patient corresponds one CT scan, and one binary segmentation mask. The segmentation mask is a binary volume of the same size as the CT scan, except that it is composed of zeroes everywhere there is no tumour, and 1 otherwise. This segmentation mask was built based on annotations from radiologists, who delineated by hand the tumor(s). Refer to the data section for further details of the data. The CT scans and the associated segmentation masks are subsets of two public datasets:
NSCLC Radiomics (subset of 285 patients)
NSCLC RadioGenomics(subset of 141 patients)


Both datasets can be found on The Cancer Imaging Archive. The endpoint of this challenge is the survival time in days. To this end, both training and validation contain for each patient, the time to event (days), as well as the censorship. Censorship indicates whether the event (death) was observed or whether the patient escaped the study: this can happen when the patient’s track was lost, or if the patient died of causes not related to the disease.
# Data
Labels
Our problem is a supervised one as we have survival time (endpoint) over the whole training set. Labels for the train and valid datasets are in the file train/output.csv : survival time in days and censorship (`1=death observed`, `0=escaped from study`).
Inputs
For each patient, we provided four inputs:

Images (one scan and one mask per patient): we furnish crops of both the scan and the mask, centered around the tumor region. Those crops are of fixed 92^3 mm^3 size.
Radiomics features (an ensemble of 53 quantitative features per patient, extracted from the scan).
Clinical data
Images
Images are stored in the image folder, following the format: `[patient_id].npz`. Each .npz file contains both scan and mask (3-d arrays), accessible by :


import numpy as np
archive = np.load('patient_000.npz')
scan = archive['scan']
mask = archive['mask']
# scan.shape equals mask.shape


Radiomics features
Radiomics features are stored at the root of the dataset folder in the file Radiomic_features.csv , where each row contains the 53 feature values, for each patient. Those features were extracted in order to ease the task for those whose time is limited. However, several studies point out that such hand-defined features can be highly biased and suboptimal for various tasks.
The complete list of extracted features can be found in the zip file under the name appendix.txt. Those features were extracted using the pyradiomics python library which follows international standards on those features’ definition.

Clinical data
Clinical data contains basic meta-information for each patient. Namely, each patient is described by its age, the source data it originates from, and the TNM staging of the cancer. TNM staging is a known prognostic biomarker for survival (see the Baseline document for further description).
Outputs
Outputs must be positive floats which represent the predicted survival time in days. The file `train/output.csv` simply contains two columns, indexed by patient id: one column represents the observed time to event, while the other represents the censorship (1=event observed is death, 0=event observed is the last time patient was seen alive, the patient then escaped the study).


import pandas as pd
train_output = pd.read_csv( 'train/output.csv', index_col=0)
p0 = train_output.loc[202]
print(p0.Event) # prints 1 or 0
print(p0.SurvivalTime)
# prints time to event (time to death or time to last known alive) in days


Solutions file on test input data submitted by participants shall follow the same format as the train output file with a nan-filled event column . This empty column is mandatory since input target and output predictions should follow the exact same format. Both datasets were mixed and shuffled before being split into three subsets:

Training set (70%)
Public test set (15%)
Private test set (15%)

In total the training set contains
Train set
Test set 1
(public)
Test set 2
(private)
Patients from dataset 1	
199
42
43
Patients from dataset 2	
101
20
20


We would like to highlight the fact that 63 patients is a really small test set and therefore variability between the two test sets can be expected, especially if you are overfitting the first test set by using a lot of submissions. However, the small size of our datasets is a real life problem that we have to deal with and being able to overcome this barrier is a crucial point. A second very important source of poor transfer of performance between test sets is the disparity between centers. It would be wise to take into account that two centers, potentially really heterogenous, are present in the challenge.
