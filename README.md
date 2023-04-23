# Project #2: Extract, Transform, and Load


![.jpg](README_Files/dataset-cover.png)


## Contents

* [Project Proposal](#project-proposal)
* [Aims of the Project](#aims-of-the-project)
* [Sources of Data](#sources-of-the-data)
* [Required Setup](#required-setup) 
* [Data Transformation](#data-transformation)
* [Data Loading](#data-loading)
* [Collaborators](#collaborators)


## <a id="Project-header"></a>Project Proposal
We decided to look at two datasets for YouTube viewing statistics in the UK with a view for creating and cleaning two tables to make a database ready for usage in PostGres. The Dataset we chose contained the top trending videos on the platform in Great Britain. The csv contained all the data for the videos and the JSON contained a reference to the category ID in the CSV file that could be used to categorise the data by video type.


## <a id="Aim-header"></a>Aims of the Project


Our Aim is to demonstrate how we can select a csv/json file, load the files into Jupyter Notebook to clean and prepare the data and to import into PgAdmin to create a competent Database. It is being created with the intention of analysing the popularity of videos to discover if there is a pattern on what makes a video trend. We will look at cleaning the data and including fields necessary for future analysis into what makes the top trending videos so popular.


## <a id="Sources-header"></a>Sources of the Data

We used a CSV and JSON file from Kaggle linked below. We also have a copy of the raw data in the resources/datasource folder in this repository.

https://www.kaggle.com/datasets/datasnaek/youtube-new


## <a id="Required-header"></a>Required Setup

To run the notebook.ipynb file you will need to install the following packages/dependencies:
* SQLAlchemy `pip install SQLAlchemy`
* Psycopg2 `pip install psycopg2`


To connect to the PostgreSQL database you will need to add your PgAdmin 4 username and password to a config.py file
The config.py file should be stored in your local repository folder.


## <a id="Data-header"></a>Data Transformation

Our first steps after inspecting the data were to load them into Jupyter Notebook, the first file we looked at was the JSON file. 
We imported the relevant libraries screenshotted below:

![image](https://user-images.githubusercontent.com/113051302/214705228-7360ac0d-8527-44b8-b281-523966823275.png)

We checked the categories and needed to clean the items column and extract the category_id and category_name fields into dictionaries to then convert into a DataFrame

<img width="959" alt="image" src="https://user-images.githubusercontent.com/113051302/214705937-16d91309-a7d3-48ad-bcb0-1cefd3c693fa.png">

Next was the extraction and transformation of the bigger csv file. We extracted the relevant columns that we felt were relevant to the Database and converted it into a DataFrame.

After inspecting the DataFrame we decided to drop the publish_time, trending_date, thumbnail_link and some of the other columns we rendered unimportant.

<img width="953" alt="image" src="https://user-images.githubusercontent.com/113051302/214706595-d19ba0b0-8540-48a4-922f-cc6bedead719.png">

Once this was completed we could assess to see if any columns needed further transformation ready for the database. We replaced the separator in the tags and title columns was a pipeline symbol so we replaced this with a comma.

<img width="964" alt="image" src="https://user-images.githubusercontent.com/113051302/214707021-79975abd-70b0-4bd7-be80-8a6c12fd0258.png">

Our next step was to check the keys existed in both dataframes to ensure connection. Whilst doing this we realised we needed to drop a category_id that was only present in the csv dataframe and therefore had no link to the JSON file and could not be categorised by category_id for our database. We dropped this and then moved on to check for duplication.

![image](https://user-images.githubusercontent.com/113051302/214937953-c00c7f43-8b17-4a3e-9a21-84049ae7820f.png)


Our final step was to drop the duplicates, check this step was successful and check the data types to see if further work was needed.


## <a id="Data-Loading"></a>Data Loading

To do the data load into the database, we imported the necessary components, including the password stored seperately. We did a final check on the tables before creation. 

![image](https://user-images.githubusercontent.com/113051302/214917474-cbbdde81-1908-42c8-aa18-66ca02d969d6.png)


We then created the tables and checked after creation

![image](https://user-images.githubusercontent.com/113051302/214917642-28d53041-2f9c-4064-98a8-4a350c537aef.png)

Finally we checked the data had been added by querying both tables

![image](https://user-images.githubusercontent.com/113051302/214918270-86d745ff-5eb6-40af-a2f3-fc5c45e7ad2f.png)


PgAdmin was then used to create a SQL table that included the above dataframe and a query was created to import the datasets into the respective tables as per below screenshots:


![image](https://user-images.githubusercontent.com/113051302/214937733-bd827a2c-c10a-4096-a85e-833718acd70a.png)



![image](https://user-images.githubusercontent.com/113051302/214937808-c3194fb7-f87c-4069-824b-6e2dca533e44.png)



![image](https://user-images.githubusercontent.com/113051302/214937837-0ee6dd0b-6d03-407b-b66f-6aff2019da18.png)





## <a id="Collaborators-header"></a>Collaborators


Stanley, Olive, Siobhan and Jade

