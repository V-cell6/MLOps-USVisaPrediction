# MLOps-USVisaPrediction

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
     - `data_ingestion.py`
     - `data_validation.py`
     - `data_transformation.py`
     - `model_trainer.py`
     - `model_evaluation.py`
     - `model_pusher.py`
   - **configuration:** Configuration settings.
   - **constant:** Project constants.
   - **entity:**
     - `config_entity.py`
     - `artifact_entity.py`
   - **logger:** Logging functionality.
   - **pipeline:**
     - `training_pipeline.py`
     - `prediction_pipeline.py`
   - **utils:** Utility functions for common tasks.

## Technologies Used
- **Python**: Core programming language.
- **MongoDB**: Data storage.
- **Docker**: Containerization.
- **Jupyter Notebooks**: Data exploration and analysis.
- **VS Code**: Development environment.
- **GitHub**: Version control.
- **Machine Learning Libraries:** Scikit-learn, Pandas, NumPy, Matplotlib, Seaborn.

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
