---
title: "Read me: food-riots_data"
author: Till Grallert
date: 2018-06-05
---

This repository contains data and visualisations such as plots and maps for my research project on the [genealogy of food riots](https://tillgrallert.github.io/pages/research/category_food-riots/). Source data is kept exclusively in the `csv` and `xml` folders.

# folder hierarchy

- `catalogues/`: event catalogues
- `csv/`: mostly compiled and normalised price information.
    + the titles of columns in CSV files reference controlled ontologies, such as Dublin Core and Schema.org, as far as possible:
        * `schema:date` / `dc:date`: refers to a data type that conforms to ISO 8601
        * `schema:name`: name property of things such as persons and places
        * `schema:latitude`
        * `schema:longitude`
        * [`schema:Place`](https://schema.org/Place), `dc:location`
        * [`schema:Quantity`](https://schema.org/Quantity)
- `maps/`: mostly GeoJSON files of important sites in late Ottoman Middle Eastern cities, such as Hama, Homs, Aleppo, Damascus etc.
- `plots/`: mostly R plots of price data
- `rda/`: R data frames as output by the R scripts 
- `timeplots/`
- `xml/`: compiled and normalised price information; mostly TEI XML fragments.


# files
## events

I currently maintain the main event catalogue as an MMD file. All events are recorded in a table. For processing this data with R, the MMD table is converted to CSV

## locations

Files containing toponyms, links to authority files, and geo-coded locations are based on the gazetteers I authored and maintain for my PhD and the OpenArabicPE project. `csv/locations.csv` is an export of these information as basic CSV file to be used for mapping and plotting in R

## prices

1. `prices.csv`

    Main price information---encoded as `<tei:measureGrp>`s---is automatically extracted from my data base of sources. During this process, I normalise all measures based on localised information compiled in a parameter file and the regularise everything to the unit price. The final output or TEI XML and CSV files for further processing in R. Keep in mind to never directly edit these files as they will be overwritten during the next update from the source data base.

2. `qualitative-prices.csv`

   Qualitative price information is manually tagged in my source data base and exported to this CSV file.