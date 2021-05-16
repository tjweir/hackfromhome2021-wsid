# hackfromhome2021-wsid

# Watt Should I Do?

# Problem
I want to help save the Earth, I’m busy, but I want to make an impact, what do I do?

# Solution
Use “Watt Should I do?” a global, yet hyper-relevant source of carbon footprint reduction.

With WSID, you will find people with similar energy usage profiles and find out what made the biggest impact on their carbon footprint, so you can do the same.

Stand on the shoulders of giants and improve as a planet!


# Data science solution
We [built a database](https://github.com/tjweir/hackfromhome2021-wsid/blob/main/Simulate_Data.ipynb) that allows for comparison of the effect of a wide variety of metrics on the energy usage of a user. Based on the characteristics of the user, we can:
- connect them with the wider community
- provide recommendations on what actions will optimally decrease their energy usage

```python
|    House |   latitude |   longitude | energy_type   | heating_type   | glazing_types   | vehicle_type   | domicile_type   | season   |   temperature | Temp_cat   | house_size   |   num_occupants |   year_built | insulation   | SmartHouse   | EPC_rating   |   num_appliances |   energy_usage_pm |
| --------:|-----------:|------------:|:--------------|:---------------|:----------------|:---------------|:----------------|:---------|--------------:|:-----------|:-------------|----------------:|-------------:|:-------------|:-------------|:-------------|-----------------:|------------------:|
|        1 |    50.9722 |   -2.46096  | solar         | electric       | single          | general        | semi detached   | Summer   |            24 | Medium     | Medium       |               2 |         1946 | Low          | Full         | F            |               29 |           921.183 |
|        2 |    58.8654 |   -6.66844  | solar         | electric       | double          | electric       | semi detached   | Summer   |            24 | Medium     | Medium       |               4 |         1952 | Medium       | Full         | E            |               41 |          1681.39  |
|        3 |    50.3025 |   -6.18593  | solar         | electric       | triple          | electric       | terraced        | Summer   |            24 | Medium     | Medium       |               3 |         1994 | High         | Semi         | B            |               15 |           788.82  |
|        4 |    57.6175 |    1.43463  | grid          | electric       | double          | electric       | terraced        | Summer   |            19 | Low        | Medium       |               3 |         1972 | Medium       | Full         | D            |               18 |          1383.45  |
|        5 |    55.471  |    1.18143  | grid          | natural gas    | single          | electric       | semi detached   | Summer   |            19 | Low        | Medium       |               1 |         1981 | Low          | Full         | G            |               42 |          1234.74  |
|        6 |    51.6489 |   -1.33     | solar         | electric       | double          | electric       | terraced        | Summer   |            23 | Medium     | Medium       |               3 |         1996 | Medium       | Semi         | C            |               48 |          1005.4   |
|        7 |    52.5106 |   -4.5937   | solar         | electric       | double          | general        | terraced        | Summer   |            23 | Medium     | Medium       |               3 |         1986 | Medium       | Full         | D            |               13 |           802.231 |
|        8 |    53.1629 |   -4.0228   | solar         | electric       | double          | general        | semi detached   | Summer   |            20 | High       | Small        |               3 |         1938 | Medium       | Full         | E            |               13 |           876.162 |
|        9 |    56.6824 |   -1.52844  | solar         | electric       | double          | electric       | detached        | Summer   |            21 | Medium     | Medium       |               1 |         1985 | Medium       | Semi         | C            |               29 |          1106.55  |
|       10 |    59.4325 |   -3.12034  | grid          | natural gas    | triple          | electric       | detached        | Summer   |            20 | High       | Medium       |               4 |         1964 | High         | Semi         | B            |               24 |          1184.7   |
|       11 |    53.1535 |    0.823109 | solar         | electric       | triple          | electric       | semi detached   | Summer   |            21 | Medium     | Medium       |               2 |         1973 | High         | Semi         | A            |               43 |          1133.39  |
|       12 |    53.6998 |    1.4553   | solar         | electric       | single          | electric       | semi detached   | Summer   |            16 | Low        | Small        |               5 |         1971 | Low          | Semi         | G            |               19 |          1155.95  |
|       13 |    57.3866 |   -4.56468  | solar         | electric       | single          | general        | terraced        | Summer   |            19 | Low        | Medium       |               2 |         1978 | Low          | Full         | F            |               43 |          1396.81  |
|       14 |    58.748  |   -7.62288  | grid          | heat pump      | double          | electric       | terraced        | Summer   |            23 | Medium     | Medium       |               1 |         1991 | Medium       | Full         | D            |               23 |          1315.1   |
|       15 |    51.7708 |   -3.50976  | solar         | electric       | single          | general        | semi detached   | Summer   |            20 | High       | Medium       |               2 |         1930 | Low          | Full         | F            |               39 |          1275.02  |
|       16 |    52.2959 |   -5.08968  | grid          | natural gas    | triple          | general        | semi detached   | Summer   |            20 | High       | Medium       |               1 |         1951 | High         | Full         | A            |               48 |           736.362 |
|       17 |    52.2658 |   -4.44617  | grid          | natural gas    | triple          | electric       | terraced        | Summer   |            22 | Medium     | Medium       |               2 |         1951 | High         | Semi         | A            |               18 |          1147.21  |
|       18 |    58.7962 |   -2.50764  | grid          | electric       | single          | electric       | terraced        | Summer   |            17 | Low        | Medium       |               3 |         1987 | Low          | Full         | F            |               30 |          1720.73  |
|       19 |    56.7128 |    0.19523  | grid          | natural gas    | single          | general        | semi detached   | Summer   |            17 | Low        | Medium       |               2 |         1931 | Low          | Semi         | G            |               29 |          1881.04  |
|       20 |    56.7481 |    0.552115 | grid          | heat pump      | double          | electric       | semi detached   | Summer   |            23 | Medium     | Medium       |               1 |         1960 | Medium       | Full         | E            |               45 |           920.147 |
|       21 |    59.1205 |    0.289951 | grid          | heat pump      | single          | general        | semi detached   | Summer   |            21 | Medium     | Medium       |               2 |         1994 | Low          | Semi         | G            |               13 |           826.683 |
|       22 |    55.1541 |   -3.50529  | grid          | electric       | single          | electric       | detached        | Summer   |            17 | Low        | Small        |               5 |         1946 | Low          | Full         | F            |               14 |          1836.18  |
|       23 |    51.7221 |   -1.04901  | grid          | electric       | double          | general        | terraced        | Summer   |            16 | Low        | Small        |               1 |         1964 | Medium       | Full         | E            |               19 |           917.194 |
|       24 |    51.2017 |    1.00013  | grid          | heat pump      | double          | general        | semi detached   | Summer   |            20 | High       | Medium       |               2 |         1946 | Medium       | Semi         | E            |               31 |          1060.82  |
|       25 |    50.7479 |   -1.34103  | solar         | electric       | double          | general        | detached        | Summer   |            17 | Low        | Medium       |               5 |         1980 | Medium       | Full         | E            |               21 |           820.94  |
|       26 |    54.3291 |   -0.598273 | grid          | natural gas    | single          | general        | detached        | Summer   |            20 | High       | Medium       |               1 |         1955 | Low          | Semi         | F            |               31 |          1366.56  |
|       27 |    55.296  |   -5.02879  | grid          | natural gas    | single          | general        | semi detached   | Summer   |            17 | Low        | Medium       |               4 |         1958 | Low          | Semi         | G            |               14 |          1757.66  |
|       28 |    52.6627 |   -2.70171  | solar         | electric       | single          | general        | terraced        | Summer   |            21 | Medium     | Small        |               4 |         1990 | Low          | Full         | G            |               11 |          1078.6   |
|       29 |    50.8481 |   -6.13331  | grid          | electric       | single          | general        | detached        | Summer   |            20 | High       | Medium       |               2 |         1986 | Low          | Full         | G            |               31 |          1792.9   |
```

We have imposed correlations across these features, simulating more realistic data to verify the effectiveness of our data science solutions. 
![image](https://user-images.githubusercontent.com/4414348/118413794-febcc380-b698-11eb-9658-87e3636be81a.png)

Next we applied a wide array of ML techniques to fine-tune the analyses and guide the development of our unique numE recommendation system.
![Capture1](https://user-images.githubusercontent.com/4414348/118413755-ccab6180-b698-11eb-92d4-0bd64f7017b4.JPG)

If you are interested in our data analyses, please have a look at the [Modeling_Data](https://github.com/tjweir/hackfromhome2021-wsid/blob/main/Analyze_Data.ipynb) notebook. 

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

## App Arch

![Arch](https://github.com/tjweir/hackfromhome2021-wsid/raw/main/app%20arch.png)

## User Journey

![User Journey](https://github.com/tjweir/hackfromhome2021-wsid/raw/main/user%20journey.png)

