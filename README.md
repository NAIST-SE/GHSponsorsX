# Research Artifact: "My GitHub Sponsors profile is live!" Investigating the Impact of Twitter/X Mentions on GitHub Sponsors
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.10437641.svg)](https://doi.org/10.5281/zenodo.10437641)

This is a research artifact for the paper **"My GitHub Sponsors profile is live!" Investigating the Impact of Twitter/X Mentions on GitHub Sponsors**. This artifact is a data repository including all 11,582 tweets that contain GitHub Sponsors profile links associated with the information of tweets and GitHub accounts on these tweets, and the processed data. The purpose of this artifact is enabling researchers to replicate our results of the paper, and to reuse our dataset of more than 10,000 tweets linking GitHub Sponsors profiles for further research.

## Contents
- `data` - the data utilized in the paper.
- `scripts` - the scripts utilized in the paper.
- `appendix.pdf` - coding schema examples for RQ1.2, RQ1.3, RQ1.4, and RQ2.2.
- `LICENSE.md` - [Open Data Commons Public Domain Dedication and License (PDDL)](https://opendatacommons.org/licenses/pddl/summary/)
- `README.md` - this file
- `README.pdf` - README file for the application of reusable and available artifact badges.
- `paper.pdf` - the accepted paper

## RQ1 

### RQ1.1
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

## Authors
* [Youmei Fan](https://github.com/fanyoumei)
* [Tao Xiao](https://tao-xiao.github.io/)
* [Hideaki Hata](https://hideakihata.github.io/)
* [Christoph Treude](http://ctreude.ca/)
* Kenichi Matsumoto
