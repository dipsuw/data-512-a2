# data-512-a2
Repository for 'Bias in data' assignment in D512

reproduce the analysis, including data descriptions, attributions and provenance information, and descriptions of all relevant resources and documentation (inside and outside the repo) and hyperlinks to those resources, and your writeup (if you have not included it in the notebook).

## Goal of the project:
The goal of this assignment is to explore the concept of 'bias' through data on Wikipedia articles - specifically, articles on political figures from a variety of countries.
* perform an analysis of how the coverage of politicians on Wikipedia and the quality of articles about politicians varies between countries
* list the countries with the greatest and least coverage of politicians on Wikipedia compared to their population.
* list the countries with the highest and lowest proportion of high quality articles about politicians.

#### Data Acquisition
Download data from following sources and save it as .csv for further processing:
* Wikipedia articles data is downloaded from [figshare](https://figshare.com/articles/Untitled_Item/5513449). This project contains data on most English-language Wikipedia articles within the category "Category:Politicians by nationality" and subcategories, along with the code used to generate that data. 
* Population data is downloaded from [Population Reference Bureau(PRB)](http://www.prb.org/DataFinder/Topic/Rankings.aspx?ind=14). This data is from year 2015 for 210 countries. 
#### Data Processing
* Once data is loaded from above two sources, population data needs some processing before its ready to use. The first two rows and 'Foonotes' column needs to be trimmed. The format for population data needs to be changed to number so that it can be used for percentage calculation in later steps.
* Get article quality prediction by calling [ORES](https://www.mediawiki.org/wiki/ORES) api and merge article_quality with wikipedia and population data in a single dataframe.
* Write the dataframe in a csv file and save it to disk
#### Data Analysis
* Once all the datasets are merged into a dataframe, calculate follwing for analysis:
  * the percentage of articles-per-population for each country
  * the percentage of high-quality articles(where prediction is either 'FA' or 'GA') for each country
*  Produce four tables that show:
  * 10 highest-ranked countries in terms of number of politician articles as a proportion of country population
  * 10 lowest-ranked countries in terms of number of politician articles as a proportion of country population
  * 10 highest-ranked countries in terms of number of GA and FA-quality articles as a proportion of all articles about politicians from that country
  * 10 lowest-ranked countries in terms of number of GA and FA-quality articles as a proportion of all articles about politicians from that country
* Reflect on what you have learned, what you found, what (if anything) surprised you about your findings, and/or what theories you have about why any biases might exist (if you find they exist).
## License of the source data
* MIT License(https://opensource.org/licenses/MIT)
## Wikimedia Foundation terms of use
https://wikimediafoundation.org/wiki/Terms_of_Use/en
## Relevant API documentation
* The legacy Pagecounts API (documentation, endpoint) provides access to desktop and mobile traffic data from January 2008 through July 2016. [Documentation for pagecount](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts)
* The Pageviews API (documentation, endpoint) provides access to desktop, mobile web, and mobile app traffic data from July 2015 through September 2017. [Documentation for pageviews](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews)
## Source data
Json files from api calls:
* pagecounts_desktop-site_200801-201607
* pagecounts_mobile-site_200801-201607
* pageviews_all-sites_201507-201709
* pageviews_mobile-app_201507-201709
* pageviews_mobile-web_201507-201709
## Final data
* en-wikipedia_traffic_200801-201709
#### Values of all fields in Final data file
Column name | Value | Description
--- | --- | ---
year | YYYY | Year of Wikipedia traffic from 2008-2017
month | MM | Month of Wikipedia traffic from Jan 2008- Sept 2017
timestamp | MMDDYYYY | Timestamp(Datetime format)to create the time series chart
pagecount_all_views | num_views | Number of pagecounts for mobile and desktop
pagecount_desktop_views | num_views | Number of pagecounts for desktop
pagecount_mobile_views | num_views | Number of pagecounts for mobile
pageview_all_views | num_views | Number of pageviews for mobile and desktop
pageview_desktop_views | num_views | Number of pageviews for desktop
pageview_mobile_views | num_views | Number of pageviews for mobile
