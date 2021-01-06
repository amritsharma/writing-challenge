## How can I get last week's air quality data for my city from OpenAQ?

During the winter in 2016, I found myself frantically searching for an answer to a very simple question: "Why isn't sky blue?" 

It should be, right?

But in Northern India during winter, it isn't. Not even close. It's gray, depressing and suffocating. Sunshine barely makes it through the thick layer of smog above the city that more than 46 million people call home. On a good day, air quality levels are *very unhealthy*. Otherwise, it's downright *hazardous*. That's not my opinion, by the way. That's precisely what the US EPA says it is based on the air quality measurements.

That's where OpenAQ comes in. Among other things, OpenAQ is an API for anyone to access near real-time data from air quality monitoring stations in New Delhi and around the world. It is magical. A one-stop shop for standardized research-grade air quality data from 90+ countries. 

Officially: *OpenAQ is a non-profit organization on a mission to empower people world to fight air inequality and clean their air by harmonizing, sharing, and using open air quality data.*

![OpenAQ logo](https://i.imgur.com/Kgw9ztB.png)

Fast forward to 2021.

Now that I have a couple years of Developer Relations experience under my belt, I have a few ideas for how I contribute to the open source OpenAQ platform as a community member by making it more accessible to developers worldwide.

This article is the first step in that journey.

A frequently asked question on the OpenAQ slack channel is: "How can I get last week's air quality data for my city from OpenAQ?"

If this is new to you or you are non-technical, I recommend using [@dolugen’s website](https://dolugen.github.io/openaq-browser/#/measurements). Once you’re happy with your city/date/other selectors, then you can look at the AQ data as a table, export as CSV or even copy and paste the full URL at the top of the page for future API calls.

You can use the `/measurements` API endpoint to get air quality data for any country/city/location in a date range, along with several other selectors as well.

For example: This is the what the API call to get PM2.5 data for the first 5 days of 2020 in Kathmandu, Nepal looks like:  https://api.openaq.org/v1/measurements?country=NP&city=Kathmandu&parameter=pm25&date_from=2020-01-01&date_to=2020-12-05

