# hackfromhome2021-wsid

# Watt Should I Do?

# Problem
I want to help save the Earth, I’m busy, but I want to make an impact, what do I do?

# Solution
Use “Watt Should I do?” a global, yet hyper-relevant source of carbon footprint reduction.

With WSID, you will find people with similar energy usage profiles and find out what made the biggest impact on their carbon footprint, so you can do the same.

Stand on the shoulders of giants and improve as a planet!


# Data science solution
We built a database that allows for comparison of the effect of a wide variety of metrics on the energy usage of a user. Based on the characteristics of the user, we can:
- connect them with the wider community
- provide recommendations on what actions will optimally decrease their energy usage

```python
|    House | energy_type   | heating_type   | glazing_type   | vehicle_type   | domicile_type   | EPC_rating   | temperature   |   num_occupants |   year_built |   num_appliances |   insulation |   num_floors |   surface_area |   latitude |   longitude |   energy_usage |
| --------:|:--------------|:---------------|:---------------|:---------------|:----------------|:-------------|:--------------|----------------:|-------------:|-----------------:|-------------:|-------------:|---------------:|-----------:|------------:|---------------:|
|        0 | solar         | heat pump      | single         | electric       | terraced        | C            | low           |               2 |         1937 |               27 |           36 |            1 |            117 |    60.0064 |    0.501236 |       1329.92  |
|        1 | grid          | absorption     | single         | electric       | detached        | G            | medium        |               2 |         1976 |               24 |           27 |            2 |            220 |    57.5014 |   -1.6336   |       1988.39  |
|        2 | solar         | absorption     | triple         | electric       | semi detached   | D            | high          |               1 |         1968 |               46 |           18 |            3 |            101 |    59.2192 |   -7.26614  |       1183.68  |
|        3 | grid          | natural gas    | single         | electric       | semi detached   | A            | high          |               5 |         1977 |               46 |           15 |            2 |            241 |    55.6516 |   -0.841371 |       1258.45  |
|        4 | grid          | absorption     | double         | general        | detached        | D            | low           |               1 |         1993 |               16 |           16 |            3 |            193 |    57.885  |   -1.06893  |       1259.7   |
|        5 | solar         | absorption     | triple         | electric       | semi detached   | D            | high          |               4 |         1949 |               37 |           15 |            1 |            199 |    57.912  |   -1.79095  |        644.266 |
|        6 | solar         | heat pump      | single         | general        | detached        | G            | high          |               2 |         1956 |               36 |           11 |            3 |            273 |    53.2779 |   -0.231676 |       1877.2   |
|        7 | grid          | heat pump      | single         | electric       | terraced        | F            | high          |               5 |         1996 |               38 |           16 |            3 |            158 |    55.5224 |   -5.70937  |       1720.48  |
|        8 | grid          | natural gas    | triple         | general        | detached        | B            | high          |               3 |         1958 |               43 |           40 |            3 |            107 |    58.7108 |    0.13967  |       1230.5   |
|        9 | grid          | electric       | single         | electric       | semi detached   | A            | medium        |               2 |         1983 |               37 |           19 |            2 |            103 |    59.819  |   -0.265097 |       1359.95  |
|       10 | grid          | natural gas    | double         | general        | detached        | E            | high          |               4 |         1989 |               25 |           32 |            3 |            213 |    58.8506 |    1.52765  |        932.561 |
|       11 | grid          | natural gas    | double         | electric       | flat            | B            | high          |               1 |         1943 |               45 |           30 |            1 |            138 |    55.4483 |   -2.7181   |       1206.27  |
|       12 | solar         | natural gas    | double         | general        | detached        | B            | medium        |               1 |         1971 |               23 |           26 |            2 |            275 |    58.7312 |   -6.02984  |       1931.32  |
|       13 | solar         | heat pump      | triple         | electric       | flat            | A            | high          |               2 |         1990 |               37 |           27 |            1 |            234 |    53.6141 |   -1.10395  |       1248.13  |
|       14 | solar         | heat pump      | triple         | electric       | terraced        | B            | medium        |               4 |         1950 |               45 |           19 |            1 |            144 |    52.1737 |   -2.62071  |       1186.44  |
|       15 | solar         | heat pump      | single         | electric       | detached        | B            | low           |               3 |         1952 |               11 |           33 |            3 |            280 |    58.4395 |   -5.10068  |        605.227 |
|       16 | solar         | absorption     | double         | general        | flat            | C            | high          |               4 |         1990 |               19 |           38 |            1 |            177 |    59.9566 |   -3.10803  |       1429.45  |
|       17 | grid          | natural gas    | triple         | general        | flat            | G            | low           |               4 |         1949 |               15 |           28 |            1 |            203 |    50.1509 |   -2.39254  |       1304.27  |
|       18 | solar         | electric       | single         | electric       | detached        | C            | medium        |               1 |         1935 |               46 |           36 |            2 |            146 |    57.9685 |   -6.42134  |       1181.59  |
|       19 | solar         | electric       | single         | general        | detached        | E            | high          |               1 |         1952 |               29 |           30 |            2 |            271 |    52.2231 |    1.10601  |       1405.43  |
|       20 | grid          | heat pump      | single         | general        | flat            | B            | low           |               5 |         1946 |               15 |           41 |            1 |            267 |    58.4144 |   -0.239621 |        764.605 |
|       21 | solar         | absorption     | double         | electric       | semi detached   | E            | low           |               5 |         1933 |               24 |           29 |            1 |            147 |    59.3424 |   -1.8669   |       1085.19  |
|       22 | grid          | natural gas    | single         | electric       | semi detached   | D            | high          |               4 |         1938 |               25 |           12 |            2 |            216 |    51.9911 |   -1.39307  |       1370.86  |
|       23 | solar         | absorption     | triple         | general        | detached        | G            | high          |               5 |         1988 |               47 |           13 |            1 |            146 |    50.6147 |    1.09961  |       1040.07  |
|       24 | grid          | natural gas    | double         | general        | flat            | B            | medium        |               2 |         1959 |               49 |            3 |            1 |            185 |    58.4928 |    0.238026 |       1635.41  |
|       25 | solar         | electric       | triple         | electric       | flat            | C            | medium        |               2 |         1964 |               48 |           22 |            1 |            227 |    51.0197 |   -3.08698  |       1102.54  |
|       26 | solar         | heat pump      | triple         | electric       | terraced        | E            | low           |               4 |         1960 |               15 |           19 |            1 |            236 |    55.2508 |    0.773863 |        825.361 |
|       27 | grid          | heat pump      | single         | electric       | terraced        | D            | medium        |               4 |         1994 |               16 |            6 |            3 |            148 |    59.2102 |   -7.57324  |       1392.83  |
|       28 | solar         | electric       | single         | general        | flat            | D            | low           |               5 |         1954 |               11 |            3 |            1 |            255 |    59.1092 |   -3.73815  |       1279.82  |
|       29 | grid          | heat pump      | single         | electric       | terraced        | B            | low           |               1 |         1977 |               25 |            6 |            3 |            293 |    59.3321 |   -6.67619  |        773.767 |
```

## Link a user's profile to its community
Based only on the information the user is willing to provide, we connect the user to the larger community and make recommendations on which actions will lead to the most cost-efficient and effective reduction in energy usage. 

Linking a user to the community is implented on the basis of a similarity score, computed on all the available features, as depicted in this figure.

![similarity_score](https://user-images.githubusercontent.com/4414348/118400606-39ebd200-b65a-11eb-8283-b9b0a75960b7.png)

Depending on the requirements, specific features can be weighted more or less. For example, for a geospatial community, the latitude and longitude are highly relevant. 

## Predicting the most efficient action
Using large-scale data analyses, we compute **numE**, a single number that represents the most efficient action. This takes into account the cost-effectiveness, the energy usage reduction, the local (geospatial) considerations, and much more. 

## Mockups

![Home Page](https://github.com/tjweir/hackfromhome2021-wsid/raw/main/1-homepage.png)

![Login](https://github.com/tjweir/hackfromhome2021-wsid/raw/main/2-login.png)

![Password](https://github.com/tjweir/hackfromhome2021-wsid/raw/main/3-password.png)

![HMI](https://github.com/tjweir/hackfromhome2021-wsid/raw/main/4-hmi.png)

![Filter and Listing](https://github.com/tjweir/hackfromhome2021-wsid/raw/main/5-filter-and-list.png)

![Activity Detail](https://github.com/tjweir/hackfromhome2021-wsid/raw/main/6-detail.png)

