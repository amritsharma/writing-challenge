# How To Build A Twitter Bot with Postman (In Under 20 Minutes)

This is a story about how I built a twitter bot, @AppleTesla, in 20 minutes with Postman. Frankly, it doesn't do much. Everyday it checks if www.apple.com/tesla is still returning a 404 Page Not Found error and tweets a "no". That's it.

![Apple Tesla](https://i.imgur.com/ZwtUFpZ.png)

Look. I know, I know. It's a terrible bot idea and Apple is not going to acquire Tesla anymore. 

But, almost exactly six years ago, the [rumor mill](https://www.linkedin.com/pulse/apple-buy-tesla-75b-18-months-jason-calacanis/) on twitter was abuzz with speculation that Apple may pull the trigger and buy Tesla. They almost got it right. Recently Elon Musk revealed that he did [reach out to Tim Cook](https://twitter.com/elonmusk/status/1341485211209637889?s=20) during the "dark days" of Model 3 production to have that conversation. But Tim gave him the cold shoulder.

Anyways, I was intrigued and signed up on twitter with a new handle: @AppleTesla.

So far I have sporadically tweeted a cheeky "no" from this account, maybe a few dozen times. This week I sat down with Postman and automated it in 20 minutes. 

Let's go through it step by step.

## Idea: @AppleTesla
Tweet "no" (or a slight variation of it) every day at 1pm EST if www.apple.com/tesla returns a 404 Page Not Found error. 


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


### Possibilities 

Integrate with Email? Text? Slack? Spotify? Tweets? Weather? Air quality? If there's an API for it, you can at the very least build an MVP for it within Postman. No IDEs, no server, no serverless, heck - no costs. You can create Collections on Postman and run them regularly with some generous usage limits on the FREE tier. If you find yourself hitting those limits, $12/month for the Team tier subscription is a steal.
