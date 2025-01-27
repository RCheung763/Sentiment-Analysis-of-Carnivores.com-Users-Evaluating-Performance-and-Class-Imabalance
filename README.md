# Carnivores

## Introduction
I have been working on this project as a graduate research assistant in the mathematics department, in collaboration with a professor from the biology department. The dataset consists of 3,522 submissions collected from carnivorespotter.com, a platform that gathers citizen reports of carnivore sightings. These sightings include black bears, bobcats, cougars, coyotes, red foxes, raccoons, and river otters, contributing to the Seattle Urban Carnivores Project. The overarching goal of this project is to develop a model capable of classifying these submissions by sentiment, allowing for detailed analysis of the sentiments associated with each carnivore species sighted. I plan on continually updating this repo as we make progress with this sentiment analysis. 

## Dataset 
The dataset provided consists of 3,522 submissions, with 3365 of those submissions annotated as neutral comments, leaving only 157 comments annotated as positive and negative.  The three variables utilized to train our model came from three open-ended questions asked about the sighting. There are general comments, reaction description, and conflict description. To make use of all all these entries, the answers to the open-ended questions were concatenated.

On this Git are the codebooks for the tests using a kaggle website to check performance with varying class balances. 

## Data preprocessing
A preprocessing layer was added using Keras's TextVectorization class. The standardization parameter was set to a custom normalization stripping it of leading and trailing whitespaces, punctuation, and changing all entries to lowercase. Some responses to the open-ended questions include a like to a video of the sighting. The URLs are removed from the comments leaving only the submitters original text. 

This layer tokenizes the strings. It creates a vocabulary from the text corpus and a max amount of tokens were set to 400 to manage memory use and to ensure computational efficiency. The text is transformed into sequences of integer indices, where each word is replaced by its corresponding index in the vocabulary. 

The embedding layer dimension, the size of the vector that represents each word in the comments, is set to 128. Word embeddings are dense vector representations that capture the meaning of words in a continuous space, where semantically similar words are placed closer together. The sequence length is set to 200 to ensure that all text entries have a fixed length of 200. 

## The model 
This model utilizes 1D ConvNet (Convolutional Neural Network) since our data is sequential and has a one spatial dimension. Starting with an embedding layer, followed by a dropout rate of 0.5 and two Conv1D and global max pooling layers, followed by a vanilla layer using the non-linear reLu activtion function. The model is complied with a binary crossentropy loss and the adam optimizer.

## Progress
The small dataset used to train this model posed a significant challenge. The dataset was split into a training, validation, and a test set. Using this dataset to train our model we were only able to achieve an overall accuracy around 42.86% with the model unable to correctly classify any negative comments correctly. We ran a number of 'sanity tests'. We wanted to confirm that the dataset size is the main limitation to improvement and not the models itself. 

To do this we utilized two different datasets found on Kaggle. Both datasets have been cleaned and annotated and ready to be used for trianing. The first one consisted of 18,467 tweets, 9,685 positive tweets and 8,782 negative tweets. Using this dataset I created a datasets using random selection, with the same amount of positive and negative comments. Using this dataset we achieved the same accuracy rate, 42.86%, as the original carnivores dataset. A dataset was created with the same number observation, 157, but with a more balance class distribution, 50% positive and negative comments. Using this dataset we were able to achieve an overall accuracy rate of 57.14% with the model unable to correctly classify any positive comments.Another dataset was created increasing the sample sizes but retaining a similar class distribution as the orginal dataset. Using this dataset we achieved an accuracy of 79.65%, 88% accuracy for positive comments, and 60% accuracy for negative comments. We then utilized the entire kaggle dataset and achieved an overall accuracy of 81.19%, 76% accuracy for positive comments and 87% accuracy for negative comments. For verification a second Kaggle dataset was used to recreated all these tests, and we found similar differences in our results.  

While we wait for more data samples, our next steps are to consider and test various methods in dealing with small text datasets. Techniques being consider are oversampling methods like SMOTE and using a BERT or distillBERT models. 




