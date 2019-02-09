# ETLProject
Anjali Vardhan
Henry Dinh
Extraction of Data
For our ETL project, we used two sources of data that were from Kaggle.com 
The data sources were titled Where it Pays to Attend College, which had three csv files:Degrees that pay back, salaries by college type, and salaries by region. However, for our project we only used the two csv files: salaries by college type and salaries by region. We also, used a JSON file regarding school information called schoolInfo.json regarding statastics surrounding 311 US universities. 
•	https://www.kaggle.com/wsj/college-salaries#salaries-by-region.csv
•	https://www.kaggle.com/wsj/college-salaries#salaries-by-college-type.csv
•	https://www.kaggle.com/theriley106/university-statistics

 Transformation of Data
In order to import the two csv files and the single json file, Jupyter notebook was used. The Pandas pd.read_csv and pd.read_json methods were used to import the source data files and convert them into pandas dataframes for further processing. Our original files: salaries-by-region csv file had 320 rows, the json file had 311 rows, and salaries-by-college-type had 269 rows. 

•	Cleaning of Data
_First, we read and drop the unnecessary columns keeping only school names, city, state, high school gpa, sat average in the schoolInfo.json
_Second, read the salaries-by-college-type.csv and salaries-by-region.csv file.
Third, we merge these data frames into one data frame named clean_df. We continue dropping the 
Unnecessary columns keeping only school name, state, high school GPA, region, starting median salary, Mid career 10th percentile salary , Mid career 25th percentile salary, Mid career 75th percentile salary, Mid career 90th percentile salary. 
Finnaly, we create data table named ETLProject and upload this table to mysql. s 
Pandas were used for the data cleaning process. 

One of the challenges for this project were the names of the universities were not standardized. Therefore, the parentheses and text within it. Changing the ‘-’ to ‘--’ and   ‘,’ to ‘--’.  We re-named existing columns by removing spaces in column names to be used in SQL database. The salary fields were in the string format, so it needed to be converted into floats. This would help the user to query the information easily and/or perform functions. So, we dropped $ signs and commas from the amounts. This would create floats as a result. 


Loading Database
The relational database of MYSQL was used for our project. And ORM SQLAlchemy for Python was used to communicate with the MYSQL database. 
1.1	ORM (SQLAlchemy)
SQLAlchemy is used as the ORM for Python to communicate with MYSQL database. Once the SQLAlchemy connection is established, the MYSQL tables can be populated using the ‘to_sql’ method and read using the ‘read_sql_query’ method. Examples are provided below.
Read from MySQL db table in Python:
state_list = pd.read_sql_query("Select * from state", con=engine)
Write to MySQL db table from Python:
merged.to_sql(name="college_list", con=engine, if_exists='append', index=False)

