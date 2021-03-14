# Data Modeling with Postgres & ETL Pipeline for Sparkify

## Udacity Data Engineer Nano Degree Project 1

### Introduction
Sparkify is a music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, their data resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app. However, this cannot provid an easy way to query the data.

### The goal
The purpose of this project is to create a Postgres database and ETL pipeline to optimize queries to help Sparkify's analytics team.

### Database & ETL pipeline

Using the song and log datasets, I create a star schema as shown below, which includes

- one fact table: songplays, and
- four dimension tables: users, songs, artists and time.

![Star Schema](star_schema.jpg)

### Python Scripts:
All the python scripts in the folder is run from terminal. 

e.g **python create_tables.py**

The source code is available in three separate Python scripts. Below is a brief description of the main files:

**sql_queries.py has all the queries needed to both create/drop tables for the database as well as a SQL query to get song_id and artist_id from other tables since they are not provided in logs dataset.
create_tables.py creates the database, establish the connection and creates/drops all the tables required using sql_queries module.
etl.py build the pipeline that extracts the data from JSON files, does some transformation (such as adding different time attributes from timestamp) and then insert all the data into the corresponding tables.
Therefore, we first run create_tables.py then etl.py to create the database, create tables, and then insert the data using the ETL pipeline.

### Database

The schema used for this exercise is the Star Schema: There is one main fact table containing all the measures associated with each event songplays, and 4-dimensional tables songs, artists, users and time, each with a primary key that is being referenced from the fact table.

On why to use a relational database for this case:

- The data types are structured (we know before-hand the structure of the jsons we need to analyze, and where and how to extract and transform each field)
- The amount of data we need to analyze is not big enough to require big data related solutions.
- This structure will enable the analysts to aggregate the data efficiently
- Ability to use SQL that is more than enough for this kind of analysis
