# Building the Sparkify Song Plays Analysis Database

#### Purpose:
Startup client Sparkify requested for a PostgreSQL database to handle their song plays data for analysis. the client requested for a database in a star schema, accompanied by an ETL protocol that handles JSON data.

#### Overview of the Databases and Database Schema:
There are 5 tables in total, oriented in a star schema, with one fact table, and 4 dimension tables.

###### fact table: "songplays"
- The fact table supplies the metrics used for the song plays analytics.
    - columns: songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

###### dimension table: "users"
- the registered users in the app.
    - columns: user_id, first_name, last_name, gender, level
    
###### dimension table: "songs" 
- the available songs in the database.
    - columns: song_id, title, artist_id, year, duration
    
###### dimension table: "artists"
- the available artists in the database.
    - columns: artist_id, name, location, latitude, longitude
    
###### dimension table: "time"
- a timestamp record of when a song was played.
    - columns: start_time, hour, day, week, month, year, weekday
    
#### Overview of the ETL Process:

Sparkify provided two sources of data coming from the "song_data" directory, and the "log_data"
directory. the "songs" and "artists" tables are populated using song data, and the "users" and "time" tables are populated using the song data. The fact table is then populated via cursor execution of the "song_select" query. 

Sparkify requested for granularity in the timestamp (recorded as miliseconds), and so the timestamp is further processed into a detailed datetime format before inserting into the fact table. Finally, The data insertion into the dimension tables is automated via the "process_data" function.

###### querying the table:

The example query provided searches for all records with existing artist_ids:

![Example query](example_query.png)

the subset of the data that was inserted into the database only had one song record that had the artist_id field populated.








      
