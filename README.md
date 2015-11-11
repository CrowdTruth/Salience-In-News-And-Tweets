# Crowdsourcing salient information from news and tweets

This repository contains preliminary work results for identifying linguistic features for novelty detection in news and tweets. We report here results of a crowdsourcing experimental pipeline of assessing the relevance of various tweets and news article snippets and the sentiments and intensities they indicate. The main focus of this dataset if to gather initial relevant and novel information insights, with regard to the event of "<b><a href="https://en.wikipedia.org/wiki/Whaling">whaling</a></b>". 

All the crowdsourcing experiments were performed through the CrowdTruth platform, while the results were processed and analyzed using the CrowdTruth methodology and metrics. For more information, check the <b><a href="http://crowdtruth.org/">CrowdTruth</a></b> website. For gathering the annotated data, we used the <b><a href="http://corwdflower.com/">CrowdFlower</a></b> marketplace.


## Download the data: <a href="https://github.com/CrowdTruth/Salience-In-News-And-Tweets">Salience-In-News-And-Tweets</a>


## Dataset Files:

```
|--/aggregate
```
Various aggregated datasets collected as part of collecting the salient features in news and tweets workflow. We describe here the most important files:

```
|--/aggregate/aggregatedResults_newsArticles.csv
```
This file contains the processed ground truth for the news articles related to the whaling event, in comma-separated format. The file contains aggregated results of the snippets relevance and the snippets and relevant event mentions sentiment and intensity. The columns are:

* *Dataset*: reference to the dataset, DS1
* *Unit Id*: unique ID of the data entry
* *Title Id*: news article unique title ID
* *Title*: news article title
* *Snippet Id*: news article unique snippet ID
* *Snippet*: news article snippet
* *Overlapping Snippet*: binary value describing whether the snippet contains overlapping tokens with the title (1) or not (0)
* *Snippet Relevance Score*: the snippet relevance score; computed using the cosine similarity measure, shows the likelihood that the given snippet is relevant for the news article title
* *Number of Relevant Mentions*: total number of relevant event mentions identified by the crowd in the given snippet
* *Overall Sentiment-Intensity*: binary value describing whether the following columns contain sentiment and intensity scores for the snippet (1) or for the relevant event mentions identified in the given snippet (0)
* *Relevant Mention*: relevant event mention
* *Relevant Mention Score*: the event mention relevance score; computed using the cosine similarity measure, shows the likelihood that the given mention in the snippet is relevant for the news article title
* *Positive Sentiment, Negative Sentiment, Neutral Sentiment*: the sentiment scores of the snippets and event mentions; computed using the cosine similarity measure, shows the likelihood that the given snippet or mention expresses the given sentiment
* *High Intensity, Low Intensity, Medium Intensity*: the intensity scores of the snippets and event mentions; computed using the cosine similarity measure, shows the likelihood that the given snippet or mention expresses a sentiment with the given intensity 

```
|--/aggregate/aggregatedResults_tweets2014&2015.csv
```
This file contains the processed ground truth for the tweets related to the whaling event - from 2014 and 2015, in comma-separated format. The file contains aggregated results of the tweets relevance, tweets relevant event mentions and the sentiment and intensity of the overall tweet and event mentions. The columns are:

* *Dataset*: reference to the dataset, DS2 - 2014 tweets, DS3 - 2015 tweets
* *Tweet Id*: unique ID of the tweet data entry
* *Tweet Author*: tweet author
* *Tweet Date*: tweet date
* *Tweet Seed Index*: unique tweet-event ID
* *Tweet Content*: tweet content
* *Tweet Event Relevance Score*: the tweet relevance score with regard to the whaling event; computed using the cosine similarity measure, shows the likelihood that the given tweet is relevant for the whaling event
* *Number of Relevant Mentions*: total number of relevant event mentions identified by the crowd in the given tweet
* *Overall Sentiment-Intensity*: binary value describing whether the following columns contain sentiment and intensity scores for the tweet (1) or for the relevant event mentions identified in the given tweet (0)
* *Relevant Mention*: relevant event mention
* *Relevant Mention Score*: the event mention relevance score; computed using the cosine similarity measure, shows the likelihood that the given mention in the tweet is relevant for the whaling event
* *Positive Sentiment, Negative Sentiment, Neutral Sentiment*: the sentiment scores of the tweet and event mentions; computed using the cosine similarity measure, shows the likelihood that the given tweet or mention expresses the given sentiment
* *High Intensity, Low Intensity, Medium Intensity*: the intensity scores of the tweet and event mentions; computed using the cosine similarity measure, shows the likelihood that the given tweet or mention expresses a sentiment with the given intensity 

```
|--aggregate/tweetsChangeInSentiment.csv
```
The file contains relevant event mentions in tweets that refer to "*whaling ban*". Each such relevant event mention has the associated sentiment and intensity acores.

```
|--/input
| |--/seedWords_domainExperts.csv
```
The file contains relevant seed words for the whaling event, obtained from the social sciences domain experts. Each column of the file represents a type: *Event*, *Location*, *Actor/Organization*, *Other*

```
|--/raw
| |--/Relevance Analysis
| |  |--/News
| |  |--/Tweets
| |--/Sentiment Analysis
| |  |--/News
| |  |--/Tweets
```
The raw data collected from crowdsourcing for each of the 2 tasks.



## Crowdsourcing Experiments:

The overall workflow consisted of two crowdsourcing tasks for each dataset, both news articles and tweets: 
    (1) identifying relevant snippets or tweets: "<b>Relevance Analysis</b>" task;
    (2) identifying the sentiment of each snippet or tweet and each relevant event mention identified in those snippets and tweets: "<b>Sentiment Analysis</b>" task. The crowdsourcing templates are shown below:
    
![Fig.1: CrowdTruth Workflow for Identifying Salient Features in News and Tweets.](https://github.com/CrowdTruth/Salience-In-News-And-Tweets/blob/master/img/workflow_salient_features.jpg)

During the "<b>Relevance Analysis</b>" task, for the news articles dataset, the crowd is first asked to select all the relevant snippets with regard to the article title, where the title is considered as an expression of the event and then highlight in them all the relevant event mentions. For the tweets dataset, the crowd is asked to assign relevant events (from a list of predefined events) for each tweet and also highlight all the relevant event mentions in it. This results in a set of relevant snippets and tweets and a set of relevant event mentions in those. Using CrowdTruth cosine similarity metric we compute relevance scores for each snippet, tweet and event mention of the "whaling event".

During "<b>Sentiment Analysis</b>" we gather from the crowd the sentiment (in terms of positive, neutral or negative) and its intensity (high, medium, low) for (1) all event mentions identified in the "<b>Relevance Analysis</b>" task, and (2) the overall sentiment and its intensity of each snippet and tweet. Here again, we use the CrowdTruth cosine similarity metric to compute sentiment and intensity scores for each event mention, tweet or snippet.
