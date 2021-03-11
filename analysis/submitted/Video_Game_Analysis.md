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

The data used in this analysis was obtained from [kaggle]("https://www.kaggle.com/rush4ratio/video-game-sales-with-ratings"), and is a user compiled data set of videogames, which extends a scrape already performed by Metacritic, *"a website that aggregates reviews of films, TV shows, music albums, video games and formerly, books"* [Wikipedia] (https://en.wikipedia.org/wiki/Metacritic). It includes over 16,000 unique video games, of which 6,825 have all entries complete.

This dataset does not contain all videogames from 1980-2016, and and so in this analysis it is considered a sample of that set of all videogames.
each videogame can have up to 16 associated pieces of information, here is a description of each of them:

| Column Name     | Description |
| ----------- | ----------- |
| Name      | The name of the videogame       |
| Platform   | The hardware need to play this videogame        |
| Year_of_Release      | The year this game was first released       |
| Genre   | What genre this videogame falls under(i.e. sports, shooter, racing)        |
| Publisher      | The name of the company that finances the development and production of this videogame       |
| NA_Sales   | The Number of units sold from its release until 2016 in North America(millions) |
| EU_Sales      | The Number of units sold from its release until 2016 in Europe (millions|
| JP_Sales   | The Number of units sold from its release until 2016 in Japan (millions)|
| Other_Sales      | The Number of units sold from its release until 2016 in Regions outside of North America, Europe and Japan       |
| Global_Sales   | The Number of units sold from its release until 2016 World Wide(millions)      |
| Critic_Score      | mean of all ratings given by 'Critics'  (1-10)  |
| Critic_Count   | the number of 'critic' ratings |
| User_Score      | mean of all ratings given by 'non-Critics'  (1-100)  |
| User_Count   | The number of 'non-Critic' |
| Developer      | Title       |
| Rating   | Text        |


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
A videogame platform is the hardware used to play the videogame, and although it may seem arbitrary which culmination of plastic, circuitry and ingenuity is used to play a videogame, there are very big differences between them, both statistically and culturally.

Because of these differences, different platforms *can* act as an isolated instance of videogame markets, where we can see how videogames succeed based on certain conditions which vary for each platform.

We should first consider that biases towards certain platforms will exist. This bias is, although still very minimal, is most obvious when comparing by region. The culture and history of each region most certainly has an effect on the platform purchased by a particular individual.

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


Knowing what the areas of interest were in the column, we started off the EDA by focusing the data down to what was of interest: Names,For the top three genres, we want to quickly take a look at some of the top sellers in each genre and check if there are any game series or titles that are easily recognizable.  Genres, Ratings, Global Sales, and Years of Release. We created a new dataset which was specifically to help answer these three questions, and chose to drop all the other dataset columns minus these five select ones.

When looking into the Ratings column, we saw that there were still *"outdated"* ratings being used, in particular, the *K-A* rating. In 1994, the *K-A* rating, which was for Kids-Adults, was replaced with the *E* rating, which was for Everyone. To keep things consistent with the later games (since there is only one *K-A* rating in the entire cleaned dataset), we changed the *K-A* to *E* rating - avoiding any outliers in the data.

With things cleaned further, we first made sure to take note and store the unique values for the Genres and the Ratings. These variables, kept as lists, would become useful later in the code when answering the questions of interest.

With everything set up and ready for the EDA, we can now begin looking to answering each of these three questions. 

#

### *Which videogame genre tends to sell better / more?*
To answer this, we plotted the unique genres versus the total global sales for that genre.
Below, the plot for the Videogame Genres vs Global Sales can be seen.

![Videogame Genres vs Global Sales](https://github.com/data301-2020-winter2/course-project-group_1019/blob/main/analysis/Eduardo/Milestone%202/Eduardo_EDA_Plots/sales_by_genre.png)

From the above bar chart, we see that the *most popular game genre* is Action, followed by Sports and Shooter close behind.

Action games include your Grand Theft Auto (GTA) games, Assassin's Creed games, Uncharted games, etc. Most of these games are a part of larger series, often having more than two, three, and more in the overall game collection. As a result of this, and the sheer amount of games, there are 1630 games which are Action games. 

For Sport games, we see that there is a total of 943 games. Sport games are fairly self explanatory, and include games like FIFA games, Wii Sports, NBA games, Madden, etc.

Finally, Shooter games tend to be first person shooters, like the well known Call of Duty game series, and more games similar to that. In this genre, there are 864 games.

Since there is such a variation in both the sales, roughly 1.2 billion, 833 million, and 816 million units in sales for Action, Sports, and Action games respectively, and the number of games in each genre, we were left wondering if the Action games genre came out first solely due to the fact that it had the most games, and therefore the more selling potential. 

To address this, we chose to normalize the bar chart, to show how much a game of each genre will make *on average*! Like this, we can more accurately see which game genre tends to make the most sales per game.

![Videogame Genres vs Global Sales](https://github.com/data301-2020-winter2/course-project-group_1019/blob/main/analysis/Eduardo/Milestone%202/Eduardo_EDA_Plots/sales_by_genre_normalized.png)



#





### *What is the correlation between game ratings, sales, and genre?*



### *Which videogame genre tends to sell better / more?*



------------------
## more stuff
------------------
## Conclusions