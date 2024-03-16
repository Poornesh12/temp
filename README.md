
# MongoDB Python Application

This Python application is designed to interact with MongoDB and perform various operations such as connecting to the database, bulk loading JSON data into MongoDB collections, inserting new documents into collections, and executing MongoDB queries to support different functionalities.

## Project Structure

The project consists of several Python scripts, each addressing specific tasks as outlined in the assignment:

1. **main.py**: Entry point for the application, runs all the Python scripts sequentially.
2. **Q1_connect_db.py**: Contains functions to connect to MongoDB.
3. **Q2_bulk_load_jsonData.py**: Handles bulk loading of JSON data into individual MongoDB collections (comments, movies, theaters, users).
4. **Q3_Inserting_new_doc.py**: Defines Python methods and MongoDB queries to insert new documents into respective MongoDB collections.
5. **Q4a_comments_col.py**: Implements Python methods and MongoDB queries to support operations on the comments collection, such as finding top 10 users and movies with the most comments, and calculating the total number of comments created each month in a given year.
6. **Q4b_01_Nmovies.py**: Provides functions to find top N movies based on various criteria like highest IMDB rating, highest IMDB rating in a given year, etc.
7. **Q4b_02_Ndirectors.py**: Contains functions to find top N directors who created the maximum number of movies, in a given year, or for a given genre.
8. **Q4b_03_Nactors.py**: Implements functions to find top N actors who starred in the maximum number of movies, in a given year, or for a given genre.
9. **Q4b_04_each_genre.py**: Defines functions to find top N movies for each genre with the highest IMDB rating.
10. **Q4c_theatre_col.py**: Provides functionalities to find the top 10 cities with the maximum number of theaters and the top 10 theaters nearby given coordinates.

### main.py

This file orchestrates the execution of all Python scripts sequentially. Below are the details of this file:

1. **Functionality:**
    - Executes each Python script in the project sequentially.
    - Utilizes the `subprocess` module to run individual Python scripts.
    - Generates the path to each script using the `os` module.

2. **Dependencies:**
    - Relies on the `subprocess` and `os` modules from the Python standard library.

3. **Function Description:**
    - `run_script(script_path)`: Runs a Python script.
        - Parameters:
            - `script_path`: Path to the Python script.
        - Returns:
            - None.
        - Prints status messages indicating the success or failure of script execution.


4 **Error Handling:**
    - Captures and prints any exceptions that occur during script execution.

This file serves as the entry point for the project, automating the execution of various scripts in a predefined sequence. It promotes efficiency by eliminating the need for manual execution of individual scripts and ensures consistency in the project workflow.


### Q1_connect_db.py

This script provides a function to establish a connection to a MongoDB database. Below is an overview of its functionality:

1. **Dependencies:**
    - Imports `MongoClient` from `pymongo` for connecting to MongoDB.

2. **Functionality:**
    - Defines a function `connect_to_mongodb` to connect to a MongoDB database.
    - Attempts to establish a connection to the MongoDB instance running on the specified host and port.
    - Prints a success message upon successful connection and returns the MongoDB client object.
    - Handles exceptions that may occur during the connection process and prints appropriate error messages.
   
3. **Example Usage:**
    - Demonstrates the connection to MongoDB by calling the `connect_to_mongodb` function.
    - Upon successful connection, stores the MongoDB client object in the variable `mongo_client`.

4. **Error Handling:**
    - Catches exceptions that may occur during the connection process, such as connection errors or invalid host/port.
    - Prints error messages to the console in case of connection failure.

This script serves as a utility for establishing connections to MongoDB databases, enabling other scripts in the project to interact with the MongoDB instance seamlessly.

### Q2_bulk_load_jsonData.py

This script is responsible for bulk loading JSON files into their respective MongoDB collections. Here's an explanation of its functionality:

1. **Dependencies:**
    - Imports the `connect_to_mongodb` function from `Q1_connect_db.py` to establish a connection to MongoDB.
    - Imports `bson.json_util` for JSON document loading using BSON format.

2. **Functionality:**
    - Defines a function `load_json_file_to_collection` to load a JSON file into a MongoDB collection.
    - Opens the JSON file specified by the file path and reads it line by line.
    - Converts each line into a JSON object using `bson.json_util.loads`.
    - Inserts each JSON object as a separate document into the specified MongoDB collection.
    - Handles exceptions such as file not found or errors during the insertion process.

3. **Usage:**
    - The script is intended to be executed as the main program.
    - Connects to MongoDB using the `connect_to_mongodb` function.
    - For each MongoDB collection (comments, movies, theaters, users):
        - Loads the corresponding JSON file located in the `data` directory.
        - Calls the `load_json_file_to_collection` function to insert the JSON documents into the collection.

4. **Error Handling:**
    - Catches and handles exceptions such as file not found or errors during the insertion process.
    - Prints appropriate error messages to the console.

This script automates the process of loading JSON data into MongoDB collections, enhancing efficiency and ensuring data integrity within the database.

### Q3_Inserting_new_doc.py

This script is responsible for inserting a new document into a specified MongoDB collection. Below is an overview of its functionality:

1. **Dependencies:**
    - Imports `ObjectId` from `bson` and `connect_to_mongodb` function from `Q1_connect_db.py` for connecting to MongoDB.

2. **Functionality:**
    - Defines a function `insert_document` to insert a new document into a MongoDB collection.
    - Attempts to insert the document into the specified collection using the provided MongoDB client.
    - Logs the success or failure of the insertion process along with the inserted document's ID.
    - Closes the MongoDB connection after the insertion operation.

3. **Example Usage:**
    - Demonstrates the insertion of a new movie document into the 'movies' collection as an example.
    - The script connects to MongoDB, creates a new movie document, and inserts it into the 'movies' collection.

4. **Error Handling:**
    - Handles exceptions that may occur during the insertion process, such as connection errors or invalid documents.
    - Logs appropriate error messages to the console in case of failure.

This script facilitates the insertion of new documents into MongoDB collections, providing a straightforward method for adding data to the database.


### Q4a_comments_col.py

This script provides functions to perform MongoDB queries related to the comments collection. Below is an overview of its functionality:

1. **Dependencies:**
    - Imports necessary modules, including `connect_to_mongodb` from `Q1_connect_db`, and relevant modules from `bson.son` and `datetime`.

2. **Functions:**
    - `find_top_users_with_most_comments(db)`: Finds the top 10 users who made the maximum number of comments.
    - `find_top_movies_with_most_comments(db)`: Finds the top 10 movies with the most comments, along with movie titles.
    - `find_comments_count_by_month(year, db)`: Finds the total number of comments created each month in the given year.

3. **Error Handling:**
    - Catches exceptions that may occur during the query execution and prints appropriate error messages.

4. **Example Usage:**
    - Demonstrates the usage of each function by calling them within the `__main__` block after establishing a connection to MongoDB.
    - Prints the results of each query to the console.

### Q4b_01_Nmovies.py

This script provides functions to perform MongoDB queries related to the movies collection. Below is an overview of its functionality:

1. **Dependencies:**
    - Imports necessary modules, including `connect_to_mongodb` from `Q1_connect_db`.

2. **Functions:**
    - `find_top_directors_with_most_movies(N, db)`: Finds the top N directors who created the maximum number of movies.
    - `find_top_directors_with_most_movies_in_year(N, year, db)`: Finds the top N directors who created the maximum number of movies in a given year.
    - `find_top_directors_with_most_movies_in_genre(N, genre, db)`: Finds the top N directors who created the maximum number of movies for a given genre.

3. **Error Handling:**
    - Catches exceptions that may occur during the query execution and prints appropriate error messages.

4. **Example Usage:**
    - Demonstrates the usage of each function by calling them within the `__main__` block after establishing a connection to MongoDB.
    - Prints the results of each query to the console.

### Q4b_02_Ndirectors.py

This script provides functions to perform MongoDB queries related to the movies collection, specifically focusing on directors. Below is an overview of its functionality:

1. **Dependencies:**
    - Imports necessary modules, including `connect_to_mongodb` from `Q1_connect_db`.

2. **Functions:**
    - `find_top_directors_with_most_movies(N, db)`: Finds the top N directors who created the maximum number of movies.
    - `find_top_directors_with_most_movies_in_year(N, year, db)`: Finds the top N directors who created the maximum number of movies in a given year.
    - `find_top_directors_with_most_movies_in_genre(N, genre, db)`: Finds the top N directors who created the maximum number of movies for a given genre.

3. **Error Handling:**
    - Catches exceptions that may occur during the query execution and prints appropriate error messages.

4. **Example Usage:**
    - Demonstrates the usage of each function by calling them within the `__main__` block after establishing a connection to MongoDB.
    - Prints the results of each query to the console.

These scripts provide powerful tools for analyzing movie data stored in a MongoDB database, offering insights into the directors who have made the most contributions to the collection over different periods and in various genres. They can be integrated into larger applications or used independently for data analysis and reporting purposes.

### Q4b_03_Nactors.py

This script focuses on querying data related to actors from a MongoDB collection. Here's a detailed explanation:

1. **Dependencies:**
   - It imports the `connect_to_mongodb` function from `Q1_connect_db.py`.

2. **Functions:**
   - `find_top_actors_with_most_movies(N, db)`: Finds the top N actors who starred in the maximum number of movies.
   - `find_top_actors_with_most_movies_in_year(N, year, db)`: Finds the top N actors who starred in the maximum number of movies in a given year.
   - `find_top_actors_with_most_movies_in_genre(N, genre, db)`: Finds the top N actors who starred in the maximum number of movies for a given genre.

3. **Functionality:**
   - `find_top_actors_with_most_movies` aggregates movie data to find the top N actors who starred in the maximum number of movies. It unwinds the `cast` array, groups by actor, counts their appearances, and sorts by count.
   - `find_top_actors_with_most_movies_in_year` extends the previous function by filtering movies based on a given year before performing the aggregation.
   - `find_top_actors_with_most_movies_in_genre` further extends the functionality by filtering movies based on a given genre before performing the aggregation.

4. **Example Usage:**
   - It connects to MongoDB using the `connect_to_mongodb` function.
   - It demonstrates the usage of `find_top_actors_with_most_movies` by finding and printing the top 10 actors who starred in the maximum number of movies.
   - It also showcases `find_top_actors_with_most_movies_in_year` by finding and printing the top 10 actors for a specific year.
   - Additionally, it demonstrates `find_top_actors_with_most_movies_in_genre` by finding and printing the top 10 actors for a specific genre.

This script provides versatile functions to query MongoDB for information about actors based on various criteria such as total movies, movies in a specific year, and movies in a specific genre.

### Q4b_04_each_genre.py

This script is designed to find the top movies for each genre with the highest IMDB rating. Here's a breakdown of its components:

1. **Dependencies:**
   - It imports the `connect_to_mongodb` function from `Q1_connect_db.py`.

2. **Function:**
   - `find_top_movies_by_genre_with_highest_imdb_rating(N, db)`: This function finds the top N movies for each genre with the highest IMDB rating. It takes the number of top movies to retrieve for each genre (N) and the MongoDB database object (db) as arguments.
   
3. **Functionality:**
   - The function first fetches all genres present in the database.
   - Then, for each genre, it constructs an aggregation pipeline to find the top N movies with the highest IMDB rating in that genre.
   - It retrieves the movies, sorts them by IMDB rating in descending order, and stores them in a dictionary mapping each genre to its top N movies.
   - Finally, it returns this dictionary containing the top movies for each genre.

4. **Example Usage:**
   - It connects to MongoDB using the `connect_to_mongodb` function.
   - It retrieves the top movies for each genre with the highest IMDB rating by calling the `find_top_movies_by_genre_with_highest_imdb_rating` function and prints the results to the console.

### Q4c_theatre_col.py

This script deals with querying theater data from a MongoDB collection. Let's break it down:

1. **Dependencies:**
   - It imports the `connect_to_mongodb` function from `Q1_connect_db.py`.

2. **Functions:**
   - `calculate_distance(coord1, coord2)`: Calculates the distance between two coordinates using the Haversine formula.
   - `top_theatres_nearby_coordinates(db, coordinates, N)`: Finds the top N theaters nearby the given coordinates.
   - `top_cities_with_max_theaters(db)`: Finds the top 10 cities with the maximum number of theaters.

3. **Functionality:**
   - `calculate_distance` calculates the distance between two coordinates using the Haversine formula.
   - `top_theatres_nearby_coordinates` finds the top N theaters nearby a given set of coordinates. It retrieves all theaters, calculates their distances from the given coordinates, sorts them by distance, and returns the top N nearest theaters.
   - `top_cities_with_max_theaters` aggregates theater data to find the top 10 cities with the most theaters.

4. **Example Usage:**
   - It connects to MongoDB using the `connect_to_mongodb` function.
   - It demonstrates the usage of `top_cities_with_max_theaters` by finding and printing the top 10 cities with the most theaters.
   - It also showcases `top_theatres_nearby_coordinates` by finding and printing the top 10 theaters nearby a set of example coordinates.



