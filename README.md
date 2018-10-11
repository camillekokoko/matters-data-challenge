# matters-data-challenge

* Participant is expected to choose one challenge from the following three options. 

* Python and Jupyter Notebook are preferred. R (with RStudio) and Scala (with Zeppelin Notebook) are also accepted.

* Participant should clone this repo, and submit her/his work by pushing up a new branch with the participant's name. All files needed to reproduce the result should be included in the repo, or instructions for dependencies should be included.

---


## Options

Each of the challenges are designed to be open-ended, so that the participant can explore and implement as much as her/his time and energy permits. All options will get bonus points if the computation is hosted and carried out remotely.

### a. Restraurant survival prediction and exploration with Yelp data

Yelp dataset is used in this exercise to predict and understand restraurant lifespan. It can be downloaded from [Yelp data challenge website](https://www.yelp.com/dataset) or [Kaggle's hosted version](https://www.kaggle.com/yelp-dataset/yelp-dataset). Data points in most cities are sparse, so the participant can choose one or more large cities that have enough data points.

**Requirements**:

1. Extract estimations of restaurant lifespan.
2. Using lifespan estimations, make predictions of restaurant survival rate based on available features, estimate or visualize error/precision of prediction.
3. Form initial hypothesis that explans the survival rate differences among groups.

**Bonus**:

1. Use external datasets (e.g. population density) to help the prediction and explanation.
2. Use interactive visualization (e.g. plotly.js or d3.js) to illustrate your hypothesis, or allow reader to explore the dataset.

### b. Web crawling and user similarity

Douban movie and user data is used in this exercise to calculated the similartiy between two users. The participant can crawl the website to get the needed data, or use douban api to achieve the same result.

**Requirements**:

1. On [Top 250 movies of douban](https://movie.douban.com/top250), get the viewer list of the first 100 movies. For each viewer, get her/his viewed movie list. (_hint_: you don't have to get all the users. You can sample the users with a sample size you are comfortable with)
2. Implement a method to measure/rank similarities based on each user's lists of viewed movie (i.e. for a given user, this method should calculate similarity scores or produce a similarity ranking of all other users). 

**Bonus**:
1. Implement a method to recommend new movies to a user, leveraging the user similarity above.

### c. NLP on Chinese corpus

[Chinese Emergency Corpus](https://github.com/shijiebei2009/CEC-Corpus) is used in this exercise to classify Chinese corpus.

**Requiements**:
1. Strip off meta data and only use text for the following exercise.
2. Choose and implement a suitable method (e.g. LDA) to identity the topics in each body. Alternatively, choose and implement a classification method that classify the corpus according to different topics or sentiments.
3. Implement a method that can find a list of similar text for a given piece of text.

**Bonus**:
1. Visualize the topics or classes in the analysis results.
