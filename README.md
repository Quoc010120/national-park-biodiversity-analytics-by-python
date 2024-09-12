# Introduction

This project focuses on analyzing data from the National Park Service, specifically related to various species across different park locations and their conservation status. The key sections of this project include defining objectives, data preparation, analysis, data visualization, and drawing conclusions from the findings.

The project seeks to answer the following questions:
- What is the distribution of conservation status among species?
- Are certain species types more prone to endangerment?
- Are the differences between species and their conservation status statistically significant?
- Which animal is most common, and how are they distributed across parks?

**Data sources:**

The datasets `Observations.csv` and `Species_info.csv` were provided by [Codecademy.com](https://www.codecademy.com).

Note: The data used in this project is inspired by real-world data but is primarily fictional.

# Project objective
## Project goal
In this project, the analysis will be conducted from the viewpoint of a biodiversity analyst for the National Park Service. The primary goal of the National Park Service is to protect at-risk species and sustain biodiversity within their parks. As an analyst, the main focus will be to understand the characteristics of the species, their conservation status, and how they relate to the national parks. Key questions include:

- What is the distribution of conservation status among species?
- Are certain types of species more prone to being endangered?
- Are there significant differences between species and their conservation status?
- Which animals are most common, and how are they distributed across the parks?

## Data
This project has two data sets that came with the package. The first `csv` file has information about each species and another has observations of species with park locations. This data will be used to analyze the goals of the project. 

# Data preparation
To examine the conservation status of species and their observations in national parks, the datasets are first loaded into DataFrames. Once in DataFrame format, the data can be explored and visualized using Python.

In the following steps, the contents of these DataFrames are then previewed with `.head()` to get an initial look at first five rows of the data.

The `species_info.csv` file provides details about various species found in the National Parks. The dataset includes the following columns:

- category: The taxonomic category for each species
- scientific_name: The scientific name of each species
- common_names: The common names for each species
- conservation_status: The conservation status of each species

![First table](/img/table-1.png)

The Observations.csv file provides data on species sightings recorded in various national parks over the past week. The columns in this dataset are:

- scientific_name: The scientific name of each species
- park_name: The name of the national park where the sightings occurred
- observations: The count of observations made in the past 7 days

![Second-table](/img/table-2.png)

# Analytics
This section will delve deeply into the data and use the insights gained to perform further analysis.

## Data Exploration

To begin with, we'll examine the characteristics of the data by checking the dimensions and data types of the variables in both datasets.

For the `species` dataset:
- It has 5,824 rows, each with a unique category and scientific name.
- There are 4 distinct conservation status types.
- Out of the rows, 191 have data for the conservation status, while the rest are missing values.

![Third-table](/img/table-3.png)

For the `observations` dataset:
- It contains a total of 23,296 rows.
- There are 5,541 unique scientific names.
- It includes data from only 4 parks, with "Myotis lucifugus" being the most common scientific name and "Mountains National Park" being the most frequently reported park.

![Fourth-table](/img/table-4.png)

We will further explore each column in detail. The `category` column consists of 7 categories, including plants and animals. `Reptiles` make up the smallest portion with 79 species, while `birds` represent the largest group with 521 species.

![Fifth-table](/img/table-5.png)

Next, we will examine the conservation status variable in more detail. The missing values mentioned earlier are due to species that do not require any concern, so I will replace the `NaN` values with `No Intervention`. The total counts for each conservation status are as follows: 16 species are classified as Endangered, 4 species as In Recovery, 161 species as Species of Concern, 10 species as Threatened, and 5633 species as No Intervention.
- `Species of Concern`: declining or appear to be in need of conservation.
- `Threatened`: vulnerable to endangerment in the near future.
- `Endangered`: seriously at risk of extinction.
- `In Recovery`: formerly Endangered, but currently neither in danger of extinction throughout all or a significant portion of its range.

Based on the stacked bar chart below, we can observe that many endangered species, such as birds and mammals, are currently in recovery. However, birds outnumber mammals on the recovery list.

![Sixth-table](/img/table-6.png)

![Seventh-table](/img/table-7.png)

![graph-1](/img/graph-1.png)

## Data Analytics
### In Conservation

In the previous section, we examined the distribution of different animal types and their conservation statuses. Now, we want to explore the question: Are certain species more susceptible to becoming endangered? To analyze which animal types are more likely to face endangerment, I will create a new column called `conservation`, which will include any species with data other than `No Intervention.

![Eight-table](/img/table-8.png)

Next, I will add a new column called `protected_percentage`, which will represent the proportion of protected species within each type of species.

![Nineth-table](/img/table-9.png)

In this section, we will conduct chi-squared tests to determine if there are statistically significant differences in conservation status rates across different species. To perform the chi-squared test, a contingency table will be created, which should look like this:

|             | Protected | Not Protected |
| ----------- | ---------- | -------------- |
| Mammal      | 30         | 146            |
| Bird        | 75         | 413            |

The first test, named `contingency1`, will be populated with the correct values for mammals and birds.

The chi-squared test results provide several values, including the p-value, which in this case is 0.69. The standard threshold for statistical significance is a p-value of 0.05. Since 0.69 is much larger than 0.05, this indicates that there is no significant relationship between the conservation statuses of mammals and birds, meaning these variables are independent of each other.

The next comparison will test the difference between `Reptile` and `Mammal`.

The contingency table format will be as follows:

|             | Protected | Not Protected |
| ----------- | ---------- | -------------- |
| Mammal      | 30         | 146            |
| Bird        | 5          | 73             |

In this case, the p-value is 0.039, which is below the standard threshold of 0.05. This indicates that the difference between reptiles and mammals is statistically significant. The results suggest that mammals have a significantly higher rate of needing protection compared to reptiles.

### Species in each parks
The following analysis will focus on data collected by conservationists, who have recorded sightings of various species across multiple national parks over the last 7 days.

To determine the most prevalent animal and their distribution across parks, we first examine the species' common names in the dataset. Duplicate species names within rows are removed and collapsed into a single list for easier analysis.

After processing, "Bat" appeared 23 times, and "Shrew" 18 times.

![tenth-table](/img/table-10.png)

In the dataset, multiple scientific names correspond to different bat species. The next step is to identify the rows that reference bats. A new column will be added with boolean values to indicate whether each row represents a bat species (is_bat set to True). There seems to be a lot of species of bats and a mix of protected vs. non-protected species.

![eleventh-table](/img/table-11.png)

The next step involves combining the bat species data with the observations to generate a DataFrame that captures bat sightings across the four national parks.

![twelveth-table](/img/table-12.png)

Let's examine the total number of bat observations, aggregated across all species, for each national park.

The table below shows the number of bat observations made in each park over the past week. Yellowstone National Park has the highest count with 8,362 observations, while the Great Smoky Mountains National Park has the lowest with 2,411.

![thirdteenth-table](/img/table-13.png)

Now, let's break down the bat observations at each park into protected versus non-protected bat sightings. It appears that, with the exception of the Great Smoky Mountains National Park, each park has more sightings of protected bats compared to non-protected ones. This could be seen as a positive indicator for bat populations.

The plot below shows the results of the recent data manipulation. It indicates that Yellowstone and Bryce National Parks are performing well in terms of bat conservation, as evidenced by a higher number of protected bat sightings compared to non-protected species. In contrast, the Great Smoky Mountains National Park may need to enhance its conservation efforts, as it has reported more sightings of non-protected bat species.

![second-graph](/img/graph-2.png)

# Conclusions

The project successfully produced several data visualizations and insights about species across four National Parks in the dataset. It also addressed the initial questions:

- **What is the distribution of conservation status for species?**
  - The majority of species were not under conservation, with 5,633 species not protected compared to 191 that were.

- **Are certain types of species more likely to be endangered?**
  - Mammals and birds had the highest percentage of species under engdangered.

- **Are the differences between species and their conservation status significant?**
  - Although there was no significant difference in conservation percentages between mammals and birds, a statistically significant difference was observed between mammals and reptiles.

- **Which animal is most prevalent and what is their distribution amongst parks?**
  - Bats were the most frequently observed species, with the highest occurrence in Yellowstone National Park.

# Further Research

The dataset analyzed covered only the past 7 days, limiting the ability to study changes over time. It would be valuable to examine how the conservation status of various species evolves over longer periods. Additionally, the dataset lacks information on the area of each park. Considering that Yellowstone National Park is likely much larger than the other parks, this size difference could account for more observations and greater biodiversity. Finally, if precise location data were available, it would be possible to analyze the spatial distribution of species and investigate whether these observations are spatially clustered.
