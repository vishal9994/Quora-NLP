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
