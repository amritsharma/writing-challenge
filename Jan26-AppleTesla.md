# How To Build A Twitter Bot with Postman (In Under 20 Minutes)

This is a story about how I built a twitter bot, @AppleTesla, in 20 minutes with Postman. Frankly, it doesn't do much. Every afternoon it checks if www.apple.com/tesla is still returning a 404 Page Not Found error and tweets a "no." It's the "Has Apple acquired Tesla yet?" bot. That's it.

![Apple Tesla](https://i.imgur.com/ZwtUFpZ.png)

Credit: [PDL Comics](https://twitter.com/PDLComics/status/1354111867371876352)

Look. I know, I know. It's a terrible bot idea and Apple is not going to acquire Tesla anymore. 

But, almost exactly six years ago, the [rumor mill](https://www.linkedin.com/pulse/apple-buy-tesla-75b-18-months-jason-calacanis/) on twitter was abuzz with speculation that Apple may pull the trigger and buy Tesla. They almost got it right. Recently Elon Musk revealed that he did [reach out to Tim Cook](https://twitter.com/elonmusk/status/1341485211209637889?s=20) during the "dark days" of Model 3 production to have that conversation. But Tim gave him the cold shoulder.

Anyways, I was intrigued and signed up on twitter with a new handle: @AppleTesla.

So far I have sporadically tweeted a cheeky "no" from this account, maybe a few dozen times. This week I sat down with Postman and automated it in 20 minutes. 

Let's go through it step by step.

## Idea: @AppleTesla
Tweet "no" (or a slight variation of it) every day at 1pm EST if www.apple.com/tesla returns a 404 Page Not Found error. 


### Step 1. Twitter API keys.

The Twitter Developer Portal is your one stop shop to organize your twitter app projects and manage your API keys. To get started, you will need to have a twitter account, apply to become a developer and wait for their approval.

Only Twitter's v1 API includes the ability to send a tweet with an API call. When you have set up your project, navigate to the "Keys and Tokens" tab to generate the Consumer Key, Consumer Secret, Access Token and the Token Secret tokens. You will need to include all four of these tokens in the request header to authenticate your API calls. 

Fortunately we only have to deal with OAuth 1.0a with Twitter APIs for a little while longer, v2 of Twitter's APIs use [OAuth 2.0 for authentication](https://developer.twitter.com/en/docs/authentication/overview) where you'll need to send a single bearer token with your requests.


### Step 2. Visit Apple.

In Postman, we'll create our first of two requests for this bot. 

We will ping the https://www.apple.com/tesla URL with a GET request and see what response we get. In the "Tests" tab, I wrote some javascript that checks whether the response has status code 404 Page Not Found, which will tell us that Apple still hasn't acquired Tesla yet. 

Either way, we set the `tweet_message` environment variable in Postman accordingly with the tweet text. 

![GET Apple](https://imgur.com/gPeeWEU.png)


### Step 3. Send the tweet.

Now that the `tweet_message` environment variable has the text we want tweet out. The last thing we need to do is POST request to send the tweet.

![Send tweet](https://i.imgur.com/ujhJVIH.png)


### Step 4. Automate it.

Monitors are like cron jobs within Postman. It allows you to run entire collections automatically everyday or as frequently as you'd like. Postman even creates a nifty report that shows you details and stats about each run.

![Monitors](https://imgur.com/xc6PxB4.png)

That's it.


### Possibilities with Postman

Want to integrate with Email? Text? Slack? Spotify? Tweets? Weather? Air quality? If there's an API for it, you can at the very least build an MVP for your side project within Postman. No IDEs, no servers, no configuration, heck - no costs. You can create Collections and run them regularly with some generous usage limits on Postman's FREE tier. If you find yourself hitting those limits, the $12/month for the Team tier subscription is a steal.
