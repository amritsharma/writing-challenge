## Exponential Backoff

### What is it?
Imagine this. Nowadays whether you're building a mobile app, launching a website or writing a script, you're almost certainly going to be working with APIs. *Exponential backoff* is an error-handling strategy for building resilient systems, while treating the APIs you rely on with respect.

An API responds with a 5xx status code when soemthing goes wrong on the server side while attempting to process your request. It could be any of 5xx codes, but typically you'll experience request timeouts (501) or a generic "internal server error" (500). 

Timeouts occurs when the requests takes too long to process and the servers terminates the connection. Meanwhile, the "internal server error" is a broad message that doesn't give you much information other than your request failed because of something on the server-side.  

What should you do when you get an error from an API? Should you re-try right away? How many times? When?

### Life with Exponential Backoffs

When a server fails to respond to your request, exponential backoffs mean you ought to retry the request multiple times but at an exponentially decreasing pace.

* Make a request to the API.
* If it fails, retry after 1 second. 
* If it fails again, retry after 2 seconds.
* If it fails again, retry after 4 seconds.
* If it fails again, retry after 8 seconds.
* If it fails again, retry after 16 seconds.
* ...
* If it fails again after a pre-defined number of attempts or when the backoff exceeds a length, assume the service is down and stop retrying for now.

### Why is it important?
Exponential backs are a win-win for the API and you. These are the potential challenges you and the API may experience without it.

#### Potential challenges for you:
* API access may be revoked due to excessive API calls
* If it's a paid API, not limiting your API calls with this approach can get very expensive
* Wasted resources in making API calls to a service that is returning the same response repeatedly and is possibly down.

#### Potential challenges for API:
* If the API doesn't enforce API usage limits automatically, it will continue to receive an enormous number of calls until the offender's access is manually revoked.
* Multiple API calls in quick succession when service is down can hamper efforts to get it back up and running.
* If it's a free API, there's no financial disincentive to making lots of API calls without regard.



