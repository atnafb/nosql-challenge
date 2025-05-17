# UK Food Standards Analysis

## Project Overview

This project analyzes UK Food Standards Agency data using MongoDB and Python. 

---

## Files and Folders

- **`Resources/`**
  - `establishments.json`: Contains the dataset to be imported into MongoDB.
  
- **`NoSQL_setup_starter.ipynb`**: Jupyter notebook for setting up the database, importing the dataset, and making requested modifications.

- **`NoSQL_analysis_starter.ipynb`**: Jupyter notebook for exploratory analysis based on magazine editors' questions.

---

## Prerequisites

1. **Python Libraries**
   - Install the required Python libraries:
     ```bash
     pip install pymongo pandas jupyterlab
     ```

2. **MongoDB**
   - Install and set up MongoDB on your machine.
   - Start the MongoDB server to access the database.

---

## Instructions

### Part 1: Database and Jupyter Notebook Setup

1. **Import Data into MongoDB**
   - From the terminal, import the dataset:
     ```bash
     mongoimport --type json --db uk_food --collection establishments --drop --jsonArray --file establishments.json
     ```
   - Confirm the database and collection setup using PyMongo.
   - NOTE: run the terminal at the resource folder to import data to the database 

2. **Setup Tasks**
   - Import the required libraries: `pymongo`, `pprint`.
   - Create a MongoDB client and access the `uk_food` database and the `establishments` collection.
  
---

### Part 2: Database Modifications

1. **Add a New Restaurant**  
   - The restaurant **Penang Flavours** was added to the `establishments` collection.

2. **Update Data**  
   - The `BusinessTypeID` for **Restaurant/Cafe/Canteen** was found and updated.  
   - Establishments in **Dover Local Authority** were removed from the collection.  
   - The following fields were converted:  
     - `latitude` and `longitude` were updated to decimal numbers ie Double.  
     - `RatingValue` was converted to integers, with non-numeric values coerced to null.
---

### Part 3: Exploratory Analysis

1. **Hygiene Score of 20**  
   - Establishments with a hygiene score of 20 were queried.  
   - The results were converted into a Pandas DataFrame, and the first 10 rows were displayed.

2. **Establishments in London with High Ratings**  
   - Establishments in London were queried using a `$regex` for Local Authority, with a condition of `RatingValue >= 4`.  
   - The results were converted into a Pandas DataFrame.

3. **Top 5 Establishments Near Penang Flavours**  
   - Establishments with `RatingValue = 5` were queried and sorted by:  
     - The lowest hygiene score.  
     - Proximity (within 0.01 degrees latitude and longitude) to **Penang Flavours**.

4. **Hygiene Score of 0 by Local Authority**  
   - The aggregation pipeline was used to count establishments with a hygiene score of 0 for each Local Authority.  
   - The results were sorted from highest to lowest, and the top 10 were displayed.

---

## Results and Analysis

All analysis results are documented and displayed in the respective Jupyter notebooks:
- `NoSQL_setup_starter.ipynb`
- `NoSQL_analysis_starter.ipynb`

---

## How to Run

1. **Clone the Repository**
   ```bash
   git clone <repository-url>
   cd nosql-challenge
2. **Import the dataset** - run the terminal at the Resource directory 
     ```bash
     mongoimport --type json --db uk_food --collection establishments --drop --jsonArray --file establishments.json
     ```
