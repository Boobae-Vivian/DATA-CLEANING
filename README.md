# DATA-CLEANING
## INTRODUCTION
&nbsp;&nbsp;&nbsp;&nbsp;Data cleaning is a fundamental step data analysis, ensuring that datasets are accurate, consistent, and ready for meaningful insights. Raw data often contains errors such as missing values, duplicates, inconsistencies, and outliers, which can lead to misleading conclusions if left unaddressed.  
This project focuses on demonstrating essential data cleaning techniques, applying best practices to real-world datasets. By working through key challenges such as handling missing data, removing duplicates if any, standardizing formats, and detecting outliers, we aim to improve data integrity and reliability.  
Using the provided datasets, we will explore and implement various cleaning methods to transform messy data into high-quality, structured information suitable for analysis and decision-making. 

## PROBLEM STATEMENT
1. Standardization
   - Standardize column names by capitalizing all letters to ensure consistency in formatting
   - Rename columns with lengthy and unclear names
   - Correct inconsistencies in data formats.
2. Handling Missing Data
   - Handle missing values in the dataset.
3. Outlier Detection
   - Identify and address extreme values (outliers) that could distort analysis.
4. Final Data Quality Check
   - Validate that the cleaned dataset is accurate, complete, and consistent for analysis.
     
## SKILLS and CONCEPTS DEMONSTRATED

1. Handling missing values (imputation)
2. Identifying and correcting data inconsistencies
3. Standardizing data formats (text and dates)
4. Outlier Detection & Treatment
5. Data Validation & Quality Checks

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
  
   Once these libraries are imported, the next step is to load the dataset into the Jupyter Notebook environment as a DataFrame using the pd.read_csv() function. The 
   dataset is assigned to a variable named df, allowing easy reference throughout the analysis.  

   The snapshot below shows the code snippet used to import the necessary Python libraries for data cleaning and data importation:
   LIBRARIES AND DATA IMPORTATION
   :-----------------------------:
   ![](cleaned/libanddata.png)

2. "Data Assessment to Detect Data Quality Issues":
   --- 
   Data assessment is a fundamental process in evaluating imported data to determine its suitability and cleanliness for its intended purpose. There are two primary methods 
   of data assessment: visual assessment and programmatic assessment.  
   &nbsp;&nbsp;&nbsp;First, after importing the data, we perform a visual assessment, where we examine the dataset by simply looking through it just as the name implies, 
   this step does not require any code. we manually inspect the data to identify obvious issues such as wrong columns, wrong spellings, inconsistencies, or incorrect 
   formatting.  
   &nbsp;&nbsp;&nbsp;Next, we conduct a programmatic assessment to analyze the data in greater depth. This involves using code to detect potential issues, particularly when 
   working with large datasets that contain numerous rows and columns. 

   Several Pandas attributes and functions were used for data assessment to identify potential issues in the dataset. These include:

   - df.shape: Understanding the dimensions of the dataset is crucial. This attribute returns the number of rows and columns in the DataFrame. In this case, the dataset 
   contains 48,895 rows and 16 columns.

   - df.columns: Since data cleaning focuses on maintaining integrity, it is important to review the column names. This function displays all 16 column names. During the 
   assessment, it was observed that all column names started with lowercase letters, which would require standardization. Additionally, 'calculated_host_listings_count'
   column had a lengthy and unclear name that would be shortened for clarity and readability.

   - df['column_names'].value_counts(): This function helps analyze categorical variables by displaying unique values and their frequencies. It also aids in detecting 
   inconsistencies in observational units across variables. The pd.set_option('display.max_rows', None) was utilized to critically examine each columns.
   Key finding include:  
     - name column has text casing inconsistencies.
   
   - df.info(): This function dispays a concise summary of the DataFrame, including data types and memory usage. The output revealed that all data types are correct except 
     the 'last_review column' which has an incorrect data type (object - instead of datetime), as highlighted with a yellow rectangle shape in the snapshot below.
     
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
   - Missing Values: The name, host_name, last_review, and reviews_per_month columns contain missing values, with the last two having a significant amount (10,052 missing 
   values each).


   These assessments and data quality issue detected are illustrated in the snapshots below. 
   A    |B    |  C
   :---:|:---:|:----:
   ![](cleaned/das1.png)|![](cleaned/das2.png)|![](cleaned/das3.png)

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

   BEFORE           |    AFTER
   :---------------:|:--------------:
   ![](cleaned/scolumnb.png)|![](cleaned/scolumna.png)
  
    
     
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
   df.rename(columns={'CALCULATED_HOST_LISTINGS_COUNT': 'HOST_COUNT'}, inplace=True)
   ```
   The output of the above is shown in the snapshot below.
   
   BEFORE           |    AFTER
   :---------------:|:--------------:
   ![](longcolb.png)|![](longcola.png)
  

   - (c). Correct inconsistencies in data formats:
   ---
   - (i). Text Casing Issues:
   ---
   The 'NAME' column contains inconsistent text casing, which affects data uniformity.
   Using df['NAME'].value_counts(), it was observed that the column includes a mix of uppercase, lowercase, and improperly capitalized words. To correct this, we will 
   standardize text casing by converting each word to title case (capitalizing the first letter of every word).

   The code used for this transformation is:
   ```python
   df['NAME'] = df['NAME'].str.title()
   df['NAME'].value_counts()
   ```
   The screenshot below displays the applied code and its output.

    BEFORE           |    AFTER
   :---------------:|:--------------:
   ![](cleaned/textcaseb.png)|![](cleaned/textcasea.png)

   - (ii). Incorrect Data Type(last_review Column):
   ---
   During data assessment using df.info() and df['column'].value_counts() , it was observed that all columns had the correct data types except the 'last_review' column, 
   which was stored as an object instead of a datetime format.

   To correct this, the following code was used:
   ```python
   df['LAST_REVIEW'] = pd.to_datetime(df['LAST_REVIEW'])
   df['LAST_REVIEW'].dtype  # Check the new data type
   df.info()  # Confirm overall dataset structure
   ```
   The corrected data type ensures that 'last_review' can now be used effectively for date-based analysis.
   
   Below is the snapshot showing the applied code and results.

   BEFORE           |    AFTER
   :---------------:|:--------------:
   ![](cleaned/dtyeb.png))|![](cleaned/dtyea.png))

2. Handling Missing Data:
   --
   - (a). Handle missing values in the dataset:
   ---
   During data assessment using df.isnull().sum(), missing values were detected in four different columns:

   - name: 16 missing values
   - host_name: 21 missing values
   - last_review: 10,052 missing values
   - reviews_per_month: 10,052 missing values.
  
   To address these missing values:

   - Since name and host_name are text columns, missing values will be flagged as "Unspecified".
   - last_review is a date column, and dropping it is not ideal since the missing values has a significant number. Instead, missing values will be filled with the earliest 
   available date.
   - reviews_per_month is a numerical column, so missing values will be filled with the median value to maintain data consistency.
     
   These corrections will be applied using the .fillna() function. Afterward, df.isnull().sum() will be used to confirm that all missing values have been handled 
   successfully.

   Below is a snapshot of the code snippets used and the changes observed after handling the missing values.

   BEFORE           |    AFTER
   :---------------:|:--------------:
   ![](cleaned/missingb.png))|![](missinga.png))

   

4. Outlier Detection:
   --
   - (a). Identify and address extreme values (outliers) that could distort analysis:
   ---
   Outliers can distort analysis and impact the accuracy of insights derived from data. To detect and handle extreme values, we employed the Interquartile Range (IQR) 
   method, which helps identify outliers by determining values that fall outside the expected range.

   Step 1: Identifying Outliers
    
   First, we selected only the numerical columns using the select_dtypes() function and stored them in a variable called numerical_df. Next, We computed the IQR, defined 
   the outlier thresholds and finally identified extreme values.

   Upon running the analysis, the following columns were found to contain outliers:

   - HOST_ID → 1,526 outliers
   - LATITUDE → 425 outliers
   - LONGITUDE → 2,833 outliers
   - PRICE → 2,972 outliers
   - MINIMUM_NIGHTS → 6,607 outliers
   - NUMBER_OF_REVIEWS → 6,021 outliers
   - REVIEWS_PER_MONTH → 4,103 outliers
   - HOST_COUNT → 7,081 outliers
    
   Step 2: Addressing Outliers  
  
   To handle these extreme values, we applied the clip() function, which replaces values exceeding the lower and upper thresholds with the respective boundary values. This 
   ensures the dataset remains within a reasonable range without removing crucial data.

   Step 3: Verifying Changes
  
   After applying the correction, we re-ran the outlier detection code to confirm that the extreme values were properly handled. The updated distribution of values were 
   examined to ensure that no distortions remained.

   Below is a screenshot showing the code implementation and results.

    OUTLIERS          |  ADDRESSING OUTLIERS        
   :-----------------:|:--------------------:
   ![](cleaned/outb.png)|![](cleaned/outa.png)


6. Final Data Quality Check:
   --
   - (a). Validate that the cleaned dataset is accurate, complete, and consistent for analysis.
   ---
   Throughout the data cleaning process, we continuously validated that the transformations were successfully implemented. Below are the key checks performed to confirm the 
   effectiveness of each cleaning step:

   (i). Column Name Standardization & Renaming
      code used:
      ```python
      df.columns
      ``` 
      The code verified that all column names were successfully converted to uppercase and confirmed that the column 'calculated_host_listings_count' was successfully 
      renamed to 'HOST_COUNT'.
      
   (ii). Text Casing Standardization
      code used:
      ```python
      df['NAME'].value_counts()
      ```
      This ensured that text casing inconsistencies in the 'NAME' column were corrected and verified that all values in the 'NAME' column now follow the proper casing 
      format.
   
   (iii). Data Type Correction
     code used:  
     ```python
     df['LAST_REVIEW'].dtype  
     df.info()
     ```
     This confirmed that the 'LAST_REVIEW' column was successfully converted from object to datetime format and is now in the correct data type for date-related analysis.
   
   (iv). Handling Missing Values
      code used:
      ```python
      df.isnull().sum()
      ```
      This ensured that all missing values were properly handled as well as verified that all previously detected missing values have been appropriately addressed.
   
   (v). Outlier Treatment Validation: 
     The outlier detection method was re-run and was confirmed that extreme values were successfully handled.
   
   Below is screenshots of the cleaned dataset showcasing the final data quality check after cleaning.

   CLEANED DATASET
   :-----------------------------:
   ![](cleaned/result.png))

    BEFORE CLEANING          |  AFTER CLEANING       
   :-----------------:|:--------------------:
   ![](cleaned/resultb.png)|![](cleaned/result.png)

## RECOMMENDATIONS

To maintain high data quality in future data collection and storage processes, the following recommendations are suggested:

- Implement data validation at entry points by enforcing data type constraints
- Set mandatory fields to avoid missing values in critical columns
- Standardize data entry guidelines by using a consistent text format (e.g., title case for names)
- Automate data cleaning processes by using automated scripts to check for missing values and inconsistencies periodically
- Monitor and handle outliers regularly by establishing thresholds for numerical variables to detect extreme values.

By implementing these recommendations, future datasets will require minimal cleaning, ensuring efficiency and accuracy in data-driven decision-making.

## CONCLUSION

The data cleaning process was essential to improving the quality and reliability of the dataset. Initially, several issues were detected, including missing values, inconsistent text formatting, incorrect data type and outliers. However, through systematic cleaning steps such as renaming columns, handling missing data, standardizing text formats, converting data type and treating outliers, the dataset was refined to ensure accuracy, completeness, and consistency.

After cleaning, a final data quality check confirmed that all identified issues had been successfully addressed. The dataset is now well-structured, reliable, and ready for further analysis.


   









