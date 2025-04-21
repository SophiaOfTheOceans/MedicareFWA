# Using Machine Learning Models to Detect Fraud, Waste, and Abuse in Medicare Claims

### Problem Statement

Medicare is a healthcare program established and funded by the United States Federal Government to provide affordable health insurance for individuals 65 years and older and those with permanent disabilities [1]. According to the 2024 Medicare Trustees Report [2], in 2023 Medicare provided coverage to 77.7 million beneficiaries and exceeded $1,037 billion in total expenditures. 

Unfortunately, Fraud, waste, and abuse (FWA) impose significant financial burdens on the system, leading to inflated costs and inefficient allocation of resources. Examples include, but are not limited to:
- Billing for appointments that the patient did not keep.
- Billing for services more complex than those performed.
- Billing for services not provided.
- Billing multiple times for one service.
Otherwise abusing billing codes for personal gain.

Conservative estimates by the Federal Bureau of Investigation (FBI) estimates that FWA accounts for 3–10% of all billings [3], or up to $104 billion in total and approximately $300 per person in the U.S., while other estimates suggest the number is much higher and somewhere closer to $300 billion in 2019, or about $920 per person in the U.S. as of the time the estimate was made. [4]. 

Traditionally, FWA detection has relied on rule-based systems, manual audits, and whistleblower reports. While effective in some cases, such methods are labor intensive, costly, and often inadequate in identifying more sophisticated cases of fraud. Thus, Machine Learning algorithms offer significant potential in cost and labor savings, as well as reducing error in FWA detection.

For this project, I will attempt to train and develop a machine learning model to disseminate between legitimate Medicare claims and those considered to be FWA. 

### Data Source

CMS provides publicly accessible data containing fields such as provider information and payment data, as well as a list of excluded providers named The List of Excluded Individuals and Entities (LEIE), which contains all of the individuals and entities reprimanded for FWA. 
For this project, I will be looking specifically at Medicare part D, or prescription drugs, aggregated on a provider/drug level. The reason for this limitation is other files (e.g. part B, containing inpatient, outpatient, and professional claims) contain beneficiary-level health information, albeit not specific direct identifiers, and CMS requires that any requester of the data sign a Data Usage Agreement, and approvals may take additional time. However, this does pose a limitation to how well this model can generalize to other types of claims, as well as how well previous research may apply.

### Methodology

A review of existing literature highlights the following approaches:
- Traditional Supervised Learning Models (Bauder et al. 2018) [5]:
- Algorithms such as Logistic Regression and Random Forest Classifier have been utilized by linking the List of Excluded Individuals and Entities (LEIE) to Medicare claims at the National Provider Identifier (NPI) level.
- Unsupervised Learning Methods (Goodwin et al. 2022) [6]:
- Techniques like K-Means Clustering and Spatial Density Analysis are employed to identify anomalous clusters, under the assumption that outliers are more likely to represent fraudulent claims.
- Deep Learning Approaches (Johnson et al. 2019) [7]:
- Advanced neural network architectures provide an opportunity for more sophisticated pattern recognition and anomaly detection in high-dimensional claim data.
Each of these methodologies will be explored and evaluated for their effectiveness in identifying FWA.

Additionally, the inherent imbalance, given fraudulent claims are vastly outnumbered by legitimate ones, requires careful handling. Previous studies have addressed this issue using techniques such as:
- Random Over-Sampling (ROS) and Random Under-Sampling (RUS) (Johnson et al. 2019): Methods that adjust class distributions by increasing or decreasing sample sizes.
- Synthetic Minority Oversampling Technique (SMOTE) (Goodwin et al. 2022): A technique that generates synthetic examples to enhance minority class representation, improving model sensitivity to fraud detection.

### Evaluation
To assess model performance, the following metrics will be used:
- Precision & Recall: While the financial impact of not successfully identifying an FWA claim is obvious, false positives should also be minimized as inaccurate allegations could prevent genuine claims from being processed.
- F1-Score: A harmonic mean of precision and recall for balanced evaluation.
- Cost Savings Estimation: Calculating potential financial impact by comparing detected fraud cases against actual Medicare losses.

### Bibliography
[1] U.S. Government, U.S. Centers for Medicare & Medicaid Services. The Official U.S. Government Site for Medicare. https://www.medicare.gov/. Accessed 25 Feb 2025.
[2] Centers For Medicare & Medicaid Services. Trustees report & trust funds. https://www.cms.gov/oact/tr/2024. Accessed 25 Feb 2025.
[3] Trousdale T. Health care fraud & the FBI. Mo Med. 2012 Mar-Apr;109(2):102-5. PMID: 22675787; PMCID: PMC6181733.
[4] Nicholas, L. H., Segal, J., Hanson, C., Zhang, K., & Eisenberg, M. D. (2019). Medicare Beneficiaries' Exposure To Fraud And Abuse Perpetrators. Health affairs (Project Hope), 38(5), 788-793. https://doi.org/10.1377/hlthaff.2018.05149
[5] Bauder, R., Da Rosa, R., & Khoshgoftaar, T. (2018, July). Identifying medicare provider fraud with unsupervised machine learning. In 2018 IEEE international conference on information Reuse and integration (IRI) (pp. 285-292). IEEE.
[6] Goodwin, B. P., Canton, A., & Olanipekun, B. (2022). Exploration of Data Science Toolbox and Predictive Models to Detect and Prevent Medicare Fraud, Waste, and Abuse. SMU Data Science Review, 6(2), 18.
[7] Johnson, J. M., & Khoshgoftaar, T. M. (2019). Medicare fraud detection using neural networks. Journal of Big Data, 6(1), 63.
