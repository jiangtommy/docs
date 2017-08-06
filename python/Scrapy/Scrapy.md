## Scrapy
### Spider
#### class scrapy.spiders.Spider
The simplest spider, which **every other spider must inherit**.   
It just providers a default `start_requests()` implementation which sends requests from the `start_urls` spider attribute and calls the spider's method `parse` for each of the resulting responses.   
##### name
