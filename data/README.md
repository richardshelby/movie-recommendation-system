## /data

This folder structure was taken from the cookie cutter data science template.

https://cookiecutter-data-science.drivendata.org/

```
├── data
│   ├── external       <- Data from third party sources.
│   ├── interim        <- Intermediate data that has been transformed.
│   ├── processed      <- The final, canonical data sets for modeling.
│   └── raw            <- The original, immutable data dump.
```

## data/interim

### Overview_Vector_Embeddings.csv

Contains vector embeddings from the "overview" column of the original data source.

### cleanmovies.csv

cleaned version of movies.csv in the raw folder with columns from crew.csv, prodcomps.csv, prodcountries.csv, crew.csv and spokenlangs.csv added 
Initial dataset was 4803x24, cleaned dataset is 3223x18
The following cleaning steps were taken:
    1. remove rows with missing or zero values in the budget column
    2. remove rows with missing values in the genre column
    3. remove rows with missing or zero values in the revenue column
    4. remove rows with missing or zero values in the vote_count column
    5. remove rows with missing or zero values in the directors column 
    6. remove rows with missing values in the release_date column
    7. remove rows with missing values in the cast column
    8. remove rows with missing or zero values in the runtime column
    9. left join table on movie names with array aggregated table subsets (grouping on name and movie title) from the crew.csv file
        a. data was subsetted for executive producer, original composer, director of photography, writer
    10. left join table on movie names with array aggregated table subsets (grouping on name and movie title) from the prodcomps.csv file
        a. data was subsetted for production company
    11. left join table on movie names with array aggregated table subsets (grouping on name and movie title) from the prodcountries.csvfile
        a. data was subsetted for production countries
    12. left join table on movie names with array aggregated table subsets (grouping on name and movie title) from the spokenlangs.csv file
        a. data was subsetted for language names 
    13. drop any duplicate rows and unnecessary fields 
    
cleaned movies csv has the following fields: index, title(from title in movies.csv), budget, genres, id, keywords, overview, popularity, vote_average, vote_count, cast, director, executive_producer, original_music_composer, director_photography, production_country, production_company, languages


## /data/raw

### movies.csv

### crew.csv
Nested JSON within movies.csv with crew information that has been pulled out into it's own table with a movie title column added

### prodcomps.csv
Nested JSON within movies.csv with production company information that has been pulled out into it's own table with a movie title column added

### prodcountries.csv
Nested JSON within movies.csv with production country information that has been pulled out into it's own table with a movie title column added

### spokenlangs.csv
Nested JSON within movies.csv with spoken language information that has been pulled out into it's own table with a movie title column added

source:
https://www.kaggle.com/datasets/harshshinde8/movies-csv?resource=download
