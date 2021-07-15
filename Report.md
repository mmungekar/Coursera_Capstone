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

The Foursquare and neighborhood data will be concatenated. Once venues are assigned to their neighborhoods, the concentration of Italian restaurants, pizza parlors, and general restaurants present in each neighborhood will be analyzed and classified via k-means clustering. Based on the composition of these clusters, we will recommend which neighborhoods would be the best candidates for opening a pizza place.

## Methodology

We begin by obtaining raw  New York location data by downloading the file from the provided CDN (credit: Coursera Skills Labs). From this data, we extract the 'Borough', 'Neighborhood', 'Latitude', and 'Longitude' attributes into a dataframe. In order to isolate the Staten Island data, we filter on all the data where 'Borough' is equal to 'Staten Island'.

Next, we load the necessary data from FourSquare by making an API call that outputs a list of venues that are within a defined radius of a set of specified coordinates. We query this API once for each Staten Island neighborhood, inputting the latitude and longitude coordinates obtained from the NY data each time. The result is that, for each Staten Island neighborhood, we have a list of all venues.

We conduct some preliminary analysis by viewing the quantity of venues per neighborhood. Afterward, we isolate the 'Italian Restaurant', 'Pizza Place', and 'Restaurant' classifications and build a one-hot encoding, in which all venues assign a '0' or '1' to each category depending on if the venue can be assigned to that category or not. We average all the encoding values across venues for each neighborhood to create a frequency average for each of these restaurant types for each neighborhood.

Using this encoding, we will cluster the neighborhoods into 4 groups using k-means clustering. We update our neighborhood data by tagging each individual neighborhood with its cluster label. Using Folium, we then visualize each color-coded neighborhood on a map of Staten island.

For each cluster, we look at the average Italian restaurant, pizza parlor, and restaurant frequency before examining each cluster in more detail. After we list out the neighborhoods in each cluster and their respective Italian restaurant, pizza parlor, and restaurant concentrations, we determine which cluster may be a suitable prospect for a pizza parlor owner.

## Results

The clustering results are displayed below, with Cluster 0 color-coded red, Cluster 1 color-coded purple, Cluster 2 in teal, and Cluster 3 in green.

![image](https://user-images.githubusercontent.com/25122350/125836724-339f294e-7014-42c2-9b33-b5dd66ef160e.png)

The four clusters obtained from the k-means clustering can be broken down as such:

| Cluster | Italian Restaurant Frequency | Pizza Parlor Frequency   | General Restaurant Frequency         |
| ----------------- | ------- | ------------- | -------------------------- |
0| .008103|	0.007819|	0.007126|
1|	0.158589|	0.019544|	0.012061|
2|	0.000000|	0.205634| 0.020032|
3	|0.033453|	0.098554|	0.007688|

After individually analyzing each cluster, the results are summarized as shown:
| Cluster | Italian Restaurant Frequency | Pizza Parlor Frequency   | General Restaurant Frequency         |
| ----------------- | ------- | ------------- | -------------------------- |
| 0        | Low     | Low | Low |
| 1       | High     | Low | Low |
| 2        |  Low     | Very High | Low |
| 3        | Low     | High | Low |

## Discussion

Cluster 0 appears to be the most promising candidate for opening a pizza parlor. Given a generally low concentration of all three categories examined (Italian restaurant, pizza parlor, and general restaurant), there appears to be very little direct competition. These neighborhoods appear to be on the outskirts of the island, largely to the north, away from the center.

Cluster 1 will present a moderate amount of competition to a prospective pizza place owner due to the high concentration of Italian restaurants. However, it still may be an option for a place which specializes in pizza, as the broader Italian restaurant category will tend to have other offerings on the menu and not focus as much on a single dish. This cluster is located primarily on the north-east part of the island.

Cluster 2 has a very high concentration of pizza parlors. As the saturation of pizza parlors in this region is especially high, it would not be recommended to open a pizza parlor in this cluster, which is located more towards the center of the island.

Cluster 3 has a high concentration of pizza parlors and a moderate-low concentration of Italian restaurants. This would not be a highly reccommended option unless our pizza parlor is particularly niche or provides a highly unique offering. These neighborhoods are largely clustered near the south and center of the island.

We recommend, overall, that any prospective pizza parlor owner choose to open their business on the outskirts/more suburban parts of the island, particularly in the north. Based on the assumption that competition is the driving factor in determining location, focusing on building a customer base a little further away from the island center would be a highly effective strategy unhindered by high levels of competition and market saturation closer to the island center.

## Conclusion

This project was targeted towards assisting potential pizza parlor owners in Staten Island, NY in determining which locations would be most advantageous for business. Through gathering Staten Island neighborhood data and obtaining a list of venues in each neighborhood, we were able to use k-means clustering to group all Staten Island neighborhoods by their concentrations of Italian restaurants, pizza places, and general restaurants.

The results demonstrate that the outskirts of the city (Cluster 0) are most promising option to avoid high levels of competition with other restaurants. Potential stakeholders can leverage these results to analyze the competition in potential business locations and maximize their own profit in areas with low competition and/or a demand for pizza places.

