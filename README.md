Weather Forecasting using NCDC data
=====================================
Find the complete analysis in the pdf file provided.

What is being answered:
1. Average TMIN, TMAX for each year excluding abnormalities or missing data.
2. Maximum TMAX, Minimum TMIN for each year excluding abnormalities or missing data.
3. 5 hottest, 5 coldest weather stations for each year excluding abnormalities or missing data.
4. Hottest and coldest day and corresponding weather stations in the entire dataset.
6. Median TMIN, TMAX for each year and corresponding weather stations.
7. Median TMIN, TMAX for the entire dataset

Used : HiveQL from the AWS HUE Cluster Provided. For the 6 and 7 questions, I used Pyspark partly.

Why  Hive and not SPARK or other tools?

In this section, I am going to discuss about why I used HiveQL and not Spark or other tools. Firstly, 
the SQL like interface made it much easier to write queries specific to the task. Furthermore, it 
optimizes the query in the background which eventually get converted in to map-reduce jobs.
However, the speed is by far better than other tools like pySpark. Using pySpark initially the computation took almost 
20 min whereas the simple hive query gave results in 2 min. Hence, the computation speed is a boon 
to HiveQL. Finally, the aggregate functions like avg(), min() and max() are readily available in Hive 
QL which is further facilitated query language with the GROUP BY and ORDER BY statements. And 
also, it noteworthy to mention the dense_rank(), row_number() and percentile() functions which are  condensed the chunks of code in Spark into single line.



