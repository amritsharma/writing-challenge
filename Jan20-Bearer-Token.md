## What does "bearer" in bearer token mean? 

![Bearer](https://imgur.com/3qvV7a5.png)

*a person or thing that carries or holds something*

Bearer is an odd word in the English language because we don't use too often. The most common use of the word that I've come across is "the bearer of bad news." 

#### Bearer Tokens 101
API providers may issue bearer tokens, which are short hexadecimal characters, to users for authentication. They're predominantly used with OAuth 2.0. 

#### What does it really mean to have a bearer token?
In a nutshell, it means: If you have this token, it belongs to you (the bearer) and you are who you claim to be.

As a developer using an API, a bearer token allows you to have a secure means of authenticating your API requests. Once you have received or generated your access token, that is all you need to authenticate your subsequent requests -- until that token expires.


#### Example: Twitter 
The Twitter API's bearer token is a combination of the "API key" and "API secret key" which you access from the [Twitter App Dashboard](https://developer.twitter.com/content/developer-twitter/en/apps). It is critical that you protect your tokens because unless you manually reset them, they never expire.

#### Example: ecobee's Zeus API
The Zeus API at ecobee is a B2B offering that also uses OAuth 2.0 authenication. The Bearer Tokens here are called "access tokens" and they expire every 60 minutes. When you generate an access token with an API call to the /auth endpoint using your username and password, you also receive a refresh token. This refresh token can be used to get a fresh access token without having to send your credentials to ecobee again.

In both cases, Twitter and ecobee, when you have a valid bearer token with you, you're free to send any API requests as long as you include that token in your request header. That is what tells the servers receiving your API calls that you have been authenticated and the request may be processed.

~fin~
