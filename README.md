# Quora-NLP
Objective is to predict which of the provided pairs of questions contain two questions with the same meaning. The ground truth is the set of labels that have been supplied by human experts.

# The Data
- The data set consisted of around 400,000 pairs of questions organized in the form of 6 columns as explained -

- id: Row ID

- qid 1, qid 2: The unique ID of each question in the pair

- Question 1, question 2: The actual textual contents of the questions.

- is_duplicate: Label is 0 for questions which are semantically different and 1 for questions which essentially would have only one answer (duplicate questions). 63% of the questions pairs are semantically non-similar and 37% are duplicate questions pairs.

- Duplicate questions marked as not duplicate

- We also found some question pairs that, although duplicate, were marked as 0 in the labels.

- The labels for these questions were changed to 1 to improve the accuracy of the model!

# Basic Data Analysis

- EDA is a process that helps to understand the given dataset better and more practically. It includes multiple techniques and methods to dig deep into the data to extract the hidden patterns and relationships between the different entities in the dataset. we will perform the EDA in some easy steps.

- Before performing data preprocessing, and Exploratory analysis, it’s essential to know the irregularities of our data. It helps us to drive our decision for further analysis and modeling.

1. Load the Dataset

The first task is to load the data into the notebook and import all necessary libraries.

2. Check for Null Values

We have a large corpus of data, but most importantly, it should not be empty. So NULL values must be checked before moving forward.

3. Check for Duplicate Values

It is essential to find out if we have a data redundancy problem. The question in the same column are present multiple times or not?

So the data is non-redundant, but if you plot the distribution of the target variable, then you will find the data is more inclined towards 0 means we have a little bit of a class imbalance problem with our data.

# Distribution of duplicate and non-duplicate questions

4. Check for Repeated Questions

There are no similar entries in a single question column, but there may be repetition from the total number of questions (question-1, question-2). To determine how many questions are unique and how many are repeated, we will merge the questions from both columns into a single list.

# Feature Engineering
Feature engineering is a classic way of adding new features to the data that dominates to predict output variables and improve the model’s accuracy. A crucial feature creates a direct impact on the model. Feature engineering consists of transformation, scaling, feature extraction, feature encoding, EDA, etc.

We will add 7 more features to our existing dataset. The bag of words model for questions 1 and 2 questions 2 will produce different features that will be passed to the Machine learning model after Exploratory analysis.

1. Question Length
The size of the question is a critical feature because when we vectorize it, the question gets split by words, so having the length feature is good. The length we are having is the character-wise length. So it will create 2 new features for the length of questions 1 and 2.

2. Number of Words
The number of words in both questions is another feature that should impact the model performance. So, it will add 2 new features for questions 1 and 2. To add the feature, split the sentence with space and extract the length of the list.

3. Common Words
Another feature is to know how many common words there are in both questions. It helps identify the similarity between both questions. Calculating where you only need to apply the intersection between both questions is simple. For this, we find the number of unique words in both questions and apply the set intersection to the set length.

4. Total Words
The sum of the total number of unique words in each question. In simple terms, find the number of unique words in both questions and return their sum.

5. Words Share
It is one exciting feature and simple to add. To calculate, divide the common words by the total number of words.

# ML Model Creation
1. Separate the Independent and Dependent features
First, we need to drop the unnecessary columns and pick the columns needed for training and one target feature (dependent). So we will pick questions in different dataframe for vectorizing and other features in another dataframe with the target variable. And concat them after vectorizing.

2. Vectorizing the Feature
We need to turn the questions into numerical ones because we can’t provide the string to the model. To do this, we employ a variety of feature vectorizing techniques; for the moment, we’ll use a bag of words (BOW). The bow is a technique for extracting characteristics from text input for machine learning algorithms. It displays the text that describes words’ behavior in the corpus, which entails two things. The first is words’ vocabulary (unique words in the corpus added as a new feature), and the second is a way to count the number of known words (represent the word’s presence in that query using binary format).

3. Train – Test Split
For calculating the performance of the model, we need some amount of data that the model has not seen as a test set, so we will split the final dataframe into two parts, training and test set, where 80 percent of data in the train set and 20 percent for the test set.

4. Train the Machine Learning Models
To determine which model works the best, we will train XGboost, and Random Forest both models.
