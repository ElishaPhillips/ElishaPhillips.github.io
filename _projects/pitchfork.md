---
title: 'Pitchfork Music Reviews'
subtitle: 'Exploratory NLP and Sentiment Analysis'
date: 2021-11-14 00:00:00
description: Extracting critical features from published charge stability datasets measured from two Si Quantum Dots.
featured_image: AdobeStock_320419547.png
gallery_images:
  - AdobeStock_320419547.png
---
# Motivating Questions

Initial Questions:

Are there any notable keywords or phrases that Pitchfork tends to use for negative reviews? How
about for positive or average reviews? Over the years cataloged do any genres show trends of becoming more positively or negatively reviewed?

# Data Process

I sourced my data from David Nolan's web scrape of all Pitchfork reviews from 1999-2017
  
  https://www.kaggle.com/nolanbconaway/pitchfork-data
  
I exported the individual tables through RazorSQL, and used RStudio to compile. Cleaning involved filtering out duplicate reviews, and filling missing data. I compiled all the albums without genre tags as "Miscellaneous", and albums missing a release date I copied over the Pitchfork review year. I split the datasets according to genre to perform further analysis. 

# Visualization

![Pitchfork Average Scores](https://github.com/ElishaPhillips/DATA-115-Personal-Dataset-Project/blob/main/Analysis/Main/PitchforkAverageScoresGenre.png)

The initial overview by album release year shows how albums from previous years selected for review following Pitchfork's inception in 1999 trend towards a higher rating.This is when Pitchfork started reviewing content, and anything published before 1999 was selected as a classic review - hence the higher average scores, and the more scattered distribution.There is a few key outliers, such as Metal in 2001, and Experimental in 2000.

![Pitchfork Score Distribution Boxplot](https://github.com/ElishaPhillips/DATA-115-Personal-Dataset-Project/blob/main/Analysis/Main/PitchforkGenreScoreBoxplot.png)

To investigate the distributional characteristics, I made a boxplot, sorted by genre. The median scores all hover around 7.0-7.5, and the overall distribution is either centered or slightly left skewed. Rock clearly holds the largest number of scores, and Global trends towards the highest median while being the lowest sample size.

# Analytical Technique

# Sentiment Analysis 

I utilized Sentimentr to analyze the content of the reviews, after splitting off into separate genres. I chose to focus on Rock, as it had the largest sample set. SentimentR uses negative weighted valence shifters to attempt to mitigate some of the issues inherent to NLP by adding emotive context, more than simply analysing a word. I plotted the sentiment points measured by wach album, categorized by emotion, and looked at the distribution across their scoring system. Whats interesting to note is the emotive score itself tends to have a fairly consistent linear distribution, the emotive weight being stronger as you approach a higher score.

#### Rock Main Sentiment Analysis:

![a](https://github.com/ElishaPhillips/DATA-115-Personal-Dataset-Project/blob/c7a42b0addbbdc805b3f822c0fa95e866f85458a/Analysis/Sentiment/PitchforkRockEmotionAlbumMainJitter.png)

#### Rock Sentiment Scores:

![a](https://github.com/ElishaPhillips/DATA-115-Personal-Dataset-Project/blob/c7a42b0addbbdc805b3f822c0fa95e866f85458a/Analysis/Sentiment/PitchforkRockSentimentAlbum.png)

![a](https://github.com/ElishaPhillips/DATA-115-Personal-Dataset-Project/blob/c7a42b0addbbdc805b3f822c0fa95e866f85458a/Analysis/Sentiment/PitchforkRockSentimentScore.png)

# Keyword Analysis 
Here, I focused on the Metal genre. My processing steps involved using UDPipe to annotate the UPOS and SentimentR to extract the individual sentences out of each review. Each word was categorized to positive, negative, or neutral and I cleaned the data further by filtering down to Nouns, Adjectives, and Verbs. Any punctuation or stopwords were removed as well. Focusing on the Positive/Negative words I filtered out a smaller sample set of 400 words: 200 from the most frequent 200 words, and 200 that was randomly split along the remaining set. 

I then aggregated the total count and total review score for each word, plotting in an interactive HTML plot to be able to view and select each keyword and look at the relevant score, frequency and sentiment. 

![a](https://github.com/ElishaPhillips/DATA-115-Personal-Dataset-Project/blob/cd79a32e2d9a7a2982957b2134e64985c71ec9bb/Analysis/Sentiment/Graph.PNG)

Results:

The most commonly used keywords:

> Black [Negative] Frequency: 504 Avg Score: 6.85

> New [Positive] Frequency: 437 Avg Score: 6.24

> Death [Negative] Frequency: 362 Avg Score: 6.70

> Work [Positive] Frequency: 254 Avg Score: 6.56

> Best [Positive] Frequency: 232 Avg Score: 6.41

> Well [Positive] Frequency: 219 Avg Score: 6.41

> Noise [Negative] Frequency: 192 Avg Score: 6.75

> Doom [Positive] Frequency: 183 Avg Score: 7.03 

<iframe title="D2" aria-label="Interactive line chart" id="D23D" src="/images/projects/Pitchfork/pitchforkmetal.html" scrolling="no" frameborder="0" style="width: 0; min-width: 200% !important; border: none;" height=1024></iframe>  

<script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(e){if(void 0!==e.data["datawrapper-height"]){var t=document.querySelectorAll("iframe");for(var a in e.data["datawrapper-height"])for(var r=0;r<t.length;r++){if(t[r].contentWindow===e.source)t[r].style.height=e.data["datawrapper-height"][a]+"px"}}}))}();</script>  
	


_All graphs used in this project can be downloaded from ['/projects/Pitchfork'](https://github.com/ElishaPhillips/ElishaPhillips.github.io/tree/main/images/projects/Pitchfork/)_

 
[^1]: Zwerver, A. M. J. et al. “Qubits made by advanced semiconductor manufacturing.” (2021).
		[https://arxiv.org/abs/2101.12650v1](https://arxiv.org/abs/2101.12650v1)
	


	

