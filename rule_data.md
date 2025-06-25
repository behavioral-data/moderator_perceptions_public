# Rule Taxonomy and Timelines

## Overview

Rule timelines were reconstructed from the [Wayback Machine](https://archive.org/web/), scraping at-most-weekly snapshots. These rules are then classified into a hierarchical taxonomy of 3 levels and 17 classes.

## Taxonomy

![Rule Taxonomy](https://raw.githubusercontent.com/behavioral-data/moderator_perceptions_public/refs/heads/main/figs/codebook_breakdown-cropped.png)
    
Rules were classified by a **GPT-4o**-based classification pipeline. For more details, see our [paper on arXiv](https://arxiv.org/pdf/2501.14163).

## Rule Data Download

Our rules data, spanning from 2018-04-23 to 2024-06-20, is available for download as a `.csv` file [here](https://github.com/behavioral-data/moderator_perceptions_public/raw/refs/heads/main/data/rules_APR-2018-JUN-2024.csv).

Note that due to the infrequency of Wayback Machine snapshots, there is some uncertainty in both when a rule was created and when a rule was removed. To quantify this, we include the timestamps of the Wayback Machine snapshots on either side of a rule's start and end date. For example, if a snapshot taken on Monday does not include Rule X, but the snapshot taken on Wednesday does include Rule X, we know that Rule X was created sometime between Monday and Wednesay. The same holds for a rule being removed. We include the timestamp of the Monday snapshot (`earliest_start`) and the Wednesday snapshot (`latest_start`) as these represent the lower and upper bounds, respectively, of a rule's actual (and unknown) creation date).

The file includes each rule in our dataset as a row, with each row having the following columns:

- `subreddit`: the subreddit name
- `earliest_start`: the lower bound of when the rule was added
- `latest_start`: the upper bound of when the rule was added
- `earliest_end`: the lower bound of when the rule was removed
- `latest_end`: the lower bound of when the rule was removed
- `Prescriptive`: a boolean, expressing if the rule tone is Prescriptive
- `Restrictive`: a boolean, expressing if the rule tone is Restrictive
- `Post Content`: a boolean, expressing if the rule target is Post Content
- `Post Format`: a boolean, expressing if the rule target is Post Format
- `User-Related`: a boolean, expressing if the rule target is User-Related
- `Not a Rule`: a boolean, expressing if the rule is not able to be classified as a rule
- `Spam, Low Quality, Off-Topic, and Reposts`: a boolean, expressing if the rule topic is Spam, Low Quality, Off-Topic, and Reposts
- `Post Tagging & Flairing`: a boolean, expressing if the rule topic is Post Tagging & Flairing
- `Peer Engagement`: a boolean, expressing if the rule topic is Peer Engagement
- `Links & External Content`: a boolean, expressing if the rule topic is Links & External Content
- `Images`: a boolean, expressing if the rule topic is Images
- `Commercialization`: a boolean, expressing if the rule topic is Commercialization
- `Illegal Content`: a boolean, expressing if the rule topic is Illegal Content
- `Divisive Content`: a boolean, expressing if the rule topic is Divisive Content
- `Respect for Others`: a boolean, expressing if the rule topic is Respect for Others
- `Brigading`: a boolean, expressing if the rule topic is Brigading
- `Ban Mentioned`: a boolean, expressing if the rule topic is Ban Mentioned
- `Karma/Score Mentioned`: a boolean, expressing if the rule topic is Karma/Score Mentioned
- `Rule Text`: the full text of the rule

For ease of computing, we recommend loading it using Pandas and creating a MultiIndex. This can be done with `pd.read_csv('path_to_downloaded.csv').set_index(['subreddit', 'earliest_start', 'latest_start', 'earliest_end', 'latest_end'])`.
