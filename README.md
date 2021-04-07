# Text Analysis, Natural Language Processing, and Social Media Data in Python

<a href="http://creativecommons.org/licenses/by-nc/4.0/" rel="license"><img style="border-width: 0;" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" alt="Creative Commons License" /></a>
This tutorial is licensed under a <a href="http://creativecommons.org/licenses/by-nc/4.0/" rel="license">Creative Commons Attribution-NonCommercial 4.0 International License</a>.

# Table of Contents

- [Overview](#overview)
- [The Investigation](#the-investigation)
- [The Data](#the-data)
- [Exploratory Data Analysis](#exploratory-data-analysis)
  * [Example 1](#example-1)
  * [Example 2](#example-2)
- [Your Turn: Exploratory Data Analysis](#your-turn-exploratory-data-analysis)
  * [Load Data as Pandas DataFrame](#load-data-as-pandas-dataframe)
  * [Exploratory Data Analysis in Pandas](#exploratory-data-analysis-in-pandas)
    * [Visualization in Pandas](#visualization-in-pandas)
  * [From DataFrame to Text File](#from-dataframe-to-text-file)
  * [Text Analysis Using Voyant Tools](#text-analysis-using-voyant-tools)
  * [Natural Language Processing Using NLTK](#natural-language-processing-using-nltk)
    * [Loading NLTK](#loading-nltk)
    * [Different Options for Tokenizing using NLTK](#different-options-for-tokenizing-using-nltk)
    * [Analyzing Term Frequency](#analyzing-term-frequency)
- [Putting It All Together](#putting-it-all-together)
- [Lab Notebook Components](#lab-notebook-components)

# Overview

In her 2018 book *Algorithms of Oppression*, Safiya Umoja Noble highlights the "algorithmically driven data failures that are specific to people of color and women," arguing these systems "undescore the structural ways that racism and sexism are fundamental to what I have coined *algorithmic oppression*" (4).

Noble calls for "all the voices to come to the fore and impact public policy on the most unregulated social experiment of our times: the Internet" (6).

Thinking about the chapters we read from *Algorithms of Oppression*....

Discussion questions:
- What stood out to you from Chapter 1's opening story about the UN Women campaign?
  * What connections can we make with the author’s broader framework of algorithmic oppression?

- One of the arguments Noble makes in analyzing the UN Women campaign is how efforts to raise awareness often “reinforce the idea that it is not the search engine that is the problem but, rather, the users of search engines who are” (15). What connections can we make with conversations taking place about other social media platforms, in relation to content moderation, protected speech, etc.?

- What stood out to you from Chapter 3's opening narrative about the 2015 massacre that took place at Charleston’s Mother Emanuel African Methodist Episcopal Church?
  *  connections can we make with the author’s broader framework of algorithmic oppression?

- What connections can we make with race and surveillance? Or, where do we see race and surveillance at work?

- What could it look like to push back on the framing of search results as a neutral, objective representation of reality? 

- How do we think more critically about whose interests are prioritized and/or promoted in the digital information landscape?

- Other observations, comments, or questions from these chapters.

Quotes to consider from Chapter 1:

- “What I find troubling is that the [UN Women] campaign also reinforces the idea that it is not the search engine that is the problem but, rather, the users of search engines who are. It suggests that what is most popular is simply what rises to the top of the pile. While serving as an important and disturbing critique of swexist attitudes, the campaign fails to implicate the algorithms or search engines that drive certain results to the top” (15-16)

- “Our work...is about interrogating the many ways that data and computing have become so profoundly their own ‘truth’ that even in the face of evidence, the public still struggles to hold tech companies accountable for the products and errors of their ways. These errors increasingly lead to racial and gender profiling, misrepresentation, and even economic redlining” (27-28)

- “I contend that there is work to be done to contextualize and reveal the many ways that Black women are embedded within the most popular commercial search engine--Google Search--and that this embeddedness warrants an exploration into the complexities of whether the content surfaced is a result of popularity, credibility, commerciality, or even a combination thereof” (63)

Quotes to consider from Chapter 3:

- “The provision of false information that purports to be credible news, and the devastating consequences that can come from this kind of algorithmically driven information, is an example of why we cannot afford to outsource and privatize uncurated information on the increasingly neoliberal, privatized web” (11)

- “It is critical that we think about the implications of people who are attempting to vet information in the news media about race and race relations and who are led to fascist, conservative, anti-Black, anti-Jewish, and/or White supremacist websites. The power of search engines to lead people to a breadth and depth of information cannot be more powerfully illustrated than by looking at Dylann Roof’s own alleged words about using Google to find information about the Trayvon Martin murder, which led to his racial identity development” (115)

- “What we find in search engines about people and culture is important. They oversimplify complex phenomena. They obscure any struggle over understanding, and they can mask history. Search results can reframe our thinking and deny us the ability to engage deeply with essential information and knowledge we need...Search results, in the context of commercial advertising companies, lay the groundwork...for implicit bias” (116)

# The Investigation

It doesn't take very long to find numerous examples of the racist and sexist power structures reinforced and exacerbated via internet technologies and social media platforms- *Algorithms of Oppression* presents and analyzes numerous examples of these phenomena.

But we can also think about how race, surveillance, and internet technology intersect in less visible but significant ways.

We'll think about those less-visible intersections through looking at a specific case study- targeted use of social media by Russian individuals and organizations, designed to influence the outcome of the 2016 U.S. presidential election.

To start, read U.S. House of Representatives Permanent Select Committee on Intelligence, “[Exposing Russia’s Effort to Sow Discord Online: The Internet Research Agency and Advertisements](https://intelligence.house.gov/social-media-content/default.aspx)” *U.S. House of Representatives* (16 February 2018).
- [Link to the full report](https://www.justice.gov/storage/report.pdf)

Additional background and reporting:
- Background
  * Adrian Chen, "[The Agency](https://www.nytimes.com/2015/06/07/magazine/the-agency.html?_r=0)" *New York Times* (2 June 2015)
  * [Internet Reserach Agency, Wikipedia](https://en.wikipedia.org/wiki/Internet_Research_Agency)
- News coverage
  * Alana Abramson, "[Facebook Says Russian Accounts Bought $100,000 in Ads During the 2016 Election](https://time.com/4930532/facebook-russian-accounts-2016-election/)" *Time* (6 September 2017)
  * Sam Levin, "[Did Russia fake black activism on Facebook to sow division in the US?](https://www.theguardian.com/technology/2017/sep/30/blacktivist-facebook-account-russia-us-election)" *The Guardian* (30 September 2017)
  * Mike Isaac and Scott Shane, "[Facebook's Russia-Linked Ads Came in Many Disguises](https://www.nytimes.com/2017/10/02/technology/facebook-russia-ads-.html)" *New York Times* (2 October 2017)
  * Karen Yourish, Larry Buchanan and Derek Watkins, "[The Plot to Subvert an Election: A Timeline Showing the Full Scale of Russia’s Unprecedented Interference in the 2016 Election, and Its Aftermath](https://www.nytimes.com/interactive/2018/09/20/us/politics/russia-trump-election-timeline.html)" *New York Times* (20 September 2018)
  * Nicholas Thompson, "[How Russian Trolls Used Meme Warfare to Divide America](https://www.wired.com/story/russia-ira-propaganda-senate-report/)" *Wired* (17 December 2018)
  * Ryan Broderick, "[Here's Everything The Muller Report Says About How Russian Trolls Used Social Media](https://www.buzzfeednews.com/article/ryanhatesthis/mueller-report-internet-research-agency-detailed-2016)" *Buzzfeed* (18 April 2019)
- Reports
  * New Knowledge, "[The Tactics and Tropes of the Internet Research Agency](https://assets.documentcloud.org/documents/5631777/Whitepaper-Final.pdf)" *white paper* (2018)
  * Special Counsel Robert S. Muller, III, "[Report On The Investigation Into Russian Interference In The 2016 Presidential Election](https://www.justice.gov/storage/report.pdf)" (March 2019)

Discussion questions:
- What happened?
- Who was involved?
- How did we find out?
- What was the goal/purpose of the targeted ads?
- What kinds of technology (or technology platforms) were targeted?
- Other comments/questions/observations

# The Data

The data collected via the Congressional investigation and Special Counsel's report was made public.

To get a sense of what kinds of Facebook advertisements we're talking about here, explore U.S. House of Representatives Permanent Select Committee on Intelligence, “[Social Media Advertisements](https://intelligence.house.gov/social-media-content/social-media-advertisements.htm)” U.S. House of Representatives (2018).

Thousands of PDFs are great, but not exactly a dataset that we can interact with using computational tools.

Ed Summers at the University of Maryland Institute for Technology in the Humanities (MITH) developed a Python-based program that extracts text from the redacted PDFs.

The extracted images and metadata are published online via the [`irads project` GitHub repository](https://github.com/umd-mith/irads).

Next, let's explore [that GitHub repository](https://github.com/umd-mith/irads) to get a sense of what metadata is available for these advertisements.

Discussion questions:
- From available info, what steps were taken to extract data/images from the PDFs?
- How is the data structured, or how is the data made available via this repo?
- What data points are included? What are you seeing in this dataset?
- What might be next, or what questions could you ask using this data?
- Other questions/comments/observations

# Exploratory Data Analysis

Let's look at two projects that present this data in a searcheable, exploratory interface.

## Example 1

First, let's look at the [Internet Research Agency Ads](https://archive.mith.umd.edu/irads/about.html) digital project developed by students at the University of Maryland and the Maryland Institute for Technology in the Humanities (MITH).

Discuss what you are seeing with a colleague/colleagues:
- How is the data presented in this project?
- What's the distance between the original data source and this presentation interface?
- What choices or additional interpretive decisions were made as part of that data transformation process?
- What observations/analysis/etc. would you take away from this dataset after interacting with this project?
- What other questions do you have about this data after exploring this project?
- Other questions/comments/observations

## Example 2

Next, let's look at Simon Willison's "Analyzing US Election Russian Facebook Ads" project:
- [Blog post](https://simonwillison.net/2018/Aug/6/russian-facebook-ads/)
- [Searchable interface](https://russian-ira-facebook-ads.datasettes.com/)

Discuss what you are seeing with a colleague/colleagues:
- How is the data presented in this project?
- What's the distance between the original data source and this presentation interface?
- What choices or additional interpretive decisions were made as part of that data transformation process?
- What observations/analysis/etc. would you take away from this dataset after interacting with this project?
- What other questions do you have about this data after exploring this project?
- Other questions/comments/observations


# Your Turn: Exploratory Data Analysis

We've looked at the underlying data as well as a couple of projects that analyze this data.

Now it's your turn to think about what types of questions or analysis you want to perform on this dataset.

Step 1- Consider what fields are included in the underlying dataset.

Step 2- Think about what questions you might want to ask of this data.

Step 3- Load the data as a `pandas` data frame.

Step 4- Explore the data and start to tackle your research questions in a programming environment

## Load Data As Pandas DataFrame

```Python
# import pandas
import pandas as pd

# load data as pandas dataframe from file
irads = pd.read_csv("index_irads.csv")

irads
```

```Python
# import pandas
import pandas as pd

# load data as pandas dataframe from URL
irads = pd.read_csv("https://raw.githubusercontent.com/kwaldenphd/social-media-targeted-advertising/main/index_irads.csv")

irads
```

## Exploratory Data Analysis in Pandas

```Python
# show data types
irads.dtypes

# show dataframe info
irads.info()

# show summary statistics
irads.describe()
```

```Python
# sort ad vaues by cost (descending sort)

irads.sort_values(by=["cost"], ascending=False).head()
```

```Python
# sort by number of impressions, descending

irads.sort_values(by="impressions", ascending=False).head()
```

```Python
# sort by number of clicks, descending

irads.sort_values(by="clicks", ascending=False).head()
```

```Python
# sort by number of impressions and cost (descending)

irads.sort_values(by=['clicks', 'cost'], ascending=False).head()
```

```Python
# group titles based on exclusion category 

irads[['title', 'exclude']].groupby('exclude').head()
```

```Python
# number of ads by exclusion category

irads['exclude'].value_counts()
```

```Python
# number of ads by age range

irads['age'].value_counts()
```

For more options on interacting with data in a `DataFrame`: https://github.com/kwaldenphd/pandas-machine-learning-intro#interacting-with-a-dataframe

Other datasets you could explore:
- [`interests.csv`](https://raw.githubusercontent.com/umd-mith/irads/master/analysis/interests.csv) (money, clicks, impressions, number of ads, interest)
- [`people_who_match.csv`](https://raw.githubusercontent.com/umd-mith/irads/master/analysis/people_who_match.csv) (money, clicks, impressions, number of ads, people type who match

# Vizualization in Pandas

```Python
# import pandas
import pandas as pd

# load data

interests = pd.read_csv("https://raw.githubusercontent.com/umd-mith/irads/master/analysis/interests.csv")

interests
```

```Python
# quick visual check of the data using pandas built-in plotting function

# import matplotlib
import matplotlib.pyplot as plt

# generate plot
interests.plot()

# show plot
plt.show()
```

```Python
# customize plot showing number of ads by cost

interests.plot.scatter(x='money (RUB)', y='ads', alpha=0.5)
```

```Python
# create new data frame for ads with over 100000 clicks

top_interests = interests.loc[interests['clicks']>100000]

top_interests
```

```Python
# plot number of impressions by interest
top_interests.plot.barh(x='interest', y='impressions', alpha=0.5)
```

For more on plotting data in a `dataframe`: https://github.com/kwaldenphd/more-with-matplotlib

# From DataFrame to Text File

```Python
# test for not null values

irads[irads["title"].notna()]
```

```Python
# create data frame from not null fields
text = irads[irads["description"].notna()]

text = text["description"]

text.head()
```

```Python
# write ad text column to txt file
text.to_csv('irads_text.txt', index=False)
```

# Text Analysis Using Voyant Tools

<a href="http://voyant-tools.org/">Voyant Tools</a> is an open-source web application developed by Stéfan Sinclair and Geoffrey Rockwell in 2003, with later contributions added by Andrew MacDonald, Cyril Briquet, Lisa Goddard, and Mark Turcato. While Voyant is one of the leading robust web-based textual analysis interfaces, it grew out of existing text analysis tools like HyperPo, Tapoware, and TACT. Voyant also offers <a href="https://github.com/sgsinclair/Voyant">open-source code</a> that can be used to deploy the program on a server. Voyant users can upload text files from their computer, link to online text sources, or scrape the text off a webpage for analysis and visualization. Unlike more advanced, programming-oriented textual analysis programs like R and R Studio, Voyant gives users access to a range statistical analysis and visualization features without requiring significant technical knowledge.

Download the newly-created text file.

Open a web browser (preferably Firefox or Chrome) and navigate to the <a href="http://voyant-tools.org/">Voyant Tools homepage</a>.

<p align="center"><a href="https://github.com/kwaldenphd/Voyant-tutorial/blob/master/screenshots/Capture_1.PNG?raw=true"><img class="aligncenter size-large wp-image-549" src="https://github.com/kwaldenphd/Voyant-tutorial/blob/master/screenshots/Capture_1.PNG?raw=true" alt="" width="676" height="523" /></a></p>

Upload the file and click Reveal.

<p align="center"><a href="https://github.com/kwaldenphd/Voyant-tutorial/blob/master/screenshots/Capture_2.PNG?raw=true"><img class="aligncenter size-large wp-image-550" src="https://github.com/kwaldenphd/Voyant-tutorial/blob/master/screenshots/Capture_2.PNG?raw=true" alt="" width="676" height="355" /></a></p>

Once a text or corpus has been uploaded, Voyant moves into its ‘default skin,’ or primary editing environment.

For more on Voyant's interface and functionality: https://github.com/kwaldenphd/Voyant-tutorial/tree/SPN-285#editing-in-voyant

# Natural Language Processing Using NLTK

"The Natural Language Toolkit (NLTK) is a collection of reusable Python tools (also known as a Python library that help researchers apply a set of computational methods to texts. The tools range from methods of breaking up text into smaller pieces, to identifying whether a word belongs in a given language, to sample texts that researchers can use for training and development purposes (such as the complete text of Moby Dick)." [Zoë Wilkinson Saldaña, "Sentiment Analysis for Exploratory Data Analysis," The Programming Historian 7 (2018), https://doi.org/10.46430/phen0079.]

For more info on NLTK: https://www.nltk.org/

## Loading NLTK

```Python
# load nltk
import sys 
!{sys.executable} -m pip install --user -U nltk
```

```Python
# import nltk
import nltk
nltk.download('punkt')
nltk.download('wordnet')
nltk.download('averaged_perceptron_tagger')

from nltk.tag import pos_tag
```
## Different Options for Tokenizing Using NLTK

In Natural Language Processing (NLP), "tokenizing" refers to the process of breaking a large text into smaller units (words or sentences) known as tokens.

NLTK includes a wide range of options for tokenizing text data.

```Python
# tokenize using word_tokenize
from nltk.tokenize import word_tokenize

text_str = str(text)

# text_str
    
word_tokenize(text_str)
```

```Python
# tokenize using TreebankWordTokenizer
from nltk.tokenize import TreebankWordTokenizer

text_str = str(text)

# text_str
    
tokenizer = TreebankWordTokenizer()

tokenizer.tokenize(text_str)
```

```Python
# tokenize using WordPunctTokenizer 
from nltk.tokenize import WordPunctTokenizer

text_str = str(text)

# text_str
    
tokenizer = WordPunctTokenizer()

tokenizer.tokenize(text_str)
```

```Python
#tokenize using RegexpTokenizer
from nltk.tokenize import RegexpTokenizer

text_str = str(text)

# text_str
    
tokenizer = RegexpTokenizer("[\w']+")

regex_words = tokenizer.tokenize(text_str)

regex_words
```

## Analyzing Term Frequency

We can use the most effective tokenizing method for this data in combination with a few other data wrangling steps to output a unique list of words.

```Python
# tokenize using word_tokenize
from nltk.tokenize import word_tokenize

tokens = word_tokenize(text_str)

# convert to lower case
tokens = [w.lower() for w in tokens]

# remove punctuation/special characters
import string
table = str.maketrans('', '', string.punctuation)
stripped = [w.translate(table) for w in tokens]

# remove non-text content
words = [word for word in stripped if word.isalpha()]

# filter out stop words
from nltk.corpus import stopwords

stop_words = set(stopwords.words('english'))

words = [w for w in words if not w in stop_words]

# removes words with fewer than 3 characters
# words = [word for word in words if len(word) > 3]

# output cleaned list of words
print(words)
```
We can then take that list of words and plot term frequency and distribution.

```Python
# import nltk components
import nltk
from nltk.corpus import webtext
from nltk.probability import FreqDist

nltk.download('webtext')

# analyze term frequency/distribution
data_analysis = nltk.FreqDist(words)

data_analysis
```

```Python
# plot term frequency/distribution for all terms
data_analysis.plot()
```

```Python
# show term frequency/distribution for top 10 terms
for word, frequency in data_analysis.most_common(10):
    print(u'{};{}'.format(word, frequency))
```

# Putting It All Together

Discussion questions:
- What kinds of things were you interested in exploring via this dataset?
- How did you approach those questions using computational methods?
  * This could focus on what you did in Python using `pandas` and/or `nltk`
  * You could also think about insights gained from a graphical user interface programs like Voyant Tools
- What kinds of insights were you able to determine?
- How did interacting with this data using computational methods shape your understanding of the data?
- Where would you go next?
- How are you thinking about race and surveillance after engaging with this data?
- Other questions/thoughts/observations

# Lab Notebook Components

The lab notebook consists of a narrative that documents and describes your experience working through this lab.

You can respond to/engage with other discussion questions included in the lab procedure.

But specific questions for the lab notebook (from the "Putting It All Together" section):
- What kinds of things were you interested in exploring via this dataset?
- How did you approach those questions using computational methods?
  * This could focus on what you did in Python using `pandas` and/or `nltk`
  * You could also think about insights gained from a graphical user interface programs like Voyant Tools
- What kinds of insights were you able to determine?
- How did interacting with this data using computational methods shape your understanding of the data?
- Where would you go next?
- How are you thinking about race and surveillance after engaging with this data?
- Other questions/thoughts/observations

I encourage folks to include code + screenshots as part of that narrative.
