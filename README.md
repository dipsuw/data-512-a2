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
* ORES (Objective Revision Evaluation Service) is a web service and API that provides machine learning as a service for Wikimedia projects maintained by the Scoring Platform team. The system is designed to help automate critical wiki-work – for example, vandalism detection and removal. Currently, the two general types of scores that ORES generates are in the context of "edit quality" and "article quality".More detailed API documentation can be found [here](https://www.mediawiki.org/wiki/ORES). 
## Source data
Wikipedia data:

Column name | Value | Description
--- | --- | ---
page | string | artcile name on Wikipedia
country | string | name of country
rev_id | int | revision id required to make ORES api call

Population data:

Column name | Value | Description
--- | --- | ---
Location | string | name of country
Location type | string | country type
Timeframe | string | time at which data was acquired-mid2015
Data | string(need to be converted to number format) | population size of the country

## Final data

Column name | Value | Description
--- | --- | ---
country | string | name of country
artcile_name | string | artcile name on Wikipedia
revision_id | int | revision id required to make ORES api call
artcile_quality | string | predicted quality returned from ORES api call
population | int | population size of the country

## Attributions
* Sample code provided in HCDS class for ORES api call
* [Assignment wiki](https://wiki.communitydata.cc/HCDS_(Fall_2017)/Assignments#A2:_Bias_in_data)
