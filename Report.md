## Introduction/Business Problem

This project intends to recommend the best places in Albequerque, NM for a prospective pizza place owner to open a shop.
The decision to open a business is often strongly dependent on the locale/neighborhood of the prospective business, and any business owner looking for information would be interested in more deeply analyzing location as a factor.
The problem statements would leverage the location data provided by Foursquare, which lists venues and their classifications by geographical coordinates.

## Data

This project will rely on Foursquare data of all venues located in Albequerque, NM. Attributes of relevance include venue name, venue category, and geographical coordinates in the format below:
| Venue | Latitude | Longitude   | Category         |
| ----------------- | ------- | ------------- | -------------------------- |
| Venue A        | -20     | 20 | Cafe |

This venue data will be paired with neighborhood data to list all venues present in a specific neighborhood. Neighborhood data will be obtained from Wikipedia with the following attributes:
| Borough | Neighborhood | Latitude   | Longitude         |
| ----------------- | ------- | ------------- | -------------------------- |
| Borough A        | Neighborhood B     | 20 | 80 |

The Foursquare and neighborhood data will be concatenated. Once venues are assigned to their neighborhoods, the types of venues present in each neighborhood will be analyzed to recommend which neighborhoods would be the best candidates for opening a pizza place.
