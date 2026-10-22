# AI Firewall for Threat Detection and Automated Response

## Project Overview

This project was developed for my Cybersecurity courses where I explore how machine learning can be used to find potentially malicious network traffic and support firewall security decisions.

I used Python and the UNSW-NB15 cybersecurity dataset, used a Random Forest classification model to analyze network traffic and see if it can distinguish between normal and malicious activity. 

The project includes a simulated firewall response system that generates Allow Traffic or Block traffic as well and recommendations based on the model's prediction.

The goal of the project was to gain hands-on experience with machine learning in cybersecurity, understand how traffic classification works, and explore both benefits and limitations of using AI to support network security operations. 


## Project Architecture & Workflow

The AI Firewall prototype was built using Python in Jupyter Notebook and the UNSW-NB15 cybersecurity dataset. The dataset has labeled examples of normal and malicious network traffic used to train and evaluate the machine-learning model. 

There are five main steps that the project follows:

1. Data Collection & Preparation
- Imported separate training and testing datasets using Pandas.
- Separated network traffic features from classification labels.
- Removed columns such as id and attack_cat, these are unnecessary and prevents data leakage.
- Converted categorical features into numerical values using one-hot encoding.

2. Model Training
- Used the Random Forest classification algorithm from Scikit-learn.
- Trained the model to recognize patterns related with normal and malicious network traffic

3. Traffic Classification
- Used the trained model to predict if network traffic was normal or malicious.
- Compared predictions against the actual labels in the testing dataset.

4. Model Evaluation
- Measured accuracy, precision, recall, and F1-score in the model.
- Generated a confusion matrix to analyze correct predictions, false positives, and false negatives.
- Examined feature importance to find which network traffic characteristics supported the models prediction.

5. Simulated Firewall Response
- Normal Traffic (0): ALLOW TRAFFIC
- Malicious Traffic (1): BLOCK TRAFFIC

The system generates firewall recommendations based on the model's predictions. These responses are only simulated and do not make changes to an actual firewall. 


## Model Performance & Results

I evaluated the models performance using the UNSW-NB15 testing dataset.

Model Performance 

| Metric                      | Result  |
|-----------------------------|---------|
| Overall Accuracy            | 90.43%  |
| Malicious Traffic Precision | 99%     |
| Malicious Traffic Recall    | 87%     |
| Malicious Traffic F1-Score  | 93%     |
| Testing Samples             | 175.341 |


Confusion Matrix

The confusion matrix is to help support and understand how the model performed classifying normal and malicious traffic.

| Classification Result                              | Number of Samples |
|----------------------------------------------------|-------------------|
| Normal traffic correctly identified                | 54,720            |
| Malicious traffic correctly identified             | 103,847           |
| Normal traffic incorrectly classified as malicious | 1,280             |
| Malicious traffic incorrectly classified as normal | 15,494            |


Simulated Firewall Responses

Based on the model's predictions, the prototype generated

- BLOCK TRAFFIC: 105,127 recommendations
- ALLOW TRAFFIC: 70,214 recommendations

These are simulated and are not interacting with real firewalls.


Results & Security Considerations

The model got a 90.43% accuracy, meaning it successfully identified the majority of malicious traffic in the testing dataset.

However, the confusion matrix shows that there is an important limitation which is where 15,493 malicious traffic samples were incorrectly classified as normal. 

This represents around 13% of the malicious traffic in the testing dataset. In the real-world, these false negatives could potentially allow malicious network activity to bypass security controls. 

The model also classified 1,280 normal traffic samples as malicious, meaning it can potentially disrupt legitimate network activity if blocking decisions were automated.

These results show how accuracy alone is not enough when using a security detection system. False positives, false negatives, and the potential of incorrect decisions and its impact are just as important. 

The prototype demonstrated how machine learning could support firewall decisions but additional testing and improvements would be needed before using something similar in a real network environment. 


## How to Run the Project

Requirements
- Python 3
- Jupyter Notebook or Google Colab
- Required Python Libraries: Pandas, NumPy, Scikit-learn, Matplotlib, and Seaborn

Instructions
1. Download the AI_Firewall_Threat_Detection.ipynb from this repository.
2. Download the UNSW-NB15 training and testing datasets from Kaggle.
3. Make sure the CSV files are available in the notebooks working directory:
   - UNSW_NB15_training-set.csv
   - UNSW_NB15_testing-set.csv
4. Open the notebook in Jupyter Notebook or Google Colab.
5. Install missing dependencies:
   - pip install pandas numpy scikit-learn matplotlib seaborn
6. run the notebook cells from top to bottom.

The notebook will train the Random Forest model, evaluate its performance, generate a confusion matrix, show feature importance, and produce simulated ALLOW/BLOCK firewall recommendations. 


## Project Files

- [AI Firewall Jupyter Notebook](AI_Firewall_Threat_Detection.ipynb) — Python implementation, Random Forest model, evaluation metrics, confusion matrix, and simulated firewall responses.






























