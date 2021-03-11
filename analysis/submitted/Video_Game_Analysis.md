# Videogame Analysis EDA
---------------------



## Instructions:
- You should remain focused on your research question(s) - it is very easy to get lost down rabbit holes in data analyses projects.

- If you find that your research questions are not that interesting, or you find more interesting questions (especially after your EDA) you may revise them, or add more.

- Use the lab times, as well as our office hours (TAs and instructors), to get help and guidance on your analyses.

- You should experiment with “plenty of” data visualizations to try and visualize your dataset and answer your research questions.

- Give us a narrative/story of your explorations as you go along, in-line with your data - use the new Markdown skills you learned in Task 1!

--------------------------
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
-----------------------
## Intro
This analysis looks at the different aspects of videogames over the past ~40 years using a random samples of videogames, representative of the entire industry, to relate real life qualitative events to measurable changes in the sales and consumption of videogames.

The data used in this analysis was obtained from [kaggle]("https://www.kaggle.com/rush4ratio/video-game-sales-with-ratings"), and is a user compiled data set which extends a scrape already performed by Metacritic, *"a website that aggregates reviews of films, TV shows, music albums, video games and formerly, books"* [Wikipedia] (https://en.wikipedia.org/wiki/Metacritic). It includes over 16,000 unique video games, of which 6,825 entries have all entries complete.

Each videogame has various pieces of information relating to it. As the extracted information will show, this dataset does not contain all videogames from 1980-2016, and and so in this analysis it is considered a sample of that set of all videogames.

We are going to start by cleaning the data:
  - removing all rows with na entries
  - removing user scores with TBD
  - casting all entries in the table to their proper datatypes (they are all saved as strings), i.e. integers, floats, categories
below is the head of our cleaned data:
```
Cleaned_DataFrame = project_functions.load_and_process()
Cleaned_DataFrame.head()
```
-----------------
## Platform
The platforms a particular videogame is available to refers to the different hardwares which can be used to play the videogame.

Platforms *can* act as an isolated instance of videogame markets, where we can see how videogames succeed based on certain conditions which vary for each platform, with some consideration for the competition between the companies who develop the platforms.

The things we first need to consider is that biases towards certain platforms will exist as a result of qualitative data. This is most obvious if we separate by region, as in some regions, particularly North-America, even outside of the videogame industry there exists a very strong bias towards American-made products, from the strong culture of nationalism. This will be looked at briefly, and then more in depth later on.

Hopefully from this we can find some basic indicators for the success of a videogame, by looking at the different Platforms games are released on. The focus will be on three things:

- What correlation, if any, exists between the number of videogames available and the sales of videogames?
- does a longer platform lifespan guarantee more sales?
- Is competition a big factor in sales(does less competition mean more profits)?
#
### **regional bias**
as mentioned previously we will look at how the sales of videogames from particular platforms differ by region, mainly just to see how the bias changes. I will do this by counting the number of videogames on each console, which have sales greater than 10,000 USD in each region.
If one were to use only videogames available to all platforms, there would be very little data to observe so for this purposes of this analysis we will consider all videogames available to each platform.
the data is shown below in figures 1.1-1.6:


//insert regional biases//


Although the order of the number of games bought in each region for each platform varies slightly from region to region, the general groupings of each platform tends to remain the same.
the region which 

--------------------
## Genres, Ratings, and Sales
When it comes to videogames, people, like with music, movies, books, etc., have their natural preferences. The main objective of this section is to try and establish which are the more common preferences of people with regards to the different videogame genres that there are, and if there is a specific rating that these games or genre tends to fall under. 

To answer this, there are two main questions to focus on:
- Which videogame *genre* tends to *sell better / more*?

- What is the *correlation* between *game ratings, sales, and genre*?

On the topic of videogame ratings, this dataset uses Entertainment Software Rating Board (ESRB) Ratings ratings to rate the videogames. The ESRB was created in 1994 (under a different name back then) and the ratings have changed over time. In 1999, the ratings took form into those we see and recognize today.

Through the EDA conducted while looking to answering the question on the potential correlations between the videogame ratings, sales, and genre, we came across games which had been rated by the ESRB but predated 1994...

How was this possible? This lead to us introducing and seeking to answer a third question for this section:
- When did ratings begin for videogames? 
If the game was from before 1994, how/why was it rated?

#

Knowing what the areas of interest were in the column, we started off the EDA by focusing the data down to what was of interest: Names, Genres, Ratings, Global Sales, and Years of Release. We created a new dataset which was specifically to help answer these three questions, and chose to drop all the other dataset columns minus these five select ones.

When looking into the Ratings column, we saw that there were still *"outdated"* ratings being used, in particular, the *K-A* rating. In 1994, the *K-A* rating, which was for Kids-Adults, was replaced with the *E* rating, which was for Everyone. To keep things consistent with the later games (since there is only one *K-A* rating in the entire cleaned dataset), we changed the *K-A* to *E* rating - avoiding any outliers in the data.

With things cleaned further, we first made sure to take note and store the unique values for the Genres and the Ratings. These variables, kept as lists, would become useful later in the code when answering the questions of interest.

#

With everything set up and ready for the EDA, we can now begin looking to answering each of these three questions. 

#

### *Which videogame genre tends to sell better / more?*
To answer this, we plotted the unique genres versus the total global sales for that genre.
Below, the plot for the Videogame Genres vs Global Sales can be seen.

![Videogame Genres vs Global Sales](https://github.com/data301-2020-winter2/course-project-group_1019/blob/main/analysis/Eduardo/Milestone%202/Eduardo_EDA_Plots/sales_by_genre.png)

### *What is the correlation between game ratings, sales, and genre?*



### *Which videogame genre tends to sell better / more?*



------------------
## more stuff
------------------
## Conclusions