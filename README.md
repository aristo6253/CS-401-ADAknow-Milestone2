---

# README: Trope Genderedness Assessment

## Introduction

This notebook, part of the 'Evolution of gendered tropes in film' project by ADAknow, aims to analyze gender roles in different film genres over time using gender-characteristic tropes.

## Proposed Additional Datasets

- **`film_tropes.csv`**: Contains 27,450 tropes associated with 17,000 films from the TvTropes database, including examples of these tropes.
- **Text Files (`female_word_file.txt`, `male_word_file.txt`)**: Lists of gendered pronouns, occupations, and other gendered terms from [UCLANLP's GN-GloVe](https://github.com/uclanlp/gn_glove).
- **Gendered Trope Datasets (`female_tvtropes.csv`, `male_tvtropes.csv`, `unisex_tvtropes.csv`)**: Tropes categorized as 'Always Female', 'Always Male', or 'Unisex' by TvTropes users.

## Methods

### Exploratory Data Analysis (EDA)

#### Initial Analysis

- Data import and structure verification of `film_tropes.csv`.
- Identification and handling of missing or duplicate values.

#### Univariate Analysis

- 

#### Bivariate Analysis (focused on gender)

- Exploration of relationships between tropes and gender, using the gendered lexicons.

### Data Preprocessing

#### Trope genderedness 
- Preprocessing of `film_tropes.csv` on axes of interest:
    - The 'Trope' and 'Example' columns are searched for missing values. As there are no missing values in the 'Trope' column, the rows with missing values in the 'Example' column are filled with a dummy value considering that even though an example of a trope may be Nan in a particular movie, it may be present in other movies.
    - The 'Trope' and 'Movie Title' columns are explored for duplicate values. These are also checked against the 'title_id' and 'trope_id' columns respectively to ensure their uniqueness. 
    - Having ensured their uniqueness, the dataframe is grouped by 'Trope' and the examples are aggegated into a cell. 

- Tokenisation and Lemmatisation: 
    - The examples provided for each tropes are tokenised and lemmatised using the `NLTK` library to obtain a list of words associated with each trope. This process is also undertaken for the `female_word_file.txt` and `male_word_file.txt` for consistency.
    - A new column with the processed examples is added to the dataframe containing the list of tokenised, and lemmatised words related to each trope. 
    - It is again verified that there are no tropes with no processed examples. 
    
- Quantification of 'genderness':
    - The counts of gendered words in the processed example tokens of each trope are computed using the gendered words in `female_word_file.txt` and `male_word_file.txt`. The 'MaleCount' and 'FemaleCount' column act as features for the 'Genderedness Score'.
    - A 'Genderedness Score' between [-1, 1] is assigned to each trope with [-1, 0] values signifying dominance of male characteristics and scores between [0, 1] signifying femininity.  
    - The result is exported in the `tropes_wscores.csv` file.

#### `character_metadata` gender counts exploration


### Analysis Techniques

- **Computation of 'Genderedness'**:
  - Gala et al.'s method as well as their `film_tropes.csv` dataset was employed to compute genderedness scores for each trope.
  - The distribution of genderedness scores was visualized using histograms.
  - The performance of the model was assessed using standard metrics as well as simple statistical tests.

- Model uncertainty and verification of performance:
    - The number of female and male related tropes is computed. The results are visualised with histograms verifying the skewness towards male tropes. 
    - Lists of 'Always Female', 'Always Male', and 'Unisex' tropes are extracted from TvTropes. These are converted to the CamelCase format used in the `tropes_wscores` dataframe. They are further assigned a score of 1 when 'Always Female', -1 when 'Always Male' and 2 when 'Unisex'.
    - The 'Genderedness' column of `tropes_wscores` is discretised considering the uncertainty of the model. The following thresholds are used:
        - anything above the median for female characterised tropes (i.e. [0,1]) is clearly female and assigned a score of 1
        - anything below the median for male characterised tropes (i.e. [-1,0]) is clearly male and assigned a score of -1
        - anything in between is unisex and assigned a score of 2
    - The `tropes_wscores` dataframe is merged with the processed 'Always Female', 'Always Male', and 'Unisex' dataframes for comparison.
    - The accuracy, precision, and recall of the model are computed by comparing its predictions to the 'Always Female', 'Always Male', and 'Unisex' expectations. 
    - Cohen's kappa is used to assess the statistical significance of the agreement between the model and the expected results.


- **Further Analysis**:
  - Examining the distribution of gendered tropes across film genres and time periods.
  - Assessing the representation of genders and the prevalence of gendered tropes in different genres.
  - Drawing conclusions on trope usage trends over time and across genres.

---

This README provides a comprehensive overview of the `trope_genderdedness_assessment.ipynb` notebook, outlining the datasets, methods, and analytical approaches used in the study.