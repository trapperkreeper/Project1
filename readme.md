# Project1

## About

This project aims to analyze data from the [Board Game Geek API](https://boardgamegeek.com/wiki/page/BGG_XML_API2) to see if there are any trends across the publication year, and relations between the game categories and mechanics.

### Questions

What are some insights related to the language dependency of games?
How have game mechanics evolved or changed in popularity over time?
How much are people playing board games today?
What is the financial incentive to publish boardgames in terms of industry size? And how can mechanics, categories and expected future trends assist in making this decision?

### Findings

Language Related insights:
very popular games are significantly language dense (extensively) but not fully.
followed by lang that are not dependent
not language dependent being produced and endures as a trend
A small % of games being produced use extensive amount (13% in 2020s and 17% 2020's) although there is preference for them among the top ranking.
There is room for creators that are focusing on games requiring extensive language in order to play.
Not dependent seems to always remain popular across the board.

Mechanics have not changed too much overtime in terms of which ones are the most used. The only notable change
is the rise of the solo gamer mechanic which has jumped significantly over the past 5 years, to the point that 
boardgame publishers would do well to keep in mind as a selling point for new releases if they include a solo mode.

In terms of average board game playtime, the trend as well as future forecast is trending higher. Even discounting the
outlier because of the COVID-19 pandemic, the trend after has still continued increasing compared to the years before the pandemic
signifying that board games are still a very large pastime for people.

There is significant financial incentive for board games to be an industry where people may want to invest.
The revenue is expected to double over the next 6 years.


## Methodology

### Data Cleanup

Due to how many different categories and mechanics there are, some similar
ones have been grouped together. The following tables depict how we grouped
similar categories and mechanics into broader ones.

| Grouping               | Original Category                     |
| ---------------------- | ------------------------------------- |
| Bluffing / Negotiation | Bluffing                              |
| Bluffing / Negotiation | Negotiation                           |
| Books                  | Book                                  |
| Books                  | Comic Book / Strip                    |
| Books                  | Novel-Based                           |
| Economy / Industry     | Economic                              |
| Economy / Industry     | Farming                               |
| Economy / Industry     | Industry / Manufacturing              |
| Historical Setting     | American West                         |
| Historical Setting     | Ancient                               |
| Historical Setting     | Medieval                              |
| Historical Setting     | Napoleonic                            |
| Historical Setting     | Post-Napoleonic                       |
| Historical Setting     | Prehistoric                           |
| Historical Setting     | Renaissance                           |
| War                    | (Anything with "War" in the category) |    

| Grouping   | Original Mechanic                |
| ---------- | -------------------------------- |
| Auction    | Auction/Bidding                  |
| Auction    | Auction: Dexterity               |
| Auction    | Auction: Dutch                   |
| Auction    | Auction: Dutch Priority          |
| Auction    | Auction: English                 |
| Auction    | Auction: Fixed Placement         |
| Auction    | Auction: Multiple Lot            |
| Auction    | Auction: Once Around             |
| Auction    | Auction: Sealed Bid              |
| Auction    | Auction: Turn Order Until Pass   |
| Auction    | Auction Compensation             |
| Auction    | Closed Economy Auction           |
| Auction    | Constrained Bidding              |
| Auction    | Turn Order: Auction              |
| Drafting   | Action Drafting                  |
| Drafting   | Closed Drafting                  |
| Drafting   | Open Drafting                    |
| Grid-Based | Grid Movement                    |
| Grid-Based | Hexagon Grid                     |
| Grid-Based | Square Grid                      |

## Organization

### Jupyter Notebooks

#### queries/bgg_stats_query.ipynb
This notebook handles the data fetching from the BGG API. It fetches and exports into a CSV batches of 10,000 records, according to the `batch` variable. (`batch = 10` fetches board games with `id` 100,001 through 110,000)

The last code cell in this notebook combines all the individual CSVs into a single `data/bgg_stats_all.csv` file.

#### bgg_refine.ipynb
This notebook reads in `data/bgg_stats_all.csv` and cleans up the raw data.

Steps 1-5 perform the following:

* Delete the image columns, and drop rows that do not have a publication year or metadata.
* Metadata contained in the `link` column is parsed out into their own respective columns.
* The result is exported to `data/cleaned.csv`.

Step 6 can be run independently of steps 2-5, as long as `data/cleaned.csv` exists.
It groups the categories and mechanics of each board game according to the tables
above, and removes any resulting duplicates. The result is exported to `data/cleaned2.csv`.

#### language_related.ipynb
generated the df for language related info, pulling from the data/cleaned2.csv

## EDA

Notebooks used for exploratory data analysis are organized into the `eda`
folder.

### cat_mech_by_year.ipynb

This notebook generates a chart of "Game Category by Publication Year" and a
chart of "Game Mechanic by Publication Year" to see how these trends have
changed over time.

### category_vs_mechanics.ipynb

This notebook analyzes the relationship between categories and mechanics. It
generates some line graphs analyzing mechanics over time as well as narrowing down to the last decade.
It also contains playtime analysis on avg playtime per mechanic as well as expected forecast playtime over the next 10 years.
It uses the data/cleaned.csv file to run all the code and graphs are saved to the charts/ folder.

### language_dependencies_eda
Assess language dependency aspect of top ranking games and games across decades.
Caveats:
Language information based on poll; gamer's opinion
required full dependency of language game
Limited data: 18542 games across 1960s - 2020s with polling information.


## Credits

### Contributors

[Cynthia Estrella](https://github.com/cynstar)\
[Luis Franco](https://github.com/MrFranco06)\
[Javier Ibarra-sanchez](https://github.com/ibarrajavi)\
[Racquel Jones](https://github.com/RacquelRobinsonJonesATX)\
[Iker Maruri](https://github.com/trapperkreeper)\
[Fu Thong](https://github.com/kibble)

### Data Attribution

![alt text](https://cf.geekdo-images.com/HZy35cmzmmyV9BarSuk6ug__thumb/img/gbE7sulIurZE_Tx8EQJXnZSKI6w=/fit-in/200x150/filters:strip_icc()/pic7779581.png)
