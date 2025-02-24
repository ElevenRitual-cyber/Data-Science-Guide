### **Accessors in Pandas**  
Accessors in Pandas (`.str`, `.dt`, `.cat`) are special properties that provide domain-specific methods for handling **string, datetime, and categorical** data in Pandas DataFrames and Series.

---

## **🔹 1. String Accessor (`.str`)**
- Used for **string operations** on columns with `dtype=object` (string).
- Works **element-wise** (i.e., applies methods to each value in the column).

### **Example: Using `.str` for String Operations**
```python
import pandas as pd

df = pd.DataFrame({'Name': ['Alice', 'BOB', 'Charlie']})

# Convert to lowercase
df['Name_lower'] = df['Name'].str.lower()

# Check if name starts with 'A'
df['Starts_with_A'] = df['Name'].str.startswith('A')

# Replace substring
df['Replaced'] = df['Name'].str.replace('BOB', 'Robert')

print(df)
```
🔹 **Common `.str` Methods:**  
- `.lower()`, `.upper()`, `.title()`
- `.strip()`, `.split()`, `.join()`
- `.replace()`, `.contains()`, `.startswith()`, `.endswith()`
- `.extract(r'(\d+)')` (Regex extraction)

---

## **🔹 2. Datetime Accessor (`.dt`)**
- Used for working with **datetime values** (`dtype='datetime64'`).
- Enables easy extraction of **date components** like year, month, day, etc.

### **Example: Using `.dt` for Date Extraction**
```python
df = pd.DataFrame({'Date': pd.to_datetime(['2023-01-01', '2024-05-15', '2025-08-20'])})

df['Year'] = df['Date'].dt.year
df['Month'] = df['Date'].dt.month
df['Weekday'] = df['Date'].dt.day_name()

print(df)
```
🔹 **Common `.dt` Methods:**  
- `.year`, `.month`, `.day`, `.hour`, `.minute`
- `.day_name()`, `.month_name()`
- `.weekday`, `.is_leap_year`

---

## **🔹 3. Categorical Accessor (`.cat`)**
- Used for **categorical columns** (`dtype='category'`).
- Provides methods to **rename categories, reorder them, or remove unused ones**.

### **Example: Using `.cat` for Categorical Operations**
```python
df = pd.DataFrame({'Category': pd.Categorical(['A', 'B', 'A', 'C', 'B'])})

# Rename categories
df['Category'] = df['Category'].cat.rename_categories({'A': 'Alpha', 'B': 'Beta'})

# Check the categories
print(df['Category'].cat.categories)
```
🔹 **Common `.cat` Methods:**  
- `.categories`, `.codes`
- `.rename_categories()`, `.remove_categories()`
- `.add_categories()`, `.reorder_categories()`

---

## **🚀 Summary Table of Accessors**
| Accessor  | Used For      | Example Methods |
|-----------|--------------|----------------|
| `.str`    | String Data  | `.lower()`, `.replace()`, `.split()`, `.contains()` |
| `.dt`     | Datetime Data | `.year`, `.month`, `.day_name()`, `.is_leap_year` |
| `.cat`    | Categorical Data | `.categories`, `.rename_categories()`, `.remove_unused_categories()` |
