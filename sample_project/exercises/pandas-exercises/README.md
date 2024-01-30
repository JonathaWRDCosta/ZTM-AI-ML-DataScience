# Pandas Practice - Summary and Solutions

This repository contains a Jupyter notebook with hands-on exercises for practicing various tasks with pandas, a powerful data manipulation library in Python. Solutions for the exercises are available in a separate notebook.

## Table of Contents
- [Pandas Practice - Summary and Solutions](#pandas-practice---summary-and-solutions)
  - [Table of Contents](#table-of-contents)
  - [1. Import Pandas and Create Series ](#1-import-pandas-and-create-series-)
  - [2. Import Car Sales Data ](#2-import-car-sales-data-)
  - [3. Explore DataFrame ](#3-explore-dataframe-)
  - [4. Data Types and Statistics ](#4-data-types-and-statistics-)
  - [5. Numeric Operations ](#5-numeric-operations-)
  - [6. Column Manipulation ](#6-column-manipulation-)
  - [7. Dealing with Missing Data (Continued) ](#7-dealing-with-missing-data-continued-)
  - [8. Add and Remove Columns ](#8-add-and-remove-columns-)
  - [9. Shuffling and Index Resetting ](#9-shuffling-and-index-resetting-)
  - [10. Lambda Functions and Column Renaming ](#10-lambda-functions-and-column-renaming-)
  - [11. Extensions and Further Learning ](#11-extensions-and-further-learning-)

## 1. Import Pandas and Create Series <a name="import-and-create-series"></a>
- `import pandas as pd`
- Create a series of colors: `colours = pd.Series(["White", "Black", "Orange"])`
- Create a series of car types: `cars = pd.Series(["BMW", "Volkswagen", "Porsche"])`
- Combine series into a DataFrame: `car_data = pd.DataFrame({"Car manufacturer": cars, "Colours": colours})`

## 2. Import Car Sales Data <a name="import-car-sales-data"></a>
- Import CSV data: `car_sales = pd.read_csv("data/car-sales.csv")`
- Export DataFrame to CSV: `car_sales.to_csv("data/exported_car_sales.csv", index=False)`

## 3. Explore DataFrame <a name="explore-dataframe"></a>
- Data types of DataFrame: `car_sales.dtypes`
- Descriptive statistics: `car_sales.describe()`
- DataFrame information: `car_sales.info()`
- View column names: `car_sales.columns`
- Length of DataFrame: `len(car_sales)`
- Display top and bottom rows: `car_sales.head()`, `car_sales.tail()`
- Select specific rows using `.loc` and `.iloc`
  
## 4. Data Types and Statistics <a name="data-types-and-statistics"></a>
- Create a series of numbers and find mean: `numbers.mean()`
- Create a series of numbers and find sum: `numbers.sum()`

## 5. Numeric Operations <a name="numeric-operations"></a>
- Extract specific column: `car_sales["Odometer (KM)"]`
- Find mean of a column: `car_sales["Odometer (KM)"].mean()`
- Select rows based on a condition: `car_sales[car_sales["Odometer (KM)"] > 100000]`
- Create a crosstab: `pd.crosstab(car_sales["Make"], car_sales["Doors"])`
- Group by and find average: `car_sales.groupby(["Make"]).mean(numeric_only=True)`

## 6. Column Manipulation <a name="column-manipulation"></a>
- Plotting with Matplotlib: `%matplotlib inline`, `car_sales["Odometer (KM)"].plot()`
- Create a histogram: `car_sales["Odometer (KM)"].hist()`
- Handle non-numeric column (`Price`): Remove punctuation, convert to integers

## 7. Dealing with Missing Data (Continued) <a name="dealing-with-missing-data"></a>
- Fill missing values using mean: `car_sales_missing["Odometer"].fillna(car_sales_missing["Odometer"].mean(), inplace=True)`
- Fill missing values using forward fill: `car_sales_missing["Doors"].fillna(method="ffill", inplace=True)`
- Drop rows with missing values: `car_sales_missing.dropna(inplace=True)`

## 8. Add and Remove Columns <a name="add-and-remove-columns"></a>
- Add a new column: `car_sales["Fuel per 100KM"] = car_sales["Fuel (L)"] / (car_sales["Odometer (KM)"] / 100)`
- Remove a column: `car_sales.drop("Number of Wheels", axis=1, inplace=True)`

## 9. Shuffling and Index Resetting <a name="shuffling-and-index-resetting"></a>
- Shuffle DataFrame rows: `car_sales_shuffled = car_sales.sample(frac=1)`
- Reset index: `car_sales_shuffled.reset_index(drop=True, inplace=True)`

## 10. Lambda Functions and Column Renaming <a name="lambda-functions-and-column-renaming"></a>
- Use lambda function to apply transformation: `car_sales["Odometer (Miles)"] = car_sales["Odometer (KM)"].apply(lambda x: x * 0.621371)`
- Rename columns: `car_sales.rename(columns={"Odometer (KM)": "Odometer (Miles)"}, inplace=True)`

## 11. Extensions and Further Learning <a name="extensions-and-further-learning"></a>
- Explore more pandas functions: [Pandas Documentation](https://pandas.pydata.org/pandas-docs/stable/index.html)
- Additional learning resources: [10 Minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/user_guide/10min.html), [Pandas Tutorials](https://github.com/pandas-dev/pandas/blob/main/doc/cheatsheet/Pandas_Cheat_Sheet.pdf)
