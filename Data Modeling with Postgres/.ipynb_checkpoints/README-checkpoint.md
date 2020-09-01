### Postgres Database Setup for a Music Streaming Startup

In this project, a music streaming startup company Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. In order to understand what songs users are listening to, a Postgres database with tables designed has been created to optimize queries on song play analysis.    

Language/Tool/Platform used: Python, SQL, Postgres    
 
#### Details

1. A star schema optimized for queries on song play analysis has been created. 

- A star schema fits the situation because it's denormalized and allows for fast aggregations. In this scenario, the analytics team is particular interested in understanding what songs users are listening to, which means they've already had a query in mind. Therefore, in order for teh query to be quickly run, a start schema is created.      

2. Fact and dimension tables have been defined for a particular analytic focus.        

- Fact Table
    - songplays
        - songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent
- Dimension Tables
    - users
        - user_id, first_name, last_name, gender, level
    - songs
        - song_id, title, artist_id, year, duration
    - artists
        - artist_id, name, location, latitude, longitude
    - time
        - start_time, hour, day, week, month, year, weekday

3. An ETL pipeline that transfers data from JSON files in two local directories into these tables in Postgres has been written.   

#### Files Explanation    

1. `test.ipynb` displays the first few rows of each table for database check.      
2. `create_tables.py` drops and creates tables. Run this file to reset tables before each time you run your ETL scripts.   
3. `etl.ipynb` reads and processes a single file from song_data and log_data and loads the data into tables. This notebook contains detailed instructions on the ETL process for each of the tables.    
4. `etl.py` reads and processes files from song_data and log_data and loads them into tables.     
5. `sql_queries.py` contains all sql queries, and is imported into the last three files above.    
6. `README.md` provides discussion on the project.  
  
#### Example Query

1. To know what songs haven been listened by costumers who paid 

> query = "SELECT title FROM songs JOIN songplays ON songs.user_id = songplays.user_id WHERE level = 'paid'"    

2. To To know what artists haven been listened by costumers    

> query = "SELECT title FROM artists JOIN songplays ON artists.artist_id = songplays.artist_id"    




