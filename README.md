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
First, import the library that will use to analyze in this project.
To examine the conservation status of species and their observations in national parks, the datasets are first loaded into DataFrames. Once in DataFrame format, the data can be explored and visualized using Python.

In the following steps, `Observations.csv` and `Species_info.csv` are read into DataFrames named `observations` and `species`, respectively. The contents of these DataFrames are then previewed with `.head()` to get an initial look at the data.
