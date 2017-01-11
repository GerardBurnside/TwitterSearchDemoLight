# TwitterSearchDemoLight
Short demo on new ways to filter Twitter searches

In order to run this small program, you'll need python 3 and Java (JRE) installed and in your PATH variable.
Then you'll need to update the twitter4j.properties file in order to fill out the Twitter API credentials:
-  oauth.consumerKey=
-  oauth.consumerSecret=
-  oauth.accessToken=
-  oauth.accessTokenSecret=
Go to https://apps.twitter.com/app/new in order to create those credentials.

To run the program, simply type "python TwitterSearchDemoLight.py" from the command line.

# How the program works:
- When pressing the "Collect Tweets.." button:
- It collects tweets through Twitter's Search API by performing multiple queries with all possible subsets of keywords entered in the lower textbox (i.e. if you enter 4 keywords, it will ask for tweets containing all 4 keywords, then, if the number of collected tweets is less than 1000, it will ask for all subsets of keywords of size 3, etc. until it reaches the minimum number of tweets).
- The program then sorts the collected tweets according to their similarity with the text entered in the bigger textbox (you should provide at least a full sentence for it to work properly)

The sorted tweets are then displayed in a web page on your default navigator.

Important notes and limitations/restrictions:
- The Twitter Search API only indexes all tweets for the past 6 or 7 days. After that only a limited number of tweets are kept in the index and can be returned by the API. You need to have that in mind when using the demo.
- By default this program is caching the tweets that it retrieves so that subsequent calls with the same keywords are read from cache instead of actually retrieved from the API. This behaviour can be changed:
  - permanently by setting CACHE_EXPIRATION_POLICY=-1
  - for one time only by removing files in the "cache/" directory


