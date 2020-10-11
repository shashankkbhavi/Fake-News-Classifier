# Fake-News-Classifier

### Objective

Develop a machine learning program to identify when an article might be fake news.


### Dataset overview

train.csv: A full training dataset with the following attributes:

id: Unique id for a news article
title: The title of a news article
author: Author of the news article
text: The text of the article; could be incomplete
label: A label that marks the article as potentially unreliable
1: Unreliable
0: Reliable

test.csv: A testing training dataset with all the same attributes at train.csv without the label.

Dataset Link: https://www.kaggle.com/c/fake-news/data


### Model building process:

#### Step 1: Importing Libraries

We start by importing the necessary libraries such as Pandas and Numpy.

#### Step 2: Reading the training data

We import the data to train our model. The file used here is train.csv. Once we import our data, we look at the top 5 rows along with the column headers using '.head()' method.

#### Step 3: Data Pre-processing

We begin our data pre-processing by looking at the shape of the data using '.shape' command. Then we check for missing values in our data. i.e., looking for NAN values. Since we were able to find the missing values, we drop those values as we cannot predict or figure out what data should go here.

The dropping of missing values creates missing index issue. If the 6th row contains missing values and is dropped, the index 6 goes missing. To avoid this issue, we reset our index.

After resetting the index, we divide oue features into independent and dependent features.
Here dependent feature will be 'label' as it indicates whether the news is reliable or unreliable and rest of the features will be independent features.

Since the data is in the form of text, we need to stem the data and remove the stop words inorder to make it suitable for text processing. Stemming produces intermediate representation of the word. For this purpose, we import the library 'nltk'.

By using Regex, we subsitute all the characters except [a to z and A to Z] with blank spaces. Once we have all the words, we may come across an issue where two same words, one having first letter capital and other not can be treated as two different words. Hence for this purpose, we lower all the words.

As the data is present in the textual format, the machine cannot read this. Hence we need to convert this data into numerical form. For this we use One Hot encoding technique and setting the vacabulary size to 5000.

The sentences can be of different lengths which is not desirable to train our model. To oveercome this issue, we use padding technique. The padding technique can be of two types: 'Pre' and 'Post'. This will add zeros at the beginning or at the end of the sentence (depending on the type of padding user specifies) to make all sentences of equal length. The length here is specified by the user.


#### Building Model

To build the model we are going to use Tensorflow 2.0 framework and Keras library. The model we are going to use is Bidirectional LSTM.

We import all the necessary libraries to build our network and build the model. Now we split the data into training and testing data. The training data is used to train the model. 

Once the model is trained using training data, we test it using the testing data. We repeat all the data pre-processing steps on the testing data as well to make it suitable to test our model.


#### Model Evaluation

The performance and accurace of the model can be checked using confusion matrix as we are trying to solve a classification problem. 





