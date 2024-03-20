
# PYSPARK ASSIGNMENT 

This project aims to provide analysis and insights into COVID-19 data from various countries. It includes a Flask API server for accessing the data and performing analysis.

## Features

- Fetches COVID-19 data from an external API.
- Stores the data in CSV format for further analysis.
- Provides various endpoints to retrieve specific data and metrics.
- Calculates metrics such as most affected country, least affected country, total cases, etc.
- Utilizes Spark for data processing and analysis.

## Dependencies

- Python 3.x
- Flask
- PySpark
- Requests

## Setup and Usage


1. **Install Dependencies:**
   ```bash
   pip install pyspark jsonify requests Flask
   ```

2. **Run the Flask Server:**
   ```bash
   python main_server.py
   ```

   This will start the Flask server locally.

3. **Run the Print Results Script:**
   ```bash
   python Print_Results.py
   ```

   This script will fetch data from the Flask server's endpoints and print the results.

## Endpoints

- `/data`: Get the raw COVID-19 data.
- `/most_affected_country`: Get the most affected country.
- `/least_affected_country`: Get the least affected country.
- `/highest_cases_country`: Get the country with the highest number of cases.
- `/minimum_cases_country`: Get the country with the minimum number of cases.
- `/total_cases`: Get the total number of cases.
- `/most_efficient_country`: Get the most efficient country (highest recovery rate).
- `/least_efficient_country`: Get the least efficient country (lowest recovery rate).
- `/least_critical_country`: Get the country with the least critical cases.
- `/most_critical_country`: Get the country with the most critical cases.

**Access API Endpoints:**

   Once the Flask server is running, you can access the API endpoints using any HTTP client or web browser. For example:

   - To fetch raw COVID-19 data:
     ```
     GET http://127.0.0.1:5000/data
     ```

   - To get the most affected country:
     ```
     GET http://127.0.0.1:5000/most_affected_country
     ```

   - Similarly, you can access other endpoints mentioned in the Endpoints section.

**Understanding the Output:**

   - The output returned by the API endpoints is in JSON format.
   - Each endpoint provides specific information based on the analysis performed.
   - For example, `/most_affected_country` endpoint will return the country with the highest death rate.


