# Data Modeling with Postgres
---


## Introduction

A startup called Sparkify wants to anaylze data that they have been collecting
on songs and user activity on their new music streaming app. It is of particular
interest for them what songs users are listening to. The data they have is stored
in a directory of JSON logs on user activity on the app and in a directory with
JSON metadata on the songs in their app.

This repository contains an ETL-pipeline to create tables for a postgres data base
and load the data from the JSON files into the data base. The resulting data base 
can be used to run queries and get an understanding on how Sparkify's app is used.


## Schema

### Fact Table

1. songplays - records in log data associated with song plays i.e. records with page `NextSong`
    - *songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent*

### Dimension Tables

2. users - users in the app
    - *user_id, first_name, last_name, gender, level*


3. songs - songs in music database
    - *song_id, title, artist_id, year, duration*


4. artists - artists in music database
    - *artist_id, name, location, latitude, longitude*


5. time - timestamps of records in songplays broken down into specific units
    - *start_time, hour, day, week, month, year, weekday*


## Files

`create_tables.py`

Python script to create postgres tables.

`etl.ipynb`

Jupyter Notebook for ETL testing.

`etl.py`

Python script to load data into postgres tables.

`README.md`

This file.

`sql_queries.py`

Python script with SQL-queries to create and query tables.

`test.ipynb`

Jupyter Notebook to test postgres data base.

`data/`

Folder containing sample data that is a subset of the [Million Song Dataset](http://millionsongdataset.com/).


## Example Queries

If Sparkify's analytics team would be interested in how many distinct users used an
iPhone with their app, they could run the following query on the data base:

`SELECT COUNT(DISTINCT user_id) FROM songplays WHERE user_agent LIKE '%iPhone%';`