# Biodiversity
## Cleaning and Analysis of National Parks Biodiversity Data

Data on biodiversity of endangered species in National Parks has been provided by Codecademy as part of a portfolio project prompt.

The brief on the project states that the data is from the National Parks Service and covers different species and parks. It states that we will investigate to find any patterns or themes to the types of species that become endangered. During this project we are to analyze, clean up, and plot data as well as pose questions and seek to answer them in a meaningful way. 

The initial dataset included two csv's, 'observations' and 'species_info.csv'. Observations.csv contains 23296 rows  of data on the species observed  within the subject National Parks, with a count of observations, park where it was observed and scientific name. The species_info.csv contains columns for scientific name, common names, and conservation status and has data for 5824 species.

### Data Cleaning
In a ipynb, data_cleaning_biodiversity.ipynb, the data has been merged, cleaned and deduplicated. 
- Merge data on scientific_name
- Drop fully duplicated rows
- Check for missing values
- Resolve missing values -- Many missing values for conservation status
- Replace missing values with 'No Status'
- Check for complex duplication -- duplicate scientific name with unique common names caused over-reporting of some species.
- Remove complex duplication based on all rows except 'common_names'
- Remove ' National Park' from all every value in park_name
- Check data shape -- There are now 5541 scientific names observed in 7 categories in each of the four National Parks, Bryce, Great Smoky Mountain, Yellowstone, and Yosemite.
- Save the data to a new csv, 'biodiversity_data.csv'

### Analysis
