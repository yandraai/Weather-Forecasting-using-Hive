Cloud_Homework3
===================
URL : 
------
- Find the homework here : 

Problem Statement
------------------

- Implementing a dynamic UI for Restful webservice hosting weather forecasting. Algorithm is not aimed for accuracy of the results.

Built
-------------------
- Rest API on flask framework deployed on Amazon Ec2-Linux Instance.
- The UI uses the ajax and jquery functionalities to make a API call and render the results dynamically.
- Forecast algorithm simply returns a random number in specified ranges.

How to Use 
-------------------
- Enter a data only of the format : YYYYMMDD. (At this stage of the project, I am not performing any exception handling).
- A chart displaying the weather forcast for the next 5 days including the day given.

I followed the below steps :

Step 1 - Launch EC2 instance and Install some required libraries
-------------------------------------------------------------------

- I followed the steps mentioned here: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EC2_GetStarted.html
- I chose Linux instance.
- Added a couple of security groups to enable traffic to my web application.

  ![image](../master/SG.PNG)
- Installation Commands
* sudo yum install flask
* sudo yum install flask_restplus

Step 2 - Added 5 endpoints to the Rest API 
-----------------------------------------------

| Endpoint      	| Method        | Input Format Example  		 				| Output Format Example  |
|-------------------|:-------------:|:---------------------------------------------:|:----------------------:|
| /historical/    	| GET			| NO INPUT               		 |[{"DATE": "20130101"}, {"DATE": "20130102"}, {"DATE": "20130103"}, {"DATE": "20130104"},...}] |
| /historical/date	| GET      		|   20130101                  			 |{"DATE": "20130101", "TMAX": "34.0", "TMIN": "26.0"} |
| /historical/ 		| POST      	|{"DATE": "20230101", "TMAX": "34.8", "TMIN": "26.8"} | {"DATE": "20230101"}	 |
|/historical/date 	| DELETE		|20230101												|	204 STATUS	|
|/forecast/date		| GET			| 20230101												|	[{"DATE": "20230101", "TMAX": "41.0", "TMIN": "19.0"}, {"DATE": "20230102", "TMAX": 4, "TMIN": 8}, {"DATE": "20230103", "TMAX": 42, "TMIN": 11}, {"DATE": "20230104", "TMAX": 90, "TMIN": 46}, {"DATE": "20230105", "TMAX": -20, "TMIN": 39}, {"DATE": "20230106", "TMAX": 1, "TMIN": 59}, {"DATE": "20230107", "TMAX": 65, "TMIN": 49}]						|
		

Step 3 - Created UI and linked it to the API
-----------------------------------------------	

- Please use the interactive1.html provided in the templates folder.
- Used the CanvasJS library of the ajax for the chart.
- If the date given is already present in the dailyweather.csv file which is the data on which the API has been built then the same data as that is present in the file is returned,
  else the algorithm for forecasting the values returns the values.

References 
-------------
- I referred this link : https://canvasjs.com/docs/charts/basics-of-creating-html5-chart/date-time-axis/ to get understand the REST API.