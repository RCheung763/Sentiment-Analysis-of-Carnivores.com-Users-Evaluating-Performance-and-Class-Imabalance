# Carnivores

# Introduction
I have been working on this project as a graduate research assistant in the mathematics department, in collaboration with a professor from the biology department. The dataset consists of 3,522 submissions collected from carnivorespotter.com, a platform that gathers citizen reports of carnivore sightings. These sightings include black bears, bobcats, cougars, coyotes, red foxes, raccoons, and river otters, contributing to the Seattle Urban Carnivores Project. The overarching goal of this project is to develop a model capable of classifying these submissions by sentiment, allowing for detailed analysis of the sentiments associated with each carnivore species sighted.

## Dataset 
The dataset provided consists of 3,522 submissions, with 3365 of those submissions annotated as neutral comments, leaving only 157 comments annotated as positive and negative.  The three variables utilized to train our model came from three open-ended questions asked about the sighting. There are general comments, reaction description, and conflict description. To make use of all all these entries, the answers to the open-ended questions were concatenated. 

# Data preprocessing
In order to prepare data for vectorization comments were standardized by stripping it of leading and trailing whitespaces, punctuation, and changed to lowercase. Some responses to the open-ended questions include a like to a video of the sighting. The URLs are removed from the comments leaving only the submitters original text.

