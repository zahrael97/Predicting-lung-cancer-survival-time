# Predicting lung cancer survival time
predict the survival time of a patient (remaining days to live) from one three-dimensional CT scan (grayscale image) and a set of pre-extracted quantitative imaging features, as well as clinical data.
# Goal
The challenge proposed by Owkin is a supervised survival prediction problem: predict the survival time of a patient (remaining days to live) from one three-dimensional CT scan (grayscale image) and a set of pre-extracted quantitative imaging features, as well as clinical data. To each patient corresponds one CT scan, and one binary segmentation mask. The segmentation mask is a binary volume of the same size as the CT scan, except that it is composed of zeroes everywhere there is no tumour, and 1 otherwise. This segmentation mask was built based on annotations from radiologists, who delineated by hand the tumor(s). Refer to the data section for further details of the data. The CT scans and the associated segmentation masks are subsets of two public datasets:
NSCLC Radiomics (subset of 285 patients)
NSCLC RadioGenomics(subset of 141 patients)
