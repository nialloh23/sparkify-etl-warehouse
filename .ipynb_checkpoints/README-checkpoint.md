# Sparkify Music Streaming Application 

This repo is focused on creating an **ETL pipeline** to load data related to songs and user activity  
on a new music streaming app into a **new postgresql database**.

The raw data has been provided in the form of a directory with JSON logs of app user activity and a directory with JSON metadata of songs.
The purpose of the database is to provide an optimized data store for the analytics team to carry out analysis on the apps activity.  


## Database Schema

The database shema has been chose to create a star pattern which is optimized for queries on song play analysis.
The use of the star schema ensures data intensive read queries are fast as the number of joins are minimized by the de-normalized pattern.
As the main analysis to be carried out is focused on song plays we have placed the song plays table as the central fact table.  
Other data required to describe various aspects of the song_plays (users, songs etc.) are placed in connected dimension tables.

**Fact Table**
1. songplays - records in log data associated with song plays
- songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

**Dimension Tables**
2. users - users in the app
- user_id, first_name, last_name, gender, level

3. songs - songs in music database
- song_id, title, artist_id, year, duration

4. artists - artists in music database
- artist_id, name, location, latitude, longitude

5. time - timestamps of records in songplays broken down into specific units
- start_time, hour, day, week, month, year, weekday  


## ETL Pipeline

The ETL pipeline has been designed to extract data from song and log datasets (json files).  
After some standard transformations the data is then inserted into the new database model structure outlined above.  

