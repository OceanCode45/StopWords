# StopWords for the bot
Stop Words for the Top Phrases bot

About the bot: 
The bot is a Python script that analyzes the top comments from a specified number of hot posts in a given subreddit and identifies the most common word pairs (phrases) used in those comments. It then generates a bar chart displaying the top phrases and their frequencies, and posts the chart as an image to another specified subreddit.

The script uses the PRAW (Python Reddit API Wrapper) library to interact with the Reddit API, as well as other libraries like Pandas, Seaborn, and Matplotlib for data manipulation and visualization.


In this bot, ignored words are called "Stop Words." These are common words that are often considered uninformative or irrelevant for text analysis because they don't carry much meaning by themselves. Examples of such words include "the," "and," and "i." The purpose of excluding these words is to focus on more meaningful word pairs (phrases) in the comments.

The script defines a set called IGNORED_WORDS that contains these stop words. When processing the comments and extracting word pairs, the script checks each word in the pair against the IGNORED_WORDS set. If either word is found in the set, the word pair is not included in the phrase count.

By ignoring these common stop words, the script can produce a more meaningful analysis of the top phrases used in the comments, concentrating on word pairs that provide more insight into the content and trends within the discussion.
