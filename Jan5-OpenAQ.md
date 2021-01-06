## How can I get last week's air quality data for my city from OpenAQ?

During the winter in 2016, I found myself frantically searching for an answer to a very simple question: "Why isn't sky blue?" 

It should be, right?

But in Northern India, it wasn't. Not even close. It was gray, depressing and suffocating. Sunshine barely made it through the thick layer of smog above the city that more than 46 million people call home. On a good day, air quality levels are *very unhealthy*. Otherwise, it's downright *hazardous*. That's not my opinion, by the way. That's precisely what the US EPA (Environment Protection Agency) says it is based on the air quality measurements.

That's where OpenAQ comes in. Among other things, OpenAQ is an API for anyone to access near real-time data from air quality monitoring stations in New Delhi and around the world. It is magical. A one-stop shop for standardized research-grade air quality data from 90+ countries. 

Officially: *OpenAQ is a non-profit organization on a mission to empower people world to fight air inequality and clean their air by harmonizing, sharing, and using open air quality data.*

![OpenAQ logo](https://i.imgur.com/Kgw9ztB.png)

### Fast forward to 2021

Now that I have a couple years of Developer Relations experience under my belt, I have a few ideas for how I contribute to the open source OpenAQ platform as a community member by making it more accessible to developers worldwide.

This article is the first step in that journey.

### One Small Step

A frequently asked question on the OpenAQ slack channel is: **"How can I get last week's air quality data for my city from OpenAQ?"**

#### 1. Non-technical Approach
If this is new to OpenAQ or you are non-technical, I recommend using [@dolugen’s website](https://dolugen.github.io/openaq-browser/#/measurements). Once you’re happy with your city/date/other selectors, then you can look at the AQ data as a table, export as CSV or even copy and paste the full URL at the top of the page for future API calls.

![OpenAQ GUI by Dolugen](https://i.imgur.com/ojykyQi.png)

#### 2. Overview 
The [`/measurements`](https://docs.openaq.org/#api-Measurements-GetV1Measurements) endpoint in the OpenAQ API is designed for you to get air quality data for any country, city or specific air quality monitor within a date range, and other filtering criteria.

For example: This is the what the API call to get PM2.5 pollutant data for the first 5 days of 2021 from all air quality monitoring stations in Pune, India looks like: https://api.openaq.org/v1/measurements?country=IN&city=Pune&parameter=pm25&date_from=2021-01-01&date_to=2021-01-05

| Filter        | Value           | Required  |
| ------------- |:-------------:| -----:|
| country      | IN | No |
| city      | Pune      |   No |
| parameter | pm25      |    No |
| date_from | 2021-01-01      |    No |
| date_to | 2021-01-05      |    No |


#### 3. Export as CSV or JSON
By default, the API response will be a JSON object. You can append `&format=csv` to the API call.

#### 4. Understanding the API Response 

The API response contains a block for every measurement that matches your criteria in the OpenAQ database.

| Field        | Value           |
| ------------- |:-------------:|
| location      | Karve Road, Pune - MPCB	 |
| city, country      | Pune, IN      |
| parameter | pm25      |
| value      | 45.6      |
| unit | µg/m³      |
| coordinates | 18.5011743, 73.8165527	      |
| date.local | 2021 Jan 2, 10:45:00      |

What does this block tell us? The air quality station at `Kavre Road, Pune - MPCB` in Pune, India recorded PM2.5 levels at 45.6µg/m³ on Jan 2, 2021 10:45am. This station on Kavre Road is at `18.5011743, 73.8165527` coordinates.

~
