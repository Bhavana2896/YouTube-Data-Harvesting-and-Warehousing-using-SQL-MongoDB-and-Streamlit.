# YouTube-Data-Harvesting-and-Warehousing-using-SQL-MongoDB-and-Streamlit.
Problem Statement:
The problem statement is to create a Streamlit application that allows users to access and analyze data from multiple YouTube channels. The application should have the following features:
  Ability to input a YouTube channel ID and retrieve all the relevant data (Channel name, subscribers, total video count, playlist ID, video ID, likes, dislikes, comments of each video) using Google API.
 Option to store the data in a MongoDB database as a data lake.
 Ability to collect data for up to 10 different YouTube channels and store them in the data lake by clicking a button.
 Option to select a channel name and migrate its data from the data lake to a SQL database as tables.
Ability to search and retrieve data from the SQL database using different search options, including joining tables to get channel details.

Approach: 
Set up a Streamlit app: Streamlit is a great choice for building data visualization and analysis tools quickly and easily. You can use Streamlit to create a simple UI where users can enter a YouTube channel ID, view the channel details, and select channels to migrate to the data warehouse.
Connect to the YouTube API: You'll need to use the YouTube API to retrieve channel and video data. You can use the Google API client library for Python to make requests to the API.
Store data in a MongoDB data lake: Once you retrieve the data from the YouTube API, you can store it in a MongoDB data lake. MongoDB is a great choice for a data lake because it can handle unstructured and semi-structured data easily.
Migrate data to a SQL data warehouse: After you've collected data for multiple channels, you can migrate it to a SQL data warehouse. You can use a SQL database such as MySQL or PostgreSQL for this.
Query the SQL data warehouse: You can use SQL queries to join the tables in the SQL data warehouse and retrieve data for specific channels based on user input. You can use a Python SQL library such as SQLAlchemy to interact with the SQL database.
Display data in the Streamlit app: Finally, you can display the retrieved data in the Streamlit app.
Overall, this approach involves building a simple UI with Streamlit, retrieving data from the YouTube API, storing it in a MongoDB data lake, migrating it to a SQL data warehouse, querying the data warehouse with SQL, and displaying the data in the Streamlit app.

The code provided is a Python script that uses various libraries and APIs to fetch data from YouTube, store it in MongoDB, and migrate it to a PostgreSQL database. It also includes a Streamlit application for user interaction.

Here's a breakdown of what the code does:

1. Imports necessary libraries, including `googleapiclient` for interacting with the YouTube API, `pymongo` for working with MongoDB, `psycopg2` for connecting to a PostgreSQL database, `re` for RegEx operations and `streamlit` for creating the user interface.
2. Connects to MongoDB using the provided connection string and sets the database to "youtube_data".
3. Sets the YouTube API key for making requests to the YouTube API.
4. Connects to a PostgreSQL database using the provided credentials.
5. Defines a function `parse_duration` to convert the duration of a video from the YouTube API response format to seconds.
6. Defines a function `get_channel_data` that takes a YouTube API client and a channel ID as inputs. This function retrieves channel details, video details, and comments for a given channel ID.
7. Defines a function `migrate_data_to_mongodb` that takes a channel ID as input and migrates the channel data to MongoDB. It uses the `get_channel_data` function to retrieve the data and inserts or updates the data in the "migrated_channels" collection.
8. Defines a function `migrate_data_to_sql` that takes a channel ID as input and migrates the channel data from MongoDB to a PostgreSQL database. It retrieves the channel data from MongoDB, checks if the data already exists in PostgreSQL, deletes the existing data if necessary, and inserts the new data into the appropriate tables.
9. Defines a Streamlit application function `main` that sets up the user interface using Streamlit. It includes sections for fetching data from YouTube and migrating the data to MongoDB and PostgreSQL.
10. The main function uses Streamlit components to create input fields, buttons, and dropdowns for user interaction. It calls the `get_channel_data` function to fetch channel data from YouTube and displays it as JSON. It also calls the `migrate_data_to_mongodb` and `migrate_data_to_sql` functions when the corresponding buttons are clicked, using the selected channel IDs from the dropdowns.
11. The script sets the Streamlit page layout, sets the Streamlit app title, and calls the `main` function to run the application.

Overall, this script provides a way to fetch YouTube channel data, store it in MongoDB, and migrate it to a PostgreSQL database using a Streamlit application for user interaction.
