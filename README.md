# Testing the Impact of Dataset Size and Class Distribution on Sentiment Analysis Model Performance using Carnivores.com Submissions

## Motivation

The overarching goal of the CarnivoresSpotter.com project was to develop a model capable of classifying sighting submissions by sentiment, allowing for detailed analysis of the sentiments associated with different carnivore species sighted. These sightings include black bears, bobcats, cougars, coyotes, red foxes, raccoons, and river otters, contributing to the Seattle Urban Carnivores Project. 

The small dataset from Carnivores.com submissions posed significant challenges, particularly in terms of class imbalance and limited sample size. Despite using a variety of techniques, the model achieved only modest accuracy, with a notable inability to classify negative comments. To better understand the limitations, we tested two larger, balanced datasets from Kaggle, comparing results across different sample sizes and class distributions. The findings highlight the crucial role of dataset size and balance in improving model performance and showed us what can be expected of this model when more submissions are eventually added to the dataset. 

Data 

The dataset consists of 3,522 submissions, with 3365 of those submissions annotated as neutral comments, leaving only 157 comments annotated as positive and negative. The three variables utilized to train our model came from three open-ended questions asked about the sighting. There are general comments, reaction description, and conflict description. To make use of all all these entries, the answers to the open-ended questions were concatenated.

In the repository are also the codebooks for the tests using a Kaggle website to check performance of our model with varying class balances.

Data Preprocessing

A preprocessing layer was added using Keras's TextVectorization class. The standardization parameter was set to a custom normalization stripping it of leading and trailing whitespaces, punctuation, and changing all entries to lowercase. Some responses to the open-ended questions include a like to a video of the sighting. The URLs are removed from the comments leaving only the submitters original text.

This layer tokenizes the strings. It creates a vocabulary from the text corpus and a max amount of tokens were set to 400 to manage memory use and to ensure computational efficiency. The text is transformed into sequences of integer indices, where each word is replaced by its corresponding index in the vocabulary.

The dataset was split into a training, validation, and a test set. Using this dataset to train our model we were only able to achieve an overall accuracy around 42.86% with the model unable to correctly classify any negative comments correctly. We ran a number of 'sanity tests'. We wanted to confirm that the dataset size is the main limitation to improvement and not the models itself.

Methodology

To explore the impact of dataset size and class distribution on model performance, we utilized two different Kaggle datasets, both of which were cleaned and annotated for training. The first dataset consisted of 18,467 tweets, with 9,685 positive and 8,782 negative tweets. From this dataset, we created a balanced subset through random selection, ensuring an equal number of positive and negative comments. Additionally, a smaller dataset with 157 observations was created, maintaining a 50/50 distribution of positive and negative comments. Lastly, we generated a larger dataset, preserving the class distribution but increasing the sample size.

Results

The model trained on the balanced subset achieved an accuracy rate of 42.86%, identical to the performance on the original CarnivoresSpotter.com dataset. When using the dataset with a more balanced class distribution (50% positive and 50% negative), the accuracy improved to 57.14%, though the model still struggled with correctly classifying positive comments. Expanding the sample size while retaining a similar class distribution led to an accuracy of 79.65%, with 88% accuracy for positive comments and 60% for negative comments. Finally, when we utilized the entire Kaggle dataset, the model reached an overall accuracy of 81.19%, with 76% accuracy for positive comments and 87% for negative comments. Verification with a second Kaggle dataset confirmed similar trends, further validating these findings. 

Below is the confusion matrix for a large balance dataset show what types of results we can reasonably expect when we collect more data from CarnivoresSpotter.com.

