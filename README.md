### Professional Certificate in Machine Learning and Artificial Intelligence - Capstone Project

**Sebastian Krawczuk**
<!-- TOC depthfrom:4 -->

- [Executive Summary](#executive-summary)
- [Rationale](#rationale)
- [Research Question](#research-question)
- [Data Sources](#data-sources)
- [Methodology](#methodology)
- [Results](#results)
- [Conclusion](#conclusion)
- [Next Steps](#next-steps)
- [Outline of the Project](#outline-of-the-project)

<!-- /TOC -->

#### Executive Summary

This project addresses the challenge of classifying phishing websites.

#### Rationale

Phishing attacks are commonly used to steal victim's financial assets or take over social media accounts and emails to spread attacks to victim's close circle by intercepting the victim's authentication secrets. Such malicious phishing websites are also used for targeted attacks (spearfishing) on businesses.

The average cost of a data breach against an organization is more than $4 million. -- https://www.securitymagazine.com/articles/98486-435-million-the-average-cost-of-a-data-breach

“According to UnitedHealth disclosures, the cyberattack cost the insurance giant a whopping $870 million in Q1 2024, with nearly $600 million for system restoration and response effort direct costs, and the rest related to revenue loss and business interruption. The criminals used compromised login credentials to remotely access a Change Healthcare Citrix portal that did not have multi-factor authentication, according to the testimony. That portal, offered by the private tech company Citrix Systems, allows for remote access to an organization’s desktops.” — https://www.reuters.com/technology/cybersecurity/unitedhealth-hackers-took-advantage-citrix-vulnerabilty-break-ceo-says-2024-04-29/

#### Research Question

Can we effectively classify phishing and malicious websites?

#### Data Sources

https://archive.ics.uci.edu/dataset/967/phiusiil+phishing+url+dataset

PhiUSIIL Phishing URL Dataset consists of 235,795 URLs out of which 134,850 are benign and 100,945 are phishing. For each URL a corresponding webpage was crawled. URL encoding along with HTML code was parsed and over 50 various features were extracted using methods described in the research paper - “PhiUSIIL: A diverse security profile empowered phishing URL detection framework based on similarity index and incremental learning.” by Prasad, A., & Chandra, S. (2023).

Research Paper DOI: https://doi.org/10.1016/j.cose.2023.103545

License:

This dataset is licensed under a [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/legalcode) (CC BY 4.0) license.
This allows for the sharing and adaptation of the datasets for any purpose, provided that the appropriate credit is given.

Data was donated on 3/3/2024

#### Methodology

CRISP-DM Framework

- Business Understanding:
   - Create a robust URL classification model protecting users from phishing and malicious websites.
- Data Understanding:
   - EDA.
   - Statistical analysis of the extracted URL and website features provided by the researchers.
- Visualizations.
- Data Preparation:
   - Data cleaning.
- Modeling:
   - Train classification models studied during the class: KNN, Logistic Regression, Decision Tree, SVM.
   - If time allows, explore other classification algorithms.
   - Tune hyper-parameters.
- Evaluation:
   - I will use confusion matrix, especially recall, to qualify quality of the model.
   - I will perform runtime time and space (memory usage) profiling to identify a model that is a good compromise between performance and detection quality.
- Deployment - deliberately skipped

#### Results

Generally, the dataset at first sight looks very promising. Authors extracted a lot of "fine grained
" features from their sample URLs and HTML content. 54 features to be precise.

During EDA phase a few surprising discoveries have been made however:
- There are 425 "hidden" duplicated URLs in the dataset probably caused by bugs in feature extraction process and software tools the original authors developed.
- From a random sample of 5 supposedly phishing URLs only 2 were found on `phishtank.org` service. Ideally, we would need to cross validate them with other phishing URL providers.
- Quite a bit of the "fine grained" features extracted from the HTML code are actually impractical. Technically speaking their variance is either zero or very low. They had to be dropped. Hence, 54 features became 38 features.

The models were trained to minimize False Negatives (FN) -- classifying a malicious URL as benign. We want the users to be protected against security threats coming from malicious URLs. Hitting a False Positive (FP) -- classifying a benign URL as malicious is acceptable although it compromises system's UX. UX and Security simply sit on opposite sides of the spectrum. Building Security systems is a balancing act between secured users and happy users.

Any classification model trained on the dataset is literally perfect regardless whether using default hyper-parameters or with additional hyper-parameter tuning. Models demonstrate incredible accuracy and recall scores. Too ideal to be true?...

Any classification model used in this exercise (excluding the baseline Dummy Classifier of course) can handle the task of URL qualification just fine. However Logistic Regression and SVC are best contenders for possible deployment with low False Negatives and reasonable training time.

#### Conclusion

Building a robust URL classification and conviction system is not impossible. Feature extraction techniques have improved over time. However, throwing way too many features into one bucket like with "PhiUSIIL" can lead to confused models and over-fitting. URL classification systems developed and adopted by a cyber security business need to carefully select features used for classification.  

#### Next Steps

- Even after elimination of low-variance features a strong over-fitting is still present. Perhaps eliminate even more features and compare fidelity of less complex models with models trained on the current subset of features and even full dataset.
- Try more classification models. 
- Try to tune more hyper-parameters, especially with SVC.
- Contact the original authors and recalculate all data for duplicated URL entries from their intermediate data. It is quite possible that even the other data samples (not duplicated) also have features extracted incorrectly.

#### Outline of the Project

- [Link to notebook](capstone.ipynb)
