---
title: "Read me: food-riots_data"
author: Till Grallert
date: 2018-06-05
---

This repository contains data and visualisations such as plots and maps for my research project on the [genealogy of food riots](https://tillgrallert.github.io/pages/research/category_food-riots/).

The folder hierarchy is as follows

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
- `timeplots/`
- `xml/`: compiled and normalised price information; mostly TEI XML fragments.
