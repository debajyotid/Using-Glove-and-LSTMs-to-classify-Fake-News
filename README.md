# Using-Glove-and-LSTMs-to-classify-Fake-News
## Kaggle Competition to classify fake news

Link: | https://www.kaggle.com/c/fake-news

Aim is to develop a machine learning program to identify when an article might be fake news.¶
Run by the UTK Machine Learning Club.

### Modelling Technique
The data was downloaded from Kaggle directly using their API. We used the train.csv file for training & validation.
The label (target) was removed and the remaining columns formed the feature set. The 
We trained the model on the 'title' column, which contained the news title/summary.
We pre-processed the same using logics like, removing of non alpha-numeric characters, reducing all alphabets to lower case, removing stopwords & inflections (using PorterStemmer)
We then tokenize the text using Keras Tokenizer, Pad & trim the sequences where necessary, in both the cases, from the begining, as LSTM is more influenced by later entries in a sequence.
We used Glove word embeddings to generate word embeddings for the tokenized texts and 2 layers of stacked LSTMs (with drop-out for regularization).
Optimizer was ADAM, Loss Function was Binary Cross-Entropy.
We trained for 10 epochs over batches of 64 sequences.

### Evaluation Metric
The evaluation metric for this competition is accuracy, a very straightforward metric.
[ accuracy = \frac{correct\ predictions}{correct\ predictions+incorrect\ predictions}]
Accuracy measures false positives and false negeatives equally, and really should only be used in simple cases and when classes are of generally equal class size

Below are the results:
Accuracy:   0.9292745169522421
AUC Score:  0.9267756045312805

### Data Description
train.csv: A full training dataset with the following attributes:
  id: unique id for a news article 
  title: the title of a news article 
  author: author of the news article 
  text: the text of the article; could be incomplete 
  label: a label that marks the article as potentially unreliable
    1: unreliable
    0: reliable
test.csv: A testing training dataset with all the same attributes at train.csv without the label.
submit.csv: A sample submission
