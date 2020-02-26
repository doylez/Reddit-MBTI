# Capstone Project Write Up - Doyle
## Does Reddit Know Who You Are? 
### A Look into User Personality and Behaviour Prediction on Reddit

### Abstract 

We live in the age that we constantly share our thoughts and opinions online, but does our words reveal our personalities? This project looks into the comments on the biggest online forum - Reddit, and attempts to use Machine Learning to predict users’ personality by the comments they posted.  It will hopefully shed some lights on personalities of active online users, their behaviour clusters. These information can be used to do better targeting and content curation. 


### Introduction 

Nicknamed “Front Page of the Internet”, Reddit has always been a conglomerate of information since its inception in 2005. In 2018 alone, there are 153 million posts and 1.2 billion comments added to this popular online forum (Reddit, 2018). As one of the most popular websites on the internet, the high volume of daily activity is valued by advertisers, but Reddit seems like a hard place to crack.

Unlike other social networks such as Facebook and Instagram, users can post anonymously , thus granted more freedom. But do the posts still somehow reveal who we are deep down? This project aims to  predict what type of personality (MBTI) the user is based on their posts.  

#### 1. Data Source
The data is compiled by Dylan Storey, a Data Scientist, and posted on the open scientific data platform Zenodo.
The dataset contains over 10 million rows of comments.  For this project, I plan to use a subset around 3 million rows. 
The features include users’ comments, the subreddit that the comment’s posted, users’ usernames and users’ personality indicator according to MBTI. The personality is acquired from the users’ “flair text”, which are written/chosen by the users themselves. 


#### 2. Main Research Questions
My main research questions are all based on the personalities, but expanded to three sections. 
	1. Personality Prediction: Can we predict the users’ personality based on the comments they posted?
	2.  Behaviour Clustering:  Is there any obvious user segmentation based on the sentiments in their comments/ personalities and the subreddits?
	3. Who are Reddit Users: A higher level analysis to see if we can build personas from the personality types and user clusters. 

#### 3. Planned Methodology & Models
Below is a roadmap I planned for the project, from raw data in the beginning, EDA, modelling  to the final outcomes and further researches. 
![](README/reddit%20methodology%20(2).png)

The models I plan to use in the projects are: 
	- [ ] NLP/Sentiment Analysis: this is applied to the comments text data, I hope to utilise the neural network to build the model.
	- [ ] Unsupervised Learning: To be more specific, I am thinking of using one 
of the clustering methods to see if there are obvious user segmentations aside from subreddits and personalities. 

Below is a graph of a small sample set, it’s generated from a Kaggle set with similar structure(forum comments and personalities) with only ~8000 observations. It is obvious there is an imbalance there, which I suspect is also true to my dataset.
![](README/commentscount.png)

#### 4. Anticipated Challenges 
The first challenge I can see is in the cleaning step. The observations are messy: the personality types need to be extracted from it. The comments need to be filtered to ones that have > 5 words in order  not to introduce any single word bias. 

The second challenge is the imbalance of the data.  There are more observations in one class than others, however, that could reflect the actual personalities active on Reddit.

The third challenge could be the amount of internet slangs and special words in the comments. 

#### 5. Hypothesised Outcomes
	- [ ] Personality Classifier: The model would be able to take a comment and predict what personality the commenter is. However, due to the imbalance in the data and the number of classes, I don’t think the accuracy will be very high. 
	- [ ] User segmentation: Ideally the model will be able to find some clear clusters using the text data and personalities. Then I would be able to relate them to the subreddit and build a persona for reddit users. 
	- [ ] Overview of the Reddit: People with what kind of personalities like to use Reddit more? Is there any relationship between personalities and subreddits? 


### References 
- [ ] Reddit. “Reddit’s Year in Review: 2018.” **Upvoted**, 5 Dec. 2018, redditblog.com/2018/12/04/reddit-year-in-review-2018/.
- [ ] Dylan Storey. (2018). Myers Briggs Personality Tags on Reddit Data (Version 0.1.0) [Data set]. Zenodo. [http://doi.org/10.5281/zenodo.1482951](http://doi.org/10.5281/zenodo.1482951) 
- [ ] Thelwall, M. and Stuart, E., 2019. She’s Reddit: A source of statistically significant gendered interest information?.**Information Processing & Management**,**56**(4), pp.1543-1558.


## Limitations
There are many bias and subjective decisions in the process of this project, but  to be honest, the project is based on very biased and subjective data. I made some calls with the dataset, and one of the decisions end up hurting the performance of the models. 

There are limitations on the dataset too. User comments, especially reddit comments are extremely informal, the grammar and the spelling is poor, and there are often internet slang/emoji peppered throughout the documents. It proves to be difficult even after I processed it using different tools, almost bleached it in the end. 


## Future Improvements
There are many improvements I can see happening here. 
First, I did not get a chance to work more on LSTM and word embedding which might help with the accuracy of the models. This is the next thing I’m going to learn and work on. 

Second, to be able to use Hadoop and MapReduce would help with the volume of the dataset. I know we touched upon this during class, however, more lessons are needed. 

## Conclusion
### In response to hypothesised outcomes: 

	- [ ] Personality Classifier: The model would be able to take a comment and predict what personality the commenter is. However, due to the imbalance in the data and the number of classes, I don’t think the accuracy will be very high. 
	
Reality: Well,  at least I foresaw the terrible accuracy. But I was not able to build an input function for testing user real-time input.  The accuracy of the models are all relatively low. The best model is Logistic Regression before I under sample the data, it achieved 21% accuracy on precision/recall. Another promising model is FastText, even on the under sampled data, it achieved 19% accuracy. I will play with it more to see if it can go higher on original data. 

	- [ ] User segmentation: Ideally the model will be able to find some clear clusters using the text data and personalities. Then I would be able to relate them to the subreddit and build a persona for reddit users. 
Reality: I didn’t use unsupervised model for this, instead I used LDA topic modelling for different personality types. They actually came out great. I think it is possible to cross-reference the LDA topics / subreddits/ MBTI types to build a complete picture of the user behaviours. 

	- [ ] Overview of the Reddit: People with what kind of personalities like to use Reddit more? Is there any relationship between personalities and subreddits? 
Reality: I didn’t get a chance to explore anything related to subreddits. However, from the data, it’s plain to see that people with certain personalities ( INFP, INTP, INFJ, ENTJ..) like to post on Reddit more than others. Funny how internet is the playground of introverts.  

### This NLP Journey
Looking back, there are decisions I regret but in the end, these are valuable lessons. Even though NLP might not look as sophisticated as image recognition CNNs, it is one of the most important tools in tackling the largest format of unstructured data out there - text data. Users generate trillions of text everyday on the internet, it is one of the biggest data and it contains valuable information.  I see NLP as gold panning, it’s a lot of hard work for those few nuggets that’s highly valuable. 
Well, in conclusion, no regrets. 