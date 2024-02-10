# Project1

## About

This project aims to analyze data from the [Board Game Geek API](https://boardgamegeek.com/wiki/page/BGG_XML_API2) to see if there are any trends across the publication year, and relations between the game categories and mechanics.

### Questions

TBD

### Findings

TBD

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

## EDA

Notebooks used for exploratory data analysis are organized into the `eda`
folder.

### cat_mech_by_year.ipynb

This notebook generates a chart of "Game Category by Publication Year" and a
chart of "Game Mechanic by Publication Year" to see how these trends have
changed over time.

### category_vs_mechanics.ipynb

This notebook analyzes the relationship between categories and mechanics. It
generates a heatmap showing the number of games in which a category/mechanic
pair is featured.

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
