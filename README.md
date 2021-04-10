# Grab AI For S.E.A.

> 💡 AI For S.E.A. is an online challenge held by Grab to search for talented, innovative technologies across Southeast Asia. 
In this challenge, partcipants are tasked to select and tackle one problem statement (as shown in the image below) by leveraging data science and AI technologies.

![image](https://user-images.githubusercontent.com/38095617/114260887-1950ac80-9a0a-11eb-92d9-1c410fa40208.png)

# Solution For Safety Problem
![image](https://user-images.githubusercontent.com/38095617/114262041-51f38480-9a10-11eb-932a-648534224042.png)

## Exploratory Data Analysis
To start off the challenge, I began by performing exploratory data analysis to find out the class distribution as well as what constitutes safe or dangerous driving.

### Sample Dataset
- This is an example of the dataset provided

![image](https://user-images.githubusercontent.com/38095617/114261403-ed82f600-9a0c-11eb-8b4d-8aebadc49952.png)
   

### Binary Class Distribution
- A visualization of the class distribution of safe vs. unsafe driving (15007 safe vs. 4993 unsafe)

![image](https://user-images.githubusercontent.com/38095617/114261283-4d2cd180-9a0c-11eb-862c-25d299346d82.png)
  
  
### Analysis of Trips
- A visualization of what constitutes safe vs. unsafe driving based on the acceleration, gyro, speed, and change in speed.

![image](https://user-images.githubusercontent.com/38095617/114261185-d68fd400-9a0b-11eb-8db2-d91388bee65d.png)

## Feature Engineering
After analysing the data, I then performed feature engineering to create new features to supplement my machine learning algorithm later on.

Features Engineered include:
- Change in Bearing
- Change in Speed (Acceleration/Deceleration)
- Bucket Acceleration/Braking Values
- Bucket Speed values
- Magnitude of Acceleration/Gyro
- Change in Magnitude
- Total Distance Travelled in km
- No. of Danger Events Per Distance Travelled in km (Include Acceleration/Braking/Speeding Events)

Changes made to original features include:
- Convert Speed from m/s to km/h
- Convert Gyro from rad/s to degree/s

![image](https://user-images.githubusercontent.com/38095617/114261483-66824d80-9a0d-11eb-8a77-c6e49a2070b8.png)

## Data Preparation
Next, I prepared the data to be fed into the machine learning algorithm by converting categorical features using one-hot encoding and also aggregate the features grouped by the BookingID.

### One-Hot Encoding Categorical Features
- One-Hot encode categorical features to transform it into an appropriate format for the machine learning algorithm

![image](https://user-images.githubusercontent.com/38095617/114261641-499a4a00-9a0e-11eb-8d96-160fb55ac025.png)

### Data Aggregation
- Aggregate features to "expand the number of features"

![image](https://user-images.githubusercontent.com/38095617/114261664-6d5d9000-9a0e-11eb-9677-b9711e292190.png)

### Imputation & Train-Test-Split
- Before moving on to machine learning, I need to impute the missing values and split the dataset into training and test datasets.

![image](https://user-images.githubusercontent.com/38095617/114261759-f83e8a80-9a0e-11eb-9cde-8414438c0dcd.png)

## Machine Learning
In this challenge, I have opt to use XGBoost Classifier (a type of gradient boosted decision tree algorithm) to tackle the non-linearity in the data.

### Using Stratified K-Fold Cross Validation
- To ensure that the model performs consistently across the entire dataset, I implemented the k-fold cross validation and obtained the model's mean score on the various sets of data.

![image](https://user-images.githubusercontent.com/38095617/114261787-30de6400-9a0f-11eb-8ceb-76af925dae8f.png)

### Evaluation: Classification Report
- The model is observed to be poor in identifying dangerous driving behaviors. There are several factors that could have led to this issue:
  - Imbalanced Class Distribution
  - Insufficient Features to distinguish dangerous driving from safe driving

![image](https://user-images.githubusercontent.com/38095617/114261919-9cc0cc80-9a0f-11eb-850f-68677b351583.png)

### Feature Importance
- Based on the feature importance chart, speed and gyro magnitude seem to be the driving factors in determining safe vs. unsafe driving.

![image](https://user-images.githubusercontent.com/38095617/114261954-ced22e80-9a0f-11eb-898d-80d569d66295.png)


