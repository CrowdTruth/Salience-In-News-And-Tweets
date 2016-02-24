# Crowdsourcing salient information from news articles and tweets

[![DOI](https://zenodo.org/badge/19180/CrowdTruth/Salience-In-News-And-Tweets.svg)](https://zenodo.org/badge/latestdoi/19180/CrowdTruth/Salience-In-News-And-Tweets)

This repository contains preliminary work results for identifying linguistic features for novelty detection in news articles and tweets. We report here results of a crowdsourcing experimental pipeline of assessing the relevance of various tweets and news article snippets and the sentiments and intensities they indicate. The main focus of this dataset if to gather initial relevant and novel information insights, with regard to the event of "<b><a href="https://en.wikipedia.org/wiki/Whaling">whaling</a></b>". 

All the crowdsourcing experiments were performed through the CrowdTruth platform, while the results were processed and analyzed using the CrowdTruth methodology and metrics. For more information, check the <b><a href="http://crowdtruth.org/">CrowdTruth</a></b> website. For gathering the annotated data, we used the <b><a href="http://corwdflower.com/">CrowdFlower</a></b> marketplace.


## Check the Results & Download the Data: <a href="https://github.com/CrowdTruth/Salience-In-News-And-Tweets">Salience-In-News-And-Tweets</a>

## Table of Contents:

* [Dataset Files](#datasetfiles)
* [Crowdsourcing Experiments](#crowdsourcingexperiments)
   * [Relevance Analysis Task on News Articles (DS1)](#taskrelevancenews)
   * [Sentiment Analysis Task on News Articles (DS1)](#tasksentimentnews)
   * [Relevance Analysis Task on Tweets (DS2&DS3)](#taskrelevancetweets)
   * [Sentiment Analysis Task on Tweets (DS2&DS3)](#tasksentimenttweets)
* [Experiments Results](#results)
   * [Relevance Analysis Task on News Articles (DS1)](#resultsrelevancenews)
   * [Sentiment Analysis Task on News Articles (DS1)](#resultssentimentnews)
   * [Relevance Analysis Task on Tweets (DS2&DS3)](#resultsrelevancetweets)
   * [Sentiment Analysis Task on Tweets (DS2&DS3)](#resultssentimenttweets)


<a id="datasetfiles"></a>

## Dataset Files:

```
|--/aggregate
```
Various aggregated datasets collected as part of collecting the salient features in news articles and tweets workflow. We describe here the most important files:

```
|--/aggregate/aggregatedResults_newsArticles.csv
```
This file contains the processed ground truth for the news articles related to the whaling event, in comma-separated format. The file contains aggregated results of the snippets relevance and the snippets and relevant event mentions sentiment and intensity. The columns are:

* *Dataset*: reference to the dataset, news - DS1
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

* *Dataset*: reference to the dataset, tweets 2014 - DS2, tweets 2015 - DS3 
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
|--aggregate/orderedSnippetsByRelevance.csv
```
The file contains the relevant news snippets ordered by their relevance score. The overlapping news snippets are ordered in a descending way, while the non-overlapping news snippets are ordered ascending. 

```
|--aggregate/snippetsPositionInArticle.csv
```
The file contains measures for snippets relevance with regard to their position in the news articles.

```
|--aggregate/orderedNewsSnippetsBySentiments.csv
```
The file contains the relevant news snippets ordered by their sentiments: positive sentiment - descending, negative sentiment - ascending. 

```
|--aggregate/orderedTweetsByRelevance.csv
```
The file contains the relevant tweets ordered by their relevance score.

```
|--aggregate/orderedTweetsByMentions.csv
```
The file contains the relevant tweets ordered by their total number of relevance event mentions.

```
|--aggregate/histogramRelevantTweets.csv
```
The file contains the number of relevant tweets for each relevance score intervals.

```
|--aggregate/orderedTweetsBySentiments.csv
```
The file contains the relevant tweets ordered by their sentiments: positive sentiment - descending, negative sentiment - ascending. 

```
|--aggregate/tweetsChangeInSentiment.csv
```
The file contains relevant event mentions in tweets that refer to "*whaling ban*". Each such relevant event mention has the associated sentiment and intensity acores.

```
|--/input
|  |--/seedWords_domainExperts.csv
```
The file contains relevant seed words for the whaling event, obtained from the social sciences domain experts. Each column of the file represents a type: *Event*, *Location*, *Actor/Organization*, *Other*

```
|--/raw
|  |--/Relevance Analysis
|  |  |--/News
|  |  |--/Tweets
|  |--/Sentiment Analysis
|  |  |--/News
|  |  |--/Tweets
```
The raw data collected from crowdsourcing for each of the 2 tasks.


<a id="crowdsourcingexperiments"></a>

## Crowdsourcing Experiments:

The overall <b>workflow</b> consists of two crowdsourcing tasks for each dataset: 
1. <b>Relevance Analysis</b>: to identify the relevant news snippets and tweets; 
2. <b>Sentiment Analysis</b>: to identify (1) the sentiment of each relevant event mention in all the relevant news snippets and tweets and (2) the overall sentiment of all the relevant news snippets and tweets. 
    
During the "<b>Relevance Analysis</b>" task, for the news articles dataset, the crowd is first asked to select all the relevant snippets with regard to the article title, where the title is considered as an expression of the event and then highlight in them all the relevant event mentions. For the tweets dataset, the crowd is asked to assign relevant events (from a list of predefined events) for each tweet and also highlight all the relevant event mentions in it. This results in a set of relevant snippets and tweets and a set of relevant event mentions in those. Using CrowdTruth cosine similarity metric we compute relevance scores for each snippet, tweet and event mention of the "whaling event".

During "<b>Sentiment Analysis</b>" we gather from the crowd the sentiment (in terms of positive, neutral or negative) and its intensity (high, medium, low) for (1) all event mentions identified in the "<b>Relevance Analysis</b>" task, and (2) the overall sentiment and its intensity of each snippet and tweet. Here again, we use the CrowdTruth cosine similarity metric to compute sentiment and intensity scores for each event mention, tweet or snippet.

Check the crowdsourcing templates below. 
    
<a id="taskrelevancenews"></a>
   
### Relevance Analysis Task on News articles (DS1)  (click <a href="https://raw.githubusercontent.com/CrowdTruth/Salience-In-News-And-Tweets/master/img/taskrelevancenews.jpg" target="_blank">here</a> to enlarge the picture and read the crowdsourcing task instructions)
![Fig.1: CrowdTruth Workflow for Identifying Salient Features in News - DS1.](https://raw.githubusercontent.com/CrowdTruth/Salience-In-News-And-Tweets/master/img/taskrelevancenews-withoutInstructions.jpg)

<a id="tasksentimentnews"></a>

The relevant News Articles to the Whaling Event are used as input for the Sentiment Analysis Task.
   
### Sentiment Analysis Task on News articles (DS1) (click <a href="https://raw.githubusercontent.com/CrowdTruth/Salience-In-News-And-Tweets/master/img/tasksentimentnews.jpg" target="_blank">here</a> to enlarge the picture and read the crowdsourcing task instructions)
![Fig.1: CrowdTruth Workflow for Identifying Salient Features in News - DS1.](https://raw.githubusercontent.com/CrowdTruth/Salience-In-News-And-Tweets/master/img/tasksentimentnews-withoutInstructions.jpg)

<a id="taskrelevancetweets"></a>

### Relevance Analysis Task on Tweets (DS2&DS3) (click <a href="https://raw.githubusercontent.com/CrowdTruth/Salience-In-News-And-Tweets/master/img/taskrelevancetweets.jpg" target="_blank">here</a> to enlarge the picture and read the crowdsourcing task instructions)
![Fig.2: CrowdTruth Workflow for Identifying Salient Features in Tweets 2014 - DS2 & Tweets 2015 - DS3.](https://raw.githubusercontent.com/CrowdTruth/Salience-In-News-And-Tweets/master/img/taskrelevancetweets-withoutInstructions.jpg)

<a id="tasksentimenttweets"></a>

The relevant Tweets to the Whaling Event are used as input for the Sentiment Analysis Task on Tweets

### Sentiment Analysis Task on Tweets (DS2&DS3) (click <a href="https://raw.githubusercontent.com/CrowdTruth/Salience-In-News-And-Tweets/master/img/tasksentimenttweets.jpg" target="_blank">here</a> to enlarge the picture and read the crowdsourcing task instructions)
![Fig.2: CrowdTruth Workflow for Identifying Salient Features in Tweets 2014 - DS2 & Tweets 2015 - DS3.](https://raw.githubusercontent.com/CrowdTruth/Salience-In-News-And-Tweets/master/img/tasksentimenttweets-withoutInstructions.jpg)
