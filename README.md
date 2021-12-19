# Movies-ETL
We need to perform ETL on data from Wiki and Kaggle. Extract data from two sources stored as JSON and CSV transform it using Python and Pandas and finally load it in Postgresql database.

## Overview of the Analysis
 The Amazing Prime video team would like to develop an algorithm to predict which low budget movies being released will become popular so that they can buy streaming rights at a bargain. To inspire the team, have some fun and connect with the local coding community, Amazing Prime has decided to sponsor a hackathon. Providing a clean set of movie data and asking participants to predict the popular pictures.

Britta a member of the team has been tasked with creating the datasets for the hackathon. There are two data sources 
1. A scrape of wikipedia for all movies released since 1990, and 
2. rating data from Movie Land's website 

We need to help Britta to extract the data from the two sources , transform it into one, clean data sources, and finally load the data set into a SQL table.

## Resources
* Data Source: wikipedia-movies.json, movies_metadata.csv, ratings.csv
* Software: Python 3.7.10, Jupyter notebook 6.3.0, Postgresql -x64-11, pgAdmin 4 - version5.7

## Results:
#### Write an ETL function to read three data files
The function extract_transform_load takes in the .json and .csv files and converts them to dataframe wiki_movies_df, kaggle_metadata, ratings. You can find the function inside the jupyter notebook [ETL_function_test.ipynb](https://github.com/sucharita1/Movies-ETL/blob/4e8b4814f8039d1ad9197734ad9b7e5d55102410/ETL_function_test.ipynb)

#### Extract and Transform the Wikipedia Data
The function extract_transform_load takes in .json and .csv files then the  wikipedia data is cleaned using clean_movie function and the unwanted columns are removed then data is converted into a data frame wiki_movies_df and then using regex and parse dollar functons the row data is cleaned and format of the data is made uniform and date is changed to datetime format.You can find the function inside the jupyter notebook [ETL_clean_wiki_movies.ipynb](https://github.com/sucharita1/Movies-ETL/blob/4e8b4814f8039d1ad9197734ad9b7e5d55102410/ETL_clean_wiki_movies.ipynb)

#### Extract and Transform the Kaggle Data
The function extract_transform_load takes in .json and .csv files then the  wikipedia data is cleaned using clean_movie function and the unwanted columns are removed then data is converted into a data frame wiki_movies_dfand then using regex and parse dollar functons the row data is cleaned and format of the data is made uniform.Next the Kaggle data is also cleaned and unwanted columns are dropped. The data types of the columns are converted to numeric for fields like budget, popularity, id etc. Date is changed to datetime format. The columns are renamed after cleaning and transforming finally kaggle df, kaggle_metadata and wiki df, wiki_movies_df is merged to form movies_df. Next, ratings df is cleaned and transformed. next, ratings DataFrame is merged with the movies_df DataFrame, into the new DataFrame movies_with_ratings_df.You can find the function inside the jupyter notebook [ETL_clean_kaggle_data.ipynb](https://github.com/sucharita1/Movies-ETL/blob/4e8b4814f8039d1ad9197734ad9b7e5d55102410/ETL_clean_kaggle_data.ipynb)

#### Create the Movie Database
The function extract_transform_load takes in .json and .csv files then the  wikipedia data is cleaned using clean_movie function and the unwanted columns are removed then data is converted into a data frame wiki_movies_dfand then using regex and parse dollar functons the row data is cleaned and format of the data is made uniform.Next the Kaggle data is also cleaned and unwanted columns are dropped. The data types of the columns are converted to numeric for fields like budget, popularity, id etc. Date is changed to datetime format. The columns are renamed after cleaning and transforming finally kaggle df, kaggle_metadata and wiki df, wiki_movies_df is merged to form movies_df. Next, ratings df is cleaned and transformed. next, ratings DataFrame is merged with the movies_df DataFrame, into the new DataFrame movies_with_ratings_df. Next a connection is made to the local server and a database engine is created using sqlalchemy. Next, movies_df is converted into sql table movies using the replace if exists condition. Next, ratings table is dropped from postgresql and the code that prints out the elapsed time to import each row is added. You can find the function inside the jupyter notebook
[ETL_create_database.ipynb](https://github.com/sucharita1/Movies-ETL/blob/4e8b4814f8039d1ad9197734ad9b7e5d55102410/ETL_create_database.ipynb)

Finally, we run a query on the PostgreSQL database that retreives the number of rows for the movies and ratings tables. The movies table has 6,052 rows and the ratings table has 26,024,289 rows, as shown in the screenshots below saved as movies_query.png and ratings_query.png, respectively.

![movies_query.png](https://github.com/sucharita1/Movies-ETL/blob/4e8b4814f8039d1ad9197734ad9b7e5d55102410/Resources/movies_query.png?raw=true)

![ratings_query.png](https://github.com/sucharita1/Movies-ETL/blob/4e8b4814f8039d1ad9197734ad9b7e5d55102410/Resources/ratings_query.png?raw=true)
