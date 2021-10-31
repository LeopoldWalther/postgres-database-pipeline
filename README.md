# Data Modeling with Postgres

This project is part of the Udacity Nanodegree Data Engineer.

## Introduction

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app.
The analytics team is particularly interested in understanding what songs users are listening to.
Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

They'd like a data engineer to create a Postgres database with tables designed to optimize queries on song play analysis, and bring you on the project.
Goal of this project is to create a database schema and ETL pipeline for this analysis.
The test.ipynb file tests the database and ETL pipeline by running queries given by the analytics team from Sparkify and compare your results with their expected results.

## Project Description

Idea of this project is to do data modeling with Postgres and build an ETL pipeline using Python.
As part of this fact and dimension tables are defined for a star schema for a particular analytic focus.
Additionaly an ETL pipeline is created that transfers data from files in two local directories into these tables in Postgres using Python and SQL.

## Project Stucture

* **etl.py**: The ETL-Pipeline which connects to the database, processes the files and stores the results in the tables of the Postgres database.

* **etl.ipynb**: The jupyter-notebook to test the functions of the ETL pipeline. Only for development purposes.

* **sql_queries.py**: This file contains all the SQL commands to create, insert and query the tables.

* **test.ipynb**: This jupyter-notebook serves to test with SQL queries if the tables are created and inserted correctly.

* **create_tables.py** A file to initialize the database and create the tables.

## Data Model

### Fact Table

#### Table "songplays"

| COLUMN      | TYPE      | CONSTRAINT  |
|---          |---	      |---	        |
| songplay_id	| SERIAL  	| PRIMARY KEY	|
| start_time	| TIMESTAMP	| NOT NULL   	|
| user_id	    | int	      | NOT NULL	  |
| level	      | varchar   |   	        |
| song_id	    | varchar	  |   	        |
| artist_id	  | varchar	  |   	        |
| session_id	| int	      |   	        |
| location	  | text	    |   	        |
| user_agent	| text	    |   	        |


 ### Dimensions Tables
 Following the star shape there is a Dimensions table for each dimension in the Fact Table.


 #### Table "users"

| COLUMN  	  | TYPE  	   | CONSTRAINT  	|
|---	        |---	       |---	          |
| user_id	    | int  	     | PRIMARY KEY	|
| first_name	| varchar	   |  	          |
| last_name	  | varchar	   |  	          |
| gender	    | varchar(1) |   	          |
| level	      | varchar	   |   	          |


#### Table "songs"

| COLUMN  	  | TYPE  	   | CONSTRAINT   	|
|---	        | ---	       |---	            |
| song_id	    | varchar  	 | PRIMARY KEY	  |
| title	      | text	     |  	            |
| artist_id	  | varchar	   |   	            |
| year	      | int        |   	            |
| duration	  | numeric	   |   	            |


#### Table "artists"

| COLUMN  	  | TYPE  	    | CONSTRAINT   	|
|---	        | ---	        |---	          |
| artist_id	  | varchar  	  | PRIMARY KEY	  |
| name	      | varchar	    |   	          |
| location	  | text	      |   	          |
| latitude	  | decimal	    |   	          |
| longitude	  | decimal     |   	          |


#### Table "time"

| COLUMN  	  | TYPE  	    | CONSTRAINT   	|
|---	        |---	        |---	          |
| start_time	| TIMESTAMP  	| PRIMARY KEY	  |
| hour	      | int	        |   	          |
| day	        | int	        |   	          |
| week	      | int	        |   	          |
| month	      | int	        |   	          |
| year	      | int	        |   	          |
| weekday	    | varchar	    |   	          |

 The query to insert data on this table is:


## Local Execution

For local execution you can use PostgreeSQL docker:

- Download docker image:

`` docker pull postgres ``

- Execute docker:

``docker run --name postgres --rm  -p 5432:5432 -e -d postgres``

- Connect string:

``"host=127.0.0.1 dbname=postgres user=postgres password=postgres port=5432" ``


## Licensing, Authors, Acknowledgements

Feel free to use my code as you please:

Copyright 2021 Leopold Walther

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
