# Hannover-Karolinska Project Plan - Sam Hobson 
Date: 20201110

## Already completed: 

- [x] urine samples from 40 CKD5 patients sent from Karolinska Institutet (KI) to Mosaiques
- [x] Analysis of urine samples using CE-MS completed on independent Karolinska cohort
- [x] Cleaning of patients' data: 
    * Results: **7939 patients with age, sex, and eGFR** vailable
    * All diseases were combined into four categories: 'Diabetes/Obesity/metabolic syndrome', 'Chronic kidney disease', 'CVD/Hypertension', 'Other diseases'
    * They were divided to **4 groups according to eGFR**: 30, 60, 90
    * They are split into **training (N=7899)** and **test(N=40)**
- [x] estimated of propensity scores of eGFR-group with age and sex as covariates
    * Methods: logistic regression or generalised boosted tree
    
## Further analysis plan?
### Peptidomics
- [ ] Export the peptide abundance
- [ ] Only assess peptide with abundance in >30% patients
- [ ] Normalise the peptide abundance

### Option 1: Matching
- [ ] Propensity score matching 
    1. Match the egfr group A with highest N to group B with second highest N,
    2. Match the intersection of A and B with the third group C
    3. Match the intersection of A, B, C to and match the intersection with the fourth group D
    4. Assess the balance of covariables between group
- [ ] Sorting and list the most abundant n peptides, see if there are overlap between groups

### Option 2: Without matching
- [ ] two-way ANOVA (to assess if there is any **difference** in group means)
    1. catagorise the propensity scores into quintiles
    2. two-way ANOVA of peptide abundance between the four eGFR groups, using propensity scores quintiles as covariables
    3. adjust for multiple testing
    4. study the peptides with p<0.05 
- [ ] weighted linear regression (to assess there is any **trend** in group means)
    1. linear regression of peptide abundance between the four eGFR groups, using propensity score as weight
    3. adjust for multiple testing
    4. study the peptides with p<0.05 
    
### Questions:
* why did we categorise the egfr (which is continous) into groups (which is catagorical) in the first place? I think it is feasible to start with linear regression of peptide abundance vs eGFR, where you set age, sex, diseases as covariables.
* If you want to explore diseases, we have to fill the missing values with 0
    

## What is already known? In scope of study..
-	CKD273 shown to predict cardiovascular outcome in patients with CKD1-5 (Verbeke et al., 2019)
-	CKD273 better at predicting progressors than urine albumin excretion in early stages of CKD, while the contrary is true in later stages (Portillo et al., 2017)
-	Correlation of individual urinary peptides with CKD stage and progression showed peptides associated with glomerular filtration barrier have sieving properties, or constitute different collagen fragments (Schanstra et al., 2015)
-	Urinary peptide classifier, based on 150 peptides, could distinguish between non-obese subjects with preserved renal function and obese subjects with eGFR <45 (Wednt et al., 2020) (interesting study for implementing classifier)

## What isn’t known?
Comprehensive assessment of urinary peptides in CKD patients with end-stage disease, when using baseline eGFR to stratify patients. The use of an independent cohort consisting of 40 CKD5 patients, with a median eGFR of 7.05, will allow for validation of findings.

## Aim(s) of prospective study
To investigate if abundance of single urinary peptides changes based on CKD severity (baseline eGFR), paying special attention to late stage kidney disease
To investigate if disease aetiology has an effect on the urinary peptide profile of CKD patients

## Study design
Cross-sectional retrospective study

## Summary
Patients will be selected on the following criteria: non-diabetic, no history of RRT, and male  (since 100% of Karolinska patients are male), and with records of eGFR, disease aetiology (if applicable) and urinary albumin excretion. Two cohorts will be created: patients from Hannover Human Urinary Proteome database (training cohort) and Karolinska patients (test cohort). Once inclusion criteria has been established, patient data will be extracted. Note: since 85% of patients in Karolinska test cohort have no history of RRT, six RRT patients can be removed if deemed necessary. Furthermore, another approach would be to include females and adjust for sex accordingly. 

Once extracted, patients in the training data set will be stratified by baseline eGFR, calculated using CKD-EPI equation. eGFR groups are as follows: >120, 90-120, 60-90, 45-60, 30-45, 15-30, <15 ml/min/1.73m2. I.e., groups represent controls with normal renal function, and cases with progressively worse renal function.
In short, we will investigate if individual peptides associate with baseline eGFR adjusting for age; albumin; diabetes, if not excluded during patient selection; and statin use, since there is ample evidence that statins may reduce proteinuria. The number and origin of peptide fragments most frequently detected in each eGFR stratum will be summarised . After adjusting for disease aetiology, we can investigate if aetiology/comorbidity has an effect on urinary peptides detected in each stratum. Disease aetiology sub group analysis may be applicable, i.e., determining how many peptides overlap or differ for the different aetiologies, and then determining their involvement in different processes. Portillo et al., found urinary peptide differences in patients with mild, moderate and severe kidney disease reflected ECM damage, inflammation and glomerular damage, respectively. By having more eGFR strata and more patients with late-stage kidney disease, it would be of interest to see if we can repeat findings, but also investigate if peptides reflecting glomerular damage in patients with severe end stage disease (<15 ml/min/1.73m2) follow the observed correlation/association.

The test cohort will then be used to validate findings, i.e., do previously identified peptides (or groups of peptides) positively/negative correlate with baseline eGFR in 40 CKD5 patients with eGFR <15 ml/min/1.73m2? Note that this cohort consists of “relatively healthy” CKD5 patients undergoing living donor renal transplantation. This should be taken into account when interpreting differences/similarities between training and test cohorts. Furthermore, since all patients have had their epigastric arteries scored for calcification and fibrosis, it would be of interest to split the test group into two groups: fibrosis score = 0; fibrosis score >0 , to see if peptides known to be involved in fibrosis process in late-stage kidney disease cluster in patients with fibrosis score >0, i.e., onset of fibrosis in epigastric artery. 


## Suggested Responsibilities 
Sam: study design, writing of manuscript
Tianlin: data analysis and visualisation 
