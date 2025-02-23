## **🔹 CRUD Operations in Pandas**
CRUD stands for **Create, Read, Update, and Delete**, which are the four basic operations performed on data.  
Pandas provides various functions to **manipulate DataFrames efficiently**.

---

## **1️⃣ Create (Insert Data)**
Creating a Pandas DataFrame can be done in multiple ways:

### **🔹 Create from a Dictionary**
```python
import pandas as pd

data = {
    "ID": [101, 102, 103],
    "Name": ["Alice", "Bob", "Charlie"],
    "Age": [25, 30, 35]
}

df = pd.DataFrame(data)
print(df)
```
#### **Output**
```
    ID     Name  Age
0  101   Alice   25
1  102     Bob   30
2  103  Charlie   35
```

### **🔹 Create from a List of Tuples**
```python
df = pd.DataFrame([(101, "Alice", 25), (102, "Bob", 30), (103, "Charlie", 35)],
                  columns=["ID", "Name", "Age"])
print(df)
```

---

## **2️⃣ Read (Access Data)**
You can read data from various sources such as CSV, Excel, SQL, etc.

### **🔹 Read from CSV**
```python
df = pd.read_csv("data.csv")  # Reads from a CSV file
```

### **🔹 Read a Specific Column**
```python
print(df["Name"])  # Returns a Series
```

### **🔹 Read a Specific Row using `.loc` and `.iloc`**
```python
print(df.loc[1])   # Select row with index 1 (label-based)
print(df.iloc[1])  # Select row with index position 1 (position-based)
```

### **🔹 Read Multiple Columns**
```python
print(df[["Name", "Age"]])
```

### **🔹 Read with Conditions (Filtering)**
```python
print(df[df["Age"] > 25])  # Get rows where Age > 25
```

---

## **3️⃣ Update (Modify Data)**
Updating data involves modifying specific values, columns, or rows.

### **🔹 Update a Single Value**
```python
df.loc[1, "Age"] = 32  # Update age of Bob to 32
print(df)
```

### **🔹 Update a Column**
```python
df["Age"] = df["Age"] + 1  # Increase all ages by 1
print(df)
```

### **🔹 Update Multiple Rows with a Condition**
```python
df.loc[df["Name"] == "Alice", "Age"] = 28
print(df)
```

### **🔹 Rename Columns**
```python
df.rename(columns={"Name": "Full Name"}, inplace=True)
print(df)
```

---

## **4️⃣ Delete (Remove Data)**
You can delete rows or columns using the `.drop()` method.

### **🔹 Delete a Column**
```python
df.drop(columns=["Age"], inplace=True)  # Removes the "Age" column
print(df)
```

### **🔹 Delete a Row**
```python
df.drop(index=1, inplace=True)  # Removes the row with index 1
print(df)
```

### **🔹 Delete Rows Based on Condition**
```python
df = df[df["Age"] > 25]  # Keeps only rows where Age > 25
print(df)
```

---

## **🔹 Summary Table of CRUD Operations**
| Operation | Pandas Method |
|-----------|--------------|
| **Create** | `pd.DataFrame()`, `df.insert()`, `df.append()` |
| **Read** | `df.loc[]`, `df.iloc[]`, `df[columns]`, `df.query()` |
| **Update** | `df.loc[] = value`, `df.replace()`, `df.rename()` |
| **Delete** | `df.drop()`, `df[df[condition]]` |

## **🔹 How `drop()` Works in Pandas?**
The `.drop()` function in Pandas is used to **remove rows or columns** from a DataFrame.  
It does not modify the original DataFrame unless `inplace=True` is specified.

---
## index indicate= rows where columns indicate columns

## **1️⃣ Dropping Columns**
To drop a column, use `axis=1` (since columns are along axis 1).

### **🔹 Example**
```python
import pandas as pd

df = pd.DataFrame({
    "ID": [101, 102, 103],
    "Name": ["Alice", "Bob", "Charlie"],
    "Age": [25, 30, 35]
})

# Drop the "Age" column
df_new = df.drop(columns=["Age"])
print(df_new)
```
#### **🔹 Output**
```
    ID     Name
0  101   Alice
1  102     Bob
2  103  Charlie
```
- The `"Age"` column is removed.
- The **original `df` remains unchanged** because `inplace=False` by default.

---

## **2️⃣ Dropping Rows**
To drop a row, use `axis=0` (since rows are along axis 0).

### **🔹 Example**
```python
df_new = df.drop(index=1)  # Drop the row at index 1
print(df_new)
```
#### **🔹 Output**
```
    ID     Name  Age
0  101   Alice   25
2  103  Charlie   35
```
- The row with index `1` (Bob) is removed.

---

## **3️⃣ Drop Multiple Rows or Columns**
You can pass a list of **rows or columns** to remove multiple at once.

### **🔹 Drop Multiple Columns**
```python
df_new = df.drop(columns=["ID", "Age"])
print(df_new)
```
#### **Output**
```
     Name
0   Alice
1     Bob
2  Charlie
```

### **🔹 Drop Multiple Rows**
```python
df_new = df.drop(index=[0, 2])
print(df_new)
```
#### **Output**
```
    ID Name  Age
1  102  Bob   30
```
- Only the row with index `1` remains.

---

## **4️⃣ Using `inplace=True`**
By default, `.drop()` **returns a new DataFrame** without modifying the original.  
If you want to modify the original DataFrame, use `inplace=True`.

### **🔹 Example**
```python
df.drop(columns=["Age"], inplace=True)
print(df)
```
- Now, `df` itself is updated, and `"Age"` is permanently removed.

---

## **5️⃣ Drop Rows Based on a Condition**
You can drop rows where a condition is met.

### **🔹 Example: Drop Rows Where Age < 30**
```python
df = df[df["Age"] >= 30]
print(df)
```
- Keeps only rows where `"Age"` is 30 or more.

---

## **🔹 Summary of `drop()`**
| Operation | Syntax |
|-----------|--------|
| Drop a single column | `df.drop(columns=["col_name"])` |
| Drop multiple columns | `df.drop(columns=["col1", "col2"])` |
| Drop a single row | `df.drop(index=row_index)` |
| Drop multiple rows | `df.drop(index=[row1, row2])` |
| Drop with modification | `df.drop(..., inplace=True)` |

