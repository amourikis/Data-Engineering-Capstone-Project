# Data Engineering Capstone Project
## Data Engineering Capstone Project

# Project summary
This is the final project of Udacitys Data Engineering Nanodegree. For this project, I will be looking at the immigration data for the united states. More specifically, we're interested in looking at the following facts:
* the effects of temperature on the volume of travellers, 
* the seasonality of travel 
* the connection between the volume of travel and the number of entry ports (ie airports) 
* the connection between the volume of travel and the demographics of various cities

## Tools and Technologies
* Apache Airflow - To schedule and monitor our data pipeline.
* AWS S3 - For storage of raw and processed datasets.
* AWS Redshift - Used to create and store the data warehouse.
* Pandas - Used to process and transform datasets. If datasets were bigger, using Apache Spark would be better suited. 

## Architecture
<img align="left" src="https://github.com/amourikis/Data-Engineering-Capstone-Project/blob/main/Architecture.png" >

## Data Sources
To accomplish this study, we will be using the following datasets:

* **I94 Immigration Data**: This data comes from the US National Tourism and Trade Office and includes the contents of the i94 form on entry to the united states. A data dictionary is included in the workspace.
    * _countries.csv_ : table containing country codes used in the dataset, extracted from the data dictionary
    * _i94portCodes.csv_: table containing city codes used in the dataset, extracted from the data dictionary
  The dataset can be found [here.](https://travel.trade.gov/research/reports/i94/historical/2016.html)

* **World Temperature Data**: This dataset comes from Kaggle and includes the temperatures of various cities in the world fomr 1743 to 2013.
  The dataset can be found [here.](https://www.kaggle.com/berkeleyearth/climate-change-earth-surface-temperature-data)
* **U.S. City Demographic Data**: This data comes from OpenSoft. It contains information about the demographics of all US cities and census-designated places with a population greater or equal to 65,000 and comes from the US Census Bureau's 2015 American Community Survey.
  The dataset can be found [here.](https://public.opendatasoft.com/explore/dataset/us-cities-demographics/export/)
* **Airport Code Table**: This is a simple table of airport codes and corresponding cities.
  The dataset can be found [here.](https://datahub.io/core/airport-codes#data)

## Aggregations
In order to accomplish this, we will aggregate our data as follows:
* aggregate based on time (year, month, day, etc...) 
* aggregate data by cities and airports
* look at the impact of temperatures on the in and ouflux of travelers
* the impact on regional demographics

## Steps
The project follows the follow steps:
* Step 1: Scope the Project and Gather Data
* Step 2: Explore and Assess the Data
* Step 3: Define the Data Model
* Step 4: Run ETL to Model the Data
* Step 5: Complete Project Write Up

# Challenges
- Downloading and extrating 233 GB of twitter data from archive.org took forever.
	- Solution: Mount S3 to EC2 using S3fs fuse file system. Now S3 acts like a local directory to EC2 and you can dowload any amount of data directly to S3 from EC2. The configuration of EC2 can be as low as 1GB RAM.

- Preprocessing 233 GB JSON files
    - There are 36 columns in each JSON files, of which only 

- Updating the data regularly
	- Airflow DAG can be triggered everyday to take into account the newly updated data.

- Make it available to 100+ people
	- The final Dash app can be deployed on EC2 or aws beanstalk(which uses EC2 in background) to share the app with anyone. Currently I am using EC2 instance directly to deploy it.

## Instructions
All the project details and analysis will be in the project notebook.
