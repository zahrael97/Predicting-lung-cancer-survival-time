# Predicting lung cancer survival time
predict the survival time of a patient (remaining days to live) from one three-dimensional CT scan (grayscale image) and a set of pre-extracted quantitative imaging features, as well as clinical data.
# Goal
The challenge proposed by Owkin is a supervised survival prediction problem: predict the survival time of a patient (remaining days to live) from one three-dimensional CT scan (grayscale image) and a set of pre-extracted quantitative imaging features, as well as clinical data. To each patient corresponds one CT scan, and one binary segmentation mask. The segmentation mask is a binary volume of the same size as the CT scan, except that it is composed of zeroes everywhere there is no tumour, and 1 otherwise. This segmentation mask was built based on annotations from radiologists, who delineated by hand the tumor(s). Refer to the data section for further details of the data. The CT scans and the associated segmentation masks are subsets of two public datasets:
NSCLC Radiomics (subset of 285 patients)
NSCLC RadioGenomics(subset of 141 patients)
# What I know about Survival Analysis ?
absolutly nothing ... As a beginner in Machine Learning This was super exciting Like How is it possible to predict the remaining living time :o, OKay let's Start by Wikipedia .
 ```  
 Survival analysis is a branch of statistics for analyzing the expected duration of time until one or more events happen, such as death in biological organisms and failure in mechanical systems. This topic is called reliability theory or reliability analysis in engineering, duration analysis or duration modelling in economics, and event history analysis in sociology. 
 
 Survival analysis attempts to answer questions such as: what is the proportion of a population which will survive past a certain time? Of those that survive, at what rate will they die or fail? Can multiple causes of death or failure be taken into account? How do particular circumstances or characteristics increase or decrease the probability of survival? 
 
