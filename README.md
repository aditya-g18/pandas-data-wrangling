# Customer Dataset Data Cleaning Project

## 📌 Project Overview

This project focuses on **cleaning and preprocessing a messy customer dataset using Python and Pandas**.
Real-world datasets often contain missing values, incorrect data types, duplicates, and inconsistent formats.
The goal of this project is to transform raw, messy data into a **clean and analysis-ready dataset**.

This notebook demonstrates practical **data cleaning techniques used in data analysis and data science workflows**.

---

# 🧰 Tools & Technologies Used

* **Python**
* **Pandas**
* **Jupyter Notebook**

---

# 📂 Dataset Description

The dataset contains customer-related information such as:

* Customer ID
* Name
* Email
* Age
* Signup Date
* Purchase Amount

However, the dataset initially contained several issues such as:

* Missing values
* Incorrect data types
* Duplicate records
* Inconsistent date formats
* Invalid or missing customer IDs

---

# ⚠️ Problems in the Raw Dataset

The dataset had multiple data quality issues including:

1. Missing values in columns like **email, age, purchase_amount**
2. Incorrect **date formats**
3. Missing or invalid **customer IDs**
4. Duplicate rows
5. Incorrect data types (strings instead of numeric values)

These issues needed to be resolved before performing any analysis.

---

# 🧹 Data Cleaning Steps Performed

## 1️⃣ Importing Required Library

```python
import pandas as pd
```

---

## 2️⃣ Loading the Dataset

The dataset was loaded using Pandas.

```python
df = pd.read_csv("messy_customer_dataset.csv")
```

---

## 3️⃣ Cleaning the Signup Date

The `signup_date` column contained inconsistent formats and missing values.

Actions performed:

* Converted column to **datetime format**
* Replaced missing dates with a default value.

```python
df["signup_date"] = pd.to_datetime(df["signup_date"], format="mixed", dayfirst=True)
```

---

## 4️⃣ Fixing Customer ID Issues

Customer IDs contained missing or incorrect values.

Steps taken:

* Converted IDs to numeric
* Used **interpolation** to fill missing values
* Converted the column back to integer

```python
df['customer_id'] = df['customer_id'].astype(float)
df['customer_id'] = df['customer_id'].interpolate()
df['customer_id'] = df['customer_id'].astype(int)
```

---

## 5️⃣ Handling Missing Email Values

Missing emails were replaced with a default placeholder.

```python
df['email'] = df['email'].fillna('provided@gmail.com')
```

---

## 6️⃣ Cleaning the Age Column

The age column contained missing values.

Steps performed:

* Filled missing ages using the **median**
* Corrected specific incorrect entries
* Converted the column to integer

```python
df['age'] = df['age'].fillna(df['age'].median())
df['age'] = df['age'].astype(int)
```

---

## 7️⃣ Cleaning Purchase Amount

Purchase values had missing entries.

Steps taken:

* Filled missing values using the **mean**
* Converted the column to integer
* Corrected incorrect entries

```python
df['purchase_amount'] = df['purchase_amount'].fillna(df['purchase_amount'].mean())
```

---

## 8️⃣ Removing Duplicate Records

Duplicate rows were removed to ensure data integrity.

```python
df.drop_duplicates(inplace=True)
```

---

## 9️⃣ Renaming Columns

For better clarity, the column name `name` was renamed.

```python
df.rename(columns={'name': 'first_name'}, inplace=True)
```

---

# 📊 Final Data Validation

After cleaning, several checks were performed:

### Dataset Shape

```python
df.shape
```

### Dataset Information

```python
df.info()
```

### Summary Statistics

```python
df.describe()
```

### Missing Values Check

```python
df.isnull().sum()
```

### Duplicate Check

```python
df.duplicated().sum()
```

---

# ✅ Final Result

After cleaning:

* Missing values were handled
* Data types were corrected
* Duplicate rows were removed
* Columns were renamed
* Dataset became **ready for analysis and visualization**

---

# 📈 Skills Demonstrated

This project demonstrates key **data analyst skills**, including:

* Data cleaning
* Handling missing values
* Data type conversion
* Duplicate removal
* Feature renaming
* Exploratory data checks

---

# 🚀 Future Improvements

Possible next steps:

* Perform **Exploratory Data Analysis (EDA)**
* Build **visualizations**
* Create **customer insights**
* Use the cleaned dataset for **machine learning models**

---

# 📎 Author

**Aditya Gupta**

Aspiring **Data Analyst / Data Scientist** learning practical data analysis using Python.

