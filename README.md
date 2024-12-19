# SQL_Data_Cleaning_Project
This project focuses on cleaning and standardizing the 2020 - 2024 Layoffs dataset (when COVID-19 was declared) sourced from Kaggle. The dataset contains details about company layoffs, including metrics like total layoffs, percentage laid off, and industry. The goal is to ensure data accuracy, consistency, and usability.

## Dataset Information
The dataset contains information on layoffs, including fields such as company name, location, industry, total layoffs, percentage of layoffs, dates, and funding details.

## Objectives
Remove duplicate entries.
Standardize data and correct inconsistencies.
Handle missing values effectively.
Remove unnecessary rows and columns.

## Project Steps
#### 1. Create a Staging Table
To preserve the original data and provide a workspace for cleaning, we:

Created a staging table layoffs_staging.

Inserted all data from the original layoffs table into layoffs_staging.
#### 2. Remove Duplicates
Using the ROW_NUMBER() function, duplicates were identified based on multiple columns (company, location, industry, date, etc.) and removed:

A temporary Common Table Expression (CTE) identified rows with duplicate information.

A new staging table layoffs_staging2 was created to store cleaned data without duplicates.
#### 3. Standardize Data
Several inconsistencies in the dataset were addressed:

Trim and Format Company Names: Removed extra spaces and ensured uniform naming conventions.

Industry Standardization: Standardized similar categories (e.g., "Crypto" and "Crypto startups" → "Crypto").

Country Formatting: Fixed inconsistent country names (e.g., "United States." → "United States").

Date Format: Converted string dates to proper DATE format using STR_TO_DATE() and modified the column data type.
#### 4. Handle Missing Values
To address missing or incomplete data:

Industry Completion: Filled missing industry values by cross-referencing rows with the same company and location.

Elimination of Null Rows: Removed rows where total_laid_off and percentage_laid_off were both null, as these were deemed uninformative.
#### 5. Remove Irrelevant Data
Unnecessary columns and rows were removed to simplify analysis:

The row_num column, used for duplicate removal, was dropped after its purpose was fulfilled.

Redundant or irrelevant rows were deleted based on null checks and logical exclusions.
## SQL Queries and Procedures
The project involves several SQL queries to achieve the objectives. Key SQL commands include:

ROW_NUMBER() for identifying duplicates.

TRIM() and UPDATE for standardization.

STR_TO_DATE() for date formatting.

CTEs and joins for missing value imputation.

### Dataset: Layoffs Dataset (Kaggle)
