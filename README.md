After I did the data analysis and build ML models in  
https://github.com/WoradeeKongthong/medical_cost_regression,  

The RMSE of each model is as following :  
Multiple Linear Regression = 5486  
Polynomial Regression = 4610  
SVR = 4524  
Decision Tree = 4791  
Random Forest = 4082  
XGBRegression = 5301  
ANN = 4372  

I selected the Random Forest model to do the deployment.  
  
===============================================================  
Deployment details  
- create API with Flasgger and Swagger
- containerization with Docker  

===============================================================
# How to use the ML model
(after you clone or download the project  
and install the required libraries in requirements.txt)

## Flask application
1. in your terminal, cd to the project
2. start the flask api with command `$ python app.py`
3. use the api from the following options  
	3.1 prediction by input parameters  
		- goto http://0.0.0.0:8000/apidocs  
		- click GET section and Try it out  
		- age : type your age such as 35  
		- sex : type your gender, male or female  
		- bmi : type your bmi such as 18.36  
		- children : type number of children such as 3  
		- smoker : type yes or no  
		- region : northeast, northwest, southeast, or southwest  
		- click Execute button  
	3.2 prediction from csv file  
		- goto http://0.0.0.0:8000/apidocs  
		- click POST section and Try it out  
		- choose file  
		- click Execute button  
	
## Docker container
1. open your terminal, cd to the project
2. create docker image with command `$ docker build -t <projectName> .`
3. list docker images with command `$ docker images`
4. run the image with command `docker run -p 8000:8000 <projectName>`
5. use the api as the step 3 in Flas application section above
6. kill the process by opening new terminal and check the container id with the command `$docker ps` and `$ docker stop <CONTAINERID>`

## Pull my uploaded docker repository
1. pull the repository with command `$ docker pull woradee/medical_cost_flasgger:simple`
2. run the image with command `$ docker run -p 8000:8000 woradee/medical_cost_flasgger:simple`

