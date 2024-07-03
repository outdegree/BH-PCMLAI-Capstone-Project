### Professional Certificate in Machine Learning and Artificial Intelligence - Capstone Project

**Sebastian Krawczuk**

#### Executive summary

This project tackles phishing website classification challenge.

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

Generally, the dataset at first sight looks very promising. Authors extracted a lot of fine grained features from their sample URLs and HTML content.

During EDA phase a few surprising discoveries have been made however:
- There are 850 "hidden" duplicated URLs in the dataset probably caused by author's bugs in feature extraction process and software.
- From a random sample of 5 supposedly phishing URLs only 2 were found on phishtank.org service.

Any classification model trained on the dataset is literally perfect regardless whether using default hyper-parameters or with tuning. Models demonstrate incredible accuracy and recall scores. Too ideal to be true?

Any classification model used in this exercise (but the baseline Dummy of course) can handle the task of URL qualification just fine. 

#### Next steps

- Try more classification models.
- Include training and prediction runtime and memory profiling.
- Train with N-most important features and compare fidelity of such models with models trained on the full dataset. 
- Recalculate all data for duplicated URL entries from existing intermediate data, like `URLLength`, etc.

#### Outline of project

- [Link to notebook](capstone.ipynb)

##### Contact and Further Information

TBD
