# data-512-homework_2

# DATA512: Homework 2 - Considering Bias in Data

# Goal
Use Wikimedia's ORES machine learning model to make predictions of Wikipedia article qualities of cities in different US states.

# Data Source
- List of US cities: https://en.wikipedia.org/wiki/Category:Lists_of_cities_in_the_United_States_by_state.
- Census Bureau State Population: https://www.census.gov/data/tables/time-series/demo/popest/2020s-state-total.html.
- Census Bureau Regional Divisions: https://en.wikipedia.org/wiki/List_of_regions_of_the_United_States#Census_Bureau–designated_regions_and_divisions.

# API Documentation
- MediaWiki Action API: https://www.mediawiki.org/wiki/API:Main_page.
- ORES API: https://www.mediawiki.org/wiki/ORES.

# ORES Access Token
- Create a personal access token to use the API here: https://api.wikimedia.org/wiki/Authentication#Personal_API_tokens.
- Store this token in a .env file stored in your local clone of the repository.
- The main notebook will load the .env file to extract the access token.
- The .env file is ignored by the repository and should not be pushed to any remote Git repository.

# Code
- All of the analysis lives in the notebook [create_tables.ipynb](https://github.com/jmic94/data-512-homework_2/blob/main/code/create_tables.ipynb).
- [wp_ores_liftwing_example.ipynb](https://github.com/jmic94/data-512-homework_2/blob/main/code/wp_ores_liftwing_example.ipynb) contains sample code for using the ORES API along with the code license information.
- [wp_page_info_example.ipynb](https://github.com/jmic94/data-512-homework_2/blob/main/code/wp_page_info_example.ipynb) contains sample code for using the MediaWiki Action API for getting article information along with the code license information.

# Input files
- [us_cities_by_state_SEPT.2023.csv](https://github.com/jmic94/data-512-homework_2/blob/main/input/us_cities_by_state_SEPT.2023.csv): list of US cities and their articles.
- [US States by Region - US Census Bureau.xlsx](https://github.com/jmic94/data-512-homework_2/blob/main/input/US%20States%20by%20Region%20-%20US%20Census%20Bureau.xlsx): US regional divisions from the Census Bureau.
- [NST-EST2022-POP.xlsx](https://github.com/jmic94/data-512-homework_2/blob/main/input/NST-EST2022-POP.xlsx): Census Bureau state population data.

# Intermediate files
- [page_info.csv](https://github.com/jmic94/data-512-homework_2/blob/main/intermediate/page_info.csv) contains the page information of the 20,000+ city articles obtained from the MediaWiki Action API.
- [scores.csv](https://github.com/jmic94/data-512-homework_2/blob/main/intermediate/scores.csv) contains the article quality predictions from ORES for each of the 20,000 city articles.
- Any log files from the API calls will also be saved in the intermediate folder although these log files are ignored by the repository.

# Output files
- [wp_scored_city_articles_by_state.csv](https://github.com/jmic94/data-512-homework_2/blob/main/output/wp_scored_city_articles_by_state.csv) contains the predicted article quality for each city along with state, regional division, revision id and population information.

# Research Implications
I found the ORES API to be unreliable when making predictions on over 20,000 articles. The API would time out or just simply be stuck on a article indefinitely after every 1,200 articles or so. As a result, when looping over the articles to get the predictions of article quality, I had to restart the loop whereever the API timed out or got stuck. This took more than 8 hours. Extracting the revision IDs of the articles took about 2 hours and I did not find any time-out issues with the MediaWiki Action API as I did with the ORES API.

In general, there is significant overlap between the top 10 states by article coverage and the top 10 states by HIGH QUALITY article coverage. In particular, the states that are common between the two lists are Vermont, Wyoming, South Dakota, Alaska, Pennsylvania, and New Hampshire. I make a similar observation for the bottom 10 US states by article coverage and bottom 10 US states by HIGH QUALITY article coverage. The states common to both of those lists are North Carolina, Nevada, California, Arizona, Virginia, Florida, Oklahama, Kansas and Maryland.

The New England, Middle Atlantic and West North Central divisions are consistently in the top 4 divisions with the most articles per person and most high quality article per person. The Pacific, South Atlantic and Mountain divisions are consistently the worst performers for the same metrics.

## What biases did you expect to find in the data (before you started working with it), and why?
I expected the northeastern states to have good coverage of high quality articles because of the relatively longer history and historical significance of that region of the United States. Additionally, I expected states with relatively larger populations such as California and Texas to perform worse in terms of coverage of high quality articles simply due to the larger number of people who would potentially contribute to the articles. Having more people contribute to articles leads to a higher likelihood of misinformation in them. Also, larger states with many more cities simply face a more difficult time verifying those increased number of articles which ultimately leads to lower average article quality.

## What (potential) sources of bias did you discover in the course of your data processing and analysis?
According to the top 10 and bottom 10 lists in the analysis, states with a balance of the number of articles and population perform better than states with disproportionately larger populations. We can perhaps explain this with the logic outlined in the previous question. A larger potential contributor population can lead to higher occurences of misinformatio and inaccuracies in the the articles.

An exception to the observation above is Pennsylvania. Pennsylvania is the 5th most populated state in the United States (https://en.wikipedia.org/wiki/List_of_U.S._states_and_territories_by_population) but is also among the top 10 US states with highest coverage of high quality articles. A possible explanation for this result is the historical significance of the state. Pennslvania is one of the oldest formed states in the United States (https://en.wikipedia.org/wiki/List_of_U.S._states_by_date_of_admission_to_the_Union).

## What might your results suggest about (English) Wikipedia as a data source?
Wikipedia is a great source of information with a relatively robust and proactive community. However, relying on Wikipedia as a data source requires careful consideration of the potential sources of error and bias in the information. Any topic with a large number of potential people contibuting to its discussion will inevitably introduce bias, even if all individuals controbute with good intention. We see evidence of this phenomenon in the city articles, where populous states such as California and New York have lower coverage of high quality articles despite being some of the more popular destinations in the mass media of our time.
