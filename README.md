
# XML-Data-Wrangling-Repo
Springboard XML Data Wrangling Mini-project
****
Using data in 'data/mondial_database.xml', find

1. 10 countries with the lowest infant mortality rates
2. 10 cities with the largest population
3. 10 ethnic groups with the largest overall populations (sum of best/latest estimates over all countries)
4. name and country of a) longest river, b) largest lake and c) airport at highest elevation

# Solution

## Objective 1: Find 10 countries with lowest infant morality rates.

**Approach:** Loop through the document nodes to create a dictionary with `country` as the key and `infant_mortality` as the value, 
then convert this dict to a DataFrame. Use the DataFrame to get the 10 countries with the lowest infant mortality rates

## Objective 2 : 10 cities with the largest population.

**Approach:** The objective is to get the latest population of all the cities and for each city, get the latest population (i.e. population of  the most recent year). The structure of the XML to is 

`Countries --> Provinces -->City-->Population(for multiple years)`

The `province` node may or may not be present, if it is not present, the `city`  will be directly under countries. The high level steps to get the 10 cities with the largest population are
1. Setup a loop to go through each `country`
2. Create a dictionary of all provinces [key - id ; value - province name]
3. Go through each `city` in the `country`
4. Get the latest `population` entry
5. Collect all these values (`country, city, province, year, population`) in a list; use the dictionary created in step 2
6. At the end of the loop create a DataFrame from the list
7. Use the DataFrame to get the cities with the largest population



## Objective 3: 10 ethnic groups with the largest overall populations (sum of best/latest estimates over all countries)

**Approach:** Setup a list to collect the values, loop through the XML to collect the values in the list, then finally create a DataFrame from the list to get the top 10 ethnic groups. High level steps
1. Loop through each `country` 
2. For each `country` store the latest population and the year
3. Loop through each `ethnicgroup` in the `country`
4. For each `ethnicgroup` get the population by using the `percentage` and population stored in step 2


## Objective 4. Name and country of a) longest river, b) largest lake and c) airport at highest elevation

**Approach:** A similar approach will be used for all 3 elements. First step will be to create a dictionary of country ids and 
country names, this dictionary will be used when updating the record with the country name. Once the country dictionary is created, 
loop through each of the elements (river, lake, airport), gather the element values, add to the list. Finally use the list to create 
a DataFrame and use the DataFrame to get the target information
