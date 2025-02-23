## **🔹 What is Pandas?**  

**Pandas** is a **Python library** used for **data manipulation and analysis**. It provides **fast, flexible, and powerful** tools for handling structured data, such as tables, spreadsheets, and time series.

---

## **🔹 Why Use Pandas?**
- **Easy to use:** Works like Excel but with Python's flexibility.
- **Handles missing data:** Easily detects and fills missing values.
- **Supports multiple file formats:** Works with **CSV, Excel, SQL, JSON**, etc.
- **Efficient data operations:** Sorting, filtering, grouping, merging, etc.
- **Powerful indexing:** Makes searching and updating data faster.
- **Works with NumPy & Matplotlib:** Integrates well with other libraries.

---

## **🔹 Installing Pandas**
```bash
pip install pandas
```

---

## **🔹 Creating a DataFrame**
```python
import pandas as pd

# Creating a dictionary
data = {
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35],
    'City': ['New York', 'Los Angeles', 'Chicago']
}

# Converting to a DataFrame
df = pd.DataFrame(data)

print(df)
```
#### **Output**
```
     Name  Age         City
0   Alice   25     New York
1     Bob   30  Los Angeles
2  Charlie   35      Chicago
```

---

## **🔹 Basic Operations**
### **1️⃣ Viewing Data**
```python
df.head()   # First 5 rows
df.tail()   # Last 5 rows
df.info()   # Summary of DataFrame
df.describe()  # Statistics (mean, min, max, etc.)
```

### **2️⃣ Selecting Data**
```python
df['Age']    # Selects the 'Age' column
df.iloc[1]   # Selects the second row (index 1)
df.loc[0, 'Name']  # Selects a specific value (row 0, column 'Name')
```

### **3️⃣ Filtering Data**
```python
df[df['Age'] > 30]  # Shows rows where Age > 30
```

### **4️⃣ Adding & Removing Columns**
```python
df['Score'] = [85, 90, 95]  # Adding a new column
df.drop(columns='City', inplace=True)  # Removing a column
```

---

## **🔹 Reading & Writing Files**
```python
df.to_csv('data.csv', index=False)   # Save as CSV
df = pd.read_csv('data.csv')         # Load CSV file
df.to_excel('data.xlsx', index=False)  # Save as Excel
df = pd.read_excel('data.xlsx')      # Load Excel file
```

---

### **🔹 Summary**
| Feature | Pandas Function |
|---------|---------------|
| Create DataFrame | `pd.DataFrame()` |
| Read CSV | `pd.read_csv()` |
| Write CSV | `df.to_csv()` |
| View Data | `df.head()`, `df.tail()`, `df.info()` |
| Select Data | `df['column']`, `df.loc[]`, `df.iloc[]` |
| Filter Data | `df[df['column'] > value]` |
| Add Column | `df['new_col'] = values` |
| Drop Column | `df.drop(columns='col_name')` |

---

**Pandas is widely used in data science, machine learning, and analytics.** 🚀  
## **🔹 Basic Data Structures in Pandas**
Pandas has two main data structures:  

1️⃣ **Series** → One-dimensional (like a list or column in Excel)  
2️⃣ **DataFrame** → Two-dimensional (like a table or spreadsheet)  

---

## **1️⃣ Pandas Series (1D)**
A **Series** is a one-dimensional array that can store integers, floats, strings, or even objects. It has:
- **Data values**
- **An index (default: 0,1,2,..., but can be customized)**  

### **🔹 Creating a Pandas Series**
```python
import pandas as pd

# Creating a Series from a list
s = pd.Series([10, 20, 30, 40])
print(s)
```
#### **🔹 Output**
```
0    10
1    20
2    30
3    40
dtype: int64
```
- The **left column** represents the index.
- The **right column** represents the values.

### **🔹 Custom Index in Series**
```python
s = pd.Series([10, 20, 30, 40], index=['a', 'b', 'c', 'd'])
print(s)
```
#### **🔹 Output**
```
a    10
b    20
c    30
d    40
dtype: int64
```
---

## **2️⃣ Pandas DataFrame (2D)**
A **DataFrame** is a **two-dimensional table** with labeled rows and columns (like an Excel sheet or SQL table).

### **🔹 Creating a Pandas DataFrame**
```python
data = {
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35],
    'City': ['New York', 'Los Angeles', 'Chicago']
}

df = pd.DataFrame(data)
print(df)
```
#### **🔹 Output**
```
     Name  Age         City
0   Alice   25     New York
1     Bob   30  Los Angeles
2  Charlie   35      Chicago
```
---

## **🔹 Key Differences: Series vs DataFrame**
| Feature | Series | DataFrame |
|---------|--------|-----------|
| Dimension | 1D (single column) | 2D (rows & columns) |
| Structure | Similar to a list or column | Similar to an Excel table |
| Indexing | Uses a single index | Uses row & column indexing |
| Creation | `pd.Series([values])` | `pd.DataFrame({columns: values})` |

---

## **🔹 Summary**
- **Series** → 1D, like a single column.
- **DataFrame** → 2D, like a table.
- **Series is a building block for DataFrames** (each column in a DataFrame is a Series).  
