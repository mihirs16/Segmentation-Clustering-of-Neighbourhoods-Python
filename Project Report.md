
<h1>Battle of Neighbourhoods</h1>

<h2>Project Report</h2>

***

<h3>Introduction to the Business Problem </h3>

The Problem: Finding a suitable location for opening a new Food Business in the City of Manchester.

In order to determine a suitable neighbourhood to set up a food business, the most important factor to consider is the amount of Human Traffic.
This can be estimated by looking at whether the neighbourhood is well connected transportation-wise or not, or is there a nearby hotspot like a 
supermarket or a tourist spot like a Station or a Museum, etc. These could help insure a healthy intake of customers with the regulars being pleased
due to well connectivity and newcomers finding it in their paths due to proximity to hotspots.

Target Audience: To help those who might be looking to open a new food business in Manchester or let this be served as an example of how to 
                 look for a neighbourhood to open a similar food business.

<h3>Description of Data</h3>

For the project to deliver on the proposed promises, data corresponding to the factors affecting the choice of neighbourhood must be fed.

<h5>Locational Data</h5>

Locational Data will be collected in two parts:-
    1. List of Postal Codes and their corresponding neighbourhoods in Manchester
        This data can be scraped off of the Wikipedia Page(https://en.wikipedia.org/wiki/M_postcode_area).
    2. Latitude and Longitude corresponding to each Postal Code is extracted out of 
       the available CSV file(https://www.getthedata.com/open-postcode-geo).

<h5>Human Traffic Data</h5>

Amount of human traffic can be determined using the data from Foursquare API.
It can be estimated relatively to other neighbourhoods by comparing their attributes:-
    1. Ease of Access: Can be determined by analysing the no. of venues with the category indicating public transport.
    2. Area Trends: Can be determined by analysing the nearby venues for hotspots like supermarkets.
Higher is better

<h3>Methodology</h3>

The task was carried out in 4 steps:-
    1. Obtaining locational Data
    2. Obtaining venue and crowd traffic Data
    3. Clustering Neighbourhoods based on traffic Data
    4. Analysis

<h5>Obtaining Locational Data</h5> 
[cell 2 to cell 9]

A list of neighbourhoods and their corresponding postal codes were obtained by scraping data off of a Wikipedia page(https://en.wikipedia.org/wiki/M_postcode_area). This was done with the help of the popular module known as BeautifulSoup.
Then the Latitudes and Longitudes corresponding to each postal code was obtained an openly available CSV file (https://www.getthedata.com/open-postcode-geo). However, this was in a raw form and had to be cleaned. The smaller postal codes were dropped from the data and the mean of the coordinates were taken. 
Once the data was cleaned, processed and stored into a Pandas dataframe, all the neighbourhoods were plotted on a map using the popular package known as Folium.
The result is shown below:-

![map_geodata.png](attachment:map_geodata.png)

<h5>Nearby Venues and Crowd Traffic</h5>
[cell 10 to 17]

This was obtained using the Foursquare API. Using the 'explore' API Endpoint a list of venues was obtained and the venues whose category indicated that it was either a transportation hub or a hotspot were filtered out and put into a datafame. 
This dataframe was then merged with the main dataframe containing location data for all neighbourhoods.
The dataframe thus obtained was then encoded using One-Hot Encoding in order to prepare the data to be processed 'categorically'.

<h5>Clustering Data</h5>

It was decided that there would be 5 clusters of data.
The algorithm used was KMeans Clustering. A model was prepared using the KMeans tool provided in the Sci-Kit Learn Package.
The neighbourhood data was then mapped again on the Folium Map this time color coded with the respect to each of the clusters they belonged to.

The resulting plot is as shown below:-

![map_clusterdata.png](attachment:map_clusterdata.png)

<h3>Analysis</h3>

Each of the clusters were labeled as 0, 1, 2, 3 and 4 respectively.

<h5>For Cluster 0</h5>

![df_cluster_0.png](attachment:df_cluster_0.png)

The above plot was obtained indicating a better overall distribution of connectivity and nearby hotspots|

<h5>For Cluster 1</h5>

![df_cluster_1.png](attachment:df_cluster_1.png)

The above plot was obtained indicating that this cluster of neighbourhoods contained most of the supermarkets in Manchester and would provide a good traffic of regular and household customers.

<h5>For Cluster 2</h5>

![df_cluster_2.png](attachment:df_cluster_2.png)

The above plot was obtained indicating that this cluster of neighbourhoods were connected through Tram Stations and would have provided a good footfall of new customers while providing accessibility to the regulars too.

<h5>For Cluster 3</h5>

![df_cluster_3.png](attachment:df_cluster_3.png)

The above plot was obtained indicating that this cluster of neighbourhoods were connected through Train Stations and has the potential to provide a very good base of travelling and resting customers.
Although, this neighbourhood might experience a relative declination in the amount of regular customers.

<h5>For Cluster 4</h5>

![df_cluster_4.png](attachment:df_cluster_4.png)

This cluster is contains those neighbourhoods which contain a no. of Bus Stops. Therefore, these neighbourhoods experience a good base of travelling customers as well as very good accessibility for the regulars too due to its inter and intra city connectivity

<h3>Results</h3>
 Clusters 2 and 4 are excellent neighbourhoods to setup a Food Business since they provide both:
 
     1. Accessibility to the regular and city based customers.
     2. Visibility for the travelling and tourist customers.
 Due their proximity to Tram and Bus Stations respectively.
 
 Cluster 3 contains neighbourhoods great for providing with travelling customers, tourists, resting and lodging customers however might fail to provide with a healthy number of regular customers.
 
 Cluster 1 contains neighbourhoods around supermarkets which are capable of providing with a very strong regular and household customer base. Although it may not be as visible to new and travelling customers.
 
 Cluster 0 contains neighbourhoods with good overall connectivity and visibility but they score relatively low against other individually focused clusters. However the stallion of this cluster is the Manchester
 Airport which has excellent connectivity and provides a very good tourist and traveller's customer base.

<h3>Conclusion</h3>

The neighbourhoods of Manchester were successfully studied by being divided into clusters on the basis of the venues and connectivity of each neighbourhood using KMeans Clustering.
