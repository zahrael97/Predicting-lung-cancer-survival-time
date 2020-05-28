# Survival analysis
Survival analysis is the analysis of time-to-event data. Such data describe the length of time from a time origin to an endpoint of interest. For example, individuals might be followed from birth to the onset of some disease, or the survival time after the diagnosis of some disease might be studied. Survival analysis methods are usually used to analyze data collected prospectively in time, such as data from a prospective cohort study or data collected for a clinical trial.


The time origin must be specified such that individuals are as much as possible on an equal footing. For example, if the survival time of patients with a particular type of cancer is being studied, the time origin could be chosen to be the time point of diagnosis of that type of cancer. Equally importantly, the endpoint or event of interest should be appropriately specified, such that the times considered are well-defined. In the above example, this could be death due to cancer studied. Then the length of time from the time origin to the endpoint could be calculated.


One of the reasons why survival analysis requires ‘special’ techniques is the possibility of not observing the event of interest for some individuals. For example, individuals may drop out of a study, or they might have a different event, such as in the above example death due to an accident, which is not part of the endpoint of interest. Another possibility is that there might be a time point at which the study finishes and thus if any individuals have not had their event yet, their event time will not have been observed. These incomplete observations cannot be ignored, but need to be handled differently. This is called censoring. Another feature of survival data is that distributions are often skewed (asymmetric) and thus simple techniques based on the normal distribution cannot be directly used.


The objectives of survival analysis include the analysis of patterns of event times, the comparison of distributions of survival times in different groups of individuals, and examining whether and by how much some factors affect the risk of an event of interest.
# Survival Function
The Survival Function is given by,

Survival Function defines the probability that the event of interest has not occurred at time t. It can also be interpreted as the probability of survival after time t [7]. Here, T is the random lifetime taken from the population and it cannot be negative. Note that S(t) is between zero and one (inclusive), and S(t) is a non-increasing function of t[7].
Hazard Function

The Hazard Function also called the intensity function, is defined as the probability that the subject will experience an event of interest within a small time interval, provided that the individual has survived until the beginning of that interval [2]. It is the instantaneous rate calculated over a time period and this rate is considered constant [13]. 
It can also be considered as the risk of experiencing the event of interest at time t. It is the number of subjects experiencing an event in the interval beginning at time t divided by the product of the number of subjects surviving at time t and interval width[2].

Since the probability of a continuous random variable to equal a particular value is zero. That’s why we consider the probability of the event happening at a particular interval of time from T till (T + ΔT). Since our goal is to find the risk of an event and we don’t want the risk to get bigger as the time interval ΔT gets bigger. Thus, in order to adjust for that, we divide the equation by ΔT. This scales the equation by ΔT[14]. The equation of the Hazard Rate is given as:

The limit ΔT approaches zero implies that our goal is to measure the risk of an event happening at a particular point in time. So, taking the limit ΔT approaches zero yields an infinitesimally small period of time [14].
One thing to point out here is that the Hazard is not a probability. 
This is because, even though we have the probability in the numerator, but the ΔT in the denominator could result in a value that is greater than one.
Censoring
It is a type of missing data problem common in survival analysis. Other popular comparison methods, such as linear regression and t-tests do not accommodate censoring. 
This makes survival analysis attractive for data from randomized clinical studies.
In an ideal scenario, both the birth and death rates of a patient is known, which means the lifetime is known.
Right censoring occurs when the ‘death’ is unknown, but it is after some known date. e.g. The ‘death’ occurs after the end of the study, or there was no follow-up with the patient.
Left censoring occurs when the lifetime is known to be less than a certain duration. e.g. Unknown time of initial infection exposure when first meeting with a patient.
Due to the presence of the censoring in survival data, the standard evaluation metrics for regression such as the root of mean squared error and ܴ ଶ are not suitable for measuring the performance in survival analysis. Three specialized evaluation metrics for survival analysis:
1- Concordance index (C-index) what should be used in the challenge
2- Brier score
3- Mean absolute error
# Concordance Index (C‐Index)
It is a rank order statistic for predictions against true outcomes and is defined as the ratio of the concordant pairs to the total comparable pairs. For a binary outcome, C-index is identical to the area under the ROC curve (AUC).
# Kaplan–Meier estimator

Also known as the product-limit estimator is a non-parametric statistic used to estimate the survival function from lifetime data. 
In medical research, it is often used to measure the fraction of patients living for a certain amount of time after treatment. 
In other fields, Kaplan–Meier estimators may be used to measure the length of time people remain unemployed after a job loss, the time-to-failure of machine parts, or how long fleshy fruits remain on plants before they are removed by frugivores. The estimator is named after Edward L. 
Kaplan and Paul Meier, who each submitted similar manuscripts to the Journal of the American Statistical Association. The journal editor, John Tukey, convinced them to combine their work into one paper, which has been cited about 55,000 times since its publication.
# Proportional hazards

Are a class of survival models in statistics. Survival models relate the time that passes, before some event occurs, to one or more covariates that may be associated with that quantity of time. In a proportional hazards model, the unique effect of a unit increase in a covariate is multiplicative with respect to the hazard rate. For example, taking a drug may halve one’s hazard rate for a stroke occurring, or, changing the material from which a manufactured component is constructed may double its hazard rate for failure. Other types of survival models such as accelerated failure time models do not exhibit proportional hazards. The accelerated failure time model describes a situation where the biological or mechanical life history of an event is accelerated (or decelerated).
# Tools
As a pre-requisite, be sure Jupyter Notebook and Python are installed on your computer. The code snippets will run on Jupyter Notebook only.
Alright, let’s start, we can use:
1-Lifelines is an implementation of survival analysis in Python. What benefits do lifelines offer over other survival analysis implementations?
built on top of Pandas
internal plotting methods
simple and intuitive API
the only focus is survival analysis
handles right, left and interval-censored data

2- Scikit-survival is to establish a connection between covariates and the time of an event. What makes survival analysis differ from traditional machine learning is the fact that parts of the training data can only be partially observed — they are censored.


For instance, in a clinical study, patients are often monitored for a particular time period, and events occurring in this particular period are recorded. If a patient experiences an event, the exact time of the event can be recorded — the patient’s record is uncensored. In contrast, right censored records refer to patients that remained event-free during the study period and it is unknown whether an event has or has not occurred after the study ended. Consequently, survival analysis demands for models that take this unique characteristic of such a dataset into account.
3- DeepSurv, a Cox proportional hazards deep neural network and state-of-the-art survival method for modeling interactions between a patient’s covariates and treatment effectiveness in order to provide personalized treatment recommendations.
And so many more…



Medium link :https://medium.com/analytics-vidhya/survival-analysis-with-python-69e51355d18
