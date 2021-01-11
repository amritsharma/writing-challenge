## Exponential Backoff

### What is it?
Imagine this. Whether you're building a mobile app, launching a website or writing a script, you're almost certainly going to be working with APIs. Exponential Backoff is an error-handling strategy for building resilient systems, while treating APIs with respect.

An API responds with a 5xx status code when soemthing goes wrong on the server side while attempting to process your request. It could be any of 5xx codes, but typically you'll experience request timeouts (501) or a generic "internal server error" (500). 

Timeouts occurs when the requests takes too long to process and the servers terminates the connection. Meanwhile, the "internal server error" is a broad message that doesn't give you much information other than your request failed because of something on the server-side.  

What should you do when you get an error from an API? Should you re-try right away? How many times? When?

### Life with Exponential Backoffs

When a server fails to respond to your request, exponential backoffs mean you ought to retry the request multiple times but at an exponentially decreasing pace.

* When a request fails with a 5XX status code, retry it right away.
* If it fails again, retry after 1 second. 
* If it fails again, retry after 2 seconds.
* If it fails again, retry after 4 seconds.
* If it fails again, retry after 8 seconds.
* If it fails again, retry after 16 seconds.
* ...
* If it fails again after X attempts, assume the service is down and wait stop retrying until later.   

### Why is it important?
Exponential backs are a win-win for the API and you. These are the potential challenges you and the API may experience without it.

TKTK

#### Potential challenges for you:
- API access revoked
- Very expensive (if paid API)
- Lots of errors. No change in response.

#### Potential challenges for API:
- excessive API calls that all return errors
- more load on servers


