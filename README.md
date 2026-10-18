# Smite Stats

**Interactive Visualization of Personal Smite Match Data with D3.js**

A browser-based dashboard that turns a player's Smite match history into interactive charts. Matches are explored through a collapsible tree by game mode and god class, with per-class breakdowns, top-performing gods by KDA, and base stat profiles for every god played.

> Data visualization course project (VIZPOD). Author: Filip Krpes.



## Features

- Collapsible tree navigation: Smite → Match History → game mode (Joust, Arena, Conquest) → class, with match counts per node
- Class distribution pie chart for the selected game mode, with the selected class highlighted
- Table of the top 3 gods by KDA for the selected mode and class
- Line chart of kills per match for those top 3 gods, with hover tooltips
- Bar chart of games played per god, sorted by number of matches
- Radar chart of a god's normalized base stats (health, mana, speed, physical and magical protection), shown on bar click together with the class icon
- Animated transitions on tree expansion, bar growth and radar drawing

## Tech stack

| Area | Technology |
|---|---|
| Visualization | D3.js v3 |
| Frontend | HTML, CSS, vanilla JavaScript |
| Data | CSV (534 matches) |
| Data preparation | Python, pandas, NumPy |

## Project structure

```
index.html                     Page layout, tree, line chart, bar chart
PlayerStatsChart.js            Pie chart, top gods table, kills line chart
radarChart.js                  Radar chart of god base stats
smite_matches_with_class5.csv  Final dataset used by the page
*.svg                          Smite logo and class icons
Additional Files/              Raw datasets, preprocessing scripts, source links
```

## Data pipeline

```
smite_matches.csv ──┐
                    ├── merge on God_Name ──► add Class column
smite_champions.csv ┘
                                │
                                ▼
            min-max normalization of base stats,
            shifted so the median sits at 0.5
                                │
                                ▼
                 smite_matches_with_class5.csv
```

Each row holds the match type, god, kills, deaths, assists, items, class and five normalized base stats. God base stats come from the [Smite God Base Statistics](https://www.kaggle.com/datasets/mattop/smite-god-base-statistics-data) dataset on Kaggle. The preprocessing scripts are in `Additional Files/`.

