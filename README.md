# Homework 1: Professionalism & Reproducibility 
Regina-Mae Dominguez  
UW MSDS - Autumn 2022 - DATA 512 Human Centered Data Science

This assignment constructs, analysizes, and publishes a dataset of monthly article traffic for a select set of pages, a subset of Dinosaur articles, from English Wikipedia from January 1, 2015 through September 30, 2022. The data is obtained through the Pageviews API.

### API
**Pageviews:** https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews, https://wikimedia.org/api/rest_v1/#!/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end  
The Pageviews API provides access to dektop, mobile-web, and mobile-app traffic data from July 2015. This API can be used to get page views for specific articles, wikipedia projects, or even countries. 

### Datasets 
`dinosaur_genera.cleaned.SEPT.2022.csv` : Dinosaur related articles  

### Outputs
`dino_monthly_mobile_start201501_end202210.json` : JSON file with timeseries views mobile-access data for each dinosaur article from January 1 2015 to September 30, 2022.  
`dino_monthly_desktop_start201501_end202210.json` : JSON file with timeseries views desktop-access data for each dinosaur article from January 1 2015 to September 30, 2022.  
`dino_monthly_cumulative_start201501_end202210.json` : JSON file with timeseries views all-access (mobile + desktop) data for each dinosaur article from January 1 2015 to September 30, 2022.  

## Considerations 
The code requests a big chuck of data when utilizing the API call. For more efficiency, use the API call once for each type of access, save the JSON locally, and work from that specific JSON file. If using articles with special characters, such as quotes, properly parse these characters beforehand so the API call can easily create the approriate link.
