## Introduction/Business Problem

For a prospective business owner, the location of a future venture is one of the most important factors in determining its success. Not only does a potential business owner need to be cognizant of the cost of the area, but they will also need to be aware of the general composition of the neighborhood/locale, if their location is accesible from major roads, bus stops, and highways, and if they will be facing significant competition in the vicinity. 

Specifically focusing on pizza parlors, this project aims to recommend the best places in Staten Island, NY for a prospective pizza place owner to open a shop. The scope of this project will include analyzing the concentration of other pizza parlors in the neighborhood to determine if there is a high saturation of pizza parlors and/or Italian food in the vicinity. Other factors that play into whether or not a location is a good consideration for a business such as cost, major landmarks, and transportation networks, will be out of scope for this project.

We will leverage the location data provided by Foursquare, which lists venues and their classifications by geographical coordinates. To supplement this we will compile a list of Staten Island neighborhoods and their geographical coordinates from the Coursera Skills Lab NY dataset presented earlier in the course. Using a clustering approach, we will categorize neighborhoods by concentration of pizza parlors (direct competition), Italian restaurants (more moderate competition), and general restaurants (low/potential competition).

## Data

This project will rely on obtaining a list of all neighborhoods in Staten Island and listing all the pizza parlors, Italian restaurants, and other restaurants in each one. Using this data, we will analyze the neighborhoods by the frequency of occurrance of each type of venue and cluster similar neighborhoods.

Foursquare data will be used to identify all venues located in Staten Island, NY. Attributes of relevance include venue name, venue category, and geographical coordinates in the format below:
| Venue | Latitude | Longitude   | Category         |
| ----------------- | ------- | ------------- | -------------------------- |
| Venue A        | -20     | 20 | Cafe |

This venue data will be paired with neighborhood data to list all venues present in a specific neighborhood. Neighborhood data will be obtained from the NY neighborhood dataset provided on Coursera with the following attributes:
| Borough | Neighborhood | Latitude   | Longitude         |
| ----------------- | ------- | ------------- | -------------------------- |
| Borough A        | Neighborhood B     | 20 | 80 |

The Foursquare and neighborhood data will be concatenated. Once venues are assigned to their neighborhoods, the concentration of Italian restaurants, pizza parlors, and general restaurants present in each neighborhood will be analyzed to recommend which neighborhoods would be the best candidates for opening a pizza place.
