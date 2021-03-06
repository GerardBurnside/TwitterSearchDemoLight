# TwitterSearchDemoLight
Short demo on new ways to filter Twitter searches

## Before running the program
After having unzipped the file, in order to run this small program, you'll need **python 3** (see [Ubuntu instructions](#ubuntu-instructions-to-install-python3)) and **Java** (JRE) installed *and in your PATH variable*.
Then you'll need to update the **twitter4j.properties** file in order to fill out the **Twitter API credentials**:
-  oauth.consumerKey=
-  oauth.consumerSecret=
-  oauth.accessToken=
-  oauth.accessTokenSecret=

You need a Twitter account (Twitter will ask your phone number) in order to create an app:

1. Go to https://apps.twitter.com/app/new

2. Fill the form, e.g.:
  * name: TwitterSearchXYZ
  * description: Whatever XYZ
  * website: any URL will do
  * Don't forget to tick the checkbox

3. In the new page, click on "Keys and Access Tokens" in order to configure **twitter4j.properties** file:

 *  Copy/paste your Consumer Key (API Key) after oauth.consumerKey=
 *  Copy/paste your Consumer Secret (API Secret) after oauth.consumerSecret=
 *  Click on "Create my access token"
  *  Copy/paste your Access Token after oauth.accessToken=
  *  Copy/paste your Access Token Secret after oauth.accessTokenSecret

Your **twitter4j.properties** file should now contain something like:
> oauth.consumerKey=C81lYrTXYZ12xjzhZW7kjZFn7
> oauth.consumerSecret=LsuySrEXYZXYZaGA1gVrSZ1WNXCgXTyGDCYfl4fCyPOfSbJBqP
> oauth.accessToken=821019999998079489-uwuHpkNfR0kd1HkXWUq7ZHv4gajoxba
> oauth.accessTokenSecret=CkneUv6XYZxyzGrtKFGig0cCGjHI2aoLUH0hpa1efW5DN


# Running the Demo

To run the program, simply type `python3 TwitterSearchDemoLight.py` from the command line.

*Depending on your installation, you may use:* `python TwitterSearchDemoLight.py`, *but first make sure that this is version 3 by typing* `python -V`

# How the program works:
- When pressing the "Collect Tweets.." button:
- It collects tweets through Twitter's Search API by performing multiple queries with all possible subsets of keywords entered in the **lower textbox** (i.e. if you enter 4 keywords, it will ask for tweets containing all 4 keywords, then, if the number of collected tweets is less than 1000, it will ask for all subsets of keywords of size 3, etc. until it reaches the minimum number of tweets).
- The program then sorts the collected tweets according to their similarity with the text entered in the **bigger textbox** (you should provide at least a full sentence for it to work properly)

The sorted tweets are then displayed in a web page on your default navigator.

## Important notes and limitations/restrictions:
- The Twitter Search API only indexes tweets for the **past 6 or 7 days**. After that only a limited number of tweets are kept in the index and can be returned by the API. You need to have that in mind when using the demo.
- By default this program is caching the tweets that it retrieves so that subsequent calls with the same keywords are read from cache instead of actually retrieved from the API. This behaviour can be changed:
  - permanently by setting CACHE_EXPIRATION_POLICY=-1 in the *twitterSearch.properties* file
  - for one time only by removing files in the "cache/" directory

### Ubuntu instructions to install python3
> apt-get update

> apt-get updgrade

> apt-get install python3 install python3-tk
