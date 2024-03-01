# Biodiversity
## Cleaning and Analysis of National Parks Biodiversity Data

Data on biodiversity of endangered species in National Parks has been provided by Codecademy as part of a portfolio project prompt.

The brief on the project states that the data is from the National Parks Service and covers different species and parks. It states that we will investigate to find any patterns or themes to the types of species that become endangered. During this project we are to analyze, clean up, and plot data as well as pose questions and seek to answer them in a meaningful way. 

The initial dataset included two csv's, 'observations' and 'species_info.csv'. Observations.csv contains 23296 rows  of data on the species observed  within the subject National Parks, with a count of observations, park where it was observed and scientific name. The species_info.csv contains columns for scientific name, common names, and conservation status and has data for 5824 species.

Using python 3.10.12.
### Libraries
numpy as np
pandas as pd
matplotlib pyplot as plt
matplotlib.ticker - StrMethodFormatter
matplotlib.ticker as ticker
seaborn as sns 
statsmodels.api as sm
statsmodels.stats.multicomp - pairwise_tukeyhsd
scipy - stats
scipy.stats - chi2_contingency

### Data Cleaning
In a Jupyter Notebook, data_cleaning_biodiversity.ipynb, the data has been cleaned, deduplicated, and merged.
- Dropped fully duplicated rows
- Check for missing values
- Replaced large number of missing values in 'conservation status' with 'No Status'
- Check for and resolved conflicting values in 'conservation status'.
- Check for complex duplication -- duplicate scientific name with unique common names caused over-reporting of some species.
- Remove complex duplication due to differences in 'common_names'
- Remove ' National Park' from all every value in park_name
- Check data shape -- There are now 5541 scientific names observed in 7 categories in each of the four National Parks: Bryce, Great Smoky Mountain, Yellowstone, and Yosemite.
- Save the data to a new csv, 'biodiversity_data.csv'

### Analysis
- Added column to reflect protection_listing of species as binary value where 0 is not protected and 1 is protected status.
- Visualized data and described range of data and categorical values
- Chi2, p-values found for correlation between species category and protection listing for full dataset, subset of plants, subset of animals
- Chi2, p-values found for correlation between species category and conservation status for subset of protected status animals
- Cramér's V calculated for strength of relationship between species category and protection listing for full dataset
- Cramér's V calculated for strength of relationship between species category and protection listing for subset of protected status animals
- Ordinary Least Squares (OLS) model created for relationship between National Park (park_name) and observations
- ANOVA calucated from model fit to find F (strength of relationship) and p-value (statistical significance) for park_name/observations
- Turkey HSD performed to find pairwise combinations of all parks and their respective mean observations
- OLS modeled for interaction of National Park and species category with respect to observations for the subset of protected status animals
- ANOVA two-way calculated from model to find relationship of each variable and their interaction

### Conclusions
Species category across the dataset was moderately correlated with protection listing.
Plant species had no correlation with protection listing. 
Animal species showed a very weak, but statisically significant correlation. 
The weak relationship between animal species and protection listing suggested that a more nuanced analysis might show a more robust influence, so covariance analysis was performed on the subset of protection listed animals.
There is a moderate strength, statistically significant relationship between species category and conservation status. 

The ANOVA for the ordinary least squares model of National Park and observations showed a statistically significant,  strong correlation to the mean observations across the dataset. Following up on the ANOVA, analysis with Tukey HSD was used to find the pairwise relationship of the means between each of the National Parks. All pairwise relationships were statistically significant. 

Finally, the interaction of species category and National Park were modeled vs observations for the subset of animals with protection listing. The strongest correlation was found between National Park and observations, with a strong, statistically significant difference of the means. Species Category was also correlated to observational means with a more moderate, but still statistically significant relationship. However, the variables are independent as the interaction between National Park and Species Category did not have a statistically significant relationship. 