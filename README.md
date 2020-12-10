# TITLE: Twitter Sentiment Analysis for Offensive Language and Hate
## Team Members: Jeffrey Wang
## Date: 12/10/2020

# Website
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/19AA-eUfYYE9YZLhuPE0LWeKPy7aqNRq5?usp=sharing)

# Problem Statement and Motivation
Social media gets a lot of criticism about not taking down offensive or hateful comments. So initially I wanted to see how effective ML could be in classification of tweets. I found a [paper](https://arxiv.org/pdf/1703.04009) by Davidson et al. from Cornell, that used a logistic regression model with l2 regularization reaching an f1 score of 0.9 on a dataset that they procurred. I've worked a bit with [transformer](https://arxiv.org/abs/1706.03762) models, so I wanted to train [ELECTRA](https://arxiv.org/abs/2003.10555) on their paper and see how it goes.

# Introduction and Description of Data
I think sentiment analysis is really interesting. It's not perfect but it can be used to flag comments so humans can take a look at it.

The data contains 24,802 tweets that were labeled as 0:hate, 1:offensive, 2:neither. Each tweet was labeled by 3 humans, although mostly anonymous volunteers, and the final label was the highest count. The authors (Davidson et al.) wanted to divide the data into those 3 categories because they thought it was a distinction that could benefit detection. They concede that their is a flaw in that anonymous humans don't agree on the same things. This presents some challenge as there is a lot of variance in the data.

The breakdown of the data was around ~75% offensive ~15% neither ~5% hate

# Literature Review/Related Work 

[Automated Hate Speech Detection and the Problem of Offensive Language](https://arxiv.org/pdf/1703.04009) - The main paper I'm going off of, has dataset + Logistic regression model with l2 regularization  
[Attention Is All You Need](https://arxiv.org/abs/1706.03762) - Transformers used for translation popularized transformers  
[BERT](https://arxiv.org/abs/1810.04805) - started the use of transformers in NLP  
[ELECTRA](https://arxiv.org/abs/2003.10555) - pretty decent model according to the GLUE benchmark, I've used it in the past for a competition  
[GLUE](https://arxiv.org/abs/1804.07461) - used as a benchmark for language understanding  
[GLUE leaderboard](https://gluebenchmark.com/leaderboard)

# Modeling Approach

ELECTRA is a GAN of Encoders. The encoders are implemented with transformers, which *...maps a sequence on input tokens... into a sequence of contextualized vector representations*. It has a generator and a discriminator network. It trains with self-supervision. The generator will corrupt words with generated words and then the discriminator is trained on binary classification of the words.  
I thought Electra-discriminator would be good at a classification task. I used [simpletransformers](https://github.com/ThilinaRajapakse/simpletransformers) to create a model and weights from [HuggingFace](https://huggingface.co/models).  
I preprocessed the data so that the tweets and labels would be the only input and output. The original paper had more features.

# Project Trajectory, Results, and Interpretation 

Paper:  
F1: 0.9  
Matrix:  
![Original Paper Confusion Matrix](https://github.com/cpsc6300/course-project-j/blob/main/paper_matrix.jpg)

Electra:  
F1: 0.95  
Accuracy: 0.98  
Matrix:  
![Electra's Confusion Matrix](https://github.com/cpsc6300/course-project-j/blob/main/electra_matrix-redo)

I think the results are pretty good, Electra seems very good at separating the tweets things in a binary way. It didn't do well in distinguishing between offensive and hateful comments in the dataset. But looking through the data, I thought there was a massive amount of grey area between offensive and hateful labeled data. So I don't think it's a bad thing that Electra didn't pick up the noise. I actually think it's probably a good thing and a sign that Electra is not overfitting, which the original authors may have had. I hope my work helps convince people that AI is ready to play a role in online moderation.

My original plan was to host a voila website on mybinder.org but I failed and did not have time to troubleshoot.
So I left it on the colab that I trained it on and hosted the weights on my gdrive and uploaded kaggle and twitter keys.

# Conclusions and Future Work

I was very impressed by Electra's ability to distinguish between Offensive/Hate tweets and neither tweets. Some things that could be done are to process the tweets more, add different fields like username, their history etc, add context-surrounding messages, use image annotation to extract image sentiment, the use of different networks working together, obtaining a more appropriate and larger dataset-scraping from many social media sites and forums and using a self-supervised approach to training. I think the biggest problem was the dataset which used anonymous human lablers. An AI model should be able to cluster the sentiments without human lables for every data point. After the training, it can be finetuned with a very high quality dataset made by experts. But the entire dataset was not well labled. Electra was trained in a self-supervised manner and I think a quality finetuning dataset is very important.  

# References:
Automated Hate Speech Detection and the Problem of Offensive Language - https://arxiv.org/pdf/1703.04009  
Attention Is All You Need - https://arxiv.org/abs/1706.03762  
BERT - https://arxiv.org/abs/1810.04805  
ELECTRA - https://arxiv.org/abs/2003.10555  
GLUE - https://arxiv.org/abs/1804.07461  
GLUE leaderboard - https://gluebenchmark.com/leaderboard  
HuggingFace - https://huggingface.co/models  
simpletransformers - https://github.com/ThilinaRajapakse/simpletransformers  

# Support Materials
[Notebook](https://colab.research.google.com/drive/19AA-eUfYYE9YZLhuPE0LWeKPy7aqNRq5?usp=sharing)  
https://colab.research.google.com/drive/19AA-eUfYYE9YZLhuPE0LWeKPy7aqNRq5?usp=sharing  
final Report, proposal, interim are in reports file in repo, notebook is in notebook file, also linked in readme.md
imgs are in repo  

# Declaration of academic integrity and responsibility

```
With my signature, I certify on my honor that:

The submitted work is my original work and not copied from the work of someone else.
Each use of existing work of others in the submitted is cited with proper reference.
Signature: Jeffrey Wang Date: 12/10/2020
```

# Credit
The above project template is based on a template developed by Harvard IACS CS109 staff (see https://github.com/Harvard-IACS/2019-CS109A/tree/master/content/projects).
