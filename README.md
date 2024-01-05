# Research Artifact: "My GitHub Sponsors profile is live!" Investigating the Impact of Twitter/X Mentions on GitHub Sponsors


This is a research artifact for the paper **"My GitHub Sponsors profile is live!" Investigating the Impact of Twitter/X Mentions on GitHub Sponsors**. This artifact is a data repository including all 11,582 tweets that contain GitHub Sponsors profile links associated with the information of tweets and GitHub accounts on these tweets, and the processed data. The purpose of this artifact is enabling researchers to replicate our results of the paper, and to reuse our dataset of more than 10,000 tweets linking GitHub Sponsors profiles for further research.

# Contents
- `data` - the data utilized in the paper.
- `scripts` - the scripts utilized in the paper.
- `appendix.pdf` - coding schema examples for RQ1.2, RQ1.3, RQ1.4, and RQ2.2.
- `LICENSE.md` - [Open Data Commons Public Domain Dedication and License (PDDL)](https://opendatacommons.org/licenses/pddl/summary/)
- `README.md` - this file
- `paper.pdf` - the accepted paper

# Purpose

We are applying for both Reusable and Available Badges.

- **Reusable Badges:** We seek the Reusable badge because our archival repository is well-documented. It contains comprehensive code for retrieving data from the GraphQL of GitHub (GHS), a recently enabled functionality. This repository is a valuable resource for researchers starting out, allowing them to explore data in GitHub. Additionally, we've provided code for extracting data from social media, a process easily replicable by other researchers or developers with a few keyword replacements. This makes our artifact a valuable reference for those interested in exploring and understanding data from GitHub and social media platforms.

- **Available Badges:** In pursuit of the Available badge, our study represents the initial stage of work on GitHub. It encompasses interactions from the GitHub community to the social media community. Our artifact provides a crucial first glimpse into how people react to the new sponsorship model in the open-source community. Furthermore, it serves as an essential reference for subsequent in-depth research. The data captured in this study can be valuable for understanding the initial dynamics and trends surrounding GitHub, both for current use and for future research endeavors.

# Provenance

The replication package comprises scripts and a dataset, accessible at [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.10461383.svg)](https://doi.org/10.5281/zenodo.10461383)

# Data
Our artifact focuses on various types of data, each with distinct characteristics and considerations.

## Raw Data
- **Tweets:** Data retrieved from the [Twitter API](https://developer.twitter.com/en/docs/twitter-api), capturing relevant social media interactions.
- **User Information:** Sourced from the [GitHub GraphQL](https://docs.github.com/en/graphql), providing details about individual users.
- **GitHub Contributions:** Retrieve the number of contributions made by GitHub users within a specified time period using web scraping.

## Coding Data
For specific research questions (RQ1.2, RQ1.3, and RQ1.4), manual coding was employed to extract the following coding data, in CSV format.

## Outcome Data (PSM Data)
The outcome data, in CSV format, specifically for Propensity Score Matching (PSM), includes values for 568 developers. This dataset is relevant to understanding the outcomes.

## Data And Scripts for Each RQ 

## RQ1 

### RQ1.
- [RQ1.1](./data/Tweets/All_tweets.csv): `All_tweets.csv` is a CSV file that contains 11,582 tweets linking to GitHub Sponsors profiles, the main columns in this CSV are `Language`, `Account type`, `Primary programming language` which are used in this RQ.
- Script: [find_tweets.ipynb](./scripts/Tweets/find_tweets.ipynb) it is script that retrieves all tweets in which the URL "github.com/sponsors/" appears.

### English tweets
- [English tweets](./data/Tweets/English_tweets.csv): `English_tweets.csv` is a CSV file that contains 10,531 tweets linking to GitHub Sponsors profiles and were written in English, it is used to obtain our sample for RQ1.2, RQ1.3, RQ1.4, and RQ2.2.

### Sample for RQ1.2, RQ1.3, and RQ1.4
- [Coding results](https://docs.google.com/spreadsheets/d/e/2PACX-1vS7m5xkt-IZpXhSE3zoroy5Cme0rDbN-SfUQ3_SMlY5f6qlqjaTaCmcfAzubYjwhaYlpAVPjjhVhs6a/pubhtml): This coding results for a statistically representative and stratified sample of 371 tweets, the main columns are `Relationship(RQ1.2)`, `Context(RQ1.3)`, and `Timing(RQ1.4)` for each RQ, respectively.

### Numbers of contributions of each activity in RQ1.4
- [A week before posting the tweet](./data/Contribution_activities/week_before.csv): `week_before.csv` is a CSV file that contains the numbers of contributions of each activity from 810 developers in a week before posting the tweet.
- [A week within posting the tweet](./data/Contribution_activities/week_within.csv): `week_within.csv` is a CSV file that contains numbers of contributions of each activity from 810 developers in a week within posting the tweet.
- [A week after posting the tweet](./data/Contribution_activities/week_after.csv): `week_after.csv` is a CSV file that contains the numbers of contributions of each activity from 810 developers in a week after posting the tweet.
- Script: [get_activity_different_time_duration.ipynb](./scripts/Contribution_activities/get_activity_different_time_duration.ipynb) it is a script that retrieves all github user's activity that occurred a week before, after, and within a week of posting the tweet. And [categorize_activities.ipynb](./scripts/Contribution_activities/categorize_activities.ipynb) it is a script that classify activities into 9 categories.


## RQ2

### RQ2.1
- [GitHub Sponsors tweets](./data/Tweets/GithubSponsors_tweets.csv): `GithubSponsors_tweets.csv` is a CSV file that contains 10,440 tweets that include links to GitHub Sponsors except for links to Paypal, Open Collective, and Patreon.
- [Paypal Tweets](./data/Tweets/Paypal_tweets.csv): `Paypal_tweets.csv` is a CSV file that contains 4 tweets that include links to `paypal.com/paypalme/` and `github.com`, but no link to Github Sponsors.
- [Open Collective Tweets](./data/Tweets/OpenCollective_tweets.csv): `OpenCollective_tweets.csv` is a CSV file that contains 88 tweets that include links to `opencollective.com/` and `github.com,` but no link to Github Sponsors.
- [Patreon Tweets](./data/Tweets/Patreon_tweets.csv): `Patreon_tweets.csv` is a CSV file that contains 228 tweets that include links to `patreon.com/` except Patreon posts (i.e., `patreon.com/posts/` ) and `github.com` , but no link to Github Sponsors.
- Script: [find_tweets_paypal.ipynb](./scripts/Tweets/find_tweets_paypal.ipynb) it is a script that retrieves tweets that include links to `paypal.com/paypalme/` and `github.com`, but no link to Github Sponsors. [find_tweets_opencollective.ipynb](./scripts/Tweets/find_tweets_opencollective.ipynb) it is a script that retrieves tweets that include links to `opencollective.com/` and `github.com`, but no link to Github Sponsors. [find_tweets_patreon.ipynb](./scripts/Tweets/find_tweets_patreon.ipynb) it is a script that retrieves tweets that include links to `patreon.com/` except Patreon posts (i.e., `patreon.com/posts/` ) and `github.com`, but no link to Github Sponsors.



### RQ2.2
- [Coding results](https://docs.google.com/spreadsheets/d/e/2PACX-1vS7m5xkt-IZpXhSE3zoroy5Cme0rDbN-SfUQ3_SMlY5f6qlqjaTaCmcfAzubYjwhaYlpAVPjjhVhs6a/pubhtml): This coding results for a statistically representative and stratified sample of 371 tweets, the main column is `Response(RQ2.2)` for this RQ.

### RQ2.3
- [PSM Data](./data/PSM/PSMdata.csv): `PSMdata.csv` is a CSV file that contains values of 568 developers for propensity score matching.
- Script: [get_PSM_data.ipynb](./scripts/PSM/get_PSM_data.ipynb) it is a script that retrieves the data for PSM, which contains the number of repositories owned by the user, the number of the given user is followed by, the number of organizations the user belongs to, the number of pull requests associated with this user, and the number of users is sponsoring, user's pull request review contributions (returns the most recently submitted review for each PR reviewed by the user) and user's primary language.
  - We executed the following script for PSM:
  ```
  library("MatchIt")
  library("tidyverse")
  library("broom")
  library("magrittr")

  data <- read.csv("PSMdata.csv")

  m_near <- matchit(formula = treatment ~ repos + sponsoring + openedPRs + reviewedPRs + language + followers + organizations,
                  data = data,
                  method = "nearest",
                  replace = TRUE)

  matched_data <- match.data(m_near)

  PSM_result <- matched_data %>%
                  lm(sponsors ~ treatment + repos + sponsoring + openedPRs + reviewedPRs + language + followers + organizations,
                  data = ., weights = weights) %>%
                  tidy()
  ```
## Appendix
- [Appendix](./appendix.pdf): Examples of each code schema in (RQ1.2, RQ1.3, RQ1.4 and RQ2.2) and examples of contribution activities on GitHub.


# Setup

To execute the code provided in the Jupyter Notebook (`{script_name}.ipynb`), please follow the instructions below.

## Hardware Requirements

The code in the Jupyter Notebook has the following hardware requirements:

- **Performance:** Standard performance is expected, and no specialized hardware acceleration is required.
- **Storage:** Ensure sufficient storage space for saving intermediate results and outputs.
- **Device-Type:** The code does not have specific requirements for GPU devices.

## Software Requirements

To set up the software environment for running the code, follow these steps:

- **Operating System:** The code is expected to run on any operating system that supports Python and Jupyter Notebook, including Windows, macOS, and Linux.
- **Package Dependencies:** Ensure that all the packages specified in the first cell of the Jupyter Notebook are installed.
- **Jupyter Notebook:** Ensure that Jupyter Notebook is installed on your system. [Install Jupyter Notebook](https://jupyter.org/install)

## Execution Instructions

Follow these steps to execute the code:

1. Open a terminal or command prompt.
2. Navigate to the directory containing `your_artifact.ipynb`.
3. Launch Jupyter Notebook using the command `jupyter notebook`.
4. In the Jupyter Notebook interface, open `{script_name}.ipynb`.
5. Run each cell in the notebook sequentially to execute the code.

# Usage

The instructions for obtaining the main results are presented in the paper, which focuses on retrieving Tweets:

## Retrieving Tweets Advertising GitHub Sponsorships:

1. Get the required Twitter token (Academic Research Access) and provide your "bearer token," "access token," and "access token secret."
2. Input the time duration of tweets you want to retrieve using the "start time" and "end time" variables.
3. Print the resulting dataframe. Successful execution indicates the ability to retrieve data from Twitter.

**Note:** Due to the Twitter API policy change, if the Twitter API token is generated from December 2022, the results may not be identical to those presented in the paper.

## Getting GitHub Users:

1. Obtain the `Personal access tokens` from GitHub.
2. Execute the code to retrieve information about GitHub users.
3. Print the resulting dataframe. Successful execution indicates the ability to retrieve user data from GitHub.


## Authors
* [Youmei Fan](https://github.com/fanyoumei)
* [Tao Xiao](https://tao-xiao.github.io/)
* [Hideaki Hata](https://hideakihata.github.io/)
* [Christoph Treude](http://ctreude.ca/)
* Kenichi Matsumoto
