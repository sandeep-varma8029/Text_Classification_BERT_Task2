Text Classification using BERT and Amazon SageMaker
---------------------------------------------------
This project demonstrates how to perform text classification using a BERT-based multilingual model and Amazon SageMaker. I used an augmented dataset containing sentences with 15 different framing labels focusing on two social issues: immigration and same-sex marriage. The classification was performed using a Jupyter Notebook (Text_Classification_BERT.ipynb) on Amazon SageMaker Studio Lab.

### Dataset
The augmented dataset (augmented_data.tsv) is a collection of sentences designed to help identify the framing of given paragraphs/sentences across various languages. The focus is on two social issues: immigration and same-sex marriage. The dataset contains 250 plus sentences, covering multiple framing dimensions such as economics, morality, politics, health and safety, cultural identity, and more. These dimensions are based on the "Policy Frames Codebook" by Boydstun et al. (2014).

The dataset consists of sentences in multiple languages, including English, Mandarin Chinese, Hindi, Telugu, Nepali, Bengali, Greek, German, and Swahili. It contains sentences with the following framing labels:

- "0": Economic
- "1": Capacity and Resources
- "2": Morality
- "3": Fairness and Equality
- "4": Legality, Constitutionality, Jurisdiction
- "5": Policy Prescription and Evaluation
- "6": Crime and Punishment
- "7": Security and Defense
- "8": Health and Safety
- "9": Quality of Life
- "10": Cultural Identity
- "11": Public Sentiment
- "12": Political
- "13": External Regulation and Reputation
- "14": Other

### Setup
1. Upload the augmented_data.tsv file to an S3 bucket: sagemaker-studio-r3fybtokjrb.
2. Create an IAM role for the user sandeepvarma and add permissions AmazonS3FullAccess.
3. Set the AWS access key ID and secret access key as environment variables in your Jupyter Notebook:
```python
import os

os.environ['AWS_ACCESS_KEY_ID'] = 'xxxxxxxxxxxx'
os.environ['AWS_SECRET_ACCESS_KEY'] = 'xxxxxxxxxxxxxx'
```
