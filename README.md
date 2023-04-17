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
1. I Upload the augmented_data.tsv file to an S3 bucket: sagemaker-studio-r3fybtokjrb.
2. I then Created an IAM role for the user sandeepvarma and add permissions AmazonS3FullAccess.
3. Next,Set the AWS access key ID and secret access key as environment variables in your Jupyter Notebook:
```python
import os

os.environ['AWS_ACCESS_KEY_ID'] = 'xxxxxxxxxxxx'
os.environ['AWS_SECRET_ACCESS_KEY'] = 'xxxxxxxxxxxxxx'
```
##Notebook
The Text_Classification_BERT.ipynb notebook performs the classification using the BERT-based multilingual model with the following hyperparameters:

- batch_size: 16
- optimizer: AdamW(model.parameters(), lr=5e-05) (with default values of learning rate and epsilon value)
- epochs: 25

I also used a helper script (helpers.py) that contains the necessary functions to tokenize and format the sentences, as well as a function to calculate flat accuracy.

In the notebook, I first imported the necessary helper functions and prepared the dataset by shuffling and tokenizing the sentences. Then, I created a BERT model for sequence classification and trained it using the specified hyperparameters.

After training the model, I evaluated its performance on the validation set and obtained a validation accuracy of 0.6511627906976745.

##Error Analysis
I performed error analysis on the predictions to understand the model's performance and identify potential areas for improvement.

Usage
- Open the Text_Classification_BERT.ipynb notebook in Amazon SageMaker Studio Lab.
- Ensure that the necessary libraries are installed (e.g., pandas, transformers, torch, etc.).
- Set the AWS access key ID and secret access key as environment variables in the notebook as shown in the Setup section.
- Run the cells in the notebook to perform the text classification task. Make sure to run the cells in order as they have dependencies on previous cells.
- After training the model, the notebook will display the validation accuracy. You can use this value to assess the model's performance and make any necessary adjustments to the hyperparameters or training process.
- Optionally, you can perform error analysis on the predictions to understand the model's performance and identify potential areas for improvement. This can help you fine-tune the model or guide future modifications.
- You can also use the trained model to make predictions on new text data by adapting the code in the notebook. Remember to preprocess the new data using the same steps as the training data (e.g., tokenizing and formatting) before making predictions.

By following these steps, you can successfully perform text classification using a BERT-based multilingual model and Amazon SageMaker.
