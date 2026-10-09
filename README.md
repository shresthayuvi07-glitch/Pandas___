# 🐼 Pandas Learning & Practice

Welcome to my **Pandas Learning Repository**!
This repository contains my notes, examples, exercises, and practice projects while learning **Pandas in Python** for data analysis.

---

## 📌 About Pandas

**Pandas** is a powerful Python library used for:

* 📊 Data analysis
* 🧹 Data cleaning
* 🔍 Data exploration
* 📑 Working with CSV and Excel files
* 🔄 Data transformation
* 📈 Preparing data for visualization
* 🗃️ Working with structured datasets

The two main Pandas data structures are:

* **Series** → One-dimensional data
* **DataFrame** → Two-dimensional tabular data

---

## 🛠️ Installation

Install Pandas using pip:

```bash
pip install pandas
```

Import Pandas:

```python
import pandas as pd
```

---

## 📚 Topics Covered

### 1. Pandas Basics

* Importing Pandas
* Creating a Series
* Creating a DataFrame
* Checking DataFrame shape
* Checking columns
* Checking data types
* Viewing the first and last rows

```python
import pandas as pd

df = pd.read_csv("dataset.csv")

print(df.head())
print(df.shape)
print(df.columns)
print(df.dtypes)
```

---

### 2. Reading Data

Working with different file formats:

```python
df = pd.read_csv("dataset.csv")
```

Other commonly used functions:

```python
pd.read_excel("data.xlsx")
pd.read_json("data.json")
```

---

### 3. Exploring Data

Useful functions for understanding a dataset:

```python
df.head()
df.tail()
df.info()
df.describe()
df.shape
df.columns
df.dtypes
```

For categorical/object columns:

```python
df.describe(include="object")
```

---

### 4. Selecting Columns

Select one column:

```python
df["title"]
```

Select multiple columns:

```python
df[["title", "type", "country"]]
```

---

### 5. Selecting Rows with `.loc`

Select a specific row:

```python
df.loc[0]
```

Select multiple rows:

```python
df.loc[0:5]
```

Select specific rows and columns:

```python
df.loc[0:5, ["title", "type"]]
```

---

### 6. Filtering Data

Basic condition:

```python
df[df["release_year"] > 2015]
```

Multiple conditions using **AND (`&`)**:

```python
df[(df["release_year"] > 2015) & (df["type"] == "Movie")]
```

Multiple conditions using **OR (`|`)**:

```python
df[(df["type"] == "Movie") | (df["type"] == "TV Show")]
```

> Remember: Pandas uses `&` and `|` for combining conditions.

---

### 7. Missing Values

Check missing values:

```python
df.isnull().sum()
```

Check non-missing values:

```python
df.notnull().sum()
```

Find the column with the most missing values:

```python
df.isnull().sum().idxmax()
```

Replace missing values:

```python
df["rating"] = df["rating"].fillna("UNRATED")
```

---

### 8. Unique Values

Find unique values:

```python
df["rating"].unique()
```

Count unique values:

```python
df["rating"].nunique()
```

Count each value:

```python
df["rating"].value_counts()
```

---

### 9. Sorting Data

Sort by one column:

```python
df.sort_values("release_year")
```

Descending order:

```python
df.sort_values("release_year", ascending=False)
```

Sort by multiple columns:

```python
df.sort_values(
    ["release_year", "title"],
    ascending=[False, True]
)
```

---

### 10. Adding Columns

Create a new column:

```python
df["age_years"] = 2026 - df["release_year"]
```

Create a fixed-value column:

```python
df["platform"] = "Netflix"
```

---

### 11. Renaming Columns

Rename a column:

```python
df = df.rename(columns={
    "listed_in": "genres"
})
```

---

### 12. Updating Data with `.loc`

Update a specific value:

```python
df.loc[0, "title"] = "My Favourite Show"
```

Update multiple rows based on a condition:

```python
df.loc[df["rating"].isnull(), "rating"] = "UNRATED"
```

---

### 13. String Operations

Check whether a column contains specific text:

```python
df["country"].str.contains("India", na=False)
```

Convert text to uppercase:

```python
df["title"].str.upper()
```

Remove extra spaces:

```python
df["title"].str.strip()
```

Find string length:

```python
df["title"].str.len()
```

---

### 14. Date and Time

Convert a column to datetime:

```python
df["date_added"] = pd.to_datetime(df["date_added"])
```

Extract year:

```python
df["year_added"] = df["date_added"].dt.year
```

Extract month:

```python
df["month_added"] = df["date_added"].dt.month
```

---

### 15. GroupBy

Count values by category:

```python
df.groupby("type").size()
```

Calculate average:

```python
df.groupby("type")["age_years"].mean()
```

Multiple aggregations:

```python
df.groupby("type")["release_year"].agg(
    ["min", "max", "mean"]
)
```

---

### 16. Duplicates

Check duplicate rows:

```python
df.duplicated().sum()
```

Find duplicate titles:

```python
df[df["title"].duplicated()]
```

Remove duplicate rows:

```python
df = df.drop_duplicates()
```

---

### 17. `value_counts()`

Count categories:

```python
df["type"].value_counts()
```

Calculate percentages:

```python
df["type"].value_counts(normalize=True) * 100
```

---

### 18. Working with `.shape`

Number of rows and columns:

```python
df.shape
```

Number of rows:

```python
df.shape[0]
```

Number of columns:

```python
df.shape[1]
```

---

### 19. Data Types

Check all data types:

```python
df.dtypes
```

Convert a column:

```python
df["release_year"] = df["release_year"].astype("int32")
```

---

### 20. Cross Tabulation

Create a cross-tabulation:

```python
pd.crosstab(
    df["Sex"],
    df["Survived"]
)
```

---

## 📂 Repository Structure

```text
Pandas/
│
├── README.md
│
├── datasets/
│   └── dataset.csv
│
├── basics/
│   ├── series.py
│   ├── dataframe.py
│   └── data_exploration.py
│
├── filtering/
│   ├── conditions.py
│   └── loc.py
│
├── cleaning/
│   ├── missing_values.py
│   ├── duplicates.py
│   └── data_types.py
│
├── groupby/
│   └── groupby_practice.py
│
└── projects/
    └── data_analysis.py
```

---

## 📊 Practice Dataset

I am using datasets to practice:

* Data selection
* Filtering
* Missing-value handling
* Sorting
* Grouping
* String operations
* Date manipulation
* Data cleaning
* Aggregation
* Data analysis

---

## 🎯 Learning Goals

* [x] Learn Pandas basics
* [x] Create Series and DataFrames
* [x] Load datasets
* [x] Explore datasets
* [x] Select rows and columns
* [x] Filter data
* [x] Work with missing values
* [x] Remove duplicates
* [x] Sort data
* [x] Use `groupby()`
* [x] Use `value_counts()`
* [x] Work with strings
* [x] Work with dates
* [x] Create new columns
* [ ] Complete Pandas projects
* [ ] Advanced data analysis

---

## 🧰 Tools & Technologies

* 🐍 Python
* 🐼 Pandas
* 📓 Jupyter Notebook
* ☁️ Google Colab
* 💻 VS Code
* 🔗 Git & GitHub

---

## 📖 Useful Pandas Import

```python
import pandas as pd
```

Common commands:

```python
df.head()
df.tail()
df.info()
df.describe()
df.shape
df.columns
df.dtypes
df.isnull().sum()
df.value_counts()
df.sort_values()
df.groupby()
df.loc[]
df.drop_duplicates()
```

---

## 🚀 Future Learning

I plan to continue learning:

* Advanced Pandas
* NumPy
* Matplotlib
* Seaborn
* Exploratory Data Analysis (EDA)
* Data Cleaning
* Data Visualization
* Real-world Data Analysis Projects
* SQL + Pandas
* Python Data Analysis

---

## 👨‍💻 Author

**Yubaraj Shrestha**

Learning Python, Pandas, Data Analysis, and Data Visualization.

---

⭐ If you find this repository useful, feel free to **star the repository**!
