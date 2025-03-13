# DATA-CLEANING
## INTRODUCTION
&nbsp;&nbsp;&nbsp;&nbsp;Data cleaning is a fundamental step in the data analysis pipeline, ensuring that datasets are accurate, consistent, and ready for meaningful insights. Raw data often contains errors such as missing values, duplicates, inconsistencies, and outliers, which can lead to misleading conclusions if left unaddressed.  
This project focuses on demonstrating essential data cleaning techniques, applying best practices to real-world datasets. By working through key challenges such as handling missing data, removing duplicates, standardizing formats, and detecting outliers, we aim to improve data integrity and reliability.  
Using the provided datasets, we will explore and implement various cleaning methods to transform messy data into high-quality, structured information suitable for analysis and decision-making. 

## PROBLEM STATEMENT
1. Standardization
   - Standardize categorical variables by ensuring consistency in text casing, spelling, and data types.
   - Identify and correct inconsistencies in data formats (e.g., date formats, text casing, categorical values, numerical values).
3. Handling Missing Data
   - Detect and handle any missing values in the dataset.
4. Duplicate Handling
   - Identify and remove duplicate records if any to maintain data uniqueness.
5. Outlier Detection
   - Identify and address extreme values (outliers) that could distort analysis.
6. Final Data Quality Check
   - Validate that the cleaned dataset is accurate, complete, and consistent for analysis.
     
## SKILLS and CONCEPTS DEMONSTRATED

1. Handling missing values (imputation, removal, or other strategies).
2. Identifying and correcting data inconsistencies.
3. Removing duplicate records.
4. Standardizing data formats (text, dates, numerical values).
5. Data Transformation & Standardization
6. Outlier Detection & Treatment
7. Data Validation & Quality Checks

These skills are crucial and will help ensure the dataset is ready for accurate and insightful analysis.

## STAGES TO NAVIGATE IN THE DATA CLEANING PROJECT

The project comprises three critical stages essential for successful completion, which encompass:
1. Libraries and Data Importation
2. Data Assessment to Detect Data Quality Issues
3. Data Cleaning

## EXPLANATIONS
1. "Libraries and Data Importation":
   ---  
The first step in this project is to import the essential libraries required for data cleaning. In this case, the following libraries were used:
- Pandas (pd) for data importation 
- Numpy as (np) for numerical operations
- Datetime (dt) to handle date-related operations.
- Warnings to suppress unnecessary warnings during execution.
  
Once these libraries are imported, the next step is to load the dataset into the Jupyter Notebook environment as a DataFrame using the pd.read_csv() function. The dataset is assigned to a variable named df, allowing easy reference throughout the analysis.  

The snapshot below shows the code snippet used to import the necessary Python libraries for data cleaning and data importation:
LIBRARIES AND DATA IMPORTATION
:-----------------------------:
![](Saless/library.png)

2. "Data Assessment to Detect Data Quality Issues":
   --- 
Data assessment is a fundamental process in evaluating imported data to determine its suitability and cleanliness for its intended purpose. There are two primary methods of data assessment: visual assessment and programmatic assessment.  
&nbsp;&nbsp;&nbsp;First, after importing the data, we perform a visual assessment, where we examine the dataset by simply looking through it just as the name implies, this step does not require any code. we manually inspect the data to identify obvious issues such as wrong columns, wrong spellings, inconsistencies, or incorrect formatting.  
&nbsp;&nbsp;&nbsp;Next, we conduct a programmatic assessment to analyze the data in greater depth. This involves using code to detect potential issues, particularly when working with large datasets that contain numerous rows and columns. 

Several attributes and functions provided by the pandas library were employed for data assessment, including:

- df.shape: It is neccesary to know dimensions of the dataframe and the df.shape attribute helps us achieve that. It returns the dimensions of the DataFrame (number of rows and columns). In this case, the dataset contains 48,895 rows and 16 columns.
- df.columns: Since the major purpose of this project is to clean and maintain data integrity, it is important to display the columns of the dataset as it is going to be used throughtout the data cleaning processes. The df.columns Displays all the 16 columns in the dataframe 
- df['columns'].value_counts() – This line of code examines the 16 columns each to understand its unique categories, their frequencies and check for inconsistencies in observational units across all variables(columns). Here it was found that the name column
- df.info(): This provides a concise summary of the DataFrame, including data types and memory usage. The output revealed that the "last_review column" has an incorrect data type (object - instead of datetime), as highlighted with a yellow rectangle shape in the snapshot below.
- df.isnull().sum(): Counts the number of missing values in each column. The result indicates that the columns, name, host_name, last_review and review_per_month has missing values and they are 16, 21, 10052 and 10052 respectively.
- df.duplicated().sum(): Identifies duplicate rows in the DataFrame. The output confirms that no duplicate records are present.
 
Findings:  
Based on these assessments, the data quality issues detected are as follows:


These assessments and data quality issue detected are illustrated in the snapshots below. 
A    |B    
:---:|:---:
![](Saless/datass1.png)|![](Saless/datass2.png)

3. "Data Cleaning (Analysis of the Problem Statement)":
   ---
1, 
1, Missing Data and Data Integrity:
   -- 
   - Detect and handle any missing values in the dataset
   ---






