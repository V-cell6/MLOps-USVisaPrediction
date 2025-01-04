# MLOps for US Visa Prediction

## Overview
This project focuses on building an end-to-end MLOps pipeline for predicting the status of US Visa applications. It integrates data preprocessing, exploratory data analysis (EDA), machine learning model development, and deployment-ready code into a cohesive framework. The workflow follows best practices in MLOps and ensures seamless integration of various components to deliver a robust solution.

## Dataset
The project utilizes the US Visa dataset from Kaggle:
[US Visa Dataset on Kaggle](https://www.kaggle.com/datasets/noro23/easyvisa-dataset?resource=download)

### Key Steps:
- **Exploratory Data Analysis (EDA):** Analyze data patterns and identify key insights.
- **Data Cleaning:** Handle missing values, outliers, and other data inconsistencies.
- **Feature Engineering:** Develop relevant features to improve model performance.
- **Model Training:** Train multiple machine learning algorithms to identify the best-fit model.
- **Model Evaluation:** Evaluate models using performance metrics to achieve maximum accuracy.

## Project Structure
The project structure is organized into three main sections:

### 1. **ML Framing**
   - **Data Input:** The dataset is read into Jupyter notebooks for EDA and data preprocessing.
   - **MongoDB Integration:** Data is loaded into MongoDB for storage and retrieval.
   - **Key Notebooks:**
     - `1_EDA_US_visa.ipynb`: Contains EDA and preprocessing steps.
     - `2_Feature_Engineering_and_Model_Training.ipynb`: Covers feature engineering and model training.

### 2. **Development Environment**
   - Code is developed using **VS Code** and version-controlled using **GitHub**.
   - **Folder Structure:**
     - `template.py`: Generates the complete folder structure.
     - `.dockerignore`, `.gitignore`, `Dockerfile`, `README.md`, `setup.py`: Supporting files for deployment.
     - `requirements.txt`: Lists the required Python libraries.
   - **YAML Files:**
     - `model.yaml`: Defines model configurations.
     - `schema.yaml`: Specifies data schema.

   #### Useful Commands:
   ```bash
   conda create -n visa python=3.8 -y
   conda activate visa
   pip install -r requirements.txt
   ```

### 3. **Deployable Code**
   The deployable code is structured into modular components:
   - **components:**
     - `data_ingestion.py`: Handles data collection and loading.
     - `data_validation.py`: Ensures data quality and consistency.
     - `data_transformation.py`: Performs feature engineering and data preparation.
     - `model_trainer.py`: Trains machine learning models.
     - `model_evaluation.py`: Evaluates model performance and metrics.
     - `model_pusher.py`: Deploys the trained model to production.
   - **configuration:** Configuration settings.
   - **constant:** Project constants.
   - **entity:**
     - `config_entity.py`: Defines configuration entities.
     - `artifact_entity.py`: Handles artifact management.
   - **logger:** Logging functionality.
   - **pipeline:**
     - `training_pipeline.py`: Orchestrates the training process.
     - `prediction_pipeline.py`: Handles predictions on new data.
   - **utils:** Utility functions for common tasks.

## AWS Deployment
The project supports deployment on AWS using GitHub Actions for CI/CD. Below are the key steps:

### AWS-CICD-Deployment-with-Github-Actions
1. **Login to AWS Console.**
2. **Create an IAM User for Deployment** with specific access:
   - **EC2 Access:** Virtual machine for hosting.
   - **ECR:** Elastic Container Registry to save your Docker image in AWS.

### Deployment Description
1. Build a Docker image of the source code.
2. Push the Docker image to ECR.
3. Launch an EC2 instance.
4. Pull the image from ECR in the EC2 instance.
5. Launch the Docker image in EC2.

### Policies for IAM User:
1. `AmazonEC2ContainerRegistryFullAccess`
2. `AmazonEC2FullAccess`

### Deployment Steps
1. **Create ECR Repository:**
   - Save the URI: `315865595366.dkr.ecr.us-east-1.amazonaws.com/visarepo`
2. **Create EC2 Instance:**
   - Use Ubuntu as the operating system.
3. **Install Docker on EC2 Instance:**
   ```bash
   sudo apt-get update -y
   sudo apt-get upgrade
   curl -fsSL https://get.docker.com -o get-docker.sh
   sudo sh get-docker.sh
   sudo usermod -aG docker ubuntu
   newgrp docker
   ```
4. **Configure EC2 as Self-Hosted Runner:**
   - Go to GitHub: `Settings > Actions > Runner > New Self-Hosted Runner`
   - Choose OS and run the commands provided by GitHub.
5. **Set Up GitHub Secrets:**
   - `AWS_ACCESS_KEY_ID`
   - `AWS_SECRET_ACCESS_KEY`
   - `AWS_DEFAULT_REGION`
   - `ECR_REPO`

## Installation
1. Clone the repository:
   ```bash
   git clone <repository_url>
   ```
2. Navigate to the project directory:
   ```bash
   cd mlops-us-visa-prediction
   ```
3. Create a virtual environment and install dependencies:
   ```bash
   conda create -n visa python=3.8 -y
   conda activate visa
   pip install -r requirements.txt
   ```

## Running the Project
1. Prepare the dataset and load it into MongoDB.
2. Execute the Jupyter notebooks for data preprocessing and model training.
3. Run the `training_pipeline.py` to train the model.
4. Use the `prediction_pipeline.py` to make predictions on new data.

## Future Work
- Implement continuous integration/continuous deployment (CI/CD) pipelines.
- Enhance model performance through hyperparameter tuning.
- Deploy the model using cloud services like AWS or Azure.

## License
This project is licensed under the MIT License. See the `LICENSE` file for more details.
