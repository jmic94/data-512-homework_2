# data-512-homework_2

# DATA512: Homework 2 - Considering Bias in Data

# Goal
Use Wikimedia's ORES machine learning model to make predictions of Wikipedia article qualities of cities in different US states.

# Data Source
- List of US cities: https://en.wikipedia.org/wiki/Category:Lists_of_cities_in_the_United_States_by_state
- Census Bureau State Population: https://www.census.gov/data/tables/time-series/demo/popest/2020s-state-total.html
- Census Bureau Regional Divisions: https://en.wikipedia.org/wiki/List_of_regions_of_the_United_States#Census_Bureau–designated_regions_and_divisions

# API Documentation
- MediaWiki Action API: https://www.mediawiki.org/wiki/API:Main_page
- ORES API: https://www.mediawiki.org/wiki/ORES

# ORES Access Token
- Create a personal access token to use the API here: https://api.wikimedia.org/wiki/Authentication#Personal_API_tokens
- Store this token in a .env file stored in your local clone of the repository
- The main notebook will load the .env file to extract the access token
- The .env file is ignored by the repository and should not be pushed to any remote Git repository

# Code
- All of the analysis lives in the notebook [create_tables.ipynb](https://github.com/jmic94/data-512-homework_2/blob/main/code/create_tables.ipynb)
- [wp_ores_liftwing_example.ipynb](https://github.com/jmic94/data-512-homework_2/blob/main/code/wp_ores_liftwing_example.ipynb) contains sample code for using the ORES API.
- [wp_page_info_example.ipynb](https://github.com/jmic94/data-512-homework_2/blob/main/code/wp_page_info_example.ipynb) contains sample code for using the MediaWiki Action API for getting article information.

# Input files
- [us_cities_by_state_SEPT.2023.csv](https://github.com/jmic94/data-512-homework_2/blob/main/input/us_cities_by_state_SEPT.2023.csv): list of US cities and their articles
- [US States by Region - US Census Bureau.xlsx](https://github.com/jmic94/data-512-homework_2/blob/main/input/US%20States%20by%20Region%20-%20US%20Census%20Bureau.xlsx): US regional divisions from the Census Bureau
- [NST-EST2022-POP.xlsx](https://github.com/jmic94/data-512-homework_2/blob/main/input/NST-EST2022-POP.xlsx): Census Bureau state population data

# Intermediate files
- 

# Output files
- 

# Research Implications
