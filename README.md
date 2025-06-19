# Diwali Sales Data Analysis
This project focuses on performing Exploratory Data Analysis (EDA) on a real-world Diwali Sales dataset using Python libraries such as Pandas, NumPy, Matplotlib, and Seaborn. The goal is to uncover key business insights that can help understand customer purchasing behavior, product trends, and revenue-driving segments during the festive Diwali season.

## Key Features:
Data Cleaning: Handling missing values, correcting data types, and removing duplicates

Univariate & Bivariate Analysis: Visualizing distributions and relationships between variables

Multivariate Analysis: Analyzing how customer age group, product category, and purchase amount interact

Outlier Detection: Using IQR to identify and handle outliers

Visualizations: Bar plots, count plots, for better decision-making

## Columns in the Dataset:
User_ID, Cust_name, Product_ID

Gender, Age Group, Age, Married_status

State, Zone, Occupation

Product_Category, Orders, Amount

## Business Questions Answered:
Which age group contributes most to revenue?

What are the top-performing product categories?

How does gender impact purchase behavior?

Which states and zones bring the highest sales?

## Technologies Used:
Python 🐍

Pandas & NumPy 📊

Seaborn & Matplotlib 📈

Jupyter Notebook 📘

## Data cleaning in Python

### 1. Import Required Libraries

import pandas as pd
import numpy as np

### 2. Load the Data

df = pd.read_csv("your_file.csv", encoding='unicode_escape')  # or use 'ISO-8859-1' if needed

### 3. Basic Inspection

df.head()        # View first 5 rows

df.tail()        # View last 5 rows

df.shape         # (rows, columns)

df.info()        # Data types & non-null count

df.describe()    # Summary stats for numerical columns

### 4. Handling Missing Data (NaN)

### Detect Missing Values:

df.isnull().sum()           # Count of missing values per column

df.isna().any()             # Boolean mask of columns with missing data

### Remove Rows/Columns:

df.dropna()                 # Drop all rows with any NaN

df.dropna(axis=1)          # Drop columns with any NaN

### Fill Missing Values:

df.fillna(0)                              # Replace NaNs with 0

df.fillna(method='ffill')                 # Forward fill

df.fillna(method='bfill')                 # Backward fill

df['col'].fillna(df['col'].mean())        # Fill with mean

df['col'].fillna(df['col'].mode()[0])     # Fill with mode

### 5. Handling Duplicates

### Check Duplicates:

df.duplicated().sum()

### Remove Duplicates:

df = df.drop_duplicates()

### 6. Fixing Data Types

df['Date'] = pd.to_datetime(df['Date'])         # Convert to datetime

df['Price'] = df['Price'].astype(float)         # Convert to float

df['ID'] = df['ID'].astype(str)                 # Convert to string

### 7. Renaming Columns

df.columns                                       # View column names

df.rename(columns={'OldName': 'NewName'}, inplace=True)

df.columns = df.columns.str.strip()             # Remove extra spaces

df.columns = df.columns.str.lower()             # Convert to lowercase

### 8. Filtering and Conditional Replacements

df = df[df['Age'] > 18]                          # Filter rows

df.loc[df['Gender'] == 'M', 'Gender'] = 'Male'   # Replace values conditionally

### 9. String Cleaning

df['Name'] = df['Name'].str.strip()              # Remove leading/trailing spaces

df['City'] = df['City'].str.lower()              # Lowercase all

df['City'] = df['City'].str.replace('[^a-zA-Z ]', '', regex=True)  # Remove special chars

### 10. Outlier Detection and Treatment

# Using IQR

Q1 = df['Amount'].quantile(0.25)

Q3 = df['Amount'].quantile(0.75)

IQR = Q3 - Q1

df = df[(df['Amount'] >= Q1 - 1.5 * IQR) & (df['Amount'] <= Q3 + 1.5 * IQR)]

### 11. Encoding Categorical Variables

pd.get_dummies(df, columns=['Gender'], drop_first=True)         # One-hot encoding

df['Gender'] = df['Gender'].map({'Male': 1, 'Female': 0})       # Label encoding

### 12. Saving the Cleaned Data

df.to_csv("cleaned_data.csv", index=False)

## Project Outcome:

The analysis helps identify target customer segments, high-performing regions, and popular product categories, allowing businesses to optimize their marketing strategy during festival seasons like Diwali.
