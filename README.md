# MLOPS-US-Visa-Approval-Prediction

This repository implements a Machine Learning Operations (MLOps) pipeline for a US visa prediction application. The application using machine learning model to predict visa approval/rejection decisions based on various parameters. This project demonstrates the integration of key MLOps practices to automate the machine learning lifecycle, ensuring efficient deployment, monitoring, and maintenance.


## Key Technologies:

-  Machine Learning Model: (KNeighborsClassifier, RandomForestClassifier) trained to predict visa approvals/rejections.
-  MongoDB: NoSQL database to store and manage database 
-  MLOps Pipeline: Data ingestion, Data Validation, Model training, model deployement are various pipeline used for effective project implementation. 
-  Docker: Containerization for packaging the application and its dependencies, ensuring consistent execution across environments.
-  AWS EC2: Cloud-based deployment platform for hosting the application in a scalable and cost-effective manner.
- GitHub Actions: Continuous Integration and Continuous Delivery (CI/CD) tool for automating the build, testing, and deployment of the application on AWS EC2 upon code changes.


## Project Structure:

-  Constant/init.py file
	* it contains folder,file,variable names, port number and URL used inside project.
- Artifact folder constains output of each steps like data ingestion, transformation, validation, model trainer.
- Config folder is user defined, user manually write these files for performing specific operation.
-  logs/logger.py class used to write Log at runtime. 
- Static and template folder, files are used for flask implementation.
- Components/DataIngestion
		* it will fetch data from mongo db and USVisa.cv
	 	* It will split the Data into train.csv and test.csv files14:36 25-03-2024
-  Components/DataValidation 
		* it will read both train and test csv files and preform bellow operations.
		* firstly it will read schema file for validation purpose.
		* it checks the number of cloumns exists as per schema file.
		* it will verify numerical and categorial columns as well. 
		* it will create report.yaml file and write drift state in that file.
- Components/DataTransformation
		* if validation status is true then only transformation will start. 
		* it will read the test and train csv files. 
		* drop unneccesary columns mentioned in schema file 
		* add reduired cloumns. 
		* apply smoteen from normalization. 
		* finally convert dataframe into numpy array which are used for model training. 
		* "preprocessing.pkl" file is used for normalization of input data by user.
	
- Components/ModelTrainer
		* initiate_model_trainer method will read numpy array files for model training. 
		* ModelFactory with is a inbuit library from ineuron used to find best model which are written in model.yaml located in config folder. it will also perform hypertunnig of given models. 
		* It retruns f1, precision, recall score. 
		* best model details will be stored in "model.pkl" file inside trained_model folder, which we later copy into model folder.
-  Components/ModelEvaluation
		* it will read model which is already uploaded inside S3 bucket and perform model evaluation

## Git commands

```bash
git add .

git commit -m "Updated"

git push origin main
```

## How to run?

```bash
conda create -n visa python=3.8 -y
```

```bash
conda activate visa
```

```bash
pip install -r requirements.txt
```

```bash
Workflow

constant
config_entity
artifact_entity
conponent
pipeline
app.py / demo.py

```


### Export the  environment variable
```bash


export MONGODB_URL="mongodb+srv://<username>:<password>...."

export AWS_ACCESS_KEY_ID=<AWS_ACCESS_KEY_ID>

export AWS_SECRET_ACCESS_KEY=<AWS_SECRET_ACCESS_KEY>
```



# AWS-CICD-Deployment-with-Github-Actions

## 1. Login to AWS console.

## 2. Create IAM user for deployment

	#with specific access

	1. EC2 access : It is virtual machine

	2. ECR: Elastic Container registry to save your docker image in aws


	#Description: About the deployment

	1. Build docker image of the source code

	2. Push your docker image to ECR

	3. Launch Your EC2 

	4. Pull Your image from ECR in EC2

	5. Lauch your docker image in EC2

	#Policy:

	1. AmazonEC2ContainerRegistryFullAccess

	2. AmazonEC2FullAccess

	
## 3. Create ECR repo to store/save docker image
    - Save the URI: 136566696263.dkr.ecr.us-east-1.amazonaws.com/mlproject

	
## 4. Create EC2 machine (Ubuntu) 

## 5. Open EC2 and Install docker in EC2 Machine:
	
	
	#optinal

	sudo apt-get update -y

	sudo apt-get upgrade
	
	#required

	curl -fsSL https://get.docker.com -o get-docker.sh

	sudo sh get-docker.sh

	sudo usermod -aG docker ubuntu

	newgrp docker
	
# 6. Configure EC2 as self-hosted runner:
    setting>actions>runner>new self hosted runner> choose os> then run command one by one


# 7. Setup github secrets:

   - AWS_ACCESS_KEY_ID
   - AWS_SECRET_ACCESS_KEY
   - AWS_DEFAULT_REGION
   - ECR_REPO

    
