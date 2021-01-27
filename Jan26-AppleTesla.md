# How To Build A Twitter Bot with Postman (In Under 20 Minutes)

This is a story about how I built a twitter bot, @AppleTesla, in 20 minutes. Frankly, it doesn't do much. Everyday it keeps an eye out for me to see whether Apple has acquired Tesla yet or not. That's it.

Look. I know, I know. It's not gonna happen anymore. Tesla isn't strapped for cash anymore, and Apple is doing their own thing. But that's not the point.

Market cap TABLE:
2017 and 2021
Apple X, X
Tesla X, X

*If a tree falls in a forest and no one is around to hear it, does it make a sound?*

If you have an idea, buy a domain for it, work on it for a few hours/days/weeks, but never launch, because.... oh I have another idea!

Side projects that need to do something simple. The dreaded email from Hover telling me that yet another domain I bought for a side project I never launched is going to expire in a week and it's going to be $13.99 for another year, where let's be honest, it may or may not see the light of day.


But back in day, In 20XX, the rumor mill was running and twitter was abuzz about whether Apple was about to acquire Tesla. I was intrigued. A couple nights after I heard Jason Calicanis' inteview on CNBC, in my probably coffee-infused late-night (procrastinating from) work sessions, I created a new account  Has Apple acquired Tesla yet? 

After a couple years of sporadically tweeting from this account a few dozen times, this week I sat down with Postman and automated it for good in 20 minutes. It would have taken me even less time if it wasn't my first time.

Let's go.


### Step 1. Twitter API keys.

Sign up for Twitter. Apply to become a developer. Wait for approval. Create app. (screenshot). Grab credentials. 
v1 API only. OAuth 1.0: Consumer Key, Consumer Secret, Access Token and the Token Secret. Twitter v2 API in beta uses OAuth 2.0 where all you need is a bearer token, but sending a tweet (aka, "POST update status") is not available yet.
SCREENSHOT of twitter UI.

### 2. Step 2. Check Apple.

Check whether Apple has acquired Twitter yet. GET that URL.
Ping the https://www.apple.com/tesla URL to check whether you still get a 404 Page Not Found, indicating that no, apple has not acquired Tesla yet.
 

In the "Tests" tab, write some javascript that checks whether it's a 404 and save a message you want to send in the `tweet_message` environment variable.
Either way, set environment variable in Postman with a tweet message. 
SCREENSHOT of request + javascript

### Step 3. Send the tweet.


POST Update Status.
Create Twitter request in Postman. 

### Step 4. Use Postman Monitors to schedule this collection to run everyday, or as frequently as you'd like.
Monitors are cron jobs within Postman. It works and creates a report that you can 

