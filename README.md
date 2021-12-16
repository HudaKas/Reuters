# Reuters

## Introduction:

The Reuters-21578 dataset is a collection of documents with news articles. It is collected from the Reuters financial newswire service in 1987. The data is available in the collection of 22 data files, an SGML DTD file describing the data file format, and six files describing the categories used to index the data. The Challenge is to implement a model or algorithm that can classify news articles of (at least) the type "earn" covered in the dataset.

## Formatting: 
The Reuters-21578 collection is distributed in 21 files. Each of
the 21 files contain 1000 documents. Each document has various tags(meta) to give information about the data. The tags of interest are Body, Topics, and Lewissplit tags.

Body: 		News Article 
Topics: 	Label of the News Article
Lewissplit: 	It can have 2 values- Training and Testing. Training indicates that the document will be used for training the model, while Testing indicates that the document will be used for model evaluation.
However, even though there are 1000 articles in each file, not every article contains a <body> tag. All those documents which do not have a body tag are removed from the training set.
## Modelling:
The challenge is visualized as a binary classification problem where are articles belonging to topic earn are labelled as 1 and all other topics are labelled as 0(others). The articles that do not have any topic mapped against them are dropped. This is done so that the model can generalize better with reduced ambiguity. The articles are cleaned by removing the stop-words, html tags and unnecessary urls. The articles are then vectorized using a Tfidf vectorizer. A Tfidf vectorizer converts the raw articles into a sparse matrix of TF-IDF features. This Tfidf vector matrix and the labels are then fed to the different ML models to train them.
## Results:
The data was evaluated on two models – Logistics Regression and Linear SVC. Both the models have performed extremely well. Linear SVC with slightly better recall has a little edge over Logistic Regression. It shows that Linear SVC can just slightly better predict the articles belonging to earn as compared to Logistic Regression. Thus, we use Linear SVC as our final model. A function is created which accepts .sgm file or normal raw text as a test input, it cleans and converts them into the trained data format and returns the result.
