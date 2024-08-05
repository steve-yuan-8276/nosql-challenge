# NoSQL Challenge

## Instructions

The UK Food Standards Agency evaluates various establishments across the United Kingdom and gives them a food hygiene rating. You've been contracted by the editors of a food magazine, _Eat Safe, Love_, to evaluate some of the ratings data to help their journalists and food critics decide where to focus future articles.

## Directory Structure
    
```    
    Nosql_Challenge/
    ├── Resources/
    │   └── establishments.json
    ├── Outputs/
    │   ├── NoSQL_setup_solution.ipynb
    │   ├── NoSQL_Analysis_Solution.ipynb
    ├── README.md
    ├── NoSQL_setup_solution.ipynb
    └── NoSQL_Analysis_Solution.ipynb
```    

### Explanation

- `NoSQL_setup_solution.ipynb`: Notebook for database setup and data updates.
- `NoSQL_Analysis_Solution.ipynb`: Notebook for exploratory data analysis.
- **Resources/**: Directory for input data files.
    - `establishments.json`: Provided food hygiene rating data file.
- **Outputs/**: Directory for Jupyter Notebooks.
    - hygiene_records.csv
    - rating_records.csv
- **README.md**: Project description file, including project background, directory structure, and instructions.

## Solution

### Part 1: Database and Jupyter Notebook Setup

Use `NoSQL_setup_solution.ipynb` for this section of the challenge.

1. Import the data provided in the `establishments.json` file from your Terminal. Name the database `uk_food` and the collection `establishments`. Copy the text you used to import your data from your Terminal to a markdown cell in your notebook.

2. Confirm that you created the database and loaded the data properly:

    - List the databases you have in MongoDB. Confirm that `uk_food` is listed.
    - List the collection(s) in the database to ensure that `establishments` is there.
    - Find and display one document in the `establishments` collection using `find_one` and display with `pprint`.
3. Assign the `establishments` collection to a variable to prepare the collection for use.

4. Add the following information to the database:
```
    
    {
        "BusinessName":"Penang Flavours",
        "BusinessType":"Restaurant/Cafe/Canteen",
        "BusinessTypeID":"",
        "AddressLine1":"Penang Flavours",
        "AddressLine2":"146A Plumstead Rd",
        "AddressLine3":"London",
        "AddressLine4":"",
        "PostCode":"SE18 7DY",
        "Phone":"",
        "LocalAuthorityCode":"511",
        "LocalAuthorityName":"Greenwich",
        "LocalAuthorityWebSite":"http://www.royalgreenwich.gov.uk",
        "LocalAuthorityEmailAddress":"health@royalgreenwich.gov.uk",
        "scores":{
            "Hygiene":"",
            "Structural":"",
            "ConfidenceInManagement":""
        },
        "SchemeType":"FHRS",
        "geocode":{
            "longitude":"0.08384000",
            "latitude":"51.49014200"
        },
        "RightToReply":"",
        "Distance":4623.9723280747176,
        "NewRatingPending":True
    }
```    

5. Find the BusinessTypeID for "Restaurant/Cafe/Canteen" and return only the `BusinessTypeID` and `BusinessType` fields.

6. Update the new restaurant with the `BusinessTypeID` you found.

7. The magazine is not interested in any establishments in Dover, so check how many documents contain the Dover Local Authority. Then, remove any establishments within the Dover Local Authority from the database, and check the number of documents to ensure they were deleted.

8. Some of the number values are stored as strings, when they should be stored as numbers.

    - Use `update_many` to convert `latitude` and `longitude` to decimal numbers.
    - Use `update_many` to convert `RatingValue` to integer numbers.

### Part 2: Exploratory Analysis

Use `NoSQL_Analysis_Solution.ipynb` for this section of the challenge.

1. Which establishments have a hygiene score equal to 20?

2. Which establishments in London have a `RatingValue` greater than or equal to 4?

3. What are the top 5 establishments with a `RatingValue` of 5, sorted by the lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?

**Hint:** You will need to compare the geocode to find the nearest locations. Search within 0.01 degree on either side of the latitude and longitude.

4. How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas.