# TITLE: Updates
## Team Members: Jeffrey Wang
## Date: 12/5/2020

# Project Description
## Probelm Statement and Motivation
I think sentiment analysis is a really interesting task. I've been really interested in NLP and the recent rise in transformers. I also think that social media platforms can do a lot more to flag comments, and the use of AI could definitely help.

## Introduction and Description of Data
~30000 tweets labeled as hate, offensive, or neither

## Literature Review/Related Work 
Automated Hate Speech Detection and the Problem of Offensive Language (ref 2), is the paper of interest. In the March 2017 paper, Davidson et al. creates a tweet dataset and gets people to label it. They create a model with an f1 score of .9

I plan on using Google's Electra (ref1) with weights from Huggingface, and using simpletransformers library to reproduce their experiment with their dataset, except with Electra model. I want to compare results and also add entertainment value by using twitter API to allow users to run sentiment analysis on custom username tweets.

# Project Progress
Original Plan was to build a voila website and host on binder, but because of time constraints, I plan on just using a colab notebook. I'll host files from my gdrive.

# References:
1. https://arxiv.org/abs/2003.10555
2. https://arxiv.org/abs/1703.04009
3. https://huggingface.co/models
4. https://github.com/ThilinaRajapakse/simpletransformers
