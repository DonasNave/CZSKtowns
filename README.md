# CZ and SK towns location data

## English

Database of CZ/SK towns and villages (combined from multiple sources, oldest at 2021) within sqlite database and csv file.

Purpose of this dataset was to combine PSC (ZIP) codes with towns and villages and their coordinates.

## Česky

Databáze českých a slovenských měst a obcí (kombinovaná z více zdrojů, nejstarší z roku 2021) v sqlite databázi a csv souboru.

Účelem tohoto datasetu bylo spojit PSČ s městy a obcemi a jejich souřadnicemi.

## Table cities

| id | name |    psc     |    latitude    |   longitude    |  location   |   country    |
|:---:|:---:|:----------:|:---------:|:---------:|:---------:|:----------:|
|  INT  | TEXT  |  TEXT  | REAL  | REAL  | TEXT  |  TEXT  |

## Usage

Simple snippets from python

```python
# Connect to the SQLite database file
conn = sqlite3.connect('cities.db')
cursor = conn.cursor()
```

```python
# Execute a SELECT query to retrieve all data from the 'cities' table
cursor.execute("SELECT * FROM cities")

# Fetch all rows from the result
rows = cursor.fetchall()
```

```python
# Insert data into the table
insert_data_query = '''
    INSERT INTO cities (name, psc, latitude, longitude, location, country) 
    VALUES (?, ?, ?, ?, ?, ?)
'''
cursor.executemany(insert_data_query, data)
conn.commit()
```
