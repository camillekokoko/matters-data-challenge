# matters-data-challenge

* Participant is expected to choose one challenge from the following three options. 

* Python and Jupyter Notebook are preferred. R (with RStudio) and Scala (with Zeppelin Notebook) are also accepted.

* Participant should clone this repo, and submit her/his work by pushing up a new branch with the participant's name. All files needed to reproduce the result should be included in the repo, or instructions for dependencies should be included.

---
Each of the challenges are designed to be open-ended, so that the participant can explore and implement as much as her/his time and energy permits. All options will get bonus points if the computation is hosted and carried out remotely.

### Restraurant survival prediction and exploration with Yelp data

Yelp dataset is used in this exercise to predict and understand restraurant lifespan. It can be downloaded from [Yelp data challenge website](https://www.yelp.com/dataset) or [Kaggle's hosted version](https://www.kaggle.com/yelp-dataset/yelp-dataset). Data points in most cities are sparse, so the participant can choose one or more large cities that have enough data points.

**Requirements**:

1. Extract estimations of restaurant lifespan.
2. Using lifespan estimations, make predictions of restaurant survival rate based on available features, estimate or visualize error/precision of prediction.
3. Form initial hypothesis that explans the survival rate differences among groups.

**Bonus**:

1. Use external datasets (e.g. population density) to help the prediction and explanation.
2. Use interactive visualization (e.g. plotly.js or d3.js) to illustrate your hypothesis, or allow reader to explore the dataset.


---

# from Andy:

### Question first, on Hypothesis:
1. The restaurants whose last records are earlier than 2018 have much higher possibility (around 74%) on "closed", others have only 4%.
2. Solely considering the "categories" has the similar predication power as solely considering other features like Stars, Review_counts... And even bagging them make not too much improvements. It might reveals that "categories" and other features are highly correlated based on the acceptable phenomenon that Pittsburghers tend to have a fixed taste preference. Some certain types of restaurants always have higher popularities.


### On Method/Approaches I used:
1. I used only Pittsburgh City's data. It has 2305 data, with 684 negative.
2. In the final version, I firstly estimated the lifespans based the "review" and "tip" review. Then, combining with the static numerical features like "star","review_count" and dimension reduced "categories" features, I try to predict if a restaurant is still open, which is shown in "is_open".
3. The model of final version is support vector machine. And I raised the cut-off for the positive predication due to the reason that training dataset is relatively skewed against the negative instances.
4. The F1-score is around 0.8 on different training dataset. It shows good competency on predicting the positive cases which is expected, however, the prediction on negative cases is only fair, which reveals a trade-off between recall and precision here (I don't what's the model for, so it's hard to make the trade-off). 
5. I also tried neural networks but they're more unstable and uninterpretable. I also tried to run SVD on my own AWS server with "ploy" kernel, but it took too long and made not much differnce.
6. Initially, my approach is not directly predicing the "is_open", but to predict the lifespan and check if they survived on 2018. But it faces some problem: (1) if I used the lasting year as the estimated lifespan, I will underestimate the lifespan of those successful restaurants. (2) if I only used the lasting year of the restaurants whose lastest record is earlier than 2018, the model will become too pessimistic since it mainly learns from the unsuccessful results (but it could be a good approach if this model is going to be used as a bad-business alarm). (3) Later, I tried to model the lifespan of the existed restaurants in future. This could be a typical machine learning approach on model estimation, but I didn't have enough time to figure it out, so I tried some arbiturary estimations. However, the model could easily become over-optimism and make more positive predications. Meanwhile, this might be an unreliable approach, because the record data not only depends on the popolarity of a restaurant, but also its costomers' habits.


### What could be done in future:
1. more feature selection
1. 10-fold cross-validation
2. oversample the negative cases and undersample the positive cases, try to balance the data
3. try more models


### Other discoveries:
1. The data is not random. I tried to use bagging approach (which gave basically the same results), and find that the front parts of the data will leads to longer lifespan predictions than the back parts. 
2. Yelp is not equally popular in different cities, even the populations of those cities are equal.
3. The "lifespan" I estimated is not the right estimation since it underestimated the successful restaurants. However, it's useful for is_open prediction.
