# Data-Cleaning-Project-






# 📊 MySQL Data Cleaning Project

## 📌 Overview
This project demonstrates data cleaning on a **Layoffs 2022 dataset** from Kaggle.  
The goal was to prepare the raw data for analysis by removing duplicates, standardizing fields, handling missing values, and cleaning up inconsistent entries.

## 🛠️ Dataset
Source: [Kaggle - Layoffs 2022](https://www.kaggle.com/datasets/swaptr/layoffs-2022)  
Imported into MySQL under the database `world_layoffs`.

## 🚀 Steps Performed
1. **Created a Staging Table**  
   - Copied the raw data into a staging table (`layoffs_staging`) to keep the original safe.  

2. **Removed Duplicates**  
   - Used `ROW_NUMBER()` with `PARTITION BY` to identify duplicate rows.  
   - Deleted rows where the duplicate flag (`row_num > 1`).  

3. **Standardized Data**  
   - Converted blank `industry` values to `NULL`.  
   - Populated missing `industry` values using other rows from the same company.  
   - Standardized inconsistent values like `CryptoCurrency` → `Crypto`.  
   - Cleaned `country` values by removing trailing periods (e.g., `United States.` → `United States`).  
   - Converted `date` strings to proper `DATE` format using `STR_TO_DATE`.

4. **Handled Null Values**  
   - Left natural nulls in fields like `total_laid_off` and `funds_raised_millions` for accurate EDA later.

5. **Removed Irrelevant Data**  
   - Deleted rows where both `total_laid_off` and `percentage_laid_off` were `NULL`.  
   - Dropped the helper column (`row_num`) after use.

## 📂 Repository Structure
