# Using-hurdle-models-to-analyze-schistosomiasis-count-data
The model codes and analysis for the paper "Using hurdle models to analyze schistosomiasis count data of school children in the southern areas of Ghana" are presented here. It is a combination of Python and R codes.

## Files

The Rmd file contains the model codes used. Six distinct models under different scenarios were used.

The python (jupyter) file contains codes used for slicing dataframes, descriptive statistics and fugure plotting

## Methods

### Rmd

The standard Poisson, negative binomial (NB), zero-inflated Possion (ZIP), zero-inflated negative binomial (ZINB), hurdle Poisson (HP), hurdle negative binomial (HNB) models are the various models used.

Their corresponding R syntaxes are showing the table that follows below

| Model | Syntax |
| --- | --- |
| Poisson | glm("dependent variable ~ x1 + x2 + ... + xn", family = 'poisson', data = count_data) |
| NB | glm("dependent variable ~ x1 + x2 + ... + xn", family = negative.binomial(1), data = count_data |
| ZIP | zeroinfl(dependent variable ~ x1 + x2 + ... + xn, data = count_data, dist = "poisson") |
| ZINB | zeroinfl(dependent variable ~ x1 + x2 + ... + xn, data = count_data, dist = "negbin") |
| HP | hurdle(dependent variable ~ x1 + x2 + ... + xn, data = count_data, dist = "poisson") |
| HNB | hurdle(dependent variable ~ x1 + x2 + ... + xn, data = count_data, dist = "negbin") |


The results output of the each model is generated by "summary(model)"

```
# using the Possion model
poisson <- glm("dependent variable ~ x1 + x2 + ... + xn", family = 'poisson', data = count_data)
summary(poisson)
```
The libraries are readxl, mass, pscl

### ModelComparison.Rmd

In the "ModelComparison.Rmd" file, "count_data" is the name assigned to the schistosomiasis count data. 

* The data contains the columns; "Age", "Sex", "Class", "Community", "S_haematobium" , "S_mansoni", "Parent_Occupation", "Pipe_borne", "Tanker_treated", "Tanker_Untreated", "River_Stream", "Well_Borehole", "Age_group", "EduLevel", "Area", "schistosomiasis" 

* The ***five predictors*** used are; Age_group, Sex, Educational level, Area and Parent's occupation and ***ten predictors*** used are; Age_group, Sex, Educational level, Area, Parent's occupation, Pipe_borne, Tanker_treated, Tanker_Untreated, River_Stream and Well_Borehole

* The different intensity data used are; the ***all intensity*** (all sample data) and the ***low intensity*** count data named "count_data" and "low_intensity_data" respectively in the Rmd file.

* The models are assigned names in the format `{modelname}.model_{intensity data type}{number of variable}`. For example, if the Poisson model is applied using all intensity data and 10 predictors then we have the name assign to such syntax as `poisson.model_all10`. For a negative binomial applied with the low intensity data with 5 predictors, we will have `negbin.model_all10`.
