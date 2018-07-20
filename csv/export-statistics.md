---
title: "Export statistics for Bilād al-Shām"
author: Till Grallert
date: 2018-07-20 13:49:45 +0300
tags:
    - project_food-riots
    - data
---

- sources: Mostly based on Britisch commercial reports (HCPP)
- measures: I assume that whenever, British consular personnel speaks about
    + "quarters", they refer to quarter (qr. av. or quartier) as to mean ¼ of a hundredweight: 2 stone or 28 avoirdupois pounds
    + "tons", they refer to British "long ton" of 2240 lbs avoirdupois

## data processing 

In order to convert this table to more practical `<tei:measureGrp>`, use the following regex:

1. find: 
    2. rows with prices: `^\|\s(\d{4})\s+\|\s(\w+).[^\|]+\s+\|\s(\w+)\s+\|\s(\w+)\s+\|\s+(\d+)\s+\|\s(\w+)\s+\|\s+(.+)\s+\|\s(.[^\|]+)\s+\|$`
    3. rows without prices: `^\|\s(\d{4})\s+\|\s(\w+).[^\|]+\s+\|\s(\w+)\s+\|\s(\w+)\s+\|\s+(\d+)\s+\|\s+\|\s+\|\s(.[^\|]+)\s+\|$`
2. replace:
    2. rows with prices
    
    ```xml
    | $1 | $2 | <measureGrp location="$2" when="$1" source="$8"><measure commodity="$3" unit="$4" quantity="$5">$3 | $4 | $5</measure> | <measure commodity="currency" unit="$6" quantity="$7">$6 | $7</measure></measureGrp> | $8 |
    ```

    3. rows without prices

    ```xml
    | $1 | $2 | <measureGrp location="$2" when="$1" source="$6"><measure commodity="$3" unit="$4" quantity="$5">$3 | $4 | $5</measure> |   | </measureGrp> | $6 |
    ```

# tables
## exports


| date |   location   | commodity | measure | quantity | currency | value  |                source                |
|------|--------------|-----------|---------|----------|----------|--------|--------------------------------------|
| 1891 | Alexandretta | cereals   | ton  |    19496 | gbp      | 113004 | ABDA2C1D-2396-475F-B922-B3307910D959 |
| 1890 | Alexandretta | cereals   | ton  |    14945 | gbp      |  85752 | ABDA2C1D-2396-475F-B922-B3307910D959 |
| 1891 | Mersin       | wheat     | ton  |    62000 | gbp      | 393000 | ABDA2C1D-2396-475F-B922-B3307910D959 |
| 1890 | Mersin       | wheat     | ton  |    28850 | gbp      |  16500 | ABDA2C1D-2396-475F-B922-B3307910D959 |
| 1891 | Mersin       | barley    | ton  |    31500 | gbp      |  22500 | ABDA2C1D-2396-475F-B922-B3307910D959 |
| 1890 | Mersin       | barley    | ton  |    18250 | gbp      |  58500 | ABDA2C1D-2396-475F-B922-B3307910D959 |
| 1891 | Mersin       | oats      | ton  |     5600 | gbp      |  22500 | ABDA2C1D-2396-475F-B922-B3307910D959 |
| 1890 | Mersin       | oats      | ton  |    10300 | gbp      |  33000 | ABDA2C1D-2396-475F-B922-B3307910D959 |
| 1891 | Mersin       | millet    | ton  |     1900 | gbp      |   9500 | ABDA2C1D-2396-475F-B922-B3307910D959 |
| 1890 | Mersin       | millet    | ton  |      600 | gbp      |   1650 | ABDA2C1D-2396-475F-B922-B3307910D959 |
| 1891 | Adana        | wheat     | ton  |   100000 | gbp      | 633000 | ABDA2C1D-2396-475F-B922-B3307910D959 |
| 1890 | Adana        | wheat     | ton  |    47700 | gbp      | 283000 | ABDA2C1D-2396-475F-B922-B3307910D959 |
| 1891 | Adana        | barley    | ton  |    66500 | gbp      | 340400 | ABDA2C1D-2396-475F-B922-B3307910D959 |
| 1890 | Adana        | barley    | ton  |    59250 | gbp      | 189500 | ABDA2C1D-2396-475F-B922-B3307910D959 |
| 1891 | Adana        | millet    | ton  |     4900 | gbp      |  24500 | ABDA2C1D-2396-475F-B922-B3307910D959 |
| 1890 | Adana        | millet    | ton  |     2100 | gbp      |   8650 | ABDA2C1D-2396-475F-B922-B3307910D959 |
| 1891 | Jaffa        | wheat     | qr   |     2695 | gbp      |   3300 | 4E6DC2B2-9835-496C-A069-E706B7277DE0 |
| 1890 | Jaffa        | wheat     | qr   |    20805 | gbp      |  19920 | 4E6DC2B2-9835-496C-A069-E706B7277DE0 |
| 1891 | Jaffa        | maize     | qr   |    18325 | gbp      |  17300 | 4E6DC2B2-9835-496C-A069-E706B7277DE0 |
| 1890 | Jaffa        | maize     | qr   |    17476 | gbp      |  11240 | 4E6DC2B2-9835-496C-A069-E706B7277DE0 |
| 1892 | Damascus     | flour     | cwt     |   187500 | gbp      |  70000 | 7DFF128B-44EC-434C-B1C3-E74CB611A1E1 |
| 1891 | Damascus     | flour     | cwt     |   125000 | gbp      |  53960 | 7DFF128B-44EC-434C-B1C3-E74CB611A1E1 |
| 1892 | Damascus     | cereals   |         |          | gbp      |   7600 | 7DFF128B-44EC-434C-B1C3-E74CB611A1E1 |
| 1891 | Damascus     | cereals   |         |          | gbp      |  20000 | 7DFF128B-44EC-434C-B1C3-E74CB611A1E1 |
| 1893 | Jaffa        | maize     | qr   |     3246 | gbp      |   2580 | E01E25C5-9CFE-4D35-8FB2-A3DFB7EC8EF0 |
| 1892 | Jaffa        | maize     | qr   |      695 | gbp      |    420 | E01E25C5-9CFE-4D35-8FB2-A3DFB7EC8EF0 |
| 1893 | Alexandretta | cereals   | ton  |     2394 | gbp      |  10357 | 729A9379-398E-48D9-864C-7A56EE088030 |
| 1892 | Alexandretta | cereals   | ton  |     7113 | gbp      |  36211 | 729A9379-398E-48D9-864C-7A56EE088030 |
| 1893 | Adana        | wheat     | ton  |    11328 | gbp      |  50000 | 729A9379-398E-48D9-864C-7A56EE088030 |
| 1892 | Adana        | wheat     | ton  |    56000 | gbp      | 325000 | 729A9379-398E-48D9-864C-7A56EE088030 |
| 1893 | Adana        | barley    | ton  |     4850 | gbp      |  15500 | 729A9379-398E-48D9-864C-7A56EE088030 |
| 1892 | Adana        | barley    | ton  |     9400 | gbp      |  38100 | 729A9379-398E-48D9-864C-7A56EE088030 |
| 1893 | Adana        | oats      | ton  |     8110 | gbp      |  32500 | 729A9379-398E-48D9-864C-7A56EE088030 |
| 1892 | Adana        | oats      | ton  |     8300 | gbp      |  31200 | 729A9379-398E-48D9-864C-7A56EE088030 |
| 1893 | Adana        | millet    | ton  |      825 | gbp      |   3300 | 729A9379-398E-48D9-864C-7A56EE088030 |
| 1892 | Adana        | millet    | ton  |      500 | gbp      |   2500 | 729A9379-398E-48D9-864C-7A56EE088030 |
| 1892 | Adana        | rye       | ton  |     1600 | gbp      |   8000 | 729A9379-398E-48D9-864C-7A56EE088030 |
| 1893 | Damascus     | flour     | cwt     |   250000 | gbp      |  72000 | 5BACF30F-DD45-4D02-ABB8-E3723CC7B194 |
| 1893 | Damascus     | cereals   | cwt     |    25000 | gbp      |   7600 | 5BACF30F-DD45-4D02-ABB8-E3723CC7B194 |
| 1892 | Damascus     | flour     | cwt     |   187500 | gbp      |  70000 | 5BACF30F-DD45-4D02-ABB8-E3723CC7B194 |
| 1892 | Damascus     | cereals   |         |          | gbp      |   7600 | 5BACF30F-DD45-4D02-ABB8-E3723CC7B194 |
| 1892 | Haifa / Acre | wheat     | qr   |    50110 | gbp      |  70154 | 3AB233EA-2076-4723-AABE-1499E9326D5C |
| 1893 | Haifa / Acre | wheat     | qr   |    13910 | gbp      |  12519 | 3AB233EA-2076-4723-AABE-1499E9326D5C |
| 1892 | Saida        | wheat     | bushel  |    16000 |          |        | 3AB233EA-2076-4723-AABE-1499E9326D5C |
| 1892 | Saida        | barley    | bushel  |    32000 |          |        | 3AB233EA-2076-4723-AABE-1499E9326D5C |
| 1892 | Saida        | millet    | bushel  |     6000 |          |        | 3AB233EA-2076-4723-AABE-1499E9326D5C |
| 1892 | Tripoli      | barley    | qr   |     1228 |          |        | 3AB233EA-2076-4723-AABE-1499E9326D5C |
| 1892 | Tripoli      | wheat     | qr   |     9260 |          |        | 3AB233EA-2076-4723-AABE-1499E9326D5C |
| 1893 | Tripoli      | wheat     | qr   |     4508 | gbp      |   6524 | 3AB233EA-2076-4723-AABE-1499E9326D5C |
| 1894 | Damascus     | flour     | qr   |   250000 | gbp      |  60000 | 8D01452F-7446-4B13-8286-C699929310FE |
| 1894 | Damascus     | cereals   | qr   |    50000 | gbp      |   8000 | 8D01452F-7446-4B13-8286-C699929310FE |
| 1894 | Damascus     | flour     | qr   |   250000 | gbp      |  72000 | 8D01452F-7446-4B13-8286-C699929310FE |
| 1894 | Damascus     | cereals   | qr   |    25000 | gbp      |   7000 | 8D01452F-7446-4B13-8286-C699929310FE |

| 1894 | Alexandretta | <measureGrp location="Alexandretta" when="1894" source="A2807B15-24DC-44A9-ADE0-3FE460392616"><measure commodity="cereals" unit="ton" quantity="2043">cereals | ton | 2043</measure>  | <measure commodity="currency" unit="gbp" quantity="9891">gbp    | 9891</measure></measureGrp>    | A2807B15-24DC-44A9-ADE0-3FE460392616 |
| 1893 | Alexandretta | <measureGrp location="Alexandretta" when="1893" source="A2807B15-24DC-44A9-ADE0-3FE460392616"><measure commodity="cereals" unit="ton" quantity="2394">cereals | ton | 2394</measure>  | <measure commodity="currency" unit="gbp" quantity="10357">gbp   | 10357</measure></measureGrp>   | A2807B15-24DC-44A9-ADE0-3FE460392616 |
| 1894 | Adana        | <measureGrp location="Adana" when="1894" source="A2807B15-24DC-44A9-ADE0-3FE460392616"><measure commodity="wheat" unit="ton" quantity="13093">wheat           | ton | 13093</measure> | <measure commodity="currency" unit="gbp" quantity="52372">gbp   | 52372</measure></measureGrp>   | A2807B15-24DC-44A9-ADE0-3FE460392616 |
| 1893 | Adana        | <measureGrp location="Adana" when="1893" source="A2807B15-24DC-44A9-ADE0-3FE460392616"><measure commodity="wheat" unit="ton" quantity="11328">wheat           | ton | 11328</measure> | <measure commodity="currency" unit="gbp" quantity="50000">gbp   | 50000</measure></measureGrp>   | A2807B15-24DC-44A9-ADE0-3FE460392616 |
| 1894 | Adana        | <measureGrp location="Adana" when="1894" source="A2807B15-24DC-44A9-ADE0-3FE460392616"><measure commodity="barley" unit="ton" quantity="4966">barley          | ton | 4966</measure>  | <measure commodity="currency" unit="gbp" quantity="14989">gbp   | 14989</measure></measureGrp>   | A2807B15-24DC-44A9-ADE0-3FE460392616 |
| 1893 | Adana        | <measureGrp location="Adana" when="1893" source="A2807B15-24DC-44A9-ADE0-3FE460392616"><measure commodity="barley" unit="ton" quantity="4850">barley          | ton | 4850</measure>  | <measure commodity="currency" unit="gbp" quantity="15500">gbp   | 15500</measure></measureGrp>   | A2807B15-24DC-44A9-ADE0-3FE460392616 |
| 1894 | Adana        | <measureGrp location="Adana" when="1894" source="A2807B15-24DC-44A9-ADE0-3FE460392616"><measure commodity="oats" unit="ton" quantity="18617">oats             | ton | 18617</measure> | <measure commodity="currency" unit="gbp" quantity="55851">gbp   | 55851</measure></measureGrp>   | A2807B15-24DC-44A9-ADE0-3FE460392616 |
| 1893 | Adana        | <measureGrp location="Adana" when="1893" source="A2807B15-24DC-44A9-ADE0-3FE460392616"><measure commodity="oats" unit="ton" quantity="8110">oats              | ton | 8110</measure>  | <measure commodity="currency" unit="gbp" quantity="32500">gbp   | 32500</measure></measureGrp>   | A2807B15-24DC-44A9-ADE0-3FE460392616 |
| 1894 | Adana        | <measureGrp location="Adana" when="1894" source="A2807B15-24DC-44A9-ADE0-3FE460392616"><measure commodity="millet" unit="ton" quantity="670">millet           | ton | 670</measure>   | <measure commodity="currency" unit="gbp" quantity="3685">gbp    | 3685</measure></measureGrp>    | A2807B15-24DC-44A9-ADE0-3FE460392616 |
| 1893 | Adana        | <measureGrp location="Adana" when="1893" source="A2807B15-24DC-44A9-ADE0-3FE460392616"><measure commodity="millet" unit="ton" quantity="825">millet           | ton | 825</measure>   | <measure commodity="currency" unit="gbp" quantity="3300">gbp    | 3300</measure></measureGrp>    | A2807B15-24DC-44A9-ADE0-3FE460392616 |
| 1894 | Jaffa        | <measureGrp location="Jaffa" when="1894" source="52572E1A-2890-47EE-AF5C-585A03A25DF7"><measure commodity="maize" unit="qr" quantity="2356">maize             | qr  | 2356</measure>  | <measure commodity="currency" unit="gbp" quantity="2000">gbp    | 2000</measure></measureGrp>    | 52572E1A-2890-47EE-AF5C-585A03A25DF7 |
| 1893 | Jaffa        | <measureGrp location="Jaffa" when="1893" source="52572E1A-2890-47EE-AF5C-585A03A25DF7"><measure commodity="maize" unit="qr" quantity="3246">maize             | qr  | 3246</measure>  | <measure commodity="currency" unit="gbp" quantity="2580">gbp    | 2580</measure></measureGrp>    | 52572E1A-2890-47EE-AF5C-585A03A25DF7 |
| 1893 | Haifa        | <measureGrp location="Haifa" when="1893" source="1E644FDC-B145-458F-9BFA-E39C26F489EA"><measure commodity="wheat" unit="qr" quantity="13910">wheat            | qr  | 13910</measure> | <measure commodity="currency" unit="gbp" quantity="12519">gbp   | 12519</measure></measureGrp>   | 1E644FDC-B145-458F-9BFA-E39C26F489EA |
| 1894 | Haifa        | <measureGrp location="Haifa" when="1894" source="1E644FDC-B145-458F-9BFA-E39C26F489EA"><measure commodity="wheat" unit="qr" quantity="10845">wheat            | qr  | 10845</measure> | <measure commodity="currency" unit="gbp" quantity="7050">gbp    | 7050</measure></measureGrp>    | 1E644FDC-B145-458F-9BFA-E39C26F489EA |
| 1899 | Haifa        | <measureGrp location="Haifa" when="1899" source="FE843889-C0E6-49B7-AB06-8F36740A5B99"><measure commodity="wheat" unit="qr" quantity="44178">wheat            | qr  | 44178</measure> | <measure commodity="currency" unit="gbp" quantity="57214">gbp   | 57214</measure></measureGrp>   | FE843889-C0E6-49B7-AB06-8F36740A5B99 |
| 1900 | Haifa        | <measureGrp location="Haifa" when="1900" source="FE843889-C0E6-49B7-AB06-8F36740A5B99"><measure commodity="wheat" unit="qr" quantity="58470">wheat            | qr  | 58470</measure> | <measure commodity="currency" unit="gbp" quantity="75116">gbp   | 75116</measure></measureGrp>   | FE843889-C0E6-49B7-AB06-8F36740A5B99 |
| 1899 | Haifa        | <measureGrp location="Haifa" when="1899" source="FE843889-C0E6-49B7-AB06-8F36740A5B99"><measure commodity="barley" unit="qr" quantity="575">barley            | qr  | 575</measure>   | <measure commodity="currency" unit="gbp" quantity="566">gbp     | 566</measure></measureGrp>     | FE843889-C0E6-49B7-AB06-8F36740A5B99 |
| 1900 | Haifa        | <measureGrp location="Haifa" when="1900" source="FE843889-C0E6-49B7-AB06-8F36740A5B99"><measure commodity="barley" unit="qr" quantity="1700">barley           | qr  | 1700</measure>  | <measure commodity="currency" unit="gbp" quantity="1364">gbp    | 1364</measure></measureGrp>    | FE843889-C0E6-49B7-AB06-8F36740A5B99 |
| 1900 | Haifa        | millet                                                                                                                                                           | qr  | 11345           | gbp                                                             | 7894                           | FE843889-C0E6-49B7-AB06-8F36740A5B99 |
| 1899 | Haifa        | millet                                                                                                                                                           | qr  | 4877            | gbp                                                             | 3692                           | FE843889-C0E6-49B7-AB06-8F36740A5B99 |
| 1899 | Tripoli      | <measureGrp location="Tripoli" when="1899" source="FE843889-C0E6-49B7-AB06-8F36740A5B99"><measure commodity="barley" unit="ton" quantity="8000">barley        | ton | 8000</measure>  | <measure commodity="currency" unit="gbp" quantity="60000">gbp   | 60000</measure></measureGrp>   | FE843889-C0E6-49B7-AB06-8F36740A5B99 |
| 1900 | Tripoli      | <measureGrp location="Tripoli" when="1900" source="FE843889-C0E6-49B7-AB06-8F36740A5B99"><measure commodity="barley" unit="ton" quantity="33000">barley       | ton | 33000</measure> | <measure commodity="currency" unit="gbp" quantity="225000">gbp  | 225000</measure></measureGrp>  | FE843889-C0E6-49B7-AB06-8F36740A5B99 |
| 1900 | Saida        | <measureGrp location="Saida" when="1900" source="FE843889-C0E6-49B7-AB06-8F36740A5B99"><measure commodity="millet" unit="qr" quantity="4500">millet           | qr  | 4500</measure>  |                                                                 | </measureGrp>                  | FE843889-C0E6-49B7-AB06-8F36740A5B99 |
| 1900 | Latakia      | <measureGrp location="Latakia" when="1900" source="FE843889-C0E6-49B7-AB06-8F36740A5B99"><measure commodity="cereals" unit="ton" quantity="5000">cereals      | ton | 5000</measure>  | <measure commodity="currency" unit="gbp" quantity="39000">gbp   | 39000</measure></measureGrp>   | FE843889-C0E6-49B7-AB06-8F36740A5B99 |
| 1899 | Latakia      | <measureGrp location="Latakia" when="1899" source="FE843889-C0E6-49B7-AB06-8F36740A5B99"><measure commodity="cereals" unit="ton" quantity="9250">cereals      | ton | 9250</measure>  | <measure commodity="currency" unit="gbp" quantity="67562">gbp   | 67562</measure></measureGrp>   | FE843889-C0E6-49B7-AB06-8F36740A5B99 |
| 1899 | Jaffa        | <measureGrp location="Jaffa" when="1899" source="B8E3F7E8-1451-42DA-B1FD-168D39F17932"><measure commodity="wheat" unit="qr" quantity="0">wheat                | qr  | 0</measure>     | <measure commodity="currency" unit="gbp" quantity="0">gbp       | 0</measure></measureGrp>       | B8E3F7E8-1451-42DA-B1FD-168D39F17932 |
| 1899 | Jaffa        | <measureGrp location="Jaffa" when="1899" source="B8E3F7E8-1451-42DA-B1FD-168D39F17932"><measure commodity="maize" unit="qr" quantity="300">maize              | qr  | 300</measure>   | <measure commodity="currency" unit="gbp" quantity="1350">gbp    | 1350</measure></measureGrp>    | B8E3F7E8-1451-42DA-B1FD-168D39F17932 |
| 1898 | Jaffa        | <measureGrp location="Jaffa" when="1898" source="B8E3F7E8-1451-42DA-B1FD-168D39F17932"><measure commodity="wheat" unit="qr" quantity="10000">wheat            | qr  | 10000</measure> | <measure commodity="currency" unit="gbp" quantity="14000">gbp   | 14000</measure></measureGrp>   | B8E3F7E8-1451-42DA-B1FD-168D39F17932 |
| 1898 | Jaffa        | <measureGrp location="Jaffa" when="1898" source="B8E3F7E8-1451-42DA-B1FD-168D39F17932"><measure commodity="maize" unit="qr" quantity="3000">maize             | qr  | 3000</measure>  | <measure commodity="currency" unit="gbp" quantity="3000">gbp    | 3000</measure></measureGrp>    | B8E3F7E8-1451-42DA-B1FD-168D39F17932 |
| 1900 | Beirut       | <measureGrp location="Beirut" when="1900" source="FE843889-C0E6-49B7-AB06-8F36740A5B99"><measure commodity="barley" unit="ton" quantity="3500">barley         | ton | 3500</measure>  | <measure commodity="currency" unit="gbp" quantity="13000">gbp   | 13000</measure></measureGrp>   | FE843889-C0E6-49B7-AB06-8F36740A5B99 |
| 1899 | Beirut       | <measureGrp location="Beirut" when="1899" source="FE843889-C0E6-49B7-AB06-8F36740A5B99"><measure commodity="barley" unit="ton" quantity="4000">barley         | ton | 4000</measure>  | <measure commodity="currency" unit="gbp" quantity="15200">gbp   | 15200</measure></measureGrp>   | FE843889-C0E6-49B7-AB06-8F36740A5B99 |
| 1898 | Damascus     | <measureGrp location="Damascus" when="1898" source="03C4A6FC-AA3B-4D47-ADA9-61DC253CE8EC"><measure commodity="barley" unit="qr" quantity="7188">barley        | qr  | 7188</measure>  | <measure commodity="currency" unit="gbp" quantity="8000">gbp    | 8000</measure></measureGrp>    | 03C4A6FC-AA3B-4D47-ADA9-61DC253CE8EC |
| 1898 | Beirut       | <measureGrp location="Beirut" when="1898" source="A85C3773-BED0-4F10-A05B-BA718961F238"><measure commodity="barley" unit="ton" quantity="2100">barley         | ton | 2100</measure>  | <measure commodity="currency" unit="gbp" quantity="9475">gbp    | 9475</measure></measureGrp>    | A85C3773-BED0-4F10-A05B-BA718961F238 |
| 1897 | Beirut       | <measureGrp location="Beirut" when="1897" source="A85C3773-BED0-4F10-A05B-BA718961F238"><measure commodity="barley" unit="ton" quantity="4150">barley         | ton | 4150</measure>  | <measure commodity="currency" unit="gbp" quantity="16000">gbp   | 16000</measure></measureGrp>   | A85C3773-BED0-4F10-A05B-BA718961F238 |
| 1898 | Haifa        | <measureGrp location="Haifa" when="1898" source="A85C3773-BED0-4F10-A05B-BA718961F238"><measure commodity="wheat" unit="qr" quantity="67500">wheat            | qr  | 67500</measure> | <measure commodity="currency" unit="gbp" quantity="102942">gbp  | 102942</measure></measureGrp>  | A85C3773-BED0-4F10-A05B-BA718961F238 |
| 1898 | Haifa        | <measureGrp location="Haifa" when="1898" source="A85C3773-BED0-4F10-A05B-BA718961F238"><measure commodity="barley" unit="qr" quantity="6600">barley           | qr  | 6600</measure>  | <measure commodity="currency" unit="gbp" quantity="3970">gbp    | 3970</measure></measureGrp>    | A85C3773-BED0-4F10-A05B-BA718961F238 |
| 1897 | Haifa        | <measureGrp location="Haifa" when="1897" source="A85C3773-BED0-4F10-A05B-BA718961F238"><measure commodity="wheat" unit="qr" quantity="36062">wheat            | qr  | 36062</measure> | <measure commodity="currency" unit="gbp" quantity="54093">gbp   | 54093</measure></measureGrp>   | A85C3773-BED0-4F10-A05B-BA718961F238 |
| 1897 | Haifa        | <measureGrp location="Haifa" when="1897" source="A85C3773-BED0-4F10-A05B-BA718961F238"><measure commodity="barley" unit="qr" quantity="1705">barley           | qr  | 1705</measure>  | <measure commodity="currency" unit="gbp" quantity="1065">gbp    | 1065</measure></measureGrp>    | A85C3773-BED0-4F10-A05B-BA718961F238 |
| 1898 | Haifa        | <measureGrp location="Haifa" when="1898" source="A85C3773-BED0-4F10-A05B-BA718961F238"><measure commodity="millet" unit="qr" quantity="10500">millet          | qr  | 10500</measure> | <measure commodity="currency" unit="gbp" quantity="8235">gbp    | 8235</measure></measureGrp>    | A85C3773-BED0-4F10-A05B-BA718961F238 |
| 1897 | Haifa        | <measureGrp location="Haifa" when="1897" source="A85C3773-BED0-4F10-A05B-BA718961F238"><measure commodity="millet" unit="qr" quantity="16988">millet          | qr  | 16988</measure> | <measure commodity="currency" unit="gbp" quantity="14864">gbp   | 14864</measure></measureGrp>   | A85C3773-BED0-4F10-A05B-BA718961F238 |
| 1898 | Latakia      | <measureGrp location="Latakia" when="1898" source="A85C3773-BED0-4F10-A05B-BA718961F238"><measure commodity="cereals" unit="ton" quantity="3941">cereals      | ton | 3941</measure>  | <measure commodity="currency" unit="gbp" quantity="23645.4">gbp | 23645.4</measure></measureGrp> | A85C3773-BED0-4F10-A05B-BA718961F238 |
| 1898 | Tripoli      | <measureGrp location="Tripoli" when="1898" source="A85C3773-BED0-4F10-A05B-BA718961F238"><measure commodity="wheat" unit="ton" quantity="1250">wheat          | ton | 1250</measure>  |                                                                 | </measureGrp>                  | A85C3773-BED0-4F10-A05B-BA718961F238 |
| 1898 | Tripoli      | <measureGrp location="Tripoli" when="1898" source="A85C3773-BED0-4F10-A05B-BA718961F238"><measure commodity="barley" unit="ton" quantity="5000">barley        | ton | 5000</measure>  |                                                                 | </measureGrp>                  | A85C3773-BED0-4F10-A05B-BA718961F238 |
| 1898 | Tripoli      | <measureGrp location="Tripoli" when="1898" source="A85C3773-BED0-4F10-A05B-BA718961F238"><measure commodity="maize" unit="ton" quantity="750">maize           | ton | 750</measure>   |                                                                 | </measureGrp>                  | A85C3773-BED0-4F10-A05B-BA718961F238 |
| 1897 | Beirut       | <measureGrp location="Beirut" when="1897" source="D3198FBB-974F-4308-BBC8-A682A14CD4F4"><measure commodity="barley" unit="ton" quantity="4150">barley         | ton | 4150</measure>  | <measure commodity="currency" unit="gbp" quantity="16000">gbp   | 16000</measure></measureGrp>   | D3198FBB-974F-4308-BBC8-A682A14CD4F4 |
| 1897 | Haifa        | <measureGrp location="Haifa" when="1897" source="D3198FBB-974F-4308-BBC8-A682A14CD4F4"><measure commodity="wheat" unit="qr" quantity="36062">wheat            | qr  | 36062</measure> | <measure commodity="currency" unit="gbp" quantity="54093">gbp   | 54093</measure></measureGrp>   | D3198FBB-974F-4308-BBC8-A682A14CD4F4 |
| 1897 | Haifa        | <measureGrp location="Haifa" when="1897" source="D3198FBB-974F-4308-BBC8-A682A14CD4F4"><measure commodity="barley" unit="qr" quantity="1705">barley           | qr  | 1705</measure>  | <measure commodity="currency" unit="gbp" quantity="1065">gbp    | 1065</measure></measureGrp>    | D3198FBB-974F-4308-BBC8-A682A14CD4F4 |
| 1897 | Tripoli      | <measureGrp location="Tripoli" when="1897" source="D3198FBB-974F-4308-BBC8-A682A14CD4F4"><measure commodity="wheat" unit="ton" quantity="4500">wheat          | ton | 4500</measure>  | <measure commodity="currency" unit="gbp" quantity="25000">gbp   | 25000</measure></measureGrp>   | D3198FBB-974F-4308-BBC8-A682A14CD4F4 |
| 1897 | Tripoli      | <measureGrp location="Tripoli" when="1897" source="D3198FBB-974F-4308-BBC8-A682A14CD4F4"><measure commodity="barley" unit="ton" quantity="14755">barley       | ton | 14755</measure> | <measure commodity="currency" unit="gbp" quantity="50020">gbp   | 50020</measure></measureGrp>   | D3198FBB-974F-4308-BBC8-A682A14CD4F4 |
| 1896 | Jaffa        | <measureGrp location="Jaffa" when="1896" source="35862167-C38B-44F4-BD35-171623673E22"><measure commodity="wheat" unit="qr" quantity="1091">wheat             | qr  | 1091</measure>  | <measure commodity="currency" unit="gbp" quantity="1920">gbp    | 1920</measure></measureGrp>    | 35862167-C38B-44F4-BD35-171623673E22 |
| 1895 | Jaffa        | <measureGrp location="Jaffa" when="1895" source="35862167-C38B-44F4-BD35-171623673E22"><measure commodity="wheat" unit="qr" quantity="4970">wheat             | qr  | 4970</measure>  | <measure commodity="currency" unit="gbp" quantity="3560">gbp    | 3560</measure></measureGrp>    | 35862167-C38B-44F4-BD35-171623673E22 |
| 1896 | Jaffa        | <measureGrp location="Jaffa" when="1896" source="35862167-C38B-44F4-BD35-171623673E22"><measure commodity="maize" unit="qr" quantity="20850">maize            | qr  | 20850</measure> | <measure commodity="currency" unit="gbp" quantity="14178">gbp   | 14178</measure></measureGrp>   | 35862167-C38B-44F4-BD35-171623673E22 |
| 1895 | Jaffa        | <measureGrp location="Jaffa" when="1895" source="35862167-C38B-44F4-BD35-171623673E22"><measure commodity="maize" unit="qr" quantity="4726">maize             | qr  | 4726</measure>  | <measure commodity="currency" unit="gbp" quantity="3200">gbp    | 3200</measure></measureGrp>    | 35862167-C38B-44F4-BD35-171623673E22 |
| 1896 | Jaffa        | <measureGrp location="Jaffa" when="1896" source="35862167-C38B-44F4-BD35-171623673E22"><measure commodity="barley" unit="qr" quantity="1000">barley           | qr  | 1000</measure>  | <measure commodity="currency" unit="gbp" quantity="635">gbp     | 635</measure></measureGrp>     | 35862167-C38B-44F4-BD35-171623673E22 |
| 1895 | Jaffa        | <measureGrp location="Jaffa" when="1895" source="35862167-C38B-44F4-BD35-171623673E22"><measure commodity="barley" unit="qr" quantity="650">barley            | qr  | 650</measure>   | <measure commodity="currency" unit="gbp" quantity="360">gbp     | 360</measure></measureGrp>     | 35862167-C38B-44F4-BD35-171623673E22 |
| 1895 | Jaffa | <measureGrp location="Jaffa" when="1895" source="48EF5545-F790-4F88-BEC9-F2B7EA906728"><measure commodity="wheat" unit="qr" quantity="4970">wheat   | qr | 4970</measure>  | <measure commodity="currency" unit="gbp" quantity="3560">gbp  | 3560</measure></measureGrp>  | 48EF5545-F790-4F88-BEC9-F2B7EA906728 |
| 1894 | Jaffa | <measureGrp location="Jaffa" when="1894" source="48EF5545-F790-4F88-BEC9-F2B7EA906728"><measure commodity="maize" unit="qr" quantity="2356">maize   | qr | 2356</measure>  | <measure commodity="currency" unit="gbp" quantity="2000">gbp  | 2000</measure></measureGrp>  | 48EF5545-F790-4F88-BEC9-F2B7EA906728 |
| 1895 | Jaffa | <measureGrp location="Jaffa" when="1895" source="48EF5545-F790-4F88-BEC9-F2B7EA906728"><measure commodity="maize" unit="qr" quantity="4726">maize   | qr | 4726</measure>  | <measure commodity="currency" unit="gbp" quantity="3200">gbp  | 3200</measure></measureGrp>  | 48EF5545-F790-4F88-BEC9-F2B7EA906728 |
| 1895 | Jaffa | <measureGrp location="Jaffa" when="1895" source="48EF5545-F790-4F88-BEC9-F2B7EA906728"><measure commodity="barley" unit="qr" quantity="650">barley  | qr | 650</measure>   | <measure commodity="currency" unit="gbp" quantity="360">gbp   | 360</measure></measureGrp>   | 48EF5545-F790-4F88-BEC9-F2B7EA906728 |
