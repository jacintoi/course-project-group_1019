# Videogame Analysis EDA
---------------------



## Instructions:
- You should remain focused on your research question(s) - it is very easy to get lost down rabbit holes in data analyses projects.

- If you find that your research questions are not that interesting, or you find more interesting questions (especially after your EDA) you may revise them, or add more.

- Use the lab times, as well as our office hours (TAs and instructors), to get help and guidance on your analyses.

- You should experiment with “plenty of” data visualizations to try and visualize your dataset and answer your research questions.

- Give us a narrative/story of your explorations as you go along, in-line with your data - use the new Markdown skills you learned in Task 1!


## Initialization:
```
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np
import pandas_profiling as pdp

sns.set_style("ticks")
import sys
sys.path.insert(1, '../scripts')

# Imports the project_functions.py file containing the different functions
import project_functions
```

![plot](https://github.com/data301-2020-winter2/course-project-group_1019/blob/main/analysis/Eduardo/Milestone%202/Eduardo_EDA_Plots/sales_by_genre_normalized.png?raw=true)
```
img src="./Eduardo/Milstone 2/Eduardo_EDA_Plots/sales_by_genre.png" width="700px"
```
#### Sample output
<img src="../Eduardo/Milstone 2/Eduardo_EDA_Plots/sales_by_genre.png"/>


## Intro
This analysis looks at the different aspects of videogames over the past ~40 years using a random sampls of videogames, representative of the entire industry, to relate real life qualitative events to measurable changes in the sales and consumption of videogames.

The data used in this analysis was obtained from [kaggle]("https://www.kaggle.com/rush4ratio/video-game-sales-with-ratings"), and is a user compiled data set which extends a scrape already performed by Metacritic, *"a website that aggregates reviews of films, TV shows, music albums, video games and formerly, books"* [Wikipedia] (https://en.wikipedia.org/wiki/Metacritic). It includes over 16,000 entries, of which 6,825 entries have all descriptors complete.

Each entry in this dataset is a videogame, and various pieces of information relating to it. As the extracted information will show, this dataset does not contain all videogames from 1980-2016, and although it contains many entries, it does not contain all videogames from 1980-2016, and so in this analysis it is considered a sample of that set of all videogames.

We are going to start by cleaning the data:
  - removing all rows with na entries
  - removing user scores with TBD
  - casting all entries in the table to their proper datatypes (they are all saved as strings), i.e. integers, floats, categories
below is the head of our cleaned data:
```
Cleaned_DataFrame = project_functions.load_and_process()
Cleaned_DataFrame.head()
```
## Platform
Platform can act as an isolated instance of videogame markets, where we can see how they succeed based on certain conditions which vary for each platform. Of course the competition between each of these platforms must be considered, but generally we can examine these Platforms and their characteristic to see how well the videogames are selling for each of them.

The things we first need to consider is that there will be variance in the popularity of Platforms across different regions in the world, and this can be the result of many different things, alot of which cannot be quantified; the culture and history of a region cannot be boiled down to numbers and data. So we will start by briefly looking at the affect locationtrying to consider quantitative factors that are measureable from the dataset.

Hopefully from this we can find some basic indicators for the success of a videogame, by looking at the different consoles games are released on.
//
insert stuff here
//

## Ratings, Sales, Genres

## more stuff

## Take-Aways/conc.