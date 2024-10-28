# data-sourcing-challenge
# NOAA Space Weather Prediction Center: Geomagnetic Storm Prediction Data Preparation

## Project Overview
This project prepares a dataset for predicting Geomagnetic Storms (GSTs) using data on Coronal Mass Ejections (CMEs) and GSTs sourced from NASA’s DONKI API. The goal is to create a merged dataset that can later be utilized in machine learning models to improve storm predictions, thereby supporting the NOAA Space Weather Prediction Center in forecasting potentially disruptive space weather events.

## Project Structure
The project is structured as follows:

1. **Part 1: Request CME Data from NASA’s DONKI API**  
   - Retrieved and processed CME data from NASA’s API, specifically targeting events between 2013-05-01 and 2024-05-01.
   - Filtered and expanded the `linkedEvents` column to facilitate a one-to-one relationship for data merging.

2. **Part 2: Request GST Data from NASA’s DONKI API**  
   - Retrieved and processed GST data using the same date range as the CME data.
   - Filtered for relevant events linked to CME activity and expanded the `linkedEvents` column to ensure compatibility with CME data.

3. **Part 3: Merge and Clean the Data for Export**
   - Merged the two datasets based on event identifiers (`gstID`, `CME_ActivityID`, `GST_ActivityID`, and `cmeID`).
   - Calculated the time difference between the occurrence of CME and subsequent GST events.
   - Exported the merged dataset as a CSV file, ready for use in machine learning modeling.

## Files
- **retrieve_data_solution.ipynb**: Main Jupyter notebook containing code to retrieve, process, and merge data from the NASA DONKI API.
- **.env**: Environment file storing the NASA API key. Ensure this file is never pushed to GitHub to maintain security.
- **merged_cme_gst_data.csv**: The final processed dataset ready for predictive modeling.

## Key Functions and Methods
- **API Integration**: Utilizes `requests` to retrieve data from NASA’s DONKI API.
- **Data Processing**: Processes JSON data to extract key fields and handle nested data structures.
- **Data Merging**: Merges data based on `activityID` fields and calculates time differences between CME and GST events.
- **Error Handling**: Includes robust error handling with `try-except` blocks to ensure data integrity.
