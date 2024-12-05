# GokulAjith_MinorProject_UserRe-identification_from_StepData
This repository contains the Python codes of data preprocessing, RNN algorithms, average hamming distance, and datasets used to re-identify 32 users by incorporating architectural diagrams.
# OVERVIEW
The widespread use of fitness bands and smartwatches has led to the extensive collection of personal physiological data, integrating activity tracking into the daily lives of many individuals. While this data offers valuable health insights, it also raises significant privacy concerns. This project highlights that anonymization techniques relying solely on unique IDs are inadequate, as a person's time-series step data over a given period can reveal behavioral patterns and enable precise identification. To explore this, a binary list was generated from step data collected through the iPhone Health app, aggregated over two intervals—15 minutes and 1 hour—across two training durations of 33 months and 21 months. Each user was then evaluated individually on trained RNN models, demonstrating the feasibility of re-identification based on step data. This project focuses on showing that the minimal binary representation of users' step-data over a certain period is enough to re-identify the user and an attempt to analyze the feasibility of using a less complex average hamming code distance technique.

# Datasets

From the rawdata collected from the iPhone Health app, 4 datasets were created by using a specific data pre-processing methodology. The 4 datasets with specific characteristics are :
 1. **Dataset I**
    - **Interval:** 1 hour  
    - **Threshold:** No  

2. **Dataset II**
   - **Interval:** 15 minutes  
   - **Threshold:** No 

3. **Dataset III**
   - **Interval:** 1 hour  
   - **Threshold:** Yes

4. **Dataset IV**
   - **Interval:** 15 minutes  
   - **Threshold:** Yes
     
Each dataset contains all 32 users' complete available data. The threshold refers to a value to filter the step counts during the aggregation of available step data on the chosen respective intervals of 1hr and 15min. The threshold used here is 25. The original dataset for the 15-minute interval consists of 36,485 rows and 108 columns (36,485 × 108), whereas for the 1-hour interval, the number of columns is reduced to 35. The columns represent the year, month, and day of the week in one-hot encoded format, along with the binary step data for the respective interval (either 15 minutes or 1 hour) in a day. The rows correspond to each user's data on a particular day, and the label column indicates the user label, ranging from 0 to 31.
# Softwares/Libraries 

1. **Google Collab**
   The data pre-processing was done using Google Collab. The complete raw dataset was uploaded into Google Drive and used for preprocessing from fetching from the drive.The methodology of datapreprocessing is 
   shown in the block diagram.
   ![Data Preprocessing Architecture](https://github.com/AmritaCSN/GokulAjith_MinorProject_UserRe-identification_from_StepData/blob/main/Dataset%20Architecture%20Diagram.png)
   
2.**Kaggle**
   The three RNN algorithms utilized in this project are LSTM, GRU, and BI-LSTM. Hyperparameter tuning, training, and testing of the models were performed on Kaggle due to the following features it offers.
   GPU processors in Kaggle are essential for accelerating machine learning (ML) tasks, especially for computationally intensive workloads like deep learning. Kaggle is a prominent online platform for data 
   science and machine learning. It offers a community-driven environment where data professionals, researchers, and enthusiasts can collaborate, learn, and compete. Kaggle provides free access to GPUs (Graphics 
   Processing Units) within its cloud-based notebook environment. You can enable GPUs when running machine learning models, particularly for tasks requiring heavy matrix computations or large-scale data 
   processing. Typically, Kaggle offers NVIDIA GPUs, such as Tesla P100 or T4 GPUs. These are high-performance GPUs optimized for machine learning and deep learning tasks.
   The methodology used for user re-identification using RNN models is shown below:
    ![Methodology](https://github.com/AmritaCSN/GokulAjith_MinorProject_UserRe-identification_from_StepData/blob/main/Methodology.png)

3.**Keras Tuner**

  Keras Tuner is an open-source library designed to simplify and automate the process of hyperparameter tuning for deep learning models built with Keras and TensorFlow. It enables data scientists and machine 
  learning engineers to find the best combination of hyperparameters to improve model performance. The hyperparameters tuned here are:

   -**LSTM units:** min_value=32, max_value=256, step=2.This describes the number of neurons used for the training purposes
   
   -**Dropout Rate:** min_value=0.1, max_value=0.5, step=0.1. This is a regularization technique used in neural networks to prevent overfitting by randomly setting a fraction of input units to zero during training
   
   -**Learning Rate:**[1e-2, 1e-3, 1e-4].The learning rate controls the size of the steps taken by the optimizer to update the model's weights during training.
   
   These hyperparameter tuning step values can be changed based on the needs of the project and also depends on the number of trials to be perfomed for hyperparameter tuning.
   
   The other parameters used here are:
   
 - **Softmax Activation Function**: The softmax activation function is widely used in the output layer of neural networks for multiclass classification tasks.

- **Adam Optimizer**: The Adam optimizer is an adaptive learning rate optimization algorithm that combines the advantages of both **AdaGrad** and **RMSProp**, making it efficient for training deep learning models. In this implementation, the Adam optimizer is used with the learning rate tuned among values of 0.01, 0.001, and 0.0001 to identify the optimal step size for parameter updates during training.

- **SparseCategoricalCrossentropy**: This is a loss function commonly used for multi-class classification problems, where labels are provided as integers rather than one-hot encoded vectors.

   
   
4.**Openpyxl**

Openpyxl is implicitly used by the pandas library to handle Excel file operations. Here openpyxl is used for writing the DataFrame to an Excel file.

5.**Pivot**

Pivot is a function in the Pandas library. Used for straightforward reshaping. It is also used here for aggregation of duplicate entries by applying a function (e.g., mean, sum)  for the specified index and columns. It can also handle missing data.

6.**Scipy.Spatial.distance Library and Hamming Distance**

The **hamming** function is imported from the **scipy.spatial.distance** module. This function calculates the **Hamming distance** between two sequences (or arrays). The **Hamming distance** measures how many positions in two sequences (strings, arrays, etc.) are different. This function is part of **SciPy**, a scientific computing library in Python, which provides a wide range of mathematical functions, including distance calculations.


# References

1.https://keras.io/keras_tuner/
