# MLOPS-US-Visa-Approval-Prediction

This repository implements a Machine Learning Operations (MLOps) pipeline for a US visa prediction application. The application using machine learning model to predict visa approval/rejection decisions based on various parameters. This project demonstrates the integration of key MLOps practices to automate the machine learning lifecycle, ensuring efficient deployment, monitoring, and maintenance.


## Key Technologies:

### Machine Learning Model: (KNeighborsClassifier, RandomForestClassifier) trained to predict visa approvals/rejections.
### MongoDB: NoSQL database to store and manage database 
### MLOps Pipeline: Data ingestion, Data Validation, Model training, model deployement are various pipeline used for effective project implementation. 
### Docker: Containerization for packaging the application and its dependencies, ensuring consistent execution across environments.
### AWS EC2: Cloud-based deployment platform for hosting the application in a scalable and cost-effective manner.
### GitHub Actions: Continuous Integration and Continuous Delivery (CI/CD) tool for automating the build, testing, and deployment of the application on AWS EC2 upon code changes.


## Project Structure:

data/: Contains the training and testing datasets.
models/: Houses the trained Random Forest model and any related files.
src/: Includes the Python code for data preprocessing, model training, and prediction.
docker/: Contains the Dockerfile and associated configuration files.
ci/: Defines the GitHub Actions workflows for automation.
README.md: This file (you're reading it now!).

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

    
