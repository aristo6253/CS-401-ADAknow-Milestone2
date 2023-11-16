# Project Title: Gender Disparity Through Time, Cultures, Age, Genres, and TV Tropes

## Abstract

(150 words)
[Provide a concise description of the project, its motivation, focus on gender disparity, specific genres, TV tropes, and the intended insights or story.]
Gender equality has been one of the most engaging and popular cause in the last decades. It concerns every domains and spheres. The cinema has not been spared as it will be show. 
This project aim at showing the gender disparities in the cinema through time, countries, genre, actors age, and TV tropes. 
Its goal is also to identify what are the most impactfull factors 
influencing this disparities.
It will focus on 
the historical events that can have impacted the gender distribution over the time and the countries,
the gender representation within the TV tropes and how this affect the gender disparity,  
how the lifetime career can be impacted by the genre of the actors


## Research Questions

[List the specific questions the project aims to address.]

1. What are the most influencing factors in the gender representation in the cinema industry?
2. Which historical events had the most impact on the gender disparities in the cinema depending on the countries?
3. ...

## Proposed Additional Datasets

[Detail any additional datasets used, their size, format, and relevance to the primary data.]

- Dataset 1: tvtropes (<https://tvtropes.org/pmwiki/pmwiki.php/Main/UnisexTropes>)
- Dataset 2: bechdel.csv (<https://www.kaggle.com/datasets/treelunar/bechdel-test-movies-as-of-feb-28-2023>)
- ...

## Methods

### Exploratory Data Analysis (EDA)

[Describe the EDA. This might include initial data visualization, identification of patterns, anomalies, or preliminary insights about gender disparities in your datasets.]

<<<<<<< HEAD
#### Univariate Analysis

#### Bivariate Analysis (focused on gender)
=======
(Scratch answer) 
EDA:
Visualisation of the files of the characters, movies, tv tropes. 
Rename the code of the movies names, countries and language with corresponding names only.
Various visualization of the data frames. 
>>>>>>> 847e0fc40d99085b75a00320d31bffdba066c76f

### Data Preprocessing

[Outline the preprocessing steps needed for your datasets. This could involve cleaning data, handling missing values, normalizing or transforming data, feature selection, etc.]

For the part of the study of the gender distribution based on various characteristics with the present actors in the character data file:
- Selection of the movies from the movie metadata with corresponding charactere and actors information from the charactere metadata.
- Dropping of the actors with none or several gender association
- Count of the unique values in the actors, movies, charactere to evaluate the size of the population.
- Naïve observations of the gender distribution over the actors and movies characteristics and selection of what appear to be the most interesting and relevant characteristics: the actors age, the movie country, genre and year of release.
- Several Pearson correlations and t-tests were naively performed over those distribution to verify if the rejection of the null hypothesis (assessing the absence of correlation) was possible.
- a Linear regressions was also performed on the distribution of the gender representation in the movies over the years to observe the difference of evolution of the two genders over the years. 
- Selection of the countries for the assesment of the culture impact on the gender repartition. In order to observe the impact of the culture over the gender distribution, it was decided to take countries from different continents to ensure the difference of cultures. The countries with the most amount of movies per continent were selected: United-States (North america), United Kingdom (Europe), India (Asia), Mexico(Center America) and Argentina(South America). No country from Africa was selected because of a lack of data.
- Definition of a range of the years for which enough movies have been released
- Definition of a range of age for which the impact of the age will be studied over the actor population 

=======
- Remove all instances of from the `character.metadata.tsv` that are missing the gender of the actor/caracter

- Added a caracter `Role` attribute to the `character.metadata.tsv` that is either Main Character (MC) or Supporting Character (SC). This was done following a naive approach, looking wether the name or surname of a character is present in the plot summary of the movie in the `plot_summaries.txt` file. If the name or surname of the character is present in the plot summary, then the character is considered a Main Character, otherwise it is considered a Supporting Character.

- Parsed the json-like structures given in the `Language`, `Country` and `Genre` attributes of the `movie.metadata.tsv` file. The parsing transformed the json structures into a list of strings, where each string is a language, country or genre of the movie.

- Reduced the number of genres from 363 down to 78, by mapping each genre to a set of more general genres (e.g. `Action/Adventure` -> `Action` and `Adventure`). The mapping was done manually, by looking at the genres and trying to find the most general genres that could be used to describe the movie. Note that it was attempted to perform the mapping through a hierarchical agglomerative clustering, but the results were not satisfactory.


### Analysis Techniques

[Discuss the analytical methods and techniques we plan to use, with essential mathematical details.]
In order to assess of the impact of the selected actors and movie characteristics, a balance of the samples need to be done for the study of each covariate. This will allow to separate and eliminate the cofounding effect of the others over the one obersved. The preselection of the data has been made according to this. The methods to be used will depend on the available samples size. For the limited size sample, random sampling with replactement method will be used to asses the stability and the consistency of the results observed. For other covariate, other matching methodes will be performed such as exact matching or propensity score.

## Proposed Timeline

- Milestone 1: Date and Objectives
- Milestone 2: Date and Objectives
- ...

## Organization Within the Team

[List roles and responsibilities of each team member, including internal milestones.]

- Alexandre Ben Ahmed Kontouli: Responsibilities
- Aristotelis Dimitriou: Responsibilities
- Juliette Dutheil: Responsibilities
- Maria Eleni Peponi: Responsibilities
- Stavros Papaiakovou: Responsibilities

## Questions for TAs (Optional)

## [Notebook Name]

[Describe the contents of the Jupyter Notebook, including initial analyses, EDA, and data handling pipelines.]
