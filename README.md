# DATA-CLEANING
## INTRODUCTION
&nbsp;&nbsp;&nbsp;&nbsp;Data cleaning is a fundamental step in the data analysis pipeline, ensuring that datasets are accurate, consistent, and ready for meaningful insights. Raw data often contains errors such as missing values, duplicates, inconsistencies, and outliers, which can lead to misleading conclusions if left unaddressed.  
This project focuses on demonstrating essential data cleaning techniques, applying best practices to real-world datasets. By working through key challenges such as handling missing data, removing duplicates, standardizing formats, and detecting outliers, we aim to improve data integrity and reliability.  
Using the provided datasets, we will explore and implement various cleaning methods to transform messy data into high-quality, structured information suitable for analysis and decision-making. 

## PROBLEM STATEMENT
1. Standardization
   - Standardize column names by capitalizing all letters to ensure consistency in formatting
   - Identify and rename columns with lengthy and unclear names
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

Several Pandas attributes and functions were used for data assessment to identify potential issues in the dataset. These include:

- df.shape: Understanding the dimensions of the dataset is crucial. This attribute returns the number of rows and columns in the DataFrame. In this case, the dataset contains 48,895 rows and 16 columns.

- df.columns: Since data cleaning focuses on maintaining integrity, it is important to review the column names. This function displays all 16 column names. During the assessment, it was observed that all column names started with lowercase letters, which would require standardization. Additionally, one column had a lengthy name that would be shortened for clarity and readability.

- df['column_name'].value_counts(): This function helps analyze categorical variables by displaying unique values and their frequencies. It also aids in detecting inconsistencies in observational units across variables. The pd.set_option('display.max_rows', None) was utilized to critically examine each columns.  
Key findings include:
  - name column has text casing inconsistencies.
  - last_review column is incorrectly stored as an object instead of a datetime format.
    
- df.isnull().sum(): Identifies missing values in each column. The following columns were found to have missing values:
  - name: 16 missing values
  - host_name: 21 missing values
  - last_review: 10,052 missing values
  - review_per_month: 10,052 missing values
    
- df.duplicated().sum(): Checks for duplicate records. The output confirms that no duplicate entries are present in the dataset.

Findings:
The data quality issues identified include:
- Column Name Formatting: All column names start with lowercase letters and needs capitalization
- A lengthy and unclear column name (Calculated_Host_Listing_Count) which needs to be shortened for clarity and readability.
- Text Casing Issues: The name column contains inconsistent text casing.
- Incorrect Data Type: The last_review column is stored as an object instead of a datetime format.
- Missing Values: The name, host_name, last_review, and review_per_month columns contain missing values, with the last two having a significant amount (10,052 missing values each).


These assessments and data quality issue detected are illustrated in the snapshots below. 
A    |B    
:---:|:---:
![](Saless/datass1.png)|![](Saless/datass2.png)

3. "Data Cleaning (Analysis of the Problem Statement)":
   ---
1, Standardization:
   --
   - (a). Standardize column names by capitalizing all letters to ensure consistency in formatting:
   ---
   Based on the assessment using df.columns, it was observed that all column names start with lowercase letters. To ensure consistency, there is a need to standardize the 
   column names by converting them to uppercase.

   To achieve this, we use the .upper() string method, which converts all characters in a string to uppercase. The syntax is as follows:
   ```python
   df.columns = df.columns.str.upper()  # Capitalize all column names
   df.columns  # Verify the transformation
   ```
   The code snippet used to achieve this and its output are shown in the snapshot below.

  
    
    
   
   - (b). Rename columns with lengthy and unclear names:
   ---
   During the assessment using df.columns, it was discovered that one column (calculated_host_listings_count) has a lengthy and unclear name. To improve the clarity and 
   readability, we will rename this column using the .rename() function.
   To do this, we will:
   - Use the columns argument in .rename() to create a dictionary mapping the old column name to the new one.
   - Set the inplace=True argument to ensure the change is applied directly to the dataset.
   - Verify the update by running df.columns.  
   The code to achieve this transformation is:
   ```python
   df.rename(columns={'calculated_host_listings_count': 'host_count'}, inplace=True)
   ```
   The output of the above is shown in the snapshot below.

   - (c). Identify and correct inconsistencies in data formats (e.g., date formats, text casing, categorical values, numerical values):







