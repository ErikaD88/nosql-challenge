## UK Food Standards Agency Data Analysis

This project analyzes food hygiene ratings from the UK Food Standards Agency. The goal is to prepare, clean, and query the data to help journalists and food critics identify establishments for future articles. The data is stored in a MongoDB NoSQL database, and Python is used for data manipulation and analysis.

# Table of Contents
	1.	Overview
	2.	Instructions
	3.	Technologies Used
	4.	Steps Performed
	      •	Part 1: Database and Jupyter Notebook Setup
	      •	Part 2: Database Updates
	      •	Part 3: Exploratory Analysis
	5.	Results
	6.	Setup and Usage

# Overview

The UK Food Standards Agency evaluates establishments across the United Kingdom and assigns hygiene ratings. This project uses a dataset (establishments.json) to create a MongoDB database and analyze the data to answer specific questions posed by the magazine Eat Safe, Love.

# Instructions

The project involves three main steps:
	1.	Database Setup: Import the provided dataset into MongoDB and validate the database structure.
	2.	Database Updates: Clean and update the data, including adding new records and removing irrelevant ones.
	3.	Exploratory Analysis: Query the database to answer specific questions using PyMongo and Pandas.

# Technologies Used
	•	Python:
	•	Libraries: pymongo, pandas, json, pprint
	•	MongoDB:
	•	Database: uk_food
	•	Collection: establishments
	•	Jupyter Notebook:
	•	For running and documenting the analysis.

# Steps Performed

# Part 1: Database and Jupyter Notebook Setup

1.	Imported the data into MongoDB using the following command:

     mongoimport --db uk_food --collection establishments --drop --file establishments.json --jsonArray

2.	Connected to MongoDB using PyMongo.
	
3.	Verified the database and collection:
	•	Listed databases to ensure uk_food exists.
	•	Listed collections to ensure establishments exists.
	•	Queried one document to confirm the data was loaded.

# Part 2: Database Updates
	
 1.	Added a New Restaurant:
	•	Inserted the following restaurant into the database:

 {
    "BusinessName": "Penang Flavours",
    "BusinessType": "Restaurant/Cafe/Canteen",
    "AddressLine1": "Penang Flavours",
    "PostCode": "SE18 7DY",
    ...
}
2.	Updated BusinessTypeID:
	•	Queried and updated the BusinessTypeID for “Penang Flavours”.
	
3.	Removed Dover Establishments:
	•	Queried and removed all establishments with LocalAuthorityName: "Dover".
	
4.	Corrected Data Types:
	•	Converted longitude, latitude, and RatingValue fields to appropriate numeric types.

# Part 3: Exploratory Analysis

The following queries were performed:
	
 1.	Establishments with a Hygiene Score of 20:
	•	Found and counted establishments where the hygiene score is 20.
	•	Displayed the first result and created a Pandas DataFrame.
	
 2.	Establishments in London with RatingValue >= 4:
	•	Queried establishments in London with a RatingValue of 4 or higher.
	
 3.	Top 5 Establishments near “Penang Flavours”:
	•	Found the top 5 establishments with a RatingValue of 5 and the lowest hygiene scores near “Penang Flavours”.
	
 4.	Local Authorities with a Hygiene Score of 0:
	•	Used aggregation to find the top 10 local authorities with the most establishments scoring 0 in hygiene.

# Results

The results of the exploratory analysis include:
	
 1.	Hygiene Score of 20:
	•	Number of establishments: 41
	•	Examples provided in the DataFrame.
	
 2.	London Establishments with RatingValue >= 4:
	•	Number of establishments: 33
	•	Examples provided in the DataFrame.
	
 3.	Top 5 Establishments near “Penang Flavours”:
	•	Sorted by hygiene score.
	•	Examples provided in the DataFrame.
	
 4.	Top Local Authorities with Hygiene Score of 0:
	•	Example:

 _id         count
Thanet      1130
Greenwich    882
Maidstone    713
...

# Setup and Usage

1.	Install MongoDB:
	•	Download and install MongoDB Community Edition.
	•	Ensure MongoDB is running on localhost:27017.

2.	Clone the Repository:

    git clone <your-repository-url>
    cd <your-repository-name>

3.	Load Data into MongoDB:
	•	Place establishments.json in the project directory.
	•	Use the mongoimport command or Python script to import the data.
	
4.	Run Jupyter Notebooks:
	•	Open the NoSQL_setup.ipynb and NoSQL_analysis.ipynb files.
	•	Follow the steps in each notebook to complete the setup and analysis.
 
