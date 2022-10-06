# Homework 1: Professionalism & Reproducibility 
Regina-Mae Dominguez  
UW MSDS - Autumn 2022 - DATA 512 Human Centered Data Science

This project constructs, analysizes, and publishes a dataset of monthly article traffic for a select set of pages, a subset of Dinosaur articles, from English Wikipedia from January 1, 2015 through September 30, 2022. The data is obtained through the Pageviews API. The data aquisition, preparation, and analysis are contained in the [Jupyter Notebook](data512_hw1_professionalism_reproducibility.ipynb) `data512_hw1_professionalism_reproducibility.ipynb`.

## API
**Pageviews:** [Documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews) , 
[Endpoint](https://wikimedia.org/api/rest_v1/#!/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end)  
The Pageviews API provides access to dektop, mobile-web, and mobile-app traffic data from July 2015. This API can be used to get page views for specific articles, wikipedia projects, or even countries. 

### License for Source Data 
* Wikimedia REST API: offers access to Wikimedia's content and metadata in machine-readable formats. It is avaliable for all major Wikimedia projects at `/api/rest_v1/`
  * By using the REST API, we agree to Wikimedia's general [Term of Use](https://foundation.wikimedia.org/wiki/Terms_of_Use/en) and [Privacy Policy](https://foundation.wikimedia.org/wiki/Privacy_policy).
  
See https://www.mediawiki.org/wiki/REST_API for more background and information.

## Datasets 
`dinosaur_genera.cleaned.SEPT.2022.csv` : Dinosaur related articles  

### Outputs
`dino_monthly_mobile_start201501_end202210.json`: JSON file with timeseries views mobile-access data for each dinosaur article from January 1 2015 to September 30, 2022.  
`dino_monthly_desktop_start201501_end202210.json`: JSON file with timeseries views desktop-access data for each dinosaur article from January 1 2015 to September 30, 2022.  
`dino_monthly_cumulative_start201501_end202210.json`: JSON file with timeseries views all-access (mobile + desktop) data for each dinosaur article from January 1 2015 to September 30, 2022.  
* Each `JSON` file is formatted with the following schema:  
```
{
[article_title] { "project:"
                  "article:"
                  "granularity:"
                  "timestamp:"
                  "agent:"
                  "views:"}, 
                  ...
}
```
where the keys are the article titles with their time series data as its values. More information on the objects _(project, .. views)_ can be found on the Endpoint documentation listed above. 


## Considerations 
The code requests a big chuck of data when utilizing the API call. For more efficiency, use the API call once for each type of access, save the JSON locally, and work from that specific JSON file. If using articles with special characters, such as quotes, properly parse these characters beforehand so the API call can easily create the approriate link.
* Other issues with the data can be found on the [Pageviews Documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews) and are [documented](https://wikitech.wikimedia.org/wiki/Analytics/Data_Lake/Traffic/Pageview_hourly#Changes_and_known_problems_since_2015-06-16) in their hive data store where data is extracted.
